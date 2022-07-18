# Cryptocurrencies
Analysis of crytpocurrency data from CryptoCompare. Unsupervised machine learning was used to establish a classification system for actively trading cryptocurrencies for potential investment prospects.


##Preprocessing:

- Data was cleaned to remove features unable to be processed through machine learning, null values and cryptocurrencies that were not actively trading were dropped.The resulting dataframe is as shown below:

![cleaned_df](https://user-images.githubusercontent.com/100040705/179439618-e1e3c709-58a9-4613-ab89-0fd64319d3f3.png)

-  The data was scaled to ensure all factors were weighted accurately in training, and string values were encoded to be numerically representated.
- The dimensions of the data were then reduced using Principle Component Analysis, yeilding 3 principal components which represent original data through mathematical manipulation involving the creation of matricies between data points and calculation of eignenvalues and eigenvectors. The resulting dataframe and its dimensions are as shown:

![pcs_df](https://user-images.githubusercontent.com/100040705/179439614-e16d87c1-a7ce-4965-ac90-05f30604676a.png)

##Clustering using KMeans:

After this preprocessing was complete, an elbow curve was created using the KMeans inertia of different k values(# of clusters) to find the ideal number of clusters to be used for analysis. Inertia was used as the objective function here because it measures the amount of variation in the dataset. Using the value for k where the line switches from a vertical to horizontal direction to minimize variation and maximize functionality, we can see from the resulting elbow graph, the best value for k is 4. Therefore out analysis will utilize 4 clusters or categories for the cryptocurrencies. 

![elbow_curve](https://user-images.githubusercontent.com/100040705/179439574-ce7021d4-9cdd-44f9-a5bd-fbfb41f35607.png)

