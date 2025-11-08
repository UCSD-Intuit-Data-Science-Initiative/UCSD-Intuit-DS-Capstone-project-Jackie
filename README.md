# Intuit Virtual Expert Platform: Workforce Management Optimization
**UCSD Data Science Capstone Project - Fall 2025**

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue)](https://www.python.org/)
[![Poetry](https://img.shields.io/badge/Poetry-1.8%2B-blue)](https://python-poetry.org/)
[![License](https://img.shields.io/badge/License-Apache%202.0-green.svg)](LICENSE)

---

## **Table of Contents**

1. [Overview](#overview)
2. [Business Problem](#business-problem)
3. [Domain Background](#domain-background)
4. [Goals & Objectives](#goals--objectives)
5. [Project Structure](#project-structure)
6. [Installation & Setup](#installation--setup)
7. [Data Access & Storage](#data-access--storage)
8. [Usage](#usage)
9. [Methodology](#methodology)
10. [Success Metrics](#success-metrics)
11. [Results](#results)
12. [Contributing](#contributing)
13. [Acknowledgments](#acknowledgments)
14. [License](#license)

---

## **Overview**

This repository contains a comprehensive solution for workforce management optimization in customer-facing operations, developed as part of the UCSD-Intuit Data Science Capstone Project. The project addresses the critical challenge of aligning staffing levels with fluctuating customer demand while meeting strict operational constraints like target response times and service level agreements (SLAs).

The solution integrates two key components:
1. **Demand Forecasting**: Machine learning models to predict customer interaction volumes
2. **Supply Optimization**: Mathematical optimization models to determine optimal headcount allocation

### **Key Features**

- **Time Series Forecasting**: Multiple ML algorithms for robust demand prediction
- **Constraint-Based Optimization**: Efficient staffing plans that meet business requirements
- **Many-to-Many Mapping**: Handles complex staff-to-demand-type relationships
- **Scalable Architecture**: Production-ready codebase with comprehensive testing
- **Interactive Notebooks**: Exploratory data analysis and model experimentation

---

## **Business Problem**

The project addresses the challenge of workforce management in customer-facing operations, focusing on aligning staffing levels with fluctuating customer demand. This is a complex optimization problem due to several industry pain points:

### **Key Challenges**

1. **Demand Volatility**: Customer interaction volumes vary significantly by hour, day, season, and external events
2. **Service Level Constraints**: Must meet strict SLAs (e.g., 80% of calls answered within 20 seconds)
3. **Many-to-Many Complexity**: Staff members have varied skill sets and efficiencies across different demand types
4. **Cost vs. Quality Trade-off**: Balancing operational costs with maintaining high service quality
5. **Real-Time Adaptability**: Need for dynamic adjustments when forecasts deviate from actuals

### **Value Proposition**

An effective solution optimizes resource utilization to:
- **Reduce operational costs** through efficient staffing
- **Maintain high service quality** and customer satisfaction
- **Improve staff utilization** and work-life balance
- **Enable data-driven decision-making** for operations managers

---

## **Domain Background**

### **Intuit's Virtual Expert Platform (VEP)**

Intuit, a leading financial software company, offers products like TurboTax and QuickBooks, and connects users with live experts through its Virtual Expert Platform (VEP). This platform's operational efficiency relies heavily on accurate demand forecasting and precise supply planning. By effectively matching expert availability with user needs, Intuit ensures timely support and maintains cost-effectiveness.

### **The Forecasting Challenge**

Forecasting models in workforce management set the stage for everything else. The expectation is to accurately capture:
- **When**: Hourly and daily patterns
- **How much**: Volume of customer interactions
- **What kind**: Types of expertise required (tax, bookkeeping, technical support, etc.)

Accuracy matters because small errors in forecasts ripple downstream, leading to:
- **Overstaffing**: Higher labor costs and reduced profitability
- **Understaffing**: Longer wait times, abandoned calls, and lower customer satisfaction

### **The Supply Planning Challenge**

Supply planning requires building staffing schedules that balance multiple, often conflicting requirements:

- **Skills Mix**: Ensuring the right distribution of expertise (e.g., tax experts vs. bookkeeping experts)
- **Peak Coverage**: Adequate staffing during high-demand periods without burnout
- **Budget Constraints**: Staying within labor budgets and regulatory limits
- **Flexibility**: Allowing for last-minute adjustments when forecasts shift

### **Operational Context**

In a real-world operations center:

- **Time Granularity**: Forecasts and schedules broken down by 30-minute intervals
- **Real-Time Monitoring**: Live adjustments like reassigning staff or calling in reserves
- **Diverse Data Sources**: Historical volumes, marketing campaigns, product releases, external events (tax deadlines)
- **Performance Metrics**: SLAs, average handling time (AHT), cost per interaction

---

## **Goals & Objectives**

The project is divided into two areas for Quarter 1 (Fall 2025):

### **Part 1: Demand Forecasting**

Develop a working demand forecasting model and evaluate several ML algorithms to produce robust forecasts.

**Learning Objectives:**
- Gain familiarity with essential Python toolkits and development environment (Poetry, Jupyter, Git)
- Master time series data handling, processing, seasonality analysis, and feature engineering
- Define key metrics, understand time series evaluation, model selection, and optimization

**Deliverables:**
- Exploratory data analysis (EDA) of historical call center data
- Feature engineering pipeline for time series data
- Comparison of multiple forecasting algorithms (ARIMA, Prophet, LSTM, XGBoost, etc.)
- Model evaluation framework with industry-standard metrics (wMAPE, MAE, MASE, RMSE)

### **Part 2: Supply Optimization**

Build a supply optimization model to determine optimal headcount allocation based on forecasted demand.

**Learning Objectives:**
- Understand constraint-based optimization and linear programming
- Model complex many-to-many staff-to-demand-type relationships
- Balance competing objectives (cost, service quality, fairness)
- Progress from simple one-to-one to complex many-to-many scenarios

**Deliverables:**
- Mathematical optimization model formulation
- Implementation using optimization libraries (PuLP, OR-Tools, Gurobi)
- Scenario analysis and sensitivity testing
- Integration with demand forecasting outputs

### **Overall Learning Objectives**

By the end of this project, students will be able to:

1. Understand the basics of forecasting and supply optimization in real-world operations
2. Recognize key trade-offs in workforce planning (quality, cost, flexibility)
3. Interpret and use data from demand patterns, schedules, and performance metrics
4. Apply optimization logic to create adaptive staffing plans
5. Work with industry partners to understand real-world constraints
6. Develop end-to-end solutions that integrate forecasting and optimization models

---

## **Project Structure**

```
UCSD-Intuit-DS-Capstone-project-Jackie/
│
├── data/                           # Data directory (excluded from Git)
│   ├── raw/                        # Immutable source data
│   │   ├── call-center-data-v2-daily.csv
│   │   └── call-center-data-v2-daily-hoo.csv
│   ├── processed/                  # Cleaned and feature-engineered data
│   │   └── call_data_clean.csv
│   ├── interim/                    # Intermediate processing outputs
│   └── external/                   # Third-party or reference data
│
├── notebooks/                      # Jupyter notebooks for exploration
│   ├── 01_data_preparation.ipynb   # Data loading and cleaning
│   ├── 02-eda.ipynb                # Exploratory data analysis
│   ├── modeling.ipynb              # Model development and evaluation
│   └── data/                       # Notebook-specific data files
│       └── processed/
│
├── src/                            # Source code (installable package)
│   └── main_module/                # Main Python package
│       ├── __init__.py
│       ├── logging.py              # Loguru configuration
│       ├── data/                   # Data loading and preprocessing
│       │   ├── __init__.py
│       │   ├── load_data.py
│       │   └── preprocess.py
│       ├── modeling/               # Training, evaluation, prediction
│       │   ├── __init__.py
│       │   ├── train.py
│       │   ├── evaluate.py
│       │   └── predict.py
│       ├── utils/                  # Utility functions
│       │   ├── __init__.py
│       │   ├── io.py
│       │   └── time.py
│       └── visualization/          # Plotting utilities
│           ├── __init__.py
│           └── plots.py
│
├── scripts/                        # CLI utilities and pipelines
│   ├── __init__.py
│   └── run_pipeline.py             # Main pipeline script
│
├── tests/                          # Test suite
│   ├── unit/                       # Unit tests
│   │   ├── test_load_data.py
│   │   ├── test_process_data.py
│   │   └── test_modeling.py
│   └── integration/                # Integration tests
│
├── docs/                           # Documentation (GitHub Pages)
│   ├── _config.yml                 # Jekyll configuration
│   ├── index.md                    # Documentation homepage
│   ├── data.md                     # Data documentation
│   ├── modeling.md                 # Modeling documentation
│   ├── overview.md                 # Project overview
│   ├── results.md                  # Results and findings
│   └── tech_stack.md               # Technology stack details
│
├── references/                     # Reference materials and papers
│
├── Makefile                        # Command automation
├── pyproject.toml                  # Poetry configuration
├── tox.ini                         # Tox configuration
├── docker-compose.yml              # Docker services configuration
├── .pre-commit-config.yaml         # Pre-commit hooks
├── .gitignore                      # Git ignore rules
├── README.md                       # This file
├── README-dev.md                   # Developer documentation
├── README_INTUIT.md                # Intuit partner documentation
└── README_TA.md                    # TA reference documentation
```

> **Note**: Folders marked with `.gitkeep` are tracked in Git even when empty to preserve directory structure.

---

## **Installation & Setup**

### **System Requirements**

- **Operating System**: macOS, Linux, or Windows (WSL2 recommended)
- **Python**: 3.10 or higher (3.11 recommended)
- **Poetry**: 1.8+ for dependency management
- **Memory**: 8GB RAM minimum, 16GB recommended
- **Storage**: 5GB free space for data and models

### **Prerequisites**

1. **Install Python 3.10+**
   ```bash
   # Check Python version
   python --version  # or python3 --version
   ```

2. **Install Poetry**
   ```bash
   # macOS/Linux
   curl -sSL https://install.python-poetry.org | python3 -
   
   # Windows (PowerShell)
   (Invoke-WebRequest -Uri https://install.python-poetry.org -UseBasicParsing).Content | py -
   
   # Verify installation
   poetry --version
   ```

3. **Clone the Repository**
   ```bash
   git clone https://github.com/UCSD-Intuit-Data-Science-Initiative/UCSD-Intuit-DS-Capstone-project-Jackie.git
   cd UCSD-Intuit-DS-Capstone-project-Jackie
   ```

### **Environment Setup**

#### **Option 1: Using Make (Recommended)**

The Makefile provides convenient commands for setup and development:

```bash
# Install all dependencies and pre-commit hooks
make install

# Verify installation by running linting
make lint

# Run tests to ensure everything is working
make test
```

#### **Option 2: Manual Setup**

```bash
# Create virtual environment and install dependencies
poetry install

# Activate the virtual environment
poetry shell

# Install pre-commit hooks
poetry run pre-commit install
```

### **Verify Installation**

```bash
# Check that the package is installed
poetry run python -c "import main_module; print('Installation successful!')"

# Run the demo pipeline
make pipeline-run
# OR
poetry run python scripts/run_pipeline.py --demo
```

---

## **Data Access & Storage**

### **Data Sources**

The project uses historical call center data from Intuit's Virtual Expert Platform. The datasets include:

1. **`call-center-data-v2-daily.csv`**: Daily aggregated call volumes
2. **`call-center-data-v2-daily-hoo.csv`**: Daily call volumes with hours of operation

### **Data Storage Structure**

```
data/
├── raw/                    # Original, immutable data files
│   ├── call-center-data-v2-daily.csv
│   └── call-center-data-v2-daily-hoo.csv
├── processed/              # Cleaned, transformed data ready for modeling
│   └── call_data_clean.csv
├── interim/                # Intermediate processing outputs
└── external/               # Third-party reference data
```

### **Accessing the Data**

**For UCSD Students & Project Team:**

1. Data files are stored in the `data/raw/` directory within the repository
2. If the data directory is empty, contact the project maintainers for access
3. For large datasets not in Git, download from the shared drive (link provided in course materials)

**Data Privacy & Security:**

- This project uses **anonymized and aggregated** call center data
- No personally identifiable information (PII) is included
- Data should not be shared outside the project team without permission

### **Loading Data in Code**

```python
from pathlib import Path
from main_module.data import load_csv

# Load raw data
data_path = Path("data/raw/call-center-data-v2-daily.csv")
df = load_csv(data_path)

# Load processed data
processed_path = Path("data/processed/call_data_clean.csv")
df_clean = load_csv(processed_path)
```

---

## **Usage**

### **Quick Start**

```bash
# 1. Activate the Poetry environment
poetry shell

# 2. Run the data preparation notebook
jupyter notebook notebooks/01_data_preparation.ipynb

# 3. Run exploratory data analysis
jupyter notebook notebooks/02-eda.ipynb

# 4. Run the modeling notebook
jupyter notebook notebooks/modeling.ipynb

# 5. Execute the full pipeline
poetry run python scripts/run_pipeline.py --data data/raw/call-center-data-v2-daily.csv
```

### **Common Commands**

| Task | Command | Description |
|------|---------|-------------|
| **Setup** |
| Install project | `make install` | Install dependencies & pre-commit hooks |
| **Development** |
| Format code | `make format` | Auto-format with Ruff |
| Lint code | `make lint` | Run linting and type checks |
| Run tests | `make test` | Execute test suite with coverage |
| **Pipeline** |
| Run pipeline (demo) | `make pipeline-run` | Run with synthetic data |
| Run pipeline (real data) | `poetry run python scripts/run_pipeline.py --data <path>` | Run with actual dataset |
| Pipeline help | `make pipeline-help` | Show CLI options |
| **Documentation** |
| Serve docs locally | `make docs-up` | Start Jekyll docs server |
| Stop docs server | `make docs-down` | Stop documentation server |
| Open docs in browser | `make docs-open` | Launch docs at localhost:4000 |
| **Maintenance** |
| Clean caches | `make clean` | Remove build artifacts |
| Run pre-commit hooks | `make precommit` | Run all hooks manually |

### **Running Notebooks**

All exploratory analysis and modeling work is in Jupyter notebooks:

```bash
# Start Jupyter Lab
poetry run jupyter lab

# Or start Jupyter Notebook
poetry run jupyter notebook
```

**Available Notebooks:**
1. **`01_data_preparation.ipynb`**: Data loading, cleaning, and initial preprocessing
2. **`02-eda.ipynb`**: Exploratory data analysis, visualization, seasonality analysis
3. **`modeling.ipynb`**: Model development, training, evaluation, and comparison

### **Running the Pipeline**

The pipeline script (`scripts/run_pipeline.py`) provides a CLI interface for end-to-end execution:

```bash
# Run with demo/synthetic data
poetry run python scripts/run_pipeline.py --demo

# Run with real data
poetry run python scripts/run_pipeline.py \
  --data data/raw/call-center-data-v2-daily.csv \
  --target call_volume

# Get help
poetry run python scripts/run_pipeline.py --help
```

### **Running Tests**

```bash
# Run all tests with coverage
make test

# Run specific test file
poetry run pytest tests/unit/test_modeling.py

# Run tests with verbose output
poetry run pytest -v

# Run tests with coverage report
poetry run pytest --cov=main_module --cov-report=html
```

### **Code Quality Checks**

```bash
# Format code automatically
make format

# Check linting and types
make lint

# Run pre-commit hooks on all files
make precommit
```

---

## **Methodology**

### **Part 1: Demand Forecasting**

#### **Data Preparation**
1. **Data Loading**: Import historical call volume data from CSV files
2. **Data Cleaning**: Handle missing values, outliers, and data quality issues
3. **Feature Engineering**:
   - Temporal features (hour, day of week, month, year)
   - Lag features (previous day/week volumes)
   - Rolling statistics (moving averages, trends)
   - Calendar features (holidays, special events)
   - Seasonality indicators

#### **Exploratory Data Analysis**
- Time series decomposition (trend, seasonality, residuals)
- Correlation analysis between features
- Visualization of demand patterns (hourly, daily, weekly, yearly)
- Anomaly detection and outlier analysis

#### **Model Development**
Multiple forecasting approaches are evaluated:

1. **Statistical Models**:
   - ARIMA (AutoRegressive Integrated Moving Average)
   - SARIMA (Seasonal ARIMA)
   - Prophet (Facebook's time series forecasting tool)

2. **Machine Learning Models**:
   - XGBoost (Gradient Boosting)
   - Random Forest
   - LightGBM

3. **Deep Learning Models**:
   - LSTM (Long Short-Term Memory networks)
   - GRU (Gated Recurrent Units)

#### **Model Evaluation**
Models are evaluated using time series cross-validation and the following metrics:
- **wMAPE** (Weighted Mean Absolute Percentage Error)
- **MAE** (Mean Absolute Error)
- **MASE** (Mean Absolute Scaled Error)
- **RMSE** (Root Mean Squared Error)

### **Part 2: Supply Optimization**

#### **Problem Formulation**
The supply optimization problem is formulated as a constrained optimization:

**Objective**: Minimize total staffing cost while meeting service level requirements

**Decision Variables**:
- Number of staff scheduled per time interval
- Staff-to-demand-type assignments (for many-to-many scenarios)

**Constraints**:
- Service level agreements (SLA): X% of calls answered within Y seconds
- Staff availability and shift constraints
- Skills matching requirements
- Budget limitations
- Minimum/maximum staffing levels

#### **Optimization Approach**
1. **One-to-One Scenario**: Simple staffing model with uniform skills
2. **Many-to-Many Scenario**: Complex model with varied skills and efficiencies

**Solution Methods**:
- Linear Programming (LP) for continuous staffing levels
- Mixed-Integer Programming (MIP) for discrete staffing decisions
- Heuristic algorithms for large-scale problems

#### **Tools & Libraries**:
- PuLP: Python linear programming library
- OR-Tools: Google's optimization toolkit
- Gurobi (optional): Commercial optimization solver

---

## **Success Metrics**

### **Technical Metrics**

#### **Demand Forecasting Accuracy**
| Metric | Description | Target |
|--------|-------------|--------|
| **wMAPE** | Weighted Mean Absolute Percentage Error | < 10% |
| **MAE** | Mean Absolute Error | Baseline improvement > 20% |
| **MASE** | Mean Absolute Scaled Error | < 1.0 (better than naive forecast) |
| **RMSE** | Root Mean Squared Error | Minimize |

#### **Supply Optimization Performance**
| Metric | Description | Target |
|--------|-------------|--------|
| **Service Level Achievement** | % of interactions within SLA | ≥ 80% |
| **ASA** | Average Speed of Answer | < 30 seconds |
| **Staff Utilization Rate** | Efficiency of resource allocation | 75-85% |
| **Cost per Interaction** | Total cost / # of interactions | Minimize |
| **Constraint Satisfaction** | % of constraints met | 100% |

### **Operational Metrics**
- **Abandonment Rate**: Percentage of customers who hang up before reaching an agent
- **First Call Resolution**: Percentage of issues resolved in a single interaction
- **Schedule Adherence**: How closely actual schedules match planned schedules

### **Business Impact**
- **Cost Savings**: Quantified reduction in operational costs
- **Customer Satisfaction**: Improvement in service quality (CSAT scores)
- **Scalability**: Model's ability to handle varying demand volumes
- **ROI**: Return on investment from implementing the solution

---

## **Results**

### **Preliminary Findings**

*This section will be updated as the project progresses.*

#### **Data Analysis**
- Call volumes exhibit strong daily and weekly seasonality
- Peak demand occurs during [specific hours/days]
- [Other key patterns observed]

#### **Forecasting Models**
- Best performing model: [Model name]
- Achieved wMAPE of [X%] on test set
- [Other model performance highlights]

#### **Optimization Results**
- Reduced staffing costs by [X%] while maintaining SLA compliance
- Improved staff utilization from [X%] to [Y%]
- [Other optimization achievements]

### **Visualizations**

Results visualizations can be found in:
- `notebooks/02-eda.ipynb`: Data exploration charts
- `notebooks/modeling.ipynb`: Model performance comparisons
- `docs/results.md`: Comprehensive results documentation

---

## **Contributing**

This is an academic project for the UCSD-Intuit Data Science Capstone. Contributions are welcome from project team members.

### **Development Workflow**

1. **Create a feature branch**
   ```bash
   git checkout -b feature/your-feature-name
   ```

2. **Make your changes**
   - Write clear, documented code
   - Follow PEP 8 style guidelines (enforced by Ruff)
   - Add tests for new functionality

3. **Run quality checks**
   ```bash
   make format  # Auto-format code
   make lint    # Check linting and types
   make test    # Run test suite
   ```

4. **Commit your changes**
   ```bash
   git add .
   git commit -m "Brief description of changes"
   ```
   Pre-commit hooks will automatically run checks.

5. **Push and create a pull request**
   ```bash
   git push origin feature/your-feature-name
   ```

### **Code Style Guidelines**

- Follow PEP 8 conventions
- Use type hints for function signatures
- Write docstrings for all public functions/classes
- Keep functions focused and modular
- Add unit tests for new functionality

---

## **Acknowledgments**

### **Industry Partner**
- **Intuit Virtual Expert Platform Team**

### **Technology & Tools**
- **Poetry**: Dependency management
- **Ruff**: Fast Python linting and formatting
- **Pytest**: Testing framework
- **Loguru**: Elegant logging
- **GitHub Pages**: Documentation hosting

### **References**
- [Add relevant papers, articles, or resources]

---

## **License**

This project is licensed under the Apache License 2.0 - see the [LICENSE](LICENSE) file for details.

---

## **Contact**

For questions or collaboration inquiries:

- **Email**: jaw039@uscd.edu

---

**Last Updated**: November 7, 2025

**Project Status**: 🚧 In Progress - Quarter 1 (Fall 2025)
