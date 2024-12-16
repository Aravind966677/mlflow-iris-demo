# mlflow-iris-demo

---

# Logistic Regression Solver Comparison with MLflow

This project implements a comparative analysis of different solvers for Logistic Regression using the Iris dataset, with experiment tracking powered by MLflow. The experiment evaluates multiple optimization algorithms (solvers) to determine their performance in multi-class classification.

## Screenshots

Here are some screenshots demonstrating the experiment tracking interface and results:

### MLflow Experiment Interface
![MLflow Experiment Interface](screenshots/mlflow_interface.png)
*MLflow interface showing multiple runs with different solvers*

### Model Comparison
![Model Comparison](screenshots/model_comparison.png)
*Parallel coordinates plot comparing different solver performances*

### Metrics Dashboard
![Metrics Dashboard](screenshots/metrics_dashboard.png)
*Dashboard showing accuracy and F1 scores across different solvers*

## Overview

The code performs the following main tasks:
1. Loads and preprocesses the Iris dataset
2. Trains multiple Logistic Regression models with different solvers
3. Tracks experiments using MLflow
4. Evaluates model performance using accuracy and F1 score
5. Automatically logs models, parameters, and metrics

## Requirements

- Python 3.7+
- Required Python packages:
```
mlflow>=2.0.0
scikit-learn>=1.0.0
pandas>=1.0.0
```

## Installation

1. Clone this repository:
```bash
git clone <repository-url>
cd <project-directory>
```

2. Install the required packages:
```bash
pip install -r requirements.txt
```

3. Start the MLflow tracking server:
```bash
mlflow server --host 127.0.0.1 --port 5000
```

## Usage

1. Ensure the MLflow server is running
2. Run the main script:
```bash
python logistic_regression_comparison.py
```

## Code Structure

The code implements the following workflow:

1. **Data Preparation**
   - Loads the Iris dataset
   - Splits data into training (80%) and test (20%) sets
   - Uses StandardScaler for feature normalization

2. **Model Training**
   - Implements a pipeline with StandardScaler and LogisticRegression
   - Trains models using different solvers:
     - lbfgs
     - liblinear
     - sag
     - saga
     - newton-cg

3. **Experiment Tracking**
   - Records parameters:
     - Solver type
     - Maximum iterations
   - Logs metrics:
     - Classification accuracy
     - Weighted F1 score
   - Saves trained models

## MLflow Tracking

The experiment tracking includes:
- Separate runs for each solver
- Automated logging of parameters and metrics
- Model registration with unique names
- Access to results via MLflow UI at `http://127.0.0.1:5000`

## Model Details

The LogisticRegression models are configured with:
- `max_iter=1000`: Maximum number of iterations
- `random_state=42`: For reproducibility
- `multi_class="auto"`: Automatically choose between 'ovr' and 'multinomial'

## Viewing Results

1. Access the MLflow UI:
   - Open a web browser
   - Navigate to `http://127.0.0.1:5000`
   - Select the "Solver Comparison for Logistic Regression" experiment

2. Compare runs by:
   - Viewing parallel coordinates plot
   - Analyzing metric values
   - Examining parameter configurations

## Project Structure

```
project/
│
├── 1-ml project/                  # Main project directory
│   └── start.ipynb               # Jupyter notebook containing the main code
│
├── mlartifacts/                  # MLflow artifacts directory
│   └── 11091597582516732/       # Run ID directory containing model artifacts
│       ├── [multiple hash directories]  # Individual run artifacts
│
├── mlruns/                       # MLflow runs directory
│   ├── .trash                    # Deleted runs
│   ├── 0                        # Default experiment directory
│   ├── 11091597582516732        # Experiment ID directory
│   ├── models                    # Stored models directory
│   └── venv                      # Virtual environment
│
├── .gitignore                    # Git ignore file
├── get-start.ipynb              # Getting started notebook
├── LICENSE                      # Project license file
├── README.md                    # This documentation file
└── requirements.txt             # Project dependencies
```

[Rest of the README remains the same]

## Contributing

1. Fork the repository
2. Create a feature branch
3. Commit changes
4. Push to the branch
5. Create a Pull Request
