# Customer Segmentation and Churn Modeling using RFM, KMeans, and BG/NBD

## Project Overview
This project analyzes customer behaviour using two complementary approach:
1. Behavioral segementation using unsupervised KMeans Clustering
2. Probabilistic churn modeling using BG/Negative Binomial Distribution

The goal is to understand customer heterogeneity, estimate churn risk, and support data-driven retention strategies.

## Data
The data used in this project obtained from Kaggle: Online Retail II UCI uploaded by mashlyn, which containing transactional data:
1. InvoiceNo
2. InvoiceDate
3. CustomerID
4. Quantity
5. UnitPrice

Then, the raw data is aggregated at the customer level to construct behavioral features.

## Feature Engineering
Customer-level features constructed:
1. Recency (last purchase till reference day)
2. Frequency
3. Monetary
4. First_Purchase
5. Last_Purchase
6. Avg_Spend
7. Max_Spend
8. Num_items (total number of item purchased)
9. Lifetime(Customer lifetime) : first purchase till last purchase
10. Interpurchase Time (IPT)
11. Observation period (T) : first purchase till reference day

## Methodology
### KMeans Clustering for Customer Segmentation
The objective is to identify behvioral customer group based on purchasing patterns
Features used: Recency, Frequency, Monetary, Avg_Spend, Lifetime, IPT, and T
#### Preprocessing
1. Feature scaling
2. Correlation inspection
3. Silhoutte score to determine the optimal k clusters
#### Output
Customer segemnt such as

0:"Active Mid-Value",
1:"One-Time Lost",
2:"Occasional",
3:"Loyal High-Value",
4:"VIP",
5:"At Risk",
6:"High Ticket"

This provides behavioral differentiation without probabilistic assumptions.

### Churn Risk Modeling using BG/NBD
The objective is to estimate the probability customer is still alive/active (prob_alive)
### Segmentation Framework
1. prob_alive < 0.3 : Churned
2. 0.3 <= prob_alive < 0.5 : At Risk
3. prob_alive >=0.5 : Active
4. "One-Time lost" segment based on KMeans automatically labeled as Churned


