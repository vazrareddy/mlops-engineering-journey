# Day 1 – Create a Python Virtual Environment for ML

## Objective

Learn how to isolate project dependencies using Python Virtual Environments.

## Concepts Learned

A virtual environment is an isolated Python workspace that allows each project to have its own packages and dependencies without affecting the system Python installation.

Benefits:

* Dependency isolation
* Avoid version conflicts
* Reproducible environments
* Industry standard for Python projects

## Important Commands

### Create Virtual Environment

```bash
python3 -m venv mlops-venv
```

Creates a virtual environment named `mlops-venv`.

### Activate Environment

```bash
source mlops-venv/bin/activate
```

Activates the environment.

### Install Packages

```bash
pip install package-name
```

Installs packages inside the virtual environment.

### Freeze Dependencies

```bash
pip freeze > requirements.txt
```

Stores installed packages for reproducibility.

## Real-World Usage

Every ML project starts with an isolated environment to ensure consistent package versions across development, testing, and production systems.

---

# Day 2 – Set Up and Configure Jupyter Notebook Server

## Objective

Learn how Jupyter Notebook provides an interactive environment for data science and machine learning development.

## Concepts Learned

Jupyter Notebook allows:

* Writing Python code interactively
* Data exploration
* Visualization
* Model experimentation
* Documentation in a single interface

## Important Commands

### Start Notebook

```bash
jupyter notebook
```

Starts the notebook server.

### Start on Custom Port

```bash
jupyter notebook --port 8888
```

Runs notebook on a specific port.

### Stop Notebook

```bash
Ctrl + C
```

Stops the running notebook server.

## Real-World Usage

Data Scientists use Jupyter extensively during EDA (Exploratory Data Analysis), feature engineering, model development, and experimentation.

---

# Day 3 – Fix a Broken UV Lockfile Specification

## Objective

Understand dependency management and reproducible Python environments using UV.

## Concepts Learned

A lock file records exact package versions so every environment installs identical dependencies.

Benefits:

* Reproducible builds
* Faster installations
* Dependency consistency
* Reliable CI/CD pipelines

## Important Commands

### Generate Lockfile

```bash
uv lock
```

Creates a lock file containing exact package versions.

### Install Dependencies

```bash
uv sync
```

Installs dependencies from lock file.

## Real-World Usage

Modern MLOps pipelines rely on lock files to guarantee reproducible training and deployment environments.

---

# Day 4 – Create a Standard ML Project Structure

## Objective

Learn how production ML projects are organized.

## Concepts Learned

A standard project structure improves:

* Maintainability
* Scalability
* Team collaboration
* Code organization

## Project Structure

```text
fraud-detection/
├── data/
├── models/
├── notebooks/
├── src/
├── tests/
├── configs/
├── requirements.txt
└── README.md
```

### Purpose of Each Directory

#### data/

Stores datasets.

* raw/
* processed/

#### models/

Stores trained model artifacts.

#### notebooks/

Contains experimentation notebooks.

#### src/

Application source code.

#### tests/

Automated test cases.

#### configs/

Configuration files.

#### requirements.txt

Python dependencies.

#### README.md

Project documentation.

## Important Commands

### Create Directories

```bash
mkdir directory-name
```

### Move Files

```bash
mv source destination
```

### Create Empty File

```bash
touch filename
```

### Create Python Package

```bash
touch __init__.py
```

Makes Python recognize directories as packages.

## Real-World Usage

Every production ML repository follows a structured layout to improve maintainability and collaboration.

---

# Day 5 – Create a Makefile for ML Workflow Automation

## Objective

Automate repetitive ML tasks using Makefile.

## Concepts Learned

A Makefile acts as a task runner.

Instead of running multiple commands manually, one command can execute an entire workflow.

## Important Targets

### setup

Creates virtual environment and installs dependencies.

```make
setup:
    python3 -m venv mlops-venv
```

### data

Runs data processing.

```make
data:
    python src/data/process_data.py
```

### train

Runs model training.

```make
train:
    python src/models/train.py
```

### test

Runs automated tests.

```make
test:
    pytest tests/
```

### clean

Removes temporary files.

```bash
find . -type d -name "__pycache__" -exec rm -fr {} +
```

Explanation:

* find → search files/directories
* . → current directory
* -type d → directories only
* -name "**pycache**" → search Python cache folders
* -exec → execute command
* rm -fr → force delete recursively
* {} → matched result
* * → execute efficiently

### all

Runs entire workflow.

```make
all: setup data train test
```

## Special Syntax

### .PHONY

```make
.PHONY: all setup data train test clean
```

Tells Make these are commands, not files.

## Real-World Usage

DevOps and MLOps engineers use Makefiles to automate setup, testing, training, deployment, and cleanup operations.

---

# Day 6 – Set Up Code Quality Tools for ML Code

## Objective

Enforce coding standards using Ruff and Black.

## Concepts Learned

Code quality tools ensure:

* Consistent formatting
* Fewer bugs
* Cleaner code
* Better team collaboration

## Ruff

A fast Python linter.

Checks:

* Syntax issues
* Unused imports
* Style violations

### Run Ruff

```bash
ruff check src/
```

Checks source code.

### Auto Fix Issues

```bash
ruff check src/ --fix
```

Automatically fixes supported issues.

## Black

Python code formatter.

### Format Code

```bash
black src/
```

Formats source code.

### Validate Formatting

```bash
black --check src/
```

Checks formatting without modifying files.

## pyproject.toml

Central configuration file for Python tools.

Example:

```toml
[tool.ruff]
line-length = 120

[tool.black]
line-length = 120
```
