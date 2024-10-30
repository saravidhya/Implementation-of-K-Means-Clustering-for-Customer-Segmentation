# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
Step 1. Start the program

Step 2. Import the necessary python libraries

Step 3. Read the dataset of Mall_Customers csv file

Step 4. From sklearn libraary select the cluster and import KMeans Clustering

Step 5. Find the sum of squared distance between each points and the centroid in a cluster using Elbow Method

Step 6. Plot the graph x and y as Number of Clusters and wcss respectively

Step 7. Using the matplotlib library draw the scatter plot for the given number of clusters (ie. here n_clusters = 5)

Step 8. Stop the program

## Program:

## Program to implement the K Means Clustering for Customer Segmentation.


```
Developed by: VIDHIYA LAKSHMI S
RegisterNumber:  212223230238
import pandas as pd
import matplotlib.pyplot as plt
data=pd.read_csv("Mall_Customers.csv")
data.head()
```
![image](https://github.com/user-attachments/assets/069e7432-eadf-4401-8db5-4d79b9de94c4)

```
data.info()
```
![image](https://github.com/user-attachments/assets/7247a85d-a997-4b21-bdb2-0d1bbdee160f)

```
data.isnull().sum()
```
![image](https://github.com/user-attachments/assets/d7cb65ca-43a5-44c9-ab2f-88bc9149cb5d)

```
from sklearn.cluster import KMeans
wcss=[]
for i in range(1,11):
  kmeans=KMeans(n_clusters=i,init="k-means++")
  kmeans.fit(data.iloc[:,3:])
  wcss.append(kmeans.inertia_)
plt.plot(range(1,11),wcss)
plt.xlabel("no of cluster")
plt.ylabel("wcss")
plt.title("Elbow Method")
```
![image](https://github.com/user-attachments/assets/734b1e16-5f92-4267-bacb-0236973c11e9)

```
km=KMeans(n_clusters=5)
km.fit(data.iloc[:,3:])
y_pred=km.predict(data.iloc[:,3:])
y_pred
```
![image](https://github.com/user-attachments/assets/3b147b8d-e701-4381-ad9b-7ee63508907e)

```
data["cluster"]=y_pred
df0=data[data["cluster"]==0]
df1=data[data["cluster"]==1]
df2=data[data["cluster"]==2]
df3=data[data["cluster"]==3]
df4=data[data["cluster"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="pink",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="green",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="blue",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="black",label="cluster4")
plt.legend()
plt.title("Customer Segments")
```
![image](https://github.com/user-attachments/assets/f928a25e-5d1f-455b-bfdd-6a25a3877a72)

*/
```

## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
