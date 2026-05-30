Project Overview

This project simulates a real-world quantitative research and risk analytics workflow used in banking, where the objective was to analyze borrower credit behavior and estimate the probability of loan default using borrower characteristics and credit scores.

The project was completed as part of a banking risk analytics use case, focusing on two major problems:

Loan Default Prediction (Probability of Default - PD)
FICO Score Quantization & Risk Rating Mapping

The final objective was to build prototype models that could assist a bank’s risk management team in estimating potential loan losses and categorizing borrowers based on credit risk.

Business Problem

Banks generate revenue through loans, but lending also introduces credit risk, meaning borrowers may fail to repay their obligations.

A borrower default can cause financial losses to the bank. Therefore, the risk management team wanted to:

Predict the Probability of Default (PD) for borrowers.
Estimate the Expected Loss (EL) from loan defaults.
Categorize borrowers into credit risk buckets based on FICO scores.
Create a scalable approach that works for future mortgage datasets.

The goal was to help the bank make better lending decisions, improve loss provisioning, and strengthen risk assessment frameworks.

Task 1: Loan Default Prediction Model
Objective

Build a predictive model capable of estimating the Probability of Default (PD) for a borrower using customer financial information.

The dataset included borrower-level information such as:

Customer ID
Credit lines outstanding
Loan amount outstanding
Total debt outstanding
Income
Years employed
FICO score
Historical default status
What I Was Supposed To Do

The objective was to:

Analyze borrower loan data.
Train a machine learning model to predict borrower default risk.
Estimate the probability that a customer may default on a loan.
Calculate the expected financial loss using a predefined recovery rate.
What I Did
1. Data Exploration & Understanding

Loaded and explored the dataset to understand:

data structure
feature distributions
missing values
data types
target variable behavior

Performed exploratory checks using:

.head()
.info()
.describe()

to understand customer financial characteristics and default patterns.

2. Feature Selection

Selected relevant borrower financial variables to train the model:

Features used:

Credit lines outstanding
Loan amount outstanding
Total debt outstanding
Income
Years employed
FICO score

Removed customer_id because it is only an identifier and has no predictive significance.

Target Variable:

default
0 = No Default
1 = Default
3. Data Splitting

Split the dataset into:

Training Set (80%)
Testing Set (20%)

This was done to evaluate how well the model performs on unseen borrower data.

4. Machine Learning Model Development

Implemented a Logistic Regression model to predict default probability.

Why Logistic Regression?

widely used in banking risk models
interpretable and regulator-friendly
suitable for binary classification
predicts probabilities effectively

The model learned patterns between borrower financial characteristics and default behavior.

Examples of learned relationships:

lower FICO scores → higher risk
higher debt → higher default probability
lower income → greater credit risk
5. Model Evaluation

Evaluated performance using:

Accuracy Score
Classification Report
Confusion Matrix

Achieved strong predictive performance:

Accuracy: ~98.6%

This indicates that the model effectively distinguished between borrowers likely and unlikely to default.

6. Expected Loss Calculation

Implemented a financial risk formula to estimate loan losses.

The expected loss formula used:

Expected Loss=PD×EAD×LGD

Where:

PD (Probability of Default) → predicted using Logistic Regression
EAD (Exposure at Default) → outstanding loan amount
LGD (Loss Given Default) → estimated loss after recovery

Assumption:

Recovery Rate = 10%
LGD = 90%

Created a reusable function to:

take borrower details as input
predict probability of default
estimate expected financial loss
Task 2: FICO Score Quantization & Risk Bucketing
Objective

The mortgage risk team required categorical credit ratings instead of raw FICO scores because their modeling system only accepted categorical inputs.

The objective was to:

convert continuous FICO scores into meaningful buckets
assign borrower ratings
estimate default probabilities for each category
What I Was Supposed To Do

Create a generalized rating system that:

automatically creates FICO score buckets
works for future datasets
summarizes borrower credit risk effectively

This process is known as:

Quantization

Quantization converts a large range of continuous values into discrete groups or categories.

What I Did
1. Automatic Bucket Generation

Implemented quantile-based bucketing (qcut) to divide borrowers into balanced groups.

Why qcut?

automatically generates buckets
evenly distributes observations
creates stable categories
suitable for future datasets

This ensured each bucket had approximately equal borrower counts.

2. Risk Rating Creation

Created a rating map where:

Lower rating = better credit quality
Higher rating = higher risk

Borrowers were grouped according to:

minimum FICO score
maximum FICO score
default probability within bucket
3. Probability of Default Estimation by Bucket

Calculated:

PD=
Total Borrowers
Defaults
	​


for each FICO category.

This helped estimate:

low-risk borrower groups
medium-risk borrower groups
high-risk borrower groups
4. Risk Visualization

Visualized probability of default across buckets to observe how:

lower FICO scores correspond to higher default rates
stronger credit profiles reduce mortgage default probability
5. Rating Prediction Function

Developed a reusable function that:

accepts a borrower FICO score
maps borrower into a rating category
returns estimated probability of default

This enables scalable credit risk assessment for new mortgage applicants.

Technologies Used
Python
Pandas
NumPy
Matplotlib
Scikit-Learn
Jupyter Notebook
Key Skills Demonstrated
Credit Risk Analytics
Machine Learning
Logistic Regression
Probability of Default Modeling (PD)
Expected Loss Estimation
Mortgage Risk Analytics
Quantization & Bucketing
Financial Risk Modeling
Data Analysis
Predictive Analytics
