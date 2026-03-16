# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1.Data Preparation: Load and explore customer data.
2.Determine Optimal Clusters: Use the Elbow Method to find the best number of clusters.
3.Apply K Means Clustering: Perform clustering on customer data. 
4.Visualize Segmented Customers: Plot clustered data to visualize customer segments.

## Program:
```
import pandas as pd
import matplotlib.pyplot as plt
from sklearn.cluster import KMeans
data = pd.read_csv("/content/Mall_Customers (1).csv")
print(data.head())
print(data.info())
print(data.isnull().sum())
wcss = []
for i in range(1, 11):
    kmeans = KMeans(n_clusters=i, init="k-means++", random_state=42)
    kmeans.fit(data.iloc[:, 3:5])
    wcss.append(kmeans.inertia_)
plt.plot(range(1, 11), wcss)
plt.xlabel("No_of_Clusters")
plt.ylabel("WCSS")
plt.title("Elbow Method")
plt.show()
km = KMeans(n_clusters=5, random_state=42)
km.fit(data.iloc[:, 3:5])
y_pred = km.predict(data.iloc[:, 3:5])
data["cluster"] = y_pred
df0 = data[data["cluster"] == 0]
df1 = data[data["cluster"] == 1]
df2 = data[data["cluster"] == 2]
df3 = data[data["cluster"] == 3]
df4 = data[data["cluster"] == 4]
plt.scatter(df0["Annual Income (k$)"], df0["Spending Score (1-100)"], c="red", label="Cluster 0")
plt.scatter(df1["Annual Income (k$)"], df1["Spending Score (1-100)"], c="black", label="Cluster 1")
plt.scatter(df2["Annual Income (k$)"], df2["Spending Score (1-100)"], c="blue", label="Cluster 2")
plt.scatter(df3["Annual Income (k$)"], df3["Spending Score (1-100)"], c="green", label="Cluster 3")
plt.scatter(df4["Annual Income (k$)"], df4["Spending Score (1-100)"], c="magenta", label="Cluster 4")
plt.xlabel("Annual Income (k$)")
plt.ylabel("Spending Score (1-100)")
plt.title("Customer Segments")
plt.legend()
plt.show()
Developed by: AMIRDAVARSHINI D
RegisterNumber:212225230013  

```

## Output:
<img src="https://img.sanishtech.com/u/feffb206c5045ac7a70b06377f24dc3a.png" alt="Screenshot 2026-03-14 153055" width="1372" height="550" loading="lazy" style="max-width:100%;height:auto;">
<img src="https://img.sanishtech.com/u/82002c40bad88e743ca20699e7c66fa9.png" alt="Screenshot 2026-02-26 113359" width="1383" height="418" loading="lazy" style="max-width:100%;height:auto;">
<img src="https://img.sanishtech.com/u/5b8ff2ebadee10fd32abafa9e5325c0e.png" alt="Screenshot 2026-03-14 153030" width="1338" height="727" loading="lazy" style="max-width:100%;height:auto;">

## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
