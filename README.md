# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Load the mall customers dataset and check for null values.
2. Use the Elbow Method to determine the optimal number of clusters by running KMeans with clusters ranging from 1 to 10 and calculating the within-cluster sum of squares (WCSS) for each.
3. Plot the WCSS against the number of clusters to identify the "elbow" point.
4. Set the number of clusters to 5 based on the Elbow Method and fit a KMeans model with this cluster count.
5. Predict and assign each customer to a cluster, adding the cluster labels to the dataset.
6. Separate the data into clusters and plot each cluster with different colors based on "Annual Income" and "Spending Score" to visualize customer segments.
## Program:
```Python
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: HASNA MUBARAK AZEEM
RegisterNumber: 212223240052
*/

import pandas as pd
df=pd.read_csv("Mall_Customers.csv")
df.head()
df.info()
df.isnull().sum()
from sklearn.cluster import KMeans
wcss=[]
import matplotlib.pyplot as plt
plt.plot(range(1,11),wcss)
plt.xlabel("No. of Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")
km=KMeans(n_clusters=5)
km.fit(df.iloc[:,3:])
y_pred=km.predict(df.iloc[:,3:])
y_pred
df["cluster"]=y_pred
data0=df[df["cluster"]==0]
data1=df[df["cluster"]==1]
data2=df[df["cluster"]==2]
data3=df[df["cluster"]==3]
data4=df[df["cluster"]==4]
plt.scatter(data0["Annual Income (k$)"],data0["Spending Score (1-100)"],c="red",label="cluster0")
plt.scatter(data1["Annual Income (k$)"],data1["Spending Score (1-100)"],c="black",label="cluster1")
plt.scatter(data2["Annual Income (k$)"],data2["Spending Score (1-100)"],c="blue",label="cluster2")
plt.scatter(data3["Annual Income (k$)"],data3["Spending Score (1-100)"],c="green",label="cluster3")
plt.scatter(data4["Annual Income (k$)"],data4["Spending Score (1-100)"],c="magenta",label="cluster4")
plt.legend()
plt.title("Customer segments")
```

## Output:

![Screenshot 2024-10-05 114548](https://github.com/user-attachments/assets/eb70b89f-03c1-4459-a8b9-4ac55afa0c9e)

![Screenshot 2024-10-05 114617](https://github.com/user-attachments/assets/ed1c5603-ff78-4866-adcb-04537c54e1df)

## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
