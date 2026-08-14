![Qintern 2026 Badge](docs/assets/QIntern2026.jpeg)

# Benchmarking Quantum Algorithms in the Cloud: A Comparative Study of Classical vs. Simulated Quantum Approaches on AWS

Comparative benchmarking of classical vs. simulated quantum algorithms (RNG, Search, QAOA, BB84) on Amazon Braket — QIntern 2026.

### CLASSICAL ALGORITHMS AVG PERFORMANCE 

| Algorithm | Input Size Range | Avg Execution Time (ms) | Avg Operations / Sec |
| :--- | :--- | ---: | ---: |
| **Diffie-Hellman** | 1,000 to 8,000 key bits | 826.16 | ~19,720 bits |
| **Linear Search** | ~3.3M elements | 5.95 | ~3,325,443 elements |
| **PRNG (MT19937)** | 10k to 80k output bits | 2.18 | ~20,734,396 bits |
| **Max Cut Solver** | N = 4 to 10 nodes | 22.91 | ~340.67 nodes |

---

### QUANTUM ALGORITHMS AVG PERFORMANCE 

| Algorithm | Input Size Range | Avg Execution Time (ms) | Avg Operations / Sec |
| :--- | :--- | ---: | ---: |
| **BB84 QKD** | 1,000 to 8,000 qubits | 27,350.00 | ~130 qubits (~70.1 key bits) |
| **Grover Search** | N = 8 to 32 elements | 224.05 | 37,168.5 queries |
| **QRNG** | 10k to 80k output bits | 65.50 | ~527,029 bits |
| **QAOA** | N = 4 to 10 nodes, p = 1 to 3 | 5,370.00 | 440 shots |


## COMPARISON
### BB84 QKD vs Diffie-Hellman
| Algorithm | Input Size Range | Avg Execution Time | Avg Operations / Sec |
| :--- | :--- | ---: | ---: |
| **Diffie-Hellman** | 1,000 to 8,000 key bits | 830.23 ms | ~19,720 bits/sec |
| **BB84 QKD** | 1,000 to 8,000 qubits | 27,350.00 ms | ~130 qubits/sec |
