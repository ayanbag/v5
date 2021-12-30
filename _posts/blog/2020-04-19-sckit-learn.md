---
layout: post
title: "Kickstart to Machine Learning with Sckit-learn"
author: "Ayan Bag"
categories: journal
tags: [python,machine-learning]
image: 
---


**Sckit-learn** is a open source Python library that provides many unsupervised and supervised learning algorithms. It also  implements a range of preprocessing, cross-validation and visualization algorithms using a unified interface

Basic example:
```python
>>> from sklearn import neighbors, datasets, preprocessing
>>> from sklearn.model_selection import train_test_split
>>> from sklearn.metrics import accuracy_score
>>> iris = datasets.load_iris()
>>> X, y = iris.data[:, :2], iris.target
>>> X_train, X_test, y_train, y_test = train_test_split(X, y, random_state=33)
>>> scaler = preprocessing.StandardScaler().fit(X_train)
>>> X_train = scaler.transform(X_train)
>>> X_test = scaler.transform(X_test)
>>> knn = neighbors.KNeighborsClassifier(n_neighbors=5)
>>> knn.fit(X_train, y_train)
>>> y_pred = knn.predict(X_test)>>> accuracy_score(y_test, y_pred)
```



### Important features of Sckit-learn

- Simple and efficient tools for data mining and data analysis. 
- Accessible to everybody and reusable in various contexts.
- Built on the top of NumPy, SciPy, and matplotlib.
- Open source, commercially usable – BSD license



### Components of Sckit-learn

Scikit-learn comes loaded with a lot of features. Here are a few of them to help you understand the spread:

- **Supervised Learning algorithms** : Supervised learning is the machine learning task of learning a function that maps an input to an output based on example input-output pairs. It infers a function from labeled training data consisting of a set of training examples.
- **Unsupervised Learning Algorithms** : There is a large spread of machine learning algorithms in the offering – starting from clustering, factor analysis, principal component analysis to unsupervised neural networks.
- **Cross-validation** : These are re-sampling procedure used to evaluate machine learning models on a limited data using sklearn.
- **Feature Extraction** : Scikit-learn for extracting features from images and text 



### Installation of Sckit-learn

Sckit-learn requires:
- Numpy
- SciPy as its dependencies

Before installing Sckit-learn , ensure that **Numpy** and **SciPy** is installed in the working directory.
The easiest way to install **Sckit-learn** is by using ```pip``` 

```python
pip install -U scikit-learn
```


---
## Loading The Data 

Your data needs to be numeric and stored as NumPy arrays or SciPy sparse matrices. Other types that are convertible to numeric arrays, such as Pandas DataFrame, are also acceptable.

```python
>>> import numpy as np
>>> X = np.random.random((30,8))
>>> y = np.array(['A','A','B','A','B'])
>>> X[X < 0.7] = 0
```


---
## Training and Testing Data

```Python
>>> from sklearn.model_selection import train_test_split
>>> X_train, X_test, y_train, y_test = train_test_split(X,Y,random_state=0)
```


---
## Preprocessing The Data

Data Preprocessing is a step in which data gets transformed or encoded, to bring it in such a state that the machine can easily parse it. In other words, the data now can be easily interpreted by the algorithms.

### Standardization

Standardization refers to shifting the distribution of each attribute to have a mean of zero and a standard deviation of one (unit variance).

```python
>>> from sklearn.preprocessing import StandardScaler
>>> scaler = StandardScaler().fit(X_train)
>>> standardized_X = scaler.transform(X_train)
>>> standardized_X_test = scaler.transform(X_test)
```

### Normalization

```python
>>> from sklearn.preprocessing import Normalizer
>>> scaler = Normalizer().fit(X_train)
>>> normalized_X = scaler.transform(X_train)
>>> normalized_X_test = scaler.transform(X_test)
```

### Binarization

```python
>>> from sklearn.preprocessing import Binarizer
>>> binarizer = Binarizer(threshold=0.0).fit(X)
>>> binary_X = binarizer.transform(X)
```

### Encoding Categorical Features

```python
>>> from sklearn.preprocessing import LabelEncoder
>>> enc = LabelEncoder()
>>> y = enc.fit_transform(y)py
```

### Imputing Missing Values

```python
>>> from sklearn.preprocessing import Imputer
>>> imp = Imputer(missing_values=0, strategy='mean', axis=0)
>>> imp.fit_transform(X_train)
```

### Generating Polynomial Features

```python
>>> from sklearn.preprocessing import PolynomialFeatures
>>> poly = PolynomialFeatures(5)
>>> poly.fit_transform(X)
```



## Creating the Model

### Supervised Learning Estimators

