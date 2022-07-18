# Cryptocurrencies
Analysis of crytpocurrency data from CryptoCompare. Unsupervised machine learning was used to establish a classification system for actively trading cryptocurrencies for potential investment prospects.


##Preprocessing:
- Data was cleaned to remove features unable to be processed through machine learning, null values and cryptocurrencies that were not actively trading were dropped. The data was scaled to ensure all factors were weighted accurately in training, and string values were encoded to be numerically representated. 
- The dimensions of the data were then reduced using Principle Component Analysis, yeilding 3 principal components which represent original data through mathematical manipulation involving the creation of matricies between data points and calculation of eignenvalues and eigenvectors. The resulting dataframe and its dimensions are as shown:

![cleaned_df](https://user-images.githubusercontent.com/100040705/179439246-df9a2c45-bf7d-45ff-bc35-c9b1d2872f43.png)

##Clustering using KMeans:
After this preprocessing was complete, an elbow curve was created using the KMeans inertia of different k values(# of clusters) to find the ideal number of clusters to be used for analysis.

the cryptocurrencies were clustered using K-means, four clusters were used 
