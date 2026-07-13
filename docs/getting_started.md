QIntern 2026 Project 26 
# Benchmarking Quantum Algorithms in the Cloud: A Comparative Study of Classical vs. Simulated Quantum Approaches on AWS

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
4. Copy the ```.env.example``` environment variables to a new ```.env``` file and change the values accordingly
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

After the steps above have been accomplished, you may modify the experiment code according to your specifications and run them.

If you would like to use our infrastructure, head over to ```/infrastructure``` and click the repository link provided on the readme file.

Afterwards, follow the steps provided within the repository.
