![Qintern 2026 Badge](docs/assets/QIntern2026.jpeg)

# Benchmarking Quantum Algorithms in the Cloud: A Comparative Study of Classical vs. Simulated Quantum Approaches on AWS

Comparative benchmarking of classical vs. simulated quantum algorithms (RNG, Search, QAOA, BB84) on Amazon Braket — QIntern 2026.

## CLASSICAL ALGORITHMS PERFORMANCE

| Algorithm | Avg Execution Time (ms) | Avg Operations / Sec 
| :--- | ---: | ---: 
| **Diffie Helman** | 826.16 | ~19,720 bits | 
| **Linear Search** | 5.95| ~3,325,443 elements| 
| **PRNG MT19937** | 2.18 | ~20,734,396 bits | 
| **Max Cut Solver** | 22.91 | ~340.67 nodes | 

## QUANTUM ALGORITHMS PERFORMANC

| Algorithm | Avg Execution Time (ms) | Avg Operations / Sec | 
| :--- | ---: | ---: |
| **BB84 QKD** | ~7.5 | ~200-230 qubits |
| **Grover Search** | ~224.05 | 37,168.5 queries |
| **QRNG** | 65.5 | 2,108,116 bits | 
| **QAOA** | 5370 | 440 shots | 
