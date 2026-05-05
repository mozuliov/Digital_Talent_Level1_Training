#### This Session
>Provides a conceptual and practical introduction to machine learning, applying decision tree models to structured financial data for forecasting and classification.
#### Learning Objectives

**By the end of this session, students will be able to:**
>1. Articulate the distinction between **traditional rule-based programming** and **machine learning**.
>2. Explore and describe a structured business dataset using **Pandas**.
>3. Partition data into **training and testing sets** and explain the rationale for doing so.
>4. Train a **Decision Tree Classifier** using Scikit-Learn to predict customer churn.
>5. **Visualize** the learned decision rules as an interpretable business logic diagram.
>6. **Evaluate** model performance and generate a risk assessment for a new, unseen customer.

[![GitHub](https://img.shields.io/badge/GitHub-05_ML_for_Predictive_Forecasting-black?logo=github)](https://github.com/mozuliov/Digital_Talent_Level1_Training/tree/main/05%20Machine%20Learning%20for%20Predictive%20Forecasting)

**Working Environment:** [![Colab|41](https://img.shields.io/badge/Colab-blue)](https://colab.research.google.com)

Use the following code in **Colab** to load data from the customer_churn_data.csv file in **GitHub** repository:

```Python
url = "https://raw.githubusercontent.com/mozuliov/Digital_Talent_Level1_Training/5714aec79ea6553387790f40977383f66cc1ef9b/05%20Machine%20Learning%20for%20Predictive%20Forecasting/customer_churn_data.csv"

df = pd.read_csv(url)
```

**Recommended [[E Session 05 Additional Reading|Reading for Session 05]]