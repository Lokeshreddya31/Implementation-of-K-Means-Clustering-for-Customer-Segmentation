# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Start the program
2. Import the necessary python libraries
3. Read the dataset of Mall_Customers csv file
4. From sklearn libraary select the cluster and import KMeans Clustering
5. Find the sum of squared distance between each points and the centroid in a cluster using Elbow Method
6. Plot the graph x and y as Number of Clusters and wcss respectively
7. Using the matplotlib library draw the scatter plot for the given number of clusters (ie. here n_clusters = 5)
8. Stop the program
## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: LOKESH REDDY A
RegisterNumber: 212223040104 
*/
import pandas as pd
import matplotlib.pyplot as plt
data=pd.read_csv("/content/Mall_Customers (3).csv")
data
data.head()
data.info()
data.isnull().sum()
from sklearn.cluster import KMeans
wcss=[]
for i in range(1,11):
  Kmeans=KMeans(n_clusters = i,init = "k-means++")
  Kmeans.fit(data.iloc[:,3:])
  wcss.append(Kmeans.inertia_)
plt.plot(range(1, 11), wcss[:10])
plt.xlabel("No. of Clusters")
plt.ylabel("WCSS")
plt.title("Elbow Method")
plt.show()
km=KMeans(n_clusters = 5)
km.fit(data.iloc[:,3:])
y_pred=km.predict(data.iloc[:,3:])
print(y_pred)
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
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="magenta",label="cluster4")
plt.legend()
plt.title("Customer Segments")
```

## Output:
![image](https://github.com/user-attachments/assets/6498c09a-3118-4afd-a7df-b88217e48835)

#### Y_Pred
![image](https://github.com/user-attachments/assets/dc5caac7-fe96-43a1-9f30-19b5a5da2f2e)

#### Cluster
![image](https://github.com/user-attachments/assets/d4c8473d-5736-437f-a1b6-b5fd46e079ba)

## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
