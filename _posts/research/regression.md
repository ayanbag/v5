---
layout: post
title: "A Comparative Study of Regression Algorithms for Predicting Graduate Admission to a University"
author: "Ayan Bag" 
categories: journal
tags: [Linear Regression , Random Forest Regression , Decision Tree Regression]
image:
---

# Abstract

Each year a large portion of students apply for graduate programs to further their education and get a deeper knowledge in their academic or career path. Universities usually consider many factors to choose between the pool of candidates. In this paper, we will be studying and analyzing these factors for graduate applications and give the probability of getting admission in that university, as output. We will be applying multiple regression models, such as Linear Regression, Decision Trees and Random Forest, to the data, and eventually, compare the models with the best score. In addition to the $ R^2 $ Score, other performance error metrics like Mean Absolute Error, Mean Square Error, and Root Mean Square Error are computed and showcased.

<br/>

# 1. Introduction

The admission to a graduate program is a very exhaustive and hectic task that requires thorough months of preparation to build a good profile and choosing universities that offer relevant programs. Many of students have problems of knowing their chances of admissions for specific universities based on their resume, and sometimes they will spend plenty of time and energy searching and applying to many academic institutions without getting good results. Some of them are whether going to give up on their plans, get to a lower ranked university, or even face some mental issues such as depression and feeling of failure. Here, using a machine learning approach, we will train our data on a range of parameters, from stellar to mediocre profile. After training, new data will be fed to the system to determine the outcome, and sample data will be tested against three different models stated earlier, in order to understand the performance of each model both in theoretically and visually. In this paper, all parameters necessary for the admission purpose like GRE Score, TOEFL Score, University Rating, Statement of Purpose and Letter of Recommendation Strength, Undergraduate GPA, and Research Experience are taken into consideration.

<br/>

# 2. Dataset 

The dataset, we are using, consists of 500 grad student's records containing information about the GRE Scores (in 340 scale), TOEFL Scores (in 120 scale), University Rating (on scale of 5), Statement of Purpose Strength (on scale of 5), Letter of Recommendation Strength (on scale of 5), CGPA (Undergraduate Grade Point), Research Experience (yes or no in which 1 denotes Yes and 0 denotes No) and Chance of Admit (a value between 0 and 1), being the target variable. In the data-set, 6 features are continuous with only 1 feature, Research Experience as categorical.

<br/>

# 3. Methodology
## 3.1 Shuffling and Spliting

The dataset is consistently shuffled and split into Training and Test Set i.e $85\%$ of 500 instances will be in Traning Set and rest $15\%$ will be in Test Set.

<br/>

## 3.2 Linear Regression

Linear Regression is one of the simplest regression models used to predict results. Its main goal, is to obtain relationship between **Independent variable (X)** and **Dependent variable (Y)**. Linear regression was the first type of regression analysis to be studied rigorously and to be used extensively in practical applications. This is because models that depend linearly on their unknown parameters are easier to fit than models that are non-linearly related to their parameters and because the statistical properties of the resulting estimators are easier to determine. In the case of Simple Linear Regression, there is one independent and one dependent variable. But, in our dataset, we have more than one independent variable and one dependent variable, so we will be using the Multiple Linear Regression Model. The Multiple Linear Regression will try to built a relationship between two or more exploratory data and a response variable by fitting a linear equation to observed data.


<figure><p style="text-align:center;"><img src="../assets/img/regression/LR1.png" alt="Fig"></p>  <figcaption  style="text-align:center;">Fig.1 - Linear Regression</figcaption></figure>

The Equation:  $ y = b_0 + b_1 * x_1 + b_2 * x_2 + ... + b_n * x_n$. This equation represents Multiple Linear Regression where $x_1$ to $x_n$ is the independent variables and y is the dependent variable.

We evaluated our train set and test set using the Linear Regression Model. As mentioned above, we splited the data into training data and test data in the ratio of 17:3 out of 500 instances. In above plot **Figure 1**,shows that there is a moderate, positive linear correlation between the predicted and the actual value. **Table 1** shows the evaluation metrics that we obtained.

<figure><p style="text-align:center;"><img src="../assets/img/regression/LRT1.png" alt="Table"></p>  <figcaption  style="text-align:center;">Table.1 - Evaluation Metrics of Linear Regression</figcaption></figure>



**R-Square** represents the proportion of variance(y) that has been explained by the independent variables(X) in the model. It provides an indication of goodness of fit and therefore a measure of how well the unseen samples are likely to be predicted by the model, thorough the proportion of explained variable. 


