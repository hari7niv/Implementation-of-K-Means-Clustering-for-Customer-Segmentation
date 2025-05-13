# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Load and inspect data: Import customer dataset, check structure and missing values.
2. Determine clusters: Use the Elbow Method to find optimal number of clusters via WCSS.
3. Apply K-Means: Fit K-Means with selected clusters (e.g., 5) on income and spending data.
4. Visualize clusters: Assign cluster labels and plot customer segments by color.

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: Hari Nivedhan P
RegisterNumber:  212224220031
*/

import pandas as pd
import matplotlib.pyplot as plt
data = pd.read_csv("Mall_Customers.csv")

data.head()

data.info()

data.isnull().sum()

from sklearn.cluster import KMeans
wcss = []

for i in range(1,11):
    kmeans = KMeans(n_clusters = i,init = "k-means++")
    kmeans.fit(data.iloc[:,3:])
    wcss.append(kmeans.inertia_)

plt.plot(range(1,11),wcss)
plt.xlabel("No of Cluster")
plt.ylabel("wcss")
plt.title("Elbow Method")

km = KMeans(n_clusters = 5)
km.fit(data.iloc[:,3:])

KMeans(n_clusters=5)

y_pred = km.predict(data.iloc[:,3:])
y_pred

data["cluster"]=y_pred
df0 = data[data["cluster"]==0]
df1 = data[data["cluster"]==1]
df2 = data[data["cluster"]==2]
df3 = data[data["cluster"]==3]
df4 = data[data["cluster"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="black",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="blue",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="green",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="magenta",label="cluster4")
plt.legend()
plt.title("Customer Segments")

```

## Output:
![Screenshot 2025-05-12 110804](https://github.com/user-attachments/assets/79b39df4-b74b-4a9f-ae75-cc0177f2c43d)
![Screenshot 2025-05-12 110810](https://github.com/user-attachments/assets/e1f526bc-7e81-4e16-a4f9-7a8793582ef4)
![Screenshot 2025-05-12 110819](https://github.com/user-attachments/assets/c063d102-ab4f-47c8-8997-b39b11ad117c)



## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
