#  Machine Learning Mini-Project.

A complete Machine Learning workflow developed as part of my **Software Systems Architecture studies**.

The project covers the main stages of a Machine Learning pipeline, from **data exploration and cleaning to preprocessing, model training and evaluation**.

---

##  Project Overview

The objective of this project is to build a reproducible Machine Learning workflow using a real-world dataset.

The project focuses on understanding the complete process rather than only training a model:

```text
Raw Dataset
     ↓
Data Exploration
     ↓
Data Cleaning
     ↓
Data Transformation
     ↓
Feature Engineering
     ↓
Preprocessing
     ↓
Model Training
     ↓
Model Evaluation
     ↓
Interpretation
```

---

##  Objectives

The main objectives are to:

- Explore and understand the dataset
- Identify missing and inconsistent values
- Detect and handle outliers
- Transform categorical and numerical variables
- Prepare features for Machine Learning
- Train Machine Learning models
- Evaluate model performance
- Interpret the obtained results
- Organize the project using Git and GitHub

---

##  Dataset

The project uses the **Adult Census Income dataset**.

The dataset contains demographic and employment-related information such as:

- Age
- Workclass
- Education
- Education Number
- Marital Status
- Occupation
- Relationship
- Race
- Sex
- Capital Gain
- Capital Loss
- Hours per Week
- Native Country

The target variable is:

```text
income
```

which represents whether an individual's income is:

```text
<=50K
>50K
```

---

#  1. Data Exploration

The first step was to understand the structure and characteristics of the dataset.

The exploration included:

- Dataset dimensions
- Data types
- Statistical summaries
- Distribution analysis
- Categorical variable analysis
- Target variable distribution
- Correlation analysis
- Visualization of important features

Example:

```python
df.shape
df.info()
df.describe()
df.isnull().sum()
```

The objective was to understand the data before applying any Machine Learning algorithm.

---

#  2. Data Cleaning

Several preprocessing operations were performed to improve data quality.

### Main operations

- Handling missing values
- Removing duplicated or invalid observations
- Cleaning categorical values
- Converting data into appropriate formats
- Treating extreme values

Special attention was given to **outliers**.

A custom `Winsorizer` transformer was used to limit extreme values based on selected quantiles.

Example:

```python
class Winsorizer(BaseEstimator, TransformerMixin):

    def __init__(self, lower=0.01, upper=0.99):
        self.lower = lower
        self.upper = upper
```

This allows the transformation to be learned from the training data and then applied consistently.

---

#  3. Data Preprocessing

The dataset contains both numerical and categorical variables.

Therefore, different preprocessing strategies were applied.

### Numerical features

Numerical variables were standardized using:

```python
StandardScaler()
```

### Categorical features

Categorical variables were transformed using:

```python
OneHotEncoder()
```

A `ColumnTransformer` was used to apply the appropriate transformation to each type of feature.

Example:

```python
preprocessor = ColumnTransformer(
    transformers=[
        ("num", StandardScaler(), numeric_features),
        ("cat", OneHotEncoder(handle_unknown="ignore"),
         categorical_features)
    ]
)
```

---

#  4. Machine Learning

After preparing the data, Machine Learning models were trained using the processed features.

The workflow separates:

```text
Training Data
      ↓
Preprocessing
      ↓
Model
      ↓
Prediction
```

Using a pipeline helps avoid data leakage and keeps preprocessing and model training consistent.

---

#  5. Model Evaluation

The models were evaluated using several classification metrics.

### Accuracy

Measures the proportion of correctly classified observations.

### Precision

Measures how many predicted positive observations were actually positive.

### Recall

Measures how many actual positive observations were correctly identified.

### F1-score

Combines Precision and Recall into a single metric.

### ROC-AUC

Measures the model's ability to distinguish between the two classes across different classification thresholds.

The ROC curve was also used to visualize the classification performance.

---

##  Evaluation Metrics

The main metrics used were:

| Metric | Purpose |
|---|---|
| Accuracy | Overall classification correctness |
| Precision | Quality of positive predictions |
| Recall | Ability to detect positive cases |
| F1-score | Balance between precision and recall |
| ROC-AUC | Overall discrimination capability |

---

#  ROC-AUC

ROC-AUC was used as an important evaluation metric.

The ROC curve represents the relationship between:

- True Positive Rate
- False Positive Rate

The **AUC (Area Under the Curve)** summarizes the model's discrimination ability.

Generally:

```text
AUC ≈ 0.5  → Random classification
AUC → 1.0  → Better discrimination
```

This makes ROC-AUC particularly useful when evaluating binary classification models.

---

# 🔬 6. Feature Analysis

Feature analysis was also performed to understand which variables could contribute to the prediction.

Important numerical variables included features such as:

```text
age
education-num
hours-per-week
```

These variables were also used for exploratory analysis and segmentation.

---

#  7. Project Structure

```text
Machine-Learning-Project/
│
├── data/
│   ├── raw/
│   └── processed/
│
├── notebooks/
│   └── ML_Project.ipynb
│
├── src/
│   ├── preprocessing/
│   ├── models/
│   └── evaluation/
│
├── results/
│   ├── figures/
│   └── metrics/
│
├── requirements.txt
├── .gitignore
└── README.md
```

> Adapt the structure above to the actual structure of the repository.

---

#  Technologies

- **Python**
- **Pandas**
- **NumPy**
- **Scikit-learn**
- **Matplotlib**
- **Seaborn**
- **Jupyter Notebook**
- **Git**
- **GitHub**

---

# 🚀 Installation

Clone the repository:

```bash
git clone YOUR_GITHUB_REPOSITORY_URL
cd YOUR_PROJECT_FOLDER
```

Create a virtual environment:

```bash
python -m venv venv
```

Activate it on Windows:

```bash
venv\Scripts\activate
```

Install the dependencies:

```bash
pip install -r requirements.txt
```

Launch Jupyter Notebook:

```bash
jupyter notebook
```

Then open the project notebook from the `notebooks/` directory.

---

#  What I Learned

This project helped me strengthen my understanding of:

- Data exploration
- Data cleaning
- Outlier treatment
- Feature preprocessing
- Machine Learning pipelines
- Classification metrics
- ROC curves and ROC-AUC
- Data visualization
- Git/GitHub workflow
- Reproducible Machine Learning workflows

More importantly, I learned that building a Machine Learning solution is a **complete engineering process**, not simply choosing an algorithm and obtaining predictions.

---

#  Future Improvements

Possible improvements include:

- Hyperparameter optimization
- Cross-validation
- Feature selection
- Comparison of additional classification algorithms
- Class imbalance analysis
- Model explainability
- Deployment through an API
- Integration into a complete software architecture

---

# Author

**Aziz Heni**

Software Engineering Student  
Interested in:

- Machine Learning
- Software Architecture
- IoT & Embedded Systems
- Cybersecurity
- Software Engineering

---

##  Acknowledgment

This project was developed as part of my academic work in **Software Systems Architecture** and Machine Learning.

If you find the project useful, feel free to  the repository.
