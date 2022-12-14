# UON-Comparison-Classification-Algorithms

# Credit Risk Classification

<a id='introduction'></a>

## Introduction
## The business question

### <span style="color:blue"> Credit Risk Classification helps in understanding what factors are most responsible for credit defaults.</span>

**The goal:** Classify features that contribute to a loan default or repayment.
Credit risk modeling is the process of using statistical techniques and machine learning algorithms to predict the likelihood that a borrower will default on a loan. This is important for lenders because it helps them to assess the risk of providing a loan to a particular borrower, and to set appropriate interest rates for that loan. 

Machine learning algorithms can be trained on historical data about loans and borrowers in order to identify patterns and make more accurate predictions about the likelihood of default. These models can take into account a wide range of factors, including the borrower's credit score, income, debt-to-income ratio, and other financial information. 

The goal of credit risk modeling is to help lenders make more informed decisions about the risks of lending money, and to manage those risks more effectively.

<ins>**How does this help UON ML 2022 Class?**<ins>
    
    By working on credit risk modeling projects, students can gain hands-on experience with applying machine learning algorithms to real-world data, and can learn how to use these algorithms to make predictions and identify patterns. This can help students to develop their technical skills and to better understand the practical applications of machine learning.

    In addition, studying credit risk modeling can also help students to develop their understanding of the financial industry and the role that machine learning plays in it. This can be valuable knowledge for students who are interested in pursuing careers in finance or in related fields. By learning about credit risk modeling, students can gain a better understanding of the challenges and opportunities that machine learning presents for the financial industry, and can develop the skills and knowledge that are needed to succeed in this field.

<ins> ** How does credit risk modelling help financial institutions?**<ins>
    
    Credit risk modeling can help financial institutions in several ways. First, it can help them to assess the risk of lending money to a particular borrower. By using machine learning algorithms to analyze historical data, lenders can predict the likelihood that a borrower will default on a loan, which can help them to decide whether to provide a loan and how much to charge in interest. This can help to reduce the overall risk of lending and to ensure that lenders only provide loans to borrowers who are likely to be able to repay them.

    Second, credit risk modeling can help financial institutions to manage their loan portfolios more effectively. By using these models to identify high-risk borrowers, lenders can take steps to reduce their exposure to those risks, such as by requiring higher interest rates or stricter repayment terms. This can help to reduce the overall level of risk in the lender's portfolio and to protect against losses from defaults.

    Third, credit risk modeling can help financial institutions to identify potential opportunities for growth. By analyzing the patterns in their historical data, lenders can identify segments of the market where there may be strong demand for loans, and where they may be able to increase their lending and generate more revenue. This can help them to grow their businesses and to better serve the needs of their customers.

## Solution

* **Assumptions:**
    1. The data used to train the model is representative of the population of borrowers that the model will be used to predict. This means that the data should be a good representation of the characteristics and behaviors of borrowers, and should accurately reflect the likelihood of default.

    2. The data used to train the model is accurate and complete. This means that the data should not contain any errors or missing values, and should be consistent with other sources of information about the borrowers.

    3. The statistical models used to predict default are valid and reliable. This means that the models should be based on sound statistical principles and should be able to accurately predict the likelihood of default.

    4. The model will be used in a stable and predictable environment. This means that the model should be able to accurately predict default in a variety of different conditions and scenarios, and should not be affected by changes in the economic or regulatory environment.

    5. The model will be used consistently over time. This means that the model should be able to accurately predict default for a long period of time, and should not need to be frequently retrained or updated.

<ins>**Observations**:<ins>

    - There are a total of 24,435 records in the dataset. 
    - Two columns have missing values: 'loan_int_rate' and 'person_emp_length'. 
    - The dataset is imbalanced, in a ratio of 1:4.6 (default:no default).
    - Loans taken for medical purposes have the highest default rates, followed closely by education loans. 
    - There is no default rate amongst grade A and B loans, while grade C has the highest default rates. 
    - Categorical variables seem to have a big influence on the default rates. They need to be used in the model. 
    - Apart from loan_int_rate and loan_status, other numerical variables do not seem to have a strong correlation with credit risk. 
    - From the categorical features, loan grade has the biggest effect on credit risk. 

