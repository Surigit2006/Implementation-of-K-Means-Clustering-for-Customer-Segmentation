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


Program to implement the K Means Clustering for Customer Segmentation.




Developed by: M.K.Suriya prakash






RegisterNumber:212224110053
```
import pandas as pd
import matplotlib.pyplot as plt
from sklearn.cluster import KMeans

# Load the dataset
data = pd.read_csv(r"C:\Users\Suriya\Downloads\Mall_Customers.csv")


print(data.head())

# Check the data info and missing values
print(data.info())
print(data.isnull().sum())

# Elbow method to find the optimal number of clusters
wcss = []  # Within-cluster sum of squares
for i in range(1, 11):  # Loop over 1 to 10 clusters
    kmeans = KMeans(n_clusters=i, init="k-means++")
    kmeans.fit(data.iloc[:, [3, 4]])  # Assuming the columns for clustering are 'Annual Income' and 'Spending Score'
    wcss.append(kmeans.inertia_)

# Plot the Elbow graph
plt.plot(range(1, 11), wcss)
plt.xlabel("Number of Clusters")
plt.ylabel("WCSS")
plt.title("Elbow Method")
plt.show()

# Fit KMeans with the optimal number of clusters (let's assume 5 clusters based on the Elbow plot)
kmeans = KMeans(n_clusters=5)
kmeans.fit(data.iloc[:, [3, 4]])  # Same columns for clustering
y_pred = kmeans.predict(data.iloc[:, [3, 4]])

# Assign the predicted clusters back to the dataframe
data["cluster"] = y_pred

# Creating separate dataframes for each cluster
df0 = data[data["cluster"] == 0]
df1 = data[data["cluster"] == 1]
df2 = data[data["cluster"] == 2]
df3 = data[data["cluster"] == 3]
df4 = data[data["cluster"] == 4]

# Plot the clusters
plt.scatter(df0["Annual Income (k$)"], df0["Spending Score (1-100)"], c="red", label="Cluster 0")
plt.scatter(df1["Annual Income (k$)"], df1["Spending Score (1-100)"], c="black", label="Cluster 1")
plt.scatter(df2["Annual Income (k$)"], df2["Spending Score (1-100)"], c="blue", label="Cluster 2")
plt.scatter(df3["Annual Income (k$)"], df3["Spending Score (1-100)"], c="green", label="Cluster 3")
plt.scatter(df4["Annual Income (k$)"], df4["Spending Score (1-100)"], c="magenta", label="Cluster 4")

# Adding labels and title to the plot
plt.legend()
plt.title("Customer Segments")
plt.xlabel("Annual Income (k$)")
plt.ylabel("Spending Score (1-100)")
plt.show()

  

```

## Output:

![Screenshot 2025-01-01 155339](https://github.com/user-attachments/assets/65bd5323-4a15-48ef-b97d-d1a13ec7f3af)


![Screenshot 2025-01-01 155417](https://github.com/user-attachments/assets/efd9598a-3bc1-4e93-8626-8e31bfa8488f)


![Screenshot 2025-01-01 155431](https://github.com/user-attachments/assets/fa06994d-5d2f-4d45-849d-746fff7b3e85)

## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