**Root Mean Square Error** represents the standard deviation of the residuals (i.e the difference between the predicted value and actual value)

<br/>

## 3.3 Random Forest Regression

A Random Forest is an ensemble technique capable of performing both regression and classification tasks with the use of multiple decision trees and a technique called Bootstrap and Aggregation, commonly known as bagging. The basic idea behind this is to combine multiple decision trees in determining the final output rather than relying on individual decision trees. Random Forest has multiple decision trees as base learning models. We randomly perform row sampling and feature sampling from the dataset forming sample datasets for every model. This part is called Bootstrap.  The random forest model is very good at handling tabular data with numerical features, or categorical features with fewer than hundreds of categories. Unlike linear models, random forests are able to capture non-linear interaction between the features and the target.

<figure><p style="text-align:center;"><img src="../assets/img/regression/RF.png" alt="Fig"></p>  <figcaption  style="text-align:center;">Fig.2 - Random Forest Regression</figcaption></figure>

Here, I have considered 100 estimators with the maximum depth of 10 for our model. Then I evaluate of metrics for this value of estimators. **Table 2** shows the evaluation metrics that we obtained.

<figure><p style="text-align:center;"><img src="../assets/img/regression/RFT1.png" alt="Table"></p>  <figcaption  style="text-align:center;">Table.2 - Evaluation Metrics of Random Forest Regression</figcaption></figure>

<br/>

## 3.4 Decision Tree Regression

Decision tree builds regression or classification models in the form of a tree structure. It breaks down a dataset into smaller and smaller subsets while at the same time an associated decision tree is incrementally developed. The final result is a tree with decision nodes and leaf nodes. A decision node has two or more branches, each representing values for the attribute tested. Leaf node represents a decision on the numerical target. The topmost decision node in a tree which corresponds to the best predictor called root node. Decision trees can handle both categorical and numerical data. 


<figure><p style="text-align:center;"><img src="../assets/img/regression/DT.png" alt="Fig"></p>  <figcaption  style="text-align:center;">Fig.3 - Decision Tree Regression</figcaption></figure>

Decision trees regression normally use mean squared error (MSE) to decide to split a node in two or more sub-nodes. Here, we have evaluated the Decision Tree with maximum numbers of features which is the default actually. **Table 3** shows the evaluation metrics that we obtained.

<figure><p style="text-align:center;"><img src="../assets/img/regression/DTT1.png" alt="Table"></p>  <figcaption  style="text-align:center;">Table.3 - Evaluation Metrics of Decision Tree Regression</figcaption></figure>

<br/>

# 4. Conclusion

Now, after evaluating all three models on the dataset, we compare the models performances on basis of two important metrics R-Squared Score and Mean Squared Error(MSE) to find out which model is better.

<figure><p style="text-align:center;"><img src="../assets/img/regression/comp.png" alt="Table"></p>  <figcaption  style="text-align:center;">Table.4 - Perfomance Analysis</figcaption></figure>

Now, it is pretty clear that Linear Regression performs best on our data set, with low MSE and high R-Square Score, followed by Random Forrest Regression. This can be due to the linear dependencies of features in the dataset although inclusion of few scattered data affected our Linear Model to some extend.

<figure><p style="text-align:center;"><img src="../assets/img/regression/comp_grp.png" alt="Fig"></p>  <figcaption  style="text-align:center;">Fig.4 - Algorithm Performance Comparison</figcaption></figure>


Moreover, we evaluated some unseen profiles using our best performing model, Linear Regression to see how well it performs. The unseen profile of students with test scores as follows :

<figure><p style="text-align:center;"><img src="../assets/img/regression/fc.png" alt="Table"></p>  <figcaption  style="text-align:center;">Table.6 - Unseen Data's Test Scores</figcaption></figure>


The result obtained closely resemble actual chances, so it is clear that the model perform well on unseen data

<br/>

# Other Links:

## 1. Cite as

>Bag, Ayan. "A comparative study of regression algorithms for predicting graduate admission to a university." (2020). ([pdf](https://www.researchgate.net/profile/Ayan-Bag/publication/343280957_A_Comparative_Study_of_Regression_Algorithms_for_Predicting_Graduate_Admission_to_a_University/links/5f7e960aa6fdccfd7b4f7ad1/A-Comparative-Study-of-Regression-Algorithms-for-Predicting-Graduate-Admission-to-a-University.pdf))



*Bibtex :*
```
@article{bag2020comparative,
  title={A comparative study of regression algorithms for predicting graduate admission to a university},
  author={Bag, Ayan},
  year={2020}
}
``` 