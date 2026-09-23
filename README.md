# HR Employee Attrition Prediction – Salifort Motors Capstone Project

[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)

## 📌 Project Overview

This capstone project was developed for **Salifort Motors**, a large consulting firm, to tackle a critical business problem: **high employee turnover**. The HR department wants to understand what drives employees to leave and to build a predictive model that identifies employees at risk of quitting.

By analyzing historical employee data, we uncover key factors that influence attrition and provide actionable, data‑driven recommendations to improve retention and reduce hiring costs.

## 🎯 Business Goal

> **“What’s likely to make an employee leave the company, and can we predict who will leave?”**

- Identify the main drivers of employee churn.
- Build a machine learning model to predict voluntary departures.
- Provide clear, evidence‑based suggestions for HR interventions.

## 📊 Dataset

**Source:** [HR Analytics & Job Prediction (Kaggle)](https://www.kaggle.com/datasets/mfaisalqureshi/hr-analytics-and-job-prediction)

- **Rows:** 14,999 (after cleaning: 11,991 unique records)
- **Features:** 10 (2 categorical, 8 numerical)

| Variable | Description |
|----------|-------------|
| `satisfaction_level` | Employee-reported job satisfaction (0–1) |
| `last_evaluation` | Score of last performance review (0–1) |
| `number_project` | Number of projects employee contributes to |
| `average_monthly_hours` | Average hours worked per month |
| `tenure` | Years with the company |
| `work_accident` | Whether the employee experienced a work accident |
| `left` | **Target variable** – 1 if employee left, 0 if stayed |
| `promotion_last_5years` | Whether promoted in last 5 years |
| `department` | Department (categorical) |
| `salary` | Salary level (low / medium / high) |

## 🔍 Key Findings (EDA)

After cleaning and exploring the data, the following patterns emerged:

### Workload & Hours
- **Employees with 7 projects → 100% left** the company.
- Normal monthly hours (40h/week, ~166.67h/month) were exceeded by most employees.
- Two distinct groups of leavers:
  - **Group A:** Worked far less than peers – possible termination or early notice.
  - **Group B:** Worked **255–295 hours/month** – clear burnout signal.
- **Optimal project count:** 3–4 projects.

### Satisfaction & Tenure
| Status | Mean Satisfaction | Median Satisfaction |
|--------|------------------|---------------------|
| Stayed | 0.667 | 0.69 |
| Left   | 0.440 | 0.41 |

- Employees with **4 years of tenure** who left had unusually low satisfaction → investigate company policy changes at that time.

### Salary Distribution
- Long‑tenured employees (≥7 years) were **not** disproportionately high‑paid.
- Suggests compensation is not the primary retention driver for senior staff.

## 🛠️ Methodology

### 1. Data Cleaning
- Renamed columns to `snake_case`:
  - `Work_accident` → `work_accident`
  - `average_montly_hours` → `average_monthly_hours`
  - `time_spend_company` → `tenure`
  - `Department` → `department`
- Removed **3,008 duplicate rows** (~20% of raw data).
- Identified outliers in `tenure` (824 rows) – to be handled during modeling.

### 2. Exploratory Data Analysis (EDA)
Visualizations included:
- Boxplots of monthly hours vs. number of projects (stayed/left)
- Histograms of project distribution
- Scatterplot of monthly hours vs. satisfaction level
- Boxplot of satisfaction by tenure
- Salary histograms for short‑ vs. long‑tenured employees

### 3. Predictive Modeling
We implemented and compared several classification algorithms:
- **Logistic Regression** (baseline)
- **Decision Tree Classifier**
- **Random Forest Classifier**
- **XGBoost Classifier**

Models were evaluated using:
- Accuracy
- Precision / Recall / F1‑score
- Confusion Matrix
- ROC‑AUC

*(The final model choice is detailed in the notebook.)*

## 📈 Results & Recommendations

### Model Performance
The best performing model achieved:
- **Accuracy:** *80%*

(Update these values from your notebook output.)

### Actionable HR Recommendations

| Priority | Recommendation |
|----------|----------------|
| 🔴 **High** | Cap projects at **4** for any employee; redistribute work for those with 6+ projects. |
| 🔴 **High** | Investigate **4‑year tenure satisfaction drop** – review promotion schedules, manager changes, or policy shifts. |
| 🟡 **Medium** | Introduce **quarterly satisfaction surveys** to catch early warning signs. |
| 🟢 **Low** | Re‑evaluate promotion criteria; ensure they are transparent and achievable. |

> **Key insight:** Most employees are overworked. The ideal workload is **3–4 projects** and **≤200 hours/month**.

## 🚀 Getting Started

### Prerequisites
- Python 3.8+
- Jupyter Notebook / JupyterLab
- Required libraries (see `requirements.txt`)

### Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/salifort-motors-hr-analytics.git
cd salifort-motors-hr-analytics

# Install dependencies
pip install -r requirements.txt
