# SpaceX Falcon 9 First Stage Landing Prediction

## 📌 Project Overview

This project analyzes **SpaceX Falcon 9 launch data** and builds machine learning models to predict whether the Falcon 9 first stage will successfully land.

The goal is to understand the factors that influence landing success and determine which machine learning algorithm provides the best prediction performance.

This project was completed as part of the **IBM Data Science Professional Certificate – Applied Data Science Capstone**.

---

## 🎯 Objectives

The main objectives of this project are:

* Collect SpaceX launch data using the SpaceX API.
* Collect additional launch information through web scraping.
* Clean and prepare the data for analysis.
* Perform Exploratory Data Analysis (EDA).
* Analyze the data using SQL.
* Create interactive visualizations using Folium and Plotly Dash.
* Build machine learning models to predict first-stage landing success.
* Compare different machine learning algorithms.
* Identify the most effective model for the prediction task.

---

## 📊 Data Collection

### SpaceX API

SpaceX launch data was collected using the SpaceX API.

The data includes information such as:

* Flight number
* Launch date
* Booster version
* Launch site
* Payload mass
* Orbit
* Customer
* Landing outcome
* Reused booster information

### Web Scraping

Additional Falcon 9 launch information was collected from Wikipedia using:

* Python
* Requests
* BeautifulSoup
* Regular Expressions
* Pandas

The scraped information includes launch dates, booster versions, launch sites, payloads, customers, orbits, and landing outcomes.

---

## 🧹 Data Wrangling

The collected data was cleaned and transformed before analysis.

Main data preparation steps included:

* Handling missing values
* Converting data types
* Selecting relevant features
* Creating the target variable
* Converting landing outcomes into binary classes
* One-hot encoding categorical variables
* Standardizing numerical features

### Target Variable

The target variable is:

```text
Class
```

Where:

```text
1 = Successful Landing
0 = Unsuccessful Landing
```

---

## 📈 Exploratory Data Analysis

Several visualizations were created to understand the relationship between launch characteristics and landing success.

### Analysis included:

* Flight Number vs. Launch Site
* Payload Mass vs. Launch Site
* Success Rate by Orbit
* Flight Number vs. Orbit
* Payload Mass vs. Orbit
* Yearly Landing Success Rate

### Key Findings

* Landing success generally improved as SpaceX gained more launch experience.
* Later flights generally had higher landing success rates.
* Some launch sites had significantly more launch activity than others.
* Payload mass and orbit are important factors when analyzing landing success.
* The overall landing success rate increased over time.

---

## 🗃️ SQL Analysis

SQL was used to analyze the SpaceX launch database.

Examples of SQL analysis include:

```sql
SELECT DISTINCT Launch_Site
FROM SPACEXTABLE;
```

Finding the total payload mass carried for NASA (CRS):

```sql
SELECT SUM(PAYLOAD_MASS__KG_)
FROM SPACEXTABLE
WHERE Customer = 'NASA (CRS)';
```

Finding the average payload mass for Falcon 9 v1.1:

```sql
SELECT AVG(PAYLOAD_MASS__KG_)
FROM SPACEXTABLE
WHERE Booster_Version = 'F9 v1.1';
```

Landing outcome frequency:

```sql
SELECT Landing_Outcome, COUNT(*) AS Total
FROM SPACEXTABLE
GROUP BY Landing_Outcome;
```

---

## 🗺️ Interactive Visual Analytics

### Folium

Folium was used to create an interactive map showing:

* SpaceX launch sites
* Successful launches
* Failed launches
* Launch locations
* Geographic relationships between launch sites and the coastline

Marker clusters were used to make multiple launch records easier to visualize.

### Plotly Dash

A Plotly Dash dashboard was created to interactively analyze:

* Launch site
* Successful vs. unsuccessful launches
* Payload mass
* Launch outcome

The dashboard contains:

* Launch site dropdown
* Success/failure pie charts
* Payload range slider
* Payload vs. launch outcome scatter plot

---

## 🤖 Predictive Analysis

Four machine learning algorithms were trained and evaluated:

1. Logistic Regression
2. Support Vector Machine (SVM)
3. Decision Tree
4. K-Nearest Neighbors (KNN)

### Machine Learning Workflow

