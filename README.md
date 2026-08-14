![Qintern 2026 Badge](docs/assets/QIntern2026.jpeg)

# Benchmarking Quantum Algorithms in the Cloud: A Comparative Study of Classical vs. Simulated Quantum Approaches on AWS

Comparative benchmarking of classical vs. simulated quantum algorithms (RNG, Search, QAOA, BB84) on Amazon Braket — QIntern 2026.

## CLASSICAL ALGORITHMS

| Algorithm | Avg Execution Time (ms) | Avg Memory Usage (MB) | Avg Operations / Sec 
| :--- | ---: | ---: | ---: 
| **Diffie Helman** | 826.16 | ~0.013 MB | ~19,845 | 
| **Linear Search** | 5.95| 112.76 MB | ~3,325,443 elements| 
| **PRNG MT19937** | 2.18 | 173.99 MB | ~20,734,396 bits | 
| **Max Cut Solver** | 22.91 | 157.07 MB | ~340.67 operations | 

## QUANTUM ALGORITHMS

| Algorithm | Execution Time (ms) | Memory Usage (MB) | Operations / Sec | Notes |
| :--- | ---: | ---: | ---: | :--- |
| **BB84 QKD** | 145.2 | 42.1 | 12,450 | Baseline implementation |
| **Grover Search** | 89.5 | 65.4 | 25,100 | Fast, but high memory overhead |
| **QRNG** | 210.8 | 31.0 | 8,900 | Lightweight, but slower execution |
| **QAOA** | 210.8 | 31.0 | 8,900 | Lightweight, but slower execution |
