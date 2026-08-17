# 🏥 Medical Insurance Cost Prediction

A Machine Learning project that predicts **medical insurance charges** based on personal and health-related information such as age, BMI, number of children, smoking habits, gender, and residential region.

The project uses **Linear Regression** to predict insurance costs and achieves an **R² score of approximately 0.706** on the test dataset.

---

## 📌 Project Overview

Medical insurance charges can vary significantly depending on several factors such as age, BMI, smoking habits, and family size.

This project applies a Machine Learning approach to estimate an individual's insurance charges using historical insurance data.

### 🎯 Objective

To build a regression model that can:

- Analyze customer demographic and health-related information
- Identify factors associated with insurance costs
- Train a Linear Regression model
- Evaluate model performance using R² Score
- Predict insurance charges for new individuals
- Serve as the foundation for a web-based prediction system

---

## 🔄 Project Workflow

```text
Import Dataset
      ↓
Data Preprocessing
      ↓
Exploratory Data Analysis
      ↓
Data Visualization
      ↓
Categorical Data Encoding
      ↓
Train-Test Split
      ↓
Model Training
      ↓
Model Evaluation
      ↓
Prediction System
      ↓
Web Application
```

---

## 📂 Dataset

The project uses the `insurance.csv` dataset containing **1,338 records** and **7 columns**.

### Features

| Feature | Description | Type |
|---|---|---|
| `age` | Age of the insured person | Numerical |
| `sex` | Gender of the insured person | Categorical |
| `bmi` | Body Mass Index | Numerical |
| `children` | Number of children covered by the insurance plan | Numerical |
| `smoker` | Whether the person is a smoker | Categorical |
| `region` | Residential region | Categorical |
| `charges` | Medical insurance cost | Target |

---

## 📊 Dataset Information

- **Total Records:** 1,338
- **Total Features:** 6
- **Target Variable:** `charges`
- **Missing Values:** None
- **Problem Type:** Regression

### Target Variable

`charges` represents the medical insurance cost billed to the individual.

---

## 🔍 Exploratory Data Analysis

Several exploratory data analysis techniques were used to understand the dataset.

### Data Inspection

```python
medical_df.shape
medical_df.info()
medical_df.describe()
```

### Visualizations

The following visualizations were created:

- Age distribution
- Gender distribution
- BMI distribution
- Number of children distribution
- Smoker distribution
- Regional distribution

These visualizations help understand the distribution of the dataset before model training.

---

## 🧹 Data Preprocessing

The dataset contains categorical variables that need to be converted into numerical values before training the Machine Learning model.

### Gender Encoding

```text
male   → 0
female → 1
```

### Smoker Encoding

```text
yes → 0
no  → 1
```

### Region Encoding

```text
southeast → 0
southwest → 1
northwest → 2
northeast → 3
```

Example:

```python
medical_df.replace({
    'sex': {
        'male': 0,
        'female': 1
    }
}, inplace=True)

medical_df.replace({
    'smoker': {
        'yes': 0,
        'no': 1
    }
}, inplace=True)

medical_df.replace({
    'region': {
        'southeast': 0,
        'southwest': 1,
        'northwest': 2,
        'northeast': 3
    }
}, inplace=True)
```

---

## 🤖 Machine Learning Model

### Linear Regression

The project uses **Linear Regression** as the prediction model.

```python
from sklearn.linear_model import LinearRegression

lg = LinearRegression()

lg.fit(X_train, y_train)
```

Linear Regression is suitable for this project because the target variable, `charges`, is continuous.

---

## 📚 Train-Test Split

The dataset was divided into training and testing sets.

```python
X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.1,
    random_state=2
)
```

### Dataset Split

| Dataset | Records |
|---|---:|
| Training Set | 1,204 |
| Testing Set | 134 |

---

## 📈 Model Evaluation

The model was evaluated using the **R² (R-squared) Score**.

