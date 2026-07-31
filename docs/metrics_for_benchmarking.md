# Benchmarking Metrics Tables

## PRNG vs QRNG

| Metric | Why (Note) | References |
|---|---|---|
| Throughput | Measures the number of random values generated per unit time, making it the primary performance metric for RNGs. | - |
| CPU Time | Measures the processor time required to generate random numbers, independent of waiting or I/O delays. | A Rational Foundation for Software Metrology (https://doi.org/10.6028/NIST.IR.8101) |
| Peak RAM | Quantifies the maximum memory consumed during execution, allowing fair comparison of implementation efficiency. | The ghost in the machine: don’t let it haunt your software performance measurements (http://dx.doi.org/10.6028/NIST.TN.1830) |
| Shannon Entropy, p-value | Quantifies the unpredictability and statistical randomness of the generated sequence. | - |
| NIST Suite | Evaluates whether the generated bitstream satisfies the statistical properties required for cryptographic randomness. | A Statistical Test Suite for Random and Pseudorandom Number Generators for Cryptographic Applications (https://doi.org/10.6028/NIST.SP.800-22r1a) |
| Dieharder Test | Provides an extensive battery of statistical tests to validate the quality of random number generators beyond NIST SP 800-22. | Dieharder: A Random Number Test Suite (https://webhome.phy.duke.edu/~rgb/General/dieharder.php) |

## Linear Search vs Grover Search

| Metric | Why (Note) | References |
|---|---|---|
| Query Complexity | Captures the theoretical computational complexity independent of hardware. It is the defining metric proving Grover's quadratic speedup from O(N) to O(sqrt(N)). | Grover’s quantum searching algorithm is optimal (https://doi.org/10.1103/PhysRevA.60.2746) |
| Success Probability | Measures the probability of finding the correct target after one execution, accounting for probabilistic quantum measurement. | - |
| CPU Usage | Measures processor utilization required by the implementation. | A Rational Foundation for Software Metrology (https://doi.org/10.6028/NIST.IR.8101) |
| Peak RAM | Measures the maximum memory consumed during execution. | The ghost in the machine: don’t let it haunt your software performance measurements (http://dx.doi.org/10.6028/NIST.TN.1830) |

## Simulated Annealing vs QAOA (MaxCut)

| Metric | Why (Note) | References |
|---|---|---|
| CPU Time | Measures the computational effort required to obtain a solution. | Performance of the Quantum Approximate Optimization Algorithm on the Maximum Cut Problem (https://doi.org/10.48550/arXiv.1811.08419) |
| Cut Value | Directly measures the quality of the MaxCut solution. | Performance of the Quantum Approximate Optimization Algorithm on the Maximum Cut Problem (https://doi.org/10.48550/arXiv.1811.08419) |
| Approximation Ratio | Normalizes solution quality with respect to the optimal solution, enabling fair comparison across graph instances. | Performance of the Quantum Approximate Optimization Algorithm on the Maximum Cut Problem (https://doi.org/10.48550/arXiv.1811.08419); Quantum Approximate Optimization Algorithm: Performance, Mechanism, and Implementation on Near-Term Devices (https://doi.org/10.1103/PhysRevX.10.021067) |
| Scalability | Evaluates how algorithm performance changes as the graph size increases. | Empirical performance bounds for quantum approximate optimization (https://www.doi.org/10.1007/s11128-021-03342-3) |
| Success Probability | Measures the likelihood of obtaining a high-quality solution over repeated executions. | Empirical performance bounds for quantum approximate optimization (https://www.doi.org/10.1007/s11128-021-03342-3); Benchmarking the Quantum Approximate Optimization Algorithm (https://doi.org/10.1007/s11128-020-02692-8) |
| Convergence Rate | Measures how quickly the optimization converges to a stable solution. | Benchmarking Metaheuristic-Integrated QAOA against Quantum Annealing (https://doi.org/10.48550/arXiv.2309.16796) |

## DH vs BB84

| Metric | Why (Note) | References |
|---|---|---|
| Wall Clock Time / Throughput | Measures the end-to-end speed of generating shared secret keys. | Post-Quantum Key Exchange for the Internet and the Open Quantum Safe Project (https://eprint.iacr.org/2016/1017); eBACS: ECRYPT Benchmarking of Cryptographic Systems (https://bench.cr.yp.to) |
| CPU Time / Utilization | Measures the processor resources consumed by protocol execution. | eBACS: ECRYPT Benchmarking of Cryptographic Systems (https://bench.cr.yp.to) |
| Peak RAM | Measures the maximum memory required during protocol execution. | The ghost in the machine: don’t let it haunt your software performance measurements (http://dx.doi.org/10.6028/NIST.TN.1830) |
| Randomness (Shannon Entropy, NIST, Dieharder) | Evaluates the statistical quality and unpredictability of the generated shared keys. | A Statistical Test Suite for Random and Pseudorandom Number Generators for Cryptographic Applications (https://doi.org/10.6028/NIST.SP.800-22r1a); Dieharder: A Random Number Test Suite (https://webhome.phy.duke.edu/~rgb/General/dieharder.php) |
| Quantum Bit Error Rate (QBER) | Measures the fraction of erroneous key bits and is a primary indicator of channel noise and eavesdropping. | The Security of Practical Quantum Key Distribution (https://doi.org/10.1103/RevModPhys.81.1301) |
| Secret Key Rate | Measures the rate of secure key generation after error correction and privacy amplification. | The Security of Practical Quantum Key Distribution (https://doi.org/10.1103/RevModPhys.81.1301) |
| Communication Overhead (Data - Bits) | Measures the total number of bits exchanged during protocol execution. | - |
| Communication Overhead (Time) | Measures the communication latency incurred during protocol execution. | - |
