# End-to-End Machine Learning Project: Student Performance Prediction

## Overview

This project is an end-to-end machine learning application designed to predict student math scores based on various demographic and academic factors. It demonstrates a complete ML pipeline, from data ingestion and preprocessing to model training, evaluation, and deployment using modern tools and best practices.

The project focuses on predicting math scores for students using features such as gender, race/ethnicity, parental level of education, lunch type, test preparation course, reading score, and writing score. It employs multiple regression models and integrates MLflow for experiment tracking.

## Features

- **Data Analysis and Visualization**: Exploratory Data Analysis (EDA) using pandas, matplotlib, and seaborn to understand the dataset.
- **Model Training**: Implementation of various regression models including Linear Regression, Ridge, Lasso, K-Neighbors, Decision Tree, Random Forest, XGBoost, CatBoost, and AdaBoost.
- **Model Evaluation**: R2 score comparison across models to select the best performer.
- **MLflow Integration**: Experiment tracking and model logging for reproducibility.
- **Web Application**: Flask-based web app for model inference.
- **Packaging**: Proper Python package structure with setup.py for easy installation.
- **Deployment Ready**: Configuration for AWS Elastic Beanstalk deployment.

## Project Structure

```
Section-48-MLproject/
├── .ebextensions/
│   └── python.config          # AWS Elastic Beanstalk configuration
├── artifacts/
│   ├── raw.csv                # Raw dataset
│   ├── test.csv               # Test dataset
│   └── train.csv              # Training dataset
├── logs/                      # Application logs
├── mlproject.egg-info/        # Package metadata
├── notebook/
│   ├── 1 . EDA STUDENT PERFORMANCE .ipynb  # Exploratory Data Analysis notebook
│   └── 2. MODEL TRAINING.ipynb             # Model training and evaluation notebook
├── src/
│   ├── __init__.py
│   ├── exception.py           # Custom exception handling
│   ├── logger.py              # Logging utilities
│   └── ...                    # Additional source files
├── templates/                 # Web app templates
├── .gitignore
├── app.py                     # Flask web application
├── README.md                  # Project documentation
├── requirements.txt           # Python dependencies
└── setup.py                   # Package setup configuration
```

## Dataset

The dataset contains student performance data with the following features:
- `gender`: Male/Female
- `race_ethnicity`: Group A/B/C/D/E
- `parental_level_of_education`: Various education levels
- `lunch`: Standard/Free or reduced
- `test_preparation_course`: None/Completed
- `math_score`: Target variable (0-100)
- `reading_score`: Reading test score (0-100)
- `writing_score`: Writing test score (0-100)

## Installation

1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd Section-48-MLproject
   ```

2. Create a virtual environment:
   ```bash
   python -m venv .venv
   source .venv/bin/activate  # On Windows: .venv\Scripts\activate
   ```

3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

4. Install the project as a package:
   ```bash
   pip install -e .
   ```

## Usage

### Data Preparation

1. Place your dataset in the `artifacts/` folder as `raw.csv`.
2. Run the EDA notebook (`notebook/1 . EDA STUDENT PERFORMANCE .ipynb`) to explore the data.

### Model Training

1. Open and run the model training notebook (`notebook/2. MODEL TRAINING.ipynb`).
2. The notebook will:
   - Load and preprocess the data
   - Train multiple regression models
   - Evaluate models using R2 score
   - Log experiments with MLflow

### Model Performance

Based on the training results, the models achieved the following R2 scores (sorted descending):

| Model Name          | R2 Score |
|---------------------|----------|
| Ridge               | 0.880593 |
| Linear Regression   | 0.880433 |
| Random Forest Regressor | 0.852021 |
| CatBoosting Regressor | 0.851632 |
| AdaBoost Regressor  | 0.848065 |
| XGBRegressor        | 0.827797 |
| Lasso               | 0.825320 |
| K-Neighbors Regressor | 0.783813 |
| Decision Tree       | 0.743588 |

### Web Application

1. Run the Flask app:
   ```bash
   python app.py
   ```

2. Access the application at `http://localhost:5000` to make predictions.

### MLflow Tracking

- Start MLflow UI to view experiments:
  ```bash
  mlflow ui
  ```
- Access at `http://localhost:5000` (different port if app is running).

## Key Technologies

- **Python**: Core programming language
- **Pandas & NumPy**: Data manipulation and analysis
- **Scikit-learn**: Machine learning algorithms and preprocessing
- **Matplotlib & Seaborn**: Data visualization
- **XGBoost & CatBoost**: Advanced boosting algorithms
- **MLflow**: Experiment tracking and model management
- **Flask**: Web framework for deployment
- **AWS Elastic Beanstalk**: Cloud deployment (configured)

## Model Details

### Preprocessing

- Categorical features are encoded using appropriate transformers
- Numerical features are scaled where necessary
- Column transformer is used to apply different preprocessing to different feature types

### Best Model

The Ridge Regression model achieved the highest R2 score of 0.880593, closely followed by Linear Regression. This model is recommended for production use.

## Deployment

The project includes configuration for AWS Elastic Beanstalk deployment. Use the `.ebextensions/python.config` for environment setup.

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

- Dataset source: Student Performance dataset
- Inspired by end-to-end ML project tutorials and best practices

For more details, refer to the individual notebooks and source code files.
