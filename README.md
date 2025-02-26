# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Moodle-Code Runner

## Algorithm
1. import pandas,matplotlib
2. read csv file and print data head,info(),isnull()
3. import Kmeans and wcss[]
4. assign for loop kmeans fit data.
5. wcss append and plot wcss value
6. plot x and y label and plot title.
7. predict the y value.
8. data cluster and assign cluster values and plot scatter for cluster values.
9. stop the program.

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: Sathish kumar M
RegisterNumber:  212220220042
*/

import pandas as pd
import matplotlib.pyplot as plt
data=pd.read_csv("/content/sample_data/Mall_Customers.csv")
data.head()
data.info()
data.isnull().sum()

from sklearn.cluster import KMeans
wcss = [] 

for i in range(1,11):
  kmeans=KMeans(n_clusters=i,init="k-means++")
  kmeans.fit(data.iloc[:,3:])
  wcss.append(kmeans.inertia_)

  plt.plot(range(1,11),wcss)
plt.xlabel("No.of clusters")
plt.ylabel("wcss")
plt.title("elbow method")

km=KMeans(n_clusters = 5)
km.fit(data.iloc[:,3:])

y_pred = km.predict(data.iloc[:,3:])
y_pred

data["cluster"]=y_pred
df0=data[data["cluster"]==0]
df1=data[data["cluster"]==1]
df2=data[data["cluster"]==2]
df3=data[data["cluster"]==3]
df4=data[data["cluster"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="black",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="blue",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="green",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="yellow",label="cluster4")
plt.legend()
plt.title("Customer segments")

```

## Output:
![K Means Clustering for Customer Segmentation](/OP%201.png)

![K Means Clustering for Customer Segmentation](/OP%202.png)

![K Means Clustering for Customer Segmentation](/OP%203.png)

![K Means Clustering for Customer Segmentation](/OP%204.png)

![K Means Clustering for Customer Segmentation](/OP%205.png)

## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
