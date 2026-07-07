# Literature Review 

The following papers mention the comparison of classical vs quantum algorithms of our consideration, or are helpful to achieve that goal. 

## PRNG vs QRNG

Title: Searching for evidence of algorithmic randomness and incomputability in the output of quantum random number generators

DOI: https://doi.org/10.1016/j.physleta.2020.127032 (https://arxiv.org/pdf/2101.01238)

NOTE: The authors compare variety of PRNG (including MT19937) and QRNG algos for randomness using five advanced tests (all the data is available and code as well) namely Borel normality and four versions of the Chaitin–Schwartz–Solovay–Strassen tests. Notably, they have taken data from ANU QRNG, and hence have no mention of data generation for QRNG. It is much more mathematically evolved for me and will take more time to go through the theorems and tests mentioned. 


Title: Comparing pseudo- and quantum-random number generators with Monte Carlo simulations

DOI:  https://doi.org/10.1063/5.0199568

NOTE: While the paper's main objective is to benchmark PRNG and QRNG with respect to the performance (critical exponent z) in a 2D Ising model, the paper reports separate testing of PRNG and QRNG on NIST test. Especially, in Results B 3 and Results D subsections.


Title: A statistical test suite for random and pseudorandom number generators for cryptographic applications (NIST test suite)

Link: https://nvlpubs.nist.gov/nistpubs/legacy/sp/nistspecialpublication800-22r1a.pdf 

Software: https://csrc.nist.gov/projects/random-bit-generation/documentation-and-software

