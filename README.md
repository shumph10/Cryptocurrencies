# Cryptocurrencies
Analysis of crytpocurrency data from CryptoCompare. Unsupervised machine learning was used to establish a classification system for actively trading cryptocurrencies for potential investment prospects.


##**Preprocessing:**

- Data was cleaned to remove features unable to be processed through machine learning, null values and cryptocurrencies that were not actively trading were dropped.The resulting dataframe is as shown below:

![cleaned_df](https://user-images.githubusercontent.com/100040705/179439618-e1e3c709-58a9-4613-ab89-0fd64319d3f3.png)

-  The data was scaled to ensure all factors were weighted accurately in training, and string values were encoded to be numerically representated.
- The dimensions of the data were then reduced using Principle Component Analysis, yeilding 3 principal components which represent original data through mathematical manipulation involving the creation of matricies between data points and calculation of eignenvalues and eigenvectors. The resulting dataframe and its dimensions are as shown:

![pcs_df](https://user-images.githubusercontent.com/100040705/179439614-e16d87c1-a7ce-4965-ac90-05f30604676a.png)

##**Clustering using KMeans:**

- After this preprocessing was complete, an elbow curve was created using the KMeans inertia of different k values(# of clusters) to find the ideal number of clusters to be used for analysis. KMeans will be used to cluster points based on the mean of all points belonging to that cluster. Inertia was used as the objective function here because it measures the amount of variation in the dataset. Using the value for k where the line switches from a vertical to horizontal direction to minimize variation and maximize functionality, we can see from the resulting elbow graph, the best value for k is 4. Therefore out analysis will utilize 4 clusters or categories for the cryptocurrencies. 


![elbow_curve](https://user-images.githubusercontent.com/100040705/179439574-ce7021d4-9cdd-44f9-a5bd-fbfb41f35607.png)

- KMeans algorithm was applied to the PCA crypto data with 4 clusters as discussed above. The model was used to make predictions on what cluster (or class) the cryptocurrency would belong to. The class data was then added to the original cleaned dataframe, and joined with the PCA dataframe so all information would be readily available in one dataset as shown below:

![clustered_df](https://user-images.githubusercontent.com/100040705/179440263-3d332154-d19b-4058-ae9a-8c80dbd9cedf.png)

##**Visualization of Results**
- The PCA data and the predicted class from the unsupervised learning model were plotted in a 3D graph for best possible visualization of cluster seperation. From this graph the class #2(shown in orange) is shown to only have one data point within it, since it is relatively far from all other groups this is most likely an outlier and after due diligence inspection may be considered to be dropped as an outlier. From all angles shown there is minimal seperation between classes 0 and 1 (shown in purple and pink respectively) and further investigation using a different unsupervised learning method may be required to establish the seperation between the two. 
- The resulting graph is shown from two angles for best visualization of results below:

![3D_plot_clusters](https://user-images.githubusercontent.com/100040705/179440404-9109857f-1df7-45f1-b289-11afdb31969c.png)
![3D_plot_clusters_angle_2](https://user-images.githubusercontent.com/100040705/179440756-c0478a8d-16c6-44ec-be38-2f753b013ab4.png)

- A table was then created to show the original features vs the class assigned by the KMeans algorithm. Original, unscaled data was provided in this graph for better depiction of difference total coins mined and coin supply. Table in crypto_clustering.ipynb is interactive allowing sorting (ascending or decending) by column. When sorting the table by total coins mined from most to least, it appears as through the coins with the most coins mined are typically in classes 0 or 1. Additional graphing or analysis will be done in the next section to visualize this observation. A sample of the table is as shown below:

![tradable_crypto_table_sorted](https://user-images.githubusercontent.com/100040705/179441189-a9c2aab2-ace6-49b6-b645-af86c87edf85.png)

- For additional clarity and visualization purposed, a new dataframe with only the scaled total coin supply and total coins mined, along with name and class was created. Scaling of these features allowed graphing to explore the connection between these features and class as discussed in the previous section. The graph shows 2 outliers rather than one as previously observed by the 3D graph. When discounting these outliers and zooming in on the area of the graph the rest of the data is concentrated there again is not a clear distinction between classes 0 and 1. The data points in class 3 appear to be clustered around the total coin supply and coins mined being nearly zero, which may be a reason the unsupervised machine learning model placed them in a group.
- The graph created is show below, first at full size, then zoomed into the more concentrated data area.

![coins_mined_vs_supply](https://user-images.githubusercontent.com/100040705/179441631-90777d34-3b8b-485d-ad53-9025ee46366e.png)
![coins_mined_vs_supply_zoomed](https://user-images.githubusercontent.com/100040705/179441635-ed062a17-a165-457b-ae38-5035ea8c4e23.png)

##**Summary**
From the analysis and cleaning of the data, 532 cryptocurrencies were able to be analyzed through unsupervised machine learning using the KMeans algorithm. From this, four classes of cryptocurrencies were identified. Of these four, class 2 appears to contain only one data point that is likely an outlier. Class 3 contains cryptocurrencies that have both a low total coins mined and low total coin supply count. This could indicate cryptocurrencies within class 3 may not be the best candidates for investment as there is both low supply and low demand. Classes 0 and 1 would need additional research and analysis to determine the features that seperate the two and what features make them the best candidates for investment. Additional analysis could be done on sale/buy percentages for a timeframe to see consumer trends, price fluctuation, if the type of coin has significant influence, or if the platform the currency is avaiable for sale on has influence. 

