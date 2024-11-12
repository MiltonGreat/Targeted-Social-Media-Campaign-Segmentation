# Social Media Ad Engagement Clustering

This project aims to segment users based on their engagement data from social media advertising campaigns. By leveraging clustering techniques, we can group users based on their interaction patterns, helping marketers understand different segments for more targeted advertising strategies.

## Project Overview

In this project, we perform user segmentation based on their engagement data from social media ads. Using clustering algorithms like KMeans, we identify groups of users with similar engagement patterns, which can help optimize marketing strategies by focusing on key audience segments.

## Dataset

The dataset is a comprehensive collection of data related to various social media advertising campaigns. It includes engagement metrics like impressions, clicks, spend, and conversion rates, across multiple platforms such as Facebook, Instagram, Pinterest, and Twitter.

### Features:

- **Campaign_ID**: Unique ID of each campaign.
- **Target_Audience**: Demographic information about the target audience.
- **Campaign_Goal**: The objective of the campaign (e.g., Product Launch, Increase Sales).
- **Conversion_Rate**: The rate at which users convert after viewing the ad.
- **Acquisition_Cost**: The cost of acquiring a customer.
- **Clicks**: Number of clicks the ad received.
- **Impressions**: Number of times the ad was shown.
- **Engagement_Score**: A custom metric indicating user engagement with the ad.
- **ROAS**: Return on Advertising Spend.
- **CTR**: Click-through Rate.
- **CLTV**: Customer Lifetime Value (proxy).

## Objective

The primary goal of the project is to group users based on their engagement with ads using clustering algorithms, enabling better understanding of customer segments. This can help businesses target specific groups more effectively and optimize their ad spend.

## Features

We use key engagement metrics to perform clustering:

- **CTR**: Click-through Rate.
- **Engagement Rate**: Engagement score divided by impressions.
- **ROAS**: Return on Advertising Spend.
- **CLTV**: Customer Lifetime Value (proxy).
- **Total Spend**: The total cost spent on a campaign.

## Project Workflow

### Data Preprocessing

1. **Data Cleaning**: 
   - Missing values were filled with the median or mode, depending on the feature type.
   - Outliers in numeric columns such as `Acquisition_Cost`, `Clicks`, `Impressions`, and `Engagement_Score` were detected and handled using the Interquartile Range (IQR) method.
   
2. **Feature Scaling**: 
   - We applied **MinMaxScaler** to normalize numerical features such as `Acquisition_Cost`, `CTR`, `ROAS`, and `CLTV` for better clustering performance.

3. **One-Hot Encoding**: 
   - Categorical features such as `Target_Audience`, `Campaign_Goal`, and `Channel_Used` were encoded using one-hot encoding to convert them into numerical format.

### Feature Engineering

- **Cost per Acquisition (CPA)**: Derived as `Acquisition_Cost / (Conversion_Rate * Clicks)`.
- **Click-Through Rate (CTR)**: Calculated as `Clicks / Impressions`.
- **Engagement Rate**: Computed as `Engagement_Score / Impressions`.
- **ROAS**: Return on Advertising Spend, calculated as `(Clicks * Conversion_Rate * CPA) / Total_Spend`.
- **CLTV**: Proxy for Customer Lifetime Value, derived as `Conversion_Rate * Total_Spend * Engagement_Rate`.

### Clustering

1. **KMeans Clustering**: 
   - We used the **KMeans** algorithm to group users into clusters based on engagement data. The optimal number of clusters was determined using the **Elbow Method**, which involves plotting the sum of squared errors (SSE) against the number of clusters.
   
2. **Dimensionality Reduction**: 
   - **PCA (Principal Component Analysis)** was used to reduce the feature dimensions to two components for better visualization of the clusters.

### Cluster Evaluation

- **Silhouette Score**: We computed the silhouette score to evaluate how well each point fits within its cluster. A higher silhouette score indicates better-defined clusters.

### Cluster Profiling

- **Cluster Analysis**: We performed cluster profiling by aggregating the numerical features (such as CTR, Engagement Rate, and ROAS) to understand the key characteristics of each cluster. This helps in identifying which segments perform better in terms of ad engagement and spend efficiency.

## Key Insights

1. **Cluster Segmentation**:
   - The users were grouped into three distinct clusters based on engagement metrics like CTR, CLTV, and Total Spend.
   - The clusters provide valuable insights into user behavior, allowing targeted advertising for each group.

2. **Silhouette Score**:
   - The silhouette score is 0.57, which indicates fairly good clustering performance. A score closer to 1 would mean well-separated clusters.

3. **Cluster Profiling**:
   - **Cluster 0**: High-engagement, high-value users, ideal for ad spend maximization.
   - **Cluster 1**: Moderate engagement, high spend users—opportunity to improve efficiency.
   - **Cluster 2**: Low-engagement users, possible candidates for reduced ad targeting.

### Source

https://www.kaggle.com/datasets/jsonk11/social-media-advertising-dataset
