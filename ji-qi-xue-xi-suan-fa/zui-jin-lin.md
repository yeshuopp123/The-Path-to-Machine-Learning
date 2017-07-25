
# sklearn
```python
import numpy as np
import pandas as pd
from sklearn.datasets import load_breast_cancer
from sklearn.model_selection import train_test_split
from sklearn.neighbors import KNeighborsClassifier

cancer = load_breast_cancer()

print(cancer.DESCR)

def convertToDataframe():
    feature = cancer['feature_names']
    df = pd.DataFrame(cancer.data,index=range(569),columns=feature)
    df['target'] =  cancer.target    
    return df

print("Now convert the dataset into dataframe:\n")
cancerdf = convertToDataframe()
print(cancerdf.head())

def classDistribution(cancerdf):
    malignant = len(cancerdf[cancerdf['target']==0])
    benign = len(cancerdf[cancerdf['target']==1])
    index = ['malignant', 'benign']
    target = pd.Series([malignant,benign],index=index)
    return target

def splitDataset(cancerdf):
    X = cancerdf[cancerdf.columns[:30]]
    y = cancerdf[cancerdf.columns[30]]
    X_train,X_test, y_train, y_test = train_test_split(X,y,random_state = 0) 
    return X_train, X_test, y_train, y_test


def trainKNN(feature_data,class_data,k):
    knn = KNeighborsClassifier(n_neighbors=k)
    knn.fit(feature_data,class_data)
    return knn

print("\nThe class distribution is:\n")
print(classDistribution(cancerdf))


print("\nUsing train_test_split, split X and y into training and test sets (X_train, X_test, y_train, and y_test).using random_state=0\n")

X_train, X_test, y_train, y_test = splitDataset(cancerdf)

print("X_train: " ,X_train.shape)
print("X_test:  " ,X_test.shape)
print("y_train: " ,y_train.shape)
print("y_test:  ", y_test.shape)


print("Now, training the Knn model: done!\n")
knn = trainKNN(X_train,y_train,1)

print("Predict the class label using the mean value for each feature.\n")
print("The mean value for each feature.\n")
means = cancerdf.mean()
print(means)
means = means[:-1].values.reshape(1, -1)
means_predict = knn.predict(means)
print("The predict result : ",means_predict)


print("Predict the class labels for the test set X_test")
test_predict = knn.predict(X_test)
print("The prediction result ：\n",test_predict)
print("The prediction result accuracy : ",knn.score(X_test,y_test))
```