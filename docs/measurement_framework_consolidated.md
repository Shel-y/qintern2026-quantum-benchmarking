# Measurement Framework — Consolidated (v1)
**Project:** Benchmarking Quantum Algorithms in the Cloud (qi26_26) | QIntern 2026
**Status:** Draft v1 — consolidating inputs from Cloud & Documentation, Quantum Computing, and Classical Computing leads. Pending Aman Ghadge's (Research & Literature Lead) contribution before finalizing.

---

## Overview

This framework has three layers, applied in order:

1. **Infrastructure Layer** — how experiments are deployed, tracked, and reproduced (Cloud & Documentation Lead).
2. **Simulator Validation Layer** — confirming the quantum simulator itself is trustworthy before any comparison is made (Quantum Computing Lead).
3. **Benchmarking Layer** — the actual classical vs. quantum comparison metrics (Classical Computing Lead).

No result from Layer 3 is valid unless Layer 2 has been passed first. Layer 1 underlies both.

---

## Layer 1 — Infrastructure & Reproducibility

**Owner:** Anjelo Jann Laroza — Cloud & Documentation Lead

**Stack:** GitHub + GitHub Actions (CI/CD for infra and paper pipeline), Terraform (reproducible infra), Boto3 (custom AWS scripting), Cloud9 (shared workspace), CloudWatch (monitoring), Matplotlib (automated visualization), Overleaf (paper pipeline).

**Metrics tracked:**
- CloudWatch CPU / Memory Utilization
- Braket Network & I/O Latency
- CI/CD Pipeline Velocity & Deployment Success Rate
- Artifact Traceability & Log Completeness
- AWS Free Tier Resource Consumption

**Purpose:** Ensures every experiment is reproducible, resource usage stays within budget, and results/artifacts are traceable back to the exact infra state that produced them.

---

## Layer 2 — Simulator Validation

**Owner:** Shahreen Sultana — Quantum Computing Lead

Before any classical vs. quantum comparison can be trusted, the simulator itself must be validated. These checks come **first**, in this order:

| Order | Metric | What it checks | Acceptance threshold |
|---|---|---|---|
| 1 | **Measurement Bias** | Simulator has no built-in 0/1 preference | p-value > 0.05 (chi-squared, Hadamard circuit, 10k+ shots) |
| 2 | **Circuit Fidelity** | Simulator reproduces expected output distribution | d-R² ≥ 0.95 |
| 3 | **Shot Noise Stability** | Minimum shots needed for stable results | CV < 0.05 across top 3 bitstrings, 3 consecutive shot levels |
| 4 | **LocalSimulator vs. SV1** | Do both simulators agree? | KS test, <5% distribution difference → else default to SV1 |
| 5 | **Circuit Depth vs. Fidelity** | Simulator's practical depth limit | Document depth where fidelity drops below 0.95 |
| 6 | **Gate Error Sensitivity** | Behavior under realistic NISQ noise (depolarizing, amplitude/phase damping, bit flip) | Test at 0.1%, 0.5%, 1.0% error rates |
| 7 | **Simulator-to-Hardware Gap** (forward-looking) | Fidelity gap vs. real QPU | Deferred to Week 5+, pending QPU access |

**Special case — BB84:** readout errors tested separately from gate errors (QBER is sensitive specifically to readout fidelity).

**Rule:** No benchmark result is reported as a valid classical-vs-quantum comparison unless Metrics 1–3 have passed for that specific circuit/benchmark.

**Logging schema:** every experiment run logs `experiment_id`, `benchmark_type`, `timestamp`, `simulator`, `circuit_params` (qubits, depth, shots, gates), `metrics` (fidelity, convergence, KS p-value, noise results, bias p-value), `environment` (SDK/Python version, instance type), and `notes`. Full JSON schema in Appendix A.

---

## Layer 3 — Classical vs. Quantum Benchmarking

**Owner:** Kanishka — Classical Computing Lead

Applies **only after Layer 2 validation passes** for the relevant benchmark.

### Algorithm pairs & input sizes

| Domain | Classical | Quantum | Input sizes |
|---|---|---|---|
| Random Number Generation | MT19937 | QRNG | 3–4 bit-length values |
| Search | Linear Search | Grover's | 8, 16, 24, 32 elements |
| Optimization (MaxCut) | Simulated Annealing | QAOA | Graphs with 4, 6, 8, 10 vertices |
| Key Exchange | Diffie–Hellman | BB84 | 3 key-length values |

### General metrics (all benchmarks)

