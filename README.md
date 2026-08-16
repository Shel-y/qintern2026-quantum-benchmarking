![Qintern 2026 Badge](docs/assets/QIntern2026.jpeg)

# Benchmarking Quantum Algorithms in the Cloud: A Comparative Study of Classical vs. Simulated Quantum Approaches on AWS

Comparative benchmarking of classical vs. simulated quantum algorithms (RNG, Search, QAOA, BB84) on Amazon Braket — QIntern 2026.

### ALGORITHM PAIRS & INPUT RANGE

| Domain | Classical | Quantum | Input Range |
|---|---|---|---|
| Random Number Generation | MT19937 | QRNG | 3–4 bit-length values |
| Search | Linear Search | Grover's | 8, 16, 24, 32 elements |
| Optimization (MaxCut) | Simulated Annealing | QAOA | Graphs with 4, 6, 8, 10 vertices |
| Key Exchange | Diffie–Hellman | BB84 | 3 key-length values |

### METRICS

---

Initial Metrics

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

---
General metrics (all benchmarks)

1. **Runtime** — average over multiple runs. Classical: `time.perf_counter()`. Quantum: Braket task/job metadata + client-side timing.
2. **Quality of Solution** — correctness/optimality vs. expected result, averaged across trials where randomness is involved.
3. **Cloud Overhead** — `Total wall-clock time − Actual execution time`, using Braket task metadata (queue time, execution time) for quantum; AWS vs. local execution time for classical.
---

---
Specific metrics

| Domain | Metrics |
|---|---|
| RNG | Shannon entropy, NIST SP 800-22 Statistical Test Suite |
| Search | Success probability, scalability with database size |
| Optimization | Cut value, approximation ratio |
| Key Exchange | Successful key establishment, key generation rate, QBER (key error rate) |

---


## Quantum Simulator (LocalSimulator vs SV1)
| Algorithm | Input Size Range | Avg Execution Time (ms) | Avg Operations / Sec |
| :--- | :--- | ---: | ---: |
| **Diffie-Hellman** | 1,000 to 8,000 key bits | 826.16 | 21,236 key bits |
| **Linear Search** | N = 8 to 32 database size | 5.95 | ~3,325,443 elements |
| **PRNG (MT19937)** | 10k to 80k output bits | 2.18 | ~20,734,396 bits |
| **Max Cut Solver** | N = 4 to 10 nodes | 22.91 | ~340.67 nodes |

### CLASSICAL ALGORITHMS AVG PERFORMANCE 

| Algorithm | Input Size Range | Avg Execution Time (ms) | Avg Operations / Sec |
| :--- | :--- | ---: | ---: |
| **Diffie-Hellman** | 1,000 to 8,000 key bits | 826.16 | 21,236 key bits |
| **Linear Search** | N = 8 to 32 database size | 5.95 | ~3,325,443 elements |
| **PRNG (MT19937)** | 10k to 80k output bits | 2.18 | ~20,734,396 bits |
| **Max Cut Solver** | N = 4 to 10 nodes | 22.91 | ~340.67 nodes |

---

### QUANTUM ALGORITHMS AVG PERFORMANCE 

| Algorithm | Input Size Range | Avg Execution Time (ms) | Avg Operations / Sec |
| :--- | :--- | ---: | ---: |
| **BB84 QKD** | 1,000 to 8,000 qubits | 27,350.00 | ~130 qubits (~70.1 key bits) |
| **Grover Search** | N = 8 to 32 elements | 224.05 | 37,168.5 queries |
| **QRNG** | 10k to 80k output bits | 65.50 | ~527,029 bits |
| **QAOA** | N = 4 to 10 nodes, p = 1 to 3 | ~4,623ms | 440 shots |


## COMPARISON
### Diffie-Hellman vs BB84 QKD
| Algorithm | Input Size Range | Avg Key Generation Rate |
| :--- | :--- | ---: |
| **Diffie-Hellman** | 1,000 to 8,000 key bits | 21,236 key bits/sec |
| **BB84 QKD** | 1,000 to 8,000 qubits | ~130 qubits/sec |

### Linear Search vs Grover Search
| Algorithm | Input Size Range | Avg Success Probability |  
| :--- | :--- | ---: |
| **Linear Search** |  N = 8 to 32 database size | 0.0 |  
| **Grover Search** |  N = 8 to 32 array size | 0.97655 |  

## REPO LAYOUT

```text
docs/
├── assets/
│   └── QIntern2026.jpeg                                     
├── .env.example                                   # Environment variables examples
├── literature_review.md                           # Relevant literature aggregation
├── measurement_framework_consolidated.md          # Measurement framework across project roles 
├── metrics_for_benchmarking.md                    # Experiment metrics 
│
infrastructure/
├── README.md                                      # Description for the project's infrastructure
│
notebooks/                                         # .ipynb and .py src codes
├── classical/
│    │   ├── diffie_hellman/
│    │   ├── linear_search/
│    │   ├── max_cut_solver/
│    │   └── prng_mt19937/
│    │
│    │
│   quantum/       
│        ├── BB84 Comparison/
│        ├── QAOA Comparison/
│        ├── bb84/
│        ├── grover_search/
│        ├── qaoa/
│        └── qrng/
│
│
results                                          # Experiment results: JSONs, CSVs, Graphs
├── classical/
│    │   ├── diffie_hellman/
│    │   ├── linear_search/
│    │   ├── max_cut_solver/
│    │   └── prng_mt19937/
│    │
│    │
│   quantum/       
│        ├── bb84/
│        ├── grover_search/
│        ├── qaoa/
│        └── qrng/
│
├── GUIDE.md                                    # Reproducibility guide
├── README.md                                   # Main README              
└── requirements.txt                            # Dependencies to be installed for reproducing

```

## AUTHORS:

* Sultana, Shahreen
* Kapati, Kanish
* Ghadge, Aman
* Laroza. Anjelo
