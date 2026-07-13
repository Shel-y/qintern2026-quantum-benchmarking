Q# Benchmarking Quantum Algorithms in the Cloud: A Comparative Study of Classical vs. Simulated Quantum Approaches on AWS

**Requirements:**
- Python, Qiskit, Amazon Braket SDK
- AWS Cloud9, EC2, S3
- Terraform

## Steps to Reproduce the Experiment

Initial Steps:
1. Clone this repository in your local machine / Jupyter Notebook / Kaggle / Google Colab / AWS Cloud9
2. Navigate the cloned repository
   * If you cloned the repository locally, navigate to the project folder through an IDE or terminal and continue the steps below.
   * If you cloned the repository to a cloud platform, step 5 is not applicable and skip over to step 6.
4. Change the ```.env.example``` file and setup the values accordingly.
5. Create a virtual environment:

Windows
```
python -m venv .venv
```
MacOS / Linux
```bash
python3 -m venv .venv
```
#### Activate:
macOS / Linux
```bash
source .venv/bin/activate
```
Windows PowerShell
```
.venv\Scripts\activate.bat
```
Windows Command Prompt
```
.venv\Scripts\Activate.ps1
```

7. Install the requirements:

*Local Machine & AWS Cloud9*
```bash
pip install -r requirements.txt
```

*Jupyter Notebook, Kaggle, & Google Colab*
```bash
!pip install -r requirements.txt
```