NOTE: Widely used and recognised test suite for randomness. The generated sequence of random numbers from PRNG and QRNG algos can be tested via this suite along with other statiscal tests. The original suite had some issues (These guys pointed it out, https://arxiv.org/abs/nlin/0401040) but I hope the newer versions would have it corrected. 





Title: Dieharder: A Random Number Test Suite

Link:https://webhome.phy.duke.edu/~rgb/General/dieharder.php ; (The precursor Diehard: https://ani.stat.fsu.edu/diehard/)

NOTE: The Dieharder tests are considered more extensive than NIST test suite and is very popular as well. 


Title: TestU01: A C library for empirical testing of random number generators

DOI: https://doi.org/10.1145/1268776.1268777

Software: https://github.com/umontreal-simul/TestU01-2009

NOTE: This should have least priority in our list as the other tests seem sufficient for our case. Moreover, this suite takes longer times to run relatively. 

Title: Some Difficult-to-pass Tests of Randomness 

Link: https://www.jstatsoft.org/article/view/v007i03 (you can also find the code link there)

NOTE: This paper entails three tests outside of NIST test suite and described as hard (beyond Diehard suite) namely, gcd, gorilla, and bday tests. We can take up these tests after NIST and Dieharder.  


Title: Statistical Tests for Random and Quantum Random Number Generators

DOI: 10.12783/dtcse/cmee2017/20019

NOTE: A very rough paper on the comparison of the two algorithms, the author made a custom PRNG in C# and generated QRNs using hardware by Quantis. The author created a combined test suite named RaBiGeTe for testing the random numbers (link: http://cristianopi.altervista.org/RaBiGeTe). For my surprise there are very less papers on this topic maybe because it's more of a comparative topic rather than any new additional research on its own)


I think this would suffice for our purpose, if you feel you need some more information for your part, let me know, I will try to get the most information about it available.

## Linear search vs Grover's Algo


Question: Which problem are we going to solve? And how are we going to generate the dataset for that? Are we going to implement the best Grover algorithm known to compare with the classical search or the basic Grover with 5,6-qubits. 


Title:Better-than-classical Grover search via quantum error detection and suppression

DOI: https://doi.org/10.1038/s41534-023-00794-6 

NOTE: The authors show the quantum advantage over classical search after using measurement error mitigation and dynamic decoupling method. They showed the analysis for 2-5 qubits. I believe we will be using the exact same method of comparison hence this paper can help verify/motivate our method. 

Title: Comparing Grover’s Quantum Search Algorithm with Classical Algorithm on Solving Satisfiability Problem

Link: https://ieeexplore.ieee.org/document/9764017

NOTE: The authors use Grover's algorithm to solve for the Boolean SAT problems and benchmark it against the classical solvers. They propose a new method of generalizing Grover algorithm for k-bit SAT problems. We can take some inspiration from the comparison part at the end. 

Title: A Scalable 5,6-Qubit Grover’s Quantum Search Algorithm 

Link: https://arxiv.org/pdf/2205.00117

NOTE: The authors have laid down complete algorithm and circuit details with results. Might help in implementation hence added here. 

These are the most useful papers I could find, with metrics comfirmation we might re-visit and explore more literature based on those metrics.


## Classical Heuristic vs QAOA for MaxCut

Title: Per-Shot Evaluation of QAOA on Max-Cut: A Black-Box Implementation Comparison with Goemans-Williamson 

DOI: https://doi.org/10.48550/arXiv.2604.08367

NOTE: The authors take a standard QAOA algorithm and test it against another classical maxcut solver Goemans-Williamson algorithm, they also mention that the graphs are taken from the Gset library which contains maxcut problems widely used as benchmarks in literature (but minimum vertices a graph has is 800. The biq mac libracy has graphs from 20 nodes and is also a standard in maxcut literature. We can also generate our own graphs using standard widely accepted graph generator algorithms from the NetworkX python library). They analyse the performance shot-by-shot claiming richer statistics this way. I believe this is the best paper which we can take inspiration from. The results are also report in a comprehensive manner. (They also develop a Python library for QAOA: https://github.com/OpenQuantumComputing/QAOA)
 
For classical solvers we can use Gurobi or CVXPY library which are used as standards, but for full control over the algorithm and its implementation I think we can follow some basic algorithms like: D-Wave Ocean SDK or The Myklebust algorithm.


Title: Sampling frequency thresholds for the quantum advantage of the quantum approximate optimization algorithm

DOI: https://doi.org/10.1038/s41534-023-00718-4

NOTE: The authors derive the minimum sampling frequency required for QAOA to match or outperform classical algorithms, which is around 10kHz (sampling frequency is basically the ratio of number of runs (candidate solutions generated) to the total time taken) for the circuit depth greater than 11. The authors have mentioned the implementations in detail, including the code and the dataset (link: https://github.com/danlkv/quantum-classical-time-maxcut), though I believe the analysis done here is overwhelming for our purpose, we will need to find better suited metrics.


Title: Solving maximum cut problems by simulated annealing 

DOI: https://doi.org/10.48550/arXiv.1505.03068

NOTE: The standard paper for stimulated annealing algorithm for maxcut problems, which can be implemented from scratch and the results are also mentioned albeit with relatively less details.

More exploration can be done once the metrics are chosen and implementation starts giving out more gaps to be filled from the literature. 


## Diffie Hellman vs BB84 key exchange protocol 

I couldn't find any specific paper in which the concerned two protocols are compared in terms of resource utilization or computational performance.  

Title: Quantum Key Distribution in the Classical Authenticated Key Exchange Framework

DOI: https://doi.org/10.48550/arXiv.1206.6150

NOTE: A very thorough paper regarding security of BB84, mentions comparison of DH, BB84 and other algos on the lines of cryptographic concepts. No mention of resource utilization or comparison thereof. Gives a detailed mathematical explanation of BB84 algo as well. I don't think we will need any of it in our project, but if someone is interested in understanding BB84 in more detail can go through this and the references mentioned. 


Title: A Comparative Evaluation of a Classical and Quantum Key Exchange System for use in a Web Application Security 

Link: https://www.researchgate.net/publication/324476848_A_Comparative_Evaluation_of_a_Classical_and_Quantum_Key_Exchange_System_for_use_in_a_Web_Application_Security

NOTE: It does nothing. I was quite hopeful reading it, mentioning it here to point it out. 

SIDE NOTE:      
https://doi.org/10.1103/PhysRevLett.85.441 is the paper in which security of BB84 is proved, if interested please give it a read (not important to project)

SIDE NOTE: https://ee.stanford.edu/~hellman/publications/24.pdf is the seminal paper on Diffie-Hellman, a good read. (not important to project)

For the testing the quality of the output of the key exchange protocols, the first sanity check is the RNG tests (NIST, Dieharder etc) after that cryptographic validation is done using NIST ACVP suite (link: https://pages.nist.gov/ACVP/) and Wycheproof (link: https://github.com/C2SP/wycheproof). While we test both of the algorithms for their key randomness and quality, BB84 will have to go through additional checks like quantum bit error rate and secret key rate. 

