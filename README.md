# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1.Import dataset and print head,info of the dataset

2.Import kmeans and fit it to the dataset

3.Plot the graph using elbow method

4.Plot the customer segment

## Program & Output:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: VAMSI KRISHNA G
RegisterNumber: 212223220120
*/
```
```
import pandas as pd
import matplotlib.pyplot as plt
from sklearn.cluster import KMeans
data = pd.read_csv("C:\\Users\\admin\\Downloads\\Mall_Customers.csv")
print(data.head())
print(data.info())
print(data.isnull().sum())
```
![image](https://github.com/user-attachments/assets/f7be6b7d-fb67-4757-8f3c-9ec94585f267)
```
wcss = []
for i in range(1, 11):
    kmeans = KMeans(n_clusters=i, init="k-means++", random_state=42)
    kmeans.fit(data.iloc[:, 3:])
    wcss.append(kmeans.inertia_)
plt.plot(range(1, 11), wcss)
plt.xlabel("No_of_Clusters")
plt.ylabel("WCSS")
plt.title("Elbow Method")
plt.show()
```
![image](https://github.com/user-attachments/assets/f8b4b5fd-986d-4fba-b26c-dc6a1c95d09f)
```
km = KMeans(n_clusters=5, init="k-means++", random_state=42)
km.fit(data.iloc[:, 3:])
y_pred = km.predict(data.iloc[:, 3:])
print(y_pred)
data["cluster"] = y_pred
df0 = data[data["cluster"] == 0]
df1 = data[data["cluster"] == 1]
df2 = data[data["cluster"] == 2]
df3 = data[data["cluster"] == 3]
df4 = data[data["cluster"] == 4]
plt.scatter(df0["Annual Income (k$)"], df0["Spending Score (1-100)"], c="red", label="cluster 0")
plt.scatter(df1["Annual Income (k$)"], df1["Spending Score (1-100)"], c="black", label="cluster 1")
plt.scatter(df2["Annual Income (k$)"], df2["Spending Score (1-100)"], c="blue", label="cluster 2")
plt.scatter(df3["Annual Income (k$)"], df3["Spending Score (1-100)"], c="green", label="cluster 3")
plt.scatter(df4["Annual Income (k$)"], df4["Spending Score (1-100)"], c="magenta", label="cluster 4")
plt.legend()
plt.title("Customer Segments")
plt.xlabel("Annual Income (k$)")
plt.ylabel("Spending Score (1-100)")
plt.show()
```
![image](https://github.com/user-attachments/assets/d6e64a68-4205-4e47-b4ea-d18a3644af44)

## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
