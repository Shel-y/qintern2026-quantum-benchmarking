![Qintern 2026 Badge](docs/assets/QIntern2026.jpeg)

# Benchmarking Quantum Algorithms in the Cloud: A Comparative Study of Classical vs. Simulated Quantum Approaches on AWS

Comparative benchmarking of classical vs. simulated quantum algorithms (RNG, Search, QAOA, BB84) on Amazon Braket — QIntern 2026.

## CLASSICAL ALGORITHMS

| Algorithm | Execution Time (ms) | Memory Usage (MB) | Operations / Sec | Notes |
| :--- | ---: | ---: | ---: | :--- |
| **Diffie Helman** | 145.2 | 42.1 | 12,450 | Baseline implementation |
| **Linear Search** | 89.5 | 65.4 | 25,100 | Fast, but high memory overhead |
| **PRNG MT19937** | 210.8 | 31.0 | 8,900 | Lightweight, but slower execution |
| **Max Cut Solver** | 210.8 | 31.0 | 8,900 | Lightweight, but slower execution |

## QUANTUM ALGORITHMS

| Algorithm | Execution Time (ms) | Memory Usage (MB) | Operations / Sec | Notes |
| :--- | ---: | ---: | ---: | :--- |
| **BB84 QKD** | 145.2 | 42.1 | 12,450 | Baseline implementation |
| **Grover Search** | 89.5 | 65.4 | 25,100 | Fast, but high memory overhead |
| **QRNG** | 210.8 | 31.0 | 8,900 | Lightweight, but slower execution |
| **QAOA** | 210.8 | 31.0 | 8,900 | Lightweight, but slower execution |