```python
from sklearn.metrics import r2_score

y_pred = lg.predict(X_test)

r2_score(y_test, y_pred)
```

### Result

**R² Score: `0.7059`**

This means the Linear Regression model explains approximately **70.6% of the variation** in medical insurance charges on the test data.

---

## 🔮 Prediction System

The trained model can be used to predict insurance charges for a new individual.

The input contains the following features:

```text
Age
Sex
BMI
Children
Smoker
Region
```

Example:

```python
input_df = (...)

np_df = np.asarray(input_df)

input_df_reshaped = np_df.reshape(1, -1)

prediction = lg.predict(input_df_reshaped)

print(prediction)
```

The model then generates the predicted insurance charge.

---

## 🌐 Web Application

The prediction system is integrated into a **Streamlit web application** where users can enter the required information and receive an estimated medical insurance charge.

### Example Input

```text
Age: 37
Sex: Female
BMI: 27.74
Children: 3
Smoker: No
Region: Northwest
```

The application converts the categorical values into the numerical format required by the trained model and generates the predicted insurance cost.

---

## 🖥️ **Application Screenshot**

[![Medical Insurance Prediction Model](./medical_insurance_prediction_model.png)
](https://github.com/GURNOOR20010/Gurnoor_Medical-insurance-prediction-model-project-2/blob/main/medical%20insurance%20prediction%20model.png)
---

## 🛠️ Technologies Used

### Programming Language

- Python

### Libraries

- NumPy
- Pandas
- Matplotlib
- Seaborn
- Scikit-learn
- Streamlit

### Machine Learning

- Linear Regression
- Train-Test Split
- R² Score

---

## 📁 Project Structure

```text
Medical-Insurance-Prediction/
│
├── insurance.csv
├── prediction model.ipynb
├── app.py
├── medical_insurance_prediction_model.png
├── Medical Insurance Prediction Model Report.docx
└── README.md
```

---

## 🚀 How to Run the Project

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR-USERNAME/Medical-Insurance-Prediction.git
```

### 2. Navigate to the Project

```bash
cd Medical-Insurance-Prediction
```

### 3. Install Required Libraries

```bash
pip install numpy pandas matplotlib seaborn scikit-learn streamlit
```

### 4. Run the Notebook

Open:

```text
prediction model.ipynb
```

and execute the cells sequentially.

### 5. Run the Streamlit Web Application

```bash
streamlit run app.py
```

---

## 📊 Key Insights

The exploratory analysis shows that insurance charges vary considerably across individuals.

Important variables considered by the model include:

- Age
- BMI
- Smoking status
- Number of children
- Gender
- Region

Smoking status and other health-related characteristics can have a substantial relationship with insurance charges.

---

## 🔮 Future Improvements

The current project uses Linear Regression as a baseline model. Future improvements could include:

- Implementing Random Forest Regression
- Implementing XGBoost
- Comparing multiple regression algorithms
- Hyperparameter tuning
- Feature engineering
- Cross-validation
- Adding MAE and RMSE metrics
- Improving the Streamlit interface
- Deploying the application online
- Adding interactive prediction visualizations

---

## 📌 Learning Outcomes

Through this project, I practiced:

- Data loading and preprocessing
- Exploratory Data Analysis
- Data visualization
- Categorical variable encoding
- Feature-target separation
- Train-test splitting
- Regression model training
- Model evaluation
- Making predictions using a trained ML model
- Building a Machine Learning web application

---

## 👨‍💻 Author

**Gurnoor Singh Arora**

Aspiring Data Analyst | Data Science | Data Engineering

- GitHub: [GURNOOR20010](https://github.com/GURNOOR20010)
- LinkedIn: [Gurnoor Singh Arora](https://www.linkedin.com/in/gurnoor-singh-arora-333a932a4/)

---

## ⭐ If you found this project useful

Consider giving this repository a ⭐ on GitHub!