1. **Runtime** — average over multiple runs. Classical: `time.perf_counter()`. Quantum: Braket task/job metadata + client-side timing.
2. **Quality of Solution** — correctness/optimality vs. expected result, averaged across trials where randomness is involved.
3. **Cloud Overhead** — `Total wall-clock time − Actual execution time`, using Braket task metadata (queue time, execution time) for quantum; AWS vs. local execution time for classical.

### Problem-specific metrics

| Domain | Metrics |
|---|---|
| RNG | Shannon entropy, NIST SP 800-22 Statistical Test Suite |
| Search | Success probability, scalability with database size |
| Optimization | Cut value, approximation ratio |
| Key Exchange | Successful key establishment, key generation rate, QBER (key error rate) |

> Note from Classical Computing Lead: problem-specific metrics are proposed but confidence is medium — open for team discussion on whether all are necessary or if some can be dropped/simplified.

---

## Fallback Protocol — When Layer 2 Validation Fails

If a benchmark fails to meet a Layer 2 threshold (e.g., fidelity stays below 0.95 at the circuit depth required for QAOA or Grover's), the team follows this decision order before escalating:

1. **Reduce problem size first.** Try the same benchmark at a smaller input size (fewer qubits/shallower circuit) where the threshold is met. Document both the passing smaller instance and the failing larger one — this is itself a finding, not just a workaround.
2. **Switch simulator.** If LocalSimulator fails but SV1 (or DM1/TN1) might handle it better, test there before giving up on the benchmark entirely.
3. **Increase shots.** If the failure is shot-noise related (not fidelity), check whether more shots resolves it within a reasonable time/cost budget.
4. **If none of the above resolves it:** the benchmark is reported as a **documented limitation**, not silently dropped. Include: what was tried, at what threshold it failed, and what this suggests about the simulator's practical limits. This becomes part of the paper's "Limitations and Future Work" section — a well-documented failure is a valid contribution.

**Nobody drops a benchmark or silently lowers a threshold without flagging it to the team first.**

---

## Decision Authority

Most technical decisions (simulator choice, threshold values, notebook structure) should be resolved by consensus among the 4 leads, since each owns their domain. However, to avoid getting stuck:

- If the relevant leads can't agree within **2–3 days** of raising the issue, **Joselyn (Mentor) makes the final call** based on the tradeoffs presented by each side.
- Any lead can escalate a blocking disagreement early — waiting until a deadline is close to raise it makes resolution harder for everyone.
- Decisions made this way are logged briefly in `docs/decisions_log.md` (one line: date, decision, reasoning) so the team doesn't revisit the same debate later in the project.

---

## Priority Implementation Order (6-week timeline)

| Week | Focus | Layer |
|---|---|---|
| Week 2 | Measurement Bias + Logging Schema setup | Layer 2 |
| Week 2–3 | Circuit Fidelity + Shot Noise Stability (per-benchmark baselines) | Layer 2 |
| Week 3 | LocalSimulator vs. SV1 decision | Layer 2 |
| Week 3–4 | First classical vs. quantum runs (RNG, Search) begin once Layer 2 passes | Layer 3 |
| Week 4 | Circuit Depth + Gate Error Sensitivity; Optimization & Cryptography benchmarks | Layer 2 + 3 |
| Week 5+ | Simulator-to-Hardware Gap (if QPU access granted); paper drafting | Layer 2 (fwd) / writing |
| Week 6 | Aggregation, cross-benchmark comparison, finalization | All |

---

## Appendix A — Logging Schema (JSON)

```json
{
  "experiment_id": "qi26_26_QRNG_001",
  "benchmark_type": "QRNG | Grover | QAOA | BB84",
  "timestamp": "ISO-8601",
  "simulator": "LocalSimulator | SV1 | TN1 | DM1",
  "circuit_params": {
    "qubits": "int",
    "depth": "int",
    "shots": "int",
    "gates": {"H": "int", "CNOT": "int", "other": "int"}
  },
  "metrics": {
    "circuit_fidelity_dR2": "float",
    "shot_noise_converged_at": "int",
    "cv_value": "float",
    "local_vs_sv1_ks_pvalue": "float",
    "gate_error_rate_tested": "float",
    "fidelity_under_noise": "float",
    "measurement_bias_pvalue": "float",
    "runtime_seconds": "float",
    "cloud_overhead_seconds": "float"
  },
  "environment": {
    "braket_sdk_version": "string",
    "python_version": "string",
    "instance_type": "string"
  },
  "notes": "string"
}
```

---

*Consolidated by: Joselyn Lagunas (Mentor) | Sources: Anjelo (Cloud & Documentation Lead), Shahreen Sultana (Quantum Computing Lead), Kanishka (Classical Computing Lead) | qi26_26 | QIntern 2026*
