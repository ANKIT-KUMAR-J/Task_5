📊 Customer Churn Analysis

This project performs Exploratory Data Analysis (EDA) on the Customer Churn dataset to identify factors influencing customer retention and churn.
The goal is to clean the dataset, explore features, visualize trends, and draw meaningful insights.

⚡ Dataset Overview

File: Customer Churn.csv

Target Column: Churn (Yes/No)

Rows & Columns: ~7,000 customers, multiple categorical and numerical features

🔍 Step 1: Basic Exploration
1. Dataset Information
df.info()


📌 Provides column names, data types, and missing values.

2. Summary Statistics
df.describe()


📌 Gives count, mean, std, min, max, and percentiles for numerical features.

3. Frequency Distribution
df['Churn'].value_counts()


📌 Shows how many customers churned vs retained.

📈 Step 2: Visual Explorations
🔹 Correlation Heatmap
sns.heatmap(df.corr(numeric_only=True), cmap="YlGnBu", annot=True)


✔️ Helps identify linear relationships between numerical features.

Observation:

MonthlyCharges and TotalCharges are highly correlated.

tenure has a strong negative correlation with Churn.

🔹 Pairplot
sns.pairplot(df, vars=['tenure','MonthlyCharges','TotalCharges'], hue="Churn")


✔️ Visualizes pairwise relationships.

Observation:

Customers with short tenure + high monthly charges are more likely to churn.

🔹 Histogram: Tenure Distribution
sns.histplot(x="tenure", data=df, bins=72, hue="Churn")


✔️ Shows distribution of customer tenure.

Observation:

Majority churn happens in the first 12–24 months.

🔹 Scatterplot: Tenure vs Monthly Charges
sns.scatterplot(x="tenure", y="MonthlyCharges", data=df, hue="Churn")


✔️ Detects customer clusters.

Observation:

Churn is high among customers with low tenure + high charges.

🔹 Boxplot: Monthly Charges vs Churn
sns.boxplot(x="Churn", y="MonthlyCharges", data=df)


✔️ Compares distributions across churn groups.

Observation:

Churned customers have higher median monthly charges.

🔹 Countplot: Contract vs Churn
sns.countplot(x="Contract", data=df, hue="Churn")


✔️ Checks customer churn by contract type.

Observation:

Customers on Month-to-Month contracts churn the most.

🔹 Pie Chart: Churn Percentage
plt.pie(df['Churn'].value_counts(), labels=df['Churn'].unique(), autopct="%1.2f%%")


✔️ Quick snapshot of churn rate.

Observation:

Roughly 26–27% customers churned.

📑 Step 3: Key Findings

Tenure & Churn:

Early-stage customers (0–24 months) are at the highest risk of churn.

Charges & Churn:

Higher monthly charges increase the likelihood of churn.

Contract Type:

Month-to-month customers have significantly higher churn than yearly/2-year contracts.

Senior Citizens:

Senior citizens show slightly higher churn compared to non-senior customers.

Correlation Insights:

MonthlyCharges and TotalCharges are strongly correlated, so one may be dropped in modeling.

🎯 Conclusion

This EDA shows that tenure, contract type, and monthly charges are the most influential factors in predicting churn.
Businesses can reduce churn by:

Offering loyalty programs for early customers.

Providing discounts on long-term contracts.

Monitoring customers with high monthly charges for proactive retention.