```text
Data
  ↓
Feature Engineering
  ↓
Train/Test Split
  ↓
Standardization
  ↓
GridSearchCV
  ↓
Model Training
  ↓
Prediction
  ↓
Model Evaluation
```

### Models Used

#### Logistic Regression

Used as a baseline classification model.

#### Support Vector Machine

Different kernels were evaluated, including:

* Linear
* RBF
* Polynomial
* Sigmoid

The **RBF kernel** performed best during validation.

#### Decision Tree

Different tree parameters were evaluated using GridSearchCV.

#### K-Nearest Neighbors

Different values of `n_neighbors`, algorithm, and distance metric were tested.

---

## 📊 Model Evaluation

The models were evaluated using:

* Test accuracy
* Confusion matrix
* Cross-validation
* GridSearchCV

Example evaluation:

```python
print("Logistic Regression:", logreg_cv.score(X_test, Y_test))
print("SVM:", svm_cv.score(X_test, Y_test))
print("Decision Tree:", tree_cv.score(X_test, Y_test))
print("KNN:", knn_cv.score(X_test, Y_test))
```

Confusion matrices were also used to understand:

* True Positives
* True Negatives
* False Positives
* False Negatives

---

## 💡 Key Insights

The analysis suggests that Falcon 9 landing success is influenced by several factors.

Important observations include:

* **Launch experience:** Success rates improved over time.
* **Flight number:** Later flights generally had better landing outcomes.
* **Payload:** Payload mass has a relationship with landing performance.
* **Orbit:** Different orbit types show different landing success patterns.
* **Launch site:** Launch site is an important categorical feature.
* **Booster reuse:** Reuse history provides useful information for prediction.

---

## 🛠️ Technologies Used

| Technology       | Purpose                            |
| ---------------- | ---------------------------------- |
| Python           | Data analysis and machine learning |
| Pandas           | Data manipulation                  |
| NumPy            | Numerical computing                |
| Matplotlib       | Data visualization                 |
| Seaborn          | Statistical visualization          |
| Scikit-learn     | Machine learning                   |
| BeautifulSoup    | Web scraping                       |
| Requests         | API/Web requests                   |
| SQLite           | SQL analysis                       |
| Folium           | Interactive maps                   |
| Plotly Dash      | Interactive dashboard              |
| Jupyter Notebook | Development environment            |
| Git & GitHub     | Version control                    |

---

## 📁 Project Structure

```text
SpaceX-Capstone/
│
├── notebooks/
│   ├── jupyter-labs-spacex-data-collection-api.ipynb
│   ├── jupyter-labs-webscraping.ipynb
│   ├── edadataviz.ipynb
│   ├── jupyter-labs-sql.ipynb
│   ├── lab_jupyter_launch_site_location.ipynb
│   └── SpaceX_Machine_Learning_Prediction_Part_5.ipynb
│
├── dataset_part_1.csv
├── dataset_part_2.csv
├── dataset_part_3.csv
├── spacex_launch_dash.csv
├── spacex_launch_geo.csv
│
├── spacex-dash-app.py
│
├── README.md
│
└── presentation/
    └── SpaceX_Capstone_Presentation.pdf
```

*Update the file names/folders above if your actual repository structure is different.*

---

## 🚀 How to Run the Project

### 1. Clone the repository

```bash
git clone git@github.com:KaungHtet6107/SpaceX-Capstone.git
```

### 2. Go to the project directory

```bash
cd SpaceX-Capstone
```

### 3. Install required libraries

```bash
pip install pandas numpy matplotlib seaborn scikit-learn requests beautifulsoup4 folium dash plotly
```

### 4. Run the notebooks

Open the notebooks using Jupyter:

```bash
jupyter notebook
```

Then run the notebooks in sequence.

### 5. Run the Dash application

```bash
python spacex-dash-app.py
```

---

## 🔗 References

* SpaceX launch data
* IBM Skills Network datasets
* Wikipedia Falcon 9 launch history
* IBM Data Science Professional Certificate
* Scikit-learn documentation

---

## 👨‍💻 Author

**Kaung Htet**

GitHub: **[KaungHtet6107](https://github.com/KaungHtet6107)**

---

## 📜 License

This project was created for educational and portfolio purposes as part of the IBM Applied Data Science Capstone.