```python
Linear Regression
>>> from sklearn.linear_model import LinearRegression
>>> lr = LinearRegression(normalize=True)   

Support Vector Machines (SVM)
>>> from sklearn.svm import SVC
>>> svc = SVC(kernel='linear')   

Naive Bayes 
>>> from sklearn.naive_bayes import GaussianNB
>>> gnb = GaussianNB()   

KNN
>>> from sklearn import neighbors
>>> knn = neighbors.KNeighborsClassifier(n_neighbors=5)
```

### Unsupervised Learning Estimators

```python
Principal Component Analysis (PCA)
>>> from sklearn.decomposition import PCA
>>> pca = PCA(n_components=0.95)   

K Means
>>> from sklearn.cluster import KMeans
>>> k_means = KMeans(n_clusters=3, random_state=0)
```


---
## Model Fitting

```python
Supervised learning 
>>> lr.fit(X, y)							# Fit the model to the data
>>> knn.fit(X_train, y_train)
>>> svc.fit(X_train, y_train)   

Unsupervised Learning
>>> k_means.fit(X_train)					# Fit the model to the data
>>> pca_model = pca.fit_transform(X_train)	# Fit to data, then transform it
```


---
## Prediction

```python
Supervised Estimators
>>> y_pred =svc.predict(np.random.random((2,5)))	# Predict labels
>>> y_pred = lr.predict(X_test)						# Predict labels
>>> y_pred = knn.predict_proba(X_test)   			# Estimate probability of a label

Unsupervised Estimators
>>> y_pred = k_means.predict(X_test)				# Predict labels in clustering algos
```


---
## Evaluating The Model's Performance

### Classification Metrics

```python
 Accuracy Score
 >>> knn.score(X_test, y_test)							# Estimator score method
 >>> from sklearn.metrics import accuracy_score			# Metric scoring functions 
 >>> accuracy_score(y_test, y_pred)  
 
 Classification Report
 >>> from sklearn.metrics import classification_report	# Precision, recall, f1-score
 >>> print(classification_report(y_test, y_pred))  
 
 Confusion Matrix
 >>> from sklearn.metrics import confusion_matrix
 >>> print(confusion_matrix(y_test, y_pred))
```

### Regression Metrics

```python
Mean Absolute Error
>>> from sklearn.metrics import mean_absolute_error
>>> y_true = [3, -0.5, 2]
>>> mean_absolute_error(y_true, y_pred)   

Mean Squared Error
>>> from sklearn.metrics import mean_squared_error
>>> mean_squared_error(y_test, y_pred)   

R² Score
>>> from sklearn.metrics import r2_score
>>> r2_score(y_true, y_pred)
```

### Clustering Metrics

```python
Adjusted Rand Index
>>> from sklearn.metrics import adjusted_rand_score
>>> adjusted_rand_score(y_true, y_pred)    

Homogeneity
>>> from sklearn.metrics import homogeneity_score
>>> homogeneity_score(y_true, y_pred)  

V-measure
>>> from sklearn.metrics import v_measure_score
>>> metrics.v_measure_score(y_true, y_pred)  
```

### Cross-Validation

```python
>>> from sklearn.cross_validation import cross_val_score
>>> print(cross_val_score(knn, X_train, y_train, cv=4))
>>> print(cross_val_score(lr, X, y, cv=2))
```


---
## Tuning The Model

### Grid Search

```python
>>> from sklearn.grid_search import GridSearchCV
>>> params = {"n_neighbors": np.arange(1,3), "metric": ["euclidean", "cityblock"]}
>>> grid = GridSearchCV(estimator=knn, param_grid=params)
>>> grid.fit(X_train, y_train)
>>> print(grid.best_score_)
>>> print(grid.best_estimator_.n_neighbors)
```

### Randomized Parameter Optimization

```python
>>> from sklearn.grid_search import RandomizedSearchCV
>>> params = {"n_neighbors": range(1,5), "weights": ["uniform", "distance"]}
>>> rsearch = RandomizedSearchCV(estimator=knn,param_distributions=params,cv=4,n_iter=8, random_state=5)
>>> rsearch.fit(X_train, y_train)>>> print(rsearch.best_score_)
```


---
## Reference

- [DataCamp](https://www.datacamp.com/courses/topic:machine_learning)
- [Machine Learning Mastery](https://machinelearningmastery.com/start-here/#python)
- [TowardsDataScience](https://towardsdatascience.com/scale-standardize-or-normalize-with-scikit-learn-6ccc7d176a02)
- [Analytics Vidya](https://www.analyticsvidhya.com/blog/2017/09/common-machine-learning-algorithms/)



