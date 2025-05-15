# RFM Analysis

## Table of Content

- [Project Overview](#project-overview)
- [Tools](#tools)
- [Data Preprocessing](#data-preprocessing)
- [KMeans Clustering](#kmeans-clustering)
- [Segment Profiling](#segment-profiling)
- [Outcome](#outcome)

### Project Overview
---
This project aims to segment customers based on their purchasing behavior using RFM (Recency, Frequency, Monetary) analysis combined with K-Means Clustering, an unsupervised machine learning technique. By identifying distinct customer groups, businesses can tailor marketing strategies to each segment, increase customer retention, and boost revenue.

### Tools

- SQL Server
- Python (Pandas, NumPy, Scikit-learn, Matplotlib, Seaborn)
- Jupyter Notebook
- K-Means Clustering
- RFM Analysis
  
### Data Preprocessing

- Lowercases all column names for consistency.
- Converts buss_date and recency to datetime format.
- Creates a zero-padded unique ID for each customer.
- Standardizes branch code (kc) to 4-digit string format.
- Recalculates recency as the number of days since the last transaction relative to the business date.
- Normalize selected columns using min-max scaling.

### KMeans Clustering

- Uses the Elbow Method to determine the optimal number of clusters for each RFM dimension (Recency, Frequency, Monetary).
- Calculates Within-Cluster Sum of Squares (WCSS) and visualizes the elbow point using KneeLocator.
- Applies KMeans clustering to each RFM feature individually.
- Assigns cluster labels as r_score, f_score, and m_score for each customer based on their respective dimension.
- Enables segmentation based on customer behavior patterns in each RFM aspect.

### Segment Profiling

- Combines individual R, F, M cluster scores into a single string rfm_score to represent overall customer segmentation.
- Converts cluster labels to strings before concatenation (e.g., "344", "521").
- Denormalizes normalized RFM values back to their original scale using stored min-max ranges for better interpretability.

### Outcome

- Loads RFM segment labels and descriptions from CSV.
- Converts rfm_score column to string type for accurate merging.
- Performs a left join to enrich the customer DataFrame with human-readable segment names and details based on their combined RFM score.