## Results
    - Three classifiers are trained on the dataset: K Nearest Neighbors, Decision Trees and Naive Bayes. 
    - We use F1 score as the evaluation metric. 
        The F1 score is a commonly used evaluation metric for classifiers, particularly in the context of imbalanced datasets. The F1 score is the harmonic mean of the precision and recall of a classifier, and is calculated as follows:

        $F1 = 2 * (precision * recall) / (precision + recall)$

        The precision of a classifier is the number of true positives (i.e. correctly predicted positive instances) divided by the total number of predicted positive instances. The recall of a classifier is the number of true positives divided by the total number of actual positive instances.

        The F1 score is a good evaluation metric for classifiers because it takes into account both the precision and the recall of the classifier. In other words, it considers both the number of false positives and the number of false negatives. This is particularly important in the context of imbalanced datasets, where there may be a large number of negative instances compared to positive instances. In this case, a classifier that simply predicts the majority class (i.e. the negative class) will have a high accuracy, but a low precision and recall. The F1 score, on the other hand, will be lower for such a classifier, providing a more accurate measure of its performance.

        Overall, the F1 score is a useful evaluation metric for classifiers because it provides a balance between precision and recall, and can be used to accurately evaluate the performance of a classifier on imbalanced datasets.
    - Due to the imbalanced nature of the dataset, we use a combination of oversampling based on minority class (defaults) and undersampling based on majority class for model training and inference. 
        Oversampling and undersampling are two techniques that can be used to adjust the balance of classes in a dataset. These techniques can be effective in improving the performance of some machine learning algorithms, particularly on imbalanced datasets.

        Oversampling involves increasing the number of instances in the minority class, while undersampling involves decreasing the number of instances in the majority class. These techniques can be useful because they can help a machine learning model to more accurately learn the characteristics of the minority class, which can in turn improve its ability to make predictions on new data.

        SMOTE (Synthetic Minority Oversampling Technique) is a specific oversampling technique that generates new synthetic samples in the minority class by interpolating between existing samples. While SMOTE can be effective in some cases, oversampling and undersampling can be more flexible because they allow you to adjust the balance of classes in a dataset in a more customized way. Additionally, SMOTE can sometimes lead to overfitting, particularly if it is used to generate too many synthetic samples. For these reasons, oversampling and undersampling can sometimes be a better choice than SMOTE.
    - Overall, Decision Tree Classifier has the highest F1 score of 0.82. We, however, find Naive Bayes to have the most balanced scores, however. 
        Naive Bayes and decision tree classifiers are two different types of machine learning algorithms that can be used for classification tasks. Both algorithms can be effective in certain situations, but they have different strengths and weaknesses.

        Naive Bayes is a probabilistic classifier that makes predictions based on the probabilities of different events occurring. It is called "naive" because it makes the assumption that all of the features in a dataset are independent of each other, which is not always true in real-world data. Despite this assumption, naive Bayes classifiers can often produce good results, particularly on datasets with many features. They are also relatively simple to train and use, which makes them a good choice for applications where computational efficiency is important.

        Decision tree classifiers, on the other hand, make predictions by learning a series of rules that split the data into smaller and smaller subsets. Each split is based on a different feature, and the tree continues to grow until it reaches a point where it can make highly accurate predictions. Decision tree classifiers are useful because they can handle complex data with many features, and they can provide clear explanations of their predictions. However, they can be prone to overfitting, particularly if the tree is allowed to grow too large.

        In general, naive Bayes classifiers are better than decision tree classifiers when the goal is to make fast and accurate predictions on large datasets with many features. Decision tree classifiers are better when it is important to understand the reasons behind the predictions and to avoid overfitting. The best choice of algorithm will depend on the specific details of the dataset and the requirements of the application.