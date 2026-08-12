# Notebooks

This repository stores the notebooks created by the Classical Computing Lead and Quantum Computing Lead - all of which
contains the src code for the experiments conducted respectively. 

---

### Classical Computing Experiments

*   **`Diffie Helman`**: Implements the cryptographic key exchange protocol, benchmarking performance across varying prime sizes and evaluating resilience against simulated man-in-the-middle attacks.
    ```python
    class DiffieHellman():
    def __init__(self, p, g) -> None:
    def generate_private_key(self) -> int:
    def generate_public_key(self, private_key) -> int:
    def generate_shared_secret(self, other_public_key, private_key) -> int:
    def perform_key_exchange(bit_size) -> tuple:
    attack_scenarios = []
    ```

*   **`Linear Search`**: A fundamental search algorithm implementation paired with benchmarking tools to measure execution time, CPU usage, and throughput against randomized arrays.
    ```python
    class LinearSearch():
    def search(arr, target) -> dict:
    def generate_array(size) -> list:
    def benchmark_linear_search(array_sizes, trials=10) -> list:
    array_sizes = []
    ```

*   **`Max Cut Solver`**: Solves the Max-Cut problem on random 3-regular graphs using simulated annealing, comparing the heuristic's approximation ratio against a brute-force optimal cut.
    ```python
    class SimulatedAnnealing():
    def __init__(self, graph) -> None:
    def cut_value(self, partition) -> int:
    def neighbour(self, partition) -> dict:
    def optimal_cut(self) -> int:
    def optimize(self, initial_partition, initial_temp=100, cooling_rate=0.995, min_temp=0.001, max_iterations=1000) -> dict:
    def generate_regular_graph(num_nodes, degree=3) -> nx.Graph:
    def initialize_partition(graph) -> dict:
    def benchmark_simulated_annealing(graph_sizes, trials=10) -> list:
    ```

*   **`Pseudo RNG MT19937`**: Evaluates the Mersenne Twister (MT19937) classical pseudorandom number generator, applying statistical analysis like Shannon entropy and Chi-squared tests to validate uniformity.
    ```python
    class MT19937():
    def __init__(self, seed) -> None:
    def extract_number(self) -> int:
    def generate_bits(mt, num_bits) -> str:
    def benchmark_mt19937(bit_sizes, trials=10, seed=5489) -> list:
    def shannon_entropy(bitstream) -> float:
    def min_entropy(bitstream) -> float:
    def chi_squared_test(bitstream) -> tuple:
    bit_sizes = []
    ```

### Quantum Computing Experiments

*   **`Quantum RNG`**: Generates random bitstreams using quantum Hadamard gates, benchmarking entropy and uniformity against classical MT19937 using Chi-squared tests, shot sweeps, and simulator validation metrics.
    ```python
    def quantum_rng(n_bits, shots=10000) -> dict:
    def classical_rng(n_bits, shots=10000) -> dict:
    def plot_comparison(quantum_counts, classical_counts, n_bits, shots) -> None:
    def statistical_analysis(quantum_counts, classical_counts, n_bits, shots) -> None:
    def shot_sweep(n_bits=4, shot_counts=[2500, 5000, 10000, 20000]) -> list:
    def plot_shot_sweep(results) -> None:
    def multiple_trials(n_bits=4, shots=10000, trials=10) -> None:
    def plot_multiple_trials(n_bits=4, shots=10000, trials=10, output_bits=None) -> None:
    def qubit_sweep(qubit_counts=[2, 4, 6, 8], shots=10000) -> list:
    def plot_qubit_sweep(qubit_results) -> None:
    def calculate_dR2(counts, n_bits, shots) -> float:
    def calculate_cv(counts, n_bits) -> float:
    def calculate_shannon_entropy(counts, n_bits, shots) -> float:
    def run_with_metrics(n_bits, shots) -> dict:
    ```

*   **`QAOA`**: Implements the Quantum Approximate Optimization Algorithm for Max-Cut on 3-regular graphs, utilizing classical parameter optimization (COBYLA) to evaluate approximation ratios and noise resilience.
    ```python
    def generate_3regular_graph(n_nodes) -> nx.Graph:
    def get_optimal_cut(G) -> tuple:
    def qaoa_circuit(G, gamma, beta, p) -> Circuit:
    def compute_cut_value(bitstring, G) -> int:
    def expected_cut_value(counts, G, shots) -> float:
    def run_qaoa(G, p, shots, gamma_init=None, beta_init=None) -> dict:
    def run_qaoa_benchmark(node_counts, p_values, shots_config, trials=10) -> list:
    ```

*   **`Grover Search`**: Implements Grover's unstructured search algorithm using phase oracle and diffusion operators, benchmarking quadratic speedup, success probabilities, and fidelity across varying database sizes.
    ```python
    def build_oracle(circuit, n_qubits, target) -> Circuit:
    def build_diffusion(circuit, n_qubits) -> Circuit:
    def build_grover_circuit(n_qubits, target, n_iterations) -> Circuit:
    def run_grover(n_qubits, target, shots, n_iter=None) -> dict:
    def run_grover_benchmark(database_sizes, shots_config, optimal_iters, trials=10) -> list:
    ```

*   **`BB84 QKD`**: Simulates the BB84 Quantum Key Distribution protocol under intercept-resend eavesdropping attacks, calculating Quantum Bit Error Rate (QBER) and Shor-Preskill secure key rates.
    ```python
    def run_bb84(n_qubits, eavesdrop_rate=0.0) -> dict:
    def binary_entropy(p) -> float:
    def secure_key_rate(qber) -> float:
    def run_bb84_benchmark(qubit_counts, eavesdrop_rates, trials=10) -> list:
    ```
---



