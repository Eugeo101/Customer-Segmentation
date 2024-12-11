# Customer Segmentation and Anomaly Detection 🚀🔍  

This project focuses on customer segmentation and anomaly detection using **RFM analysis** and advanced clustering techniques. The workflow includes data preprocessing, clustering customers into meaningful segments, and detecting anomalies to ensure high-quality predictions.  

---

## 📝 Problem Statement  
Segment customers based on **Recency**, **Frequency**, and **Monetary** (RFM) attributes to understand purchasing behaviors and detect anomalies for better decision-making in marketing strategies.  

---

## 🔍 Steps Followed  

### 1️⃣ Data Preprocessing  
- Removed noisy data and outliers using **Isolation Forest** (handles multidimensional datasets without assumptions on feature distributions).  
- Extracted RFM features from the dataset:  
  - **Recency:** Time since last purchase.  
  - **Frequency:** Number of transactions.  
  - **Monetary:** Total spend.  

---

### 2️⃣ Data Visualization  
- Visualized high-dimensional data using techniques:  
  - **t-SNE (t-distributed Stochastic Neighbor Embedding)**  
- Used t-SNE to uncover clustering patterns and select appropriate clustering techniques.  

---

### 3️⃣ Clustering  
- Tried multiple clustering algorithms:  
  - **KMeans**: Optimized `k` using inertia, silhouette scores, and silhouette samples. Best value: **k = 4**.  
  - **DBSCAN**: Used density-based clustering to find core samples of high density.  
  - **Gaussian Mixture Models (GMM)**: Determined optimal clusters using AIC and BIC. Explored **Bayesian GMM** for robust analysis.  

#### Clustering Insights:  
- **KMeans:**  
  - Cluster 0: Low frequency, small monetary.  
  - Cluster 1: Infrequent users (2+ years), small monetary.  
  - Cluster 2: Frequent users (6 months), large monetary.  
  - Cluster 3: High frequency, large monetary.  
- **BGMM:**  
  - Cluster 1: Infrequent users, small monetary.  
  - Cluster 2: Moderate frequency and transactions.  
  - Cluster 3: High frequency and transactions.  

### Final Decision:  
Used **Bayesian GMM (BGMM)** to categorize clusters:  
- **Silver Customers:** Infrequent users with low monetary values.  
- **Gold Customers:** Moderate frequency and monetary values.  
- **Platinum Customers:** Recent, frequent, and high-spending users.  

---

### 4️⃣ Anomaly Detection  
- Removed outliers by setting a density threshold (3% of the data identified as outliers).  
- Implemented a pipeline:  
  - Preprocessing → SMOTE for oversampling → **Gradient Boosting Classifier**.  
  - Achieved **98% validation accuracy** and **97.79% test accuracy**, with an **F1 score of 96.3%**.  

#### Bayesian GMM for Anomaly Detection:  
- Detected anomalies by comparing density scores of new data points to a predefined threshold.  
- Successfully identified outliers with **99.47% accuracy**.  

---

### 5️⃣ Model Deployment  
- Saved the trained clustering model and **Bayesian GMM** in `.pkl` files for production use.  
- Integrated preprocessing and anomaly detection for real-time classification and anomaly detection.  

---

## 🏆 Results  
- Effective segmentation into **Silver**, **Gold**, and **Platinum** categories.  
- High accuracy in anomaly detection with robust clustering techniques.  
- Optimized marketing strategies with actionable insights into customer behavior.  

---

## 🔧 Tools and Libraries  
- **Python:** Pandas, NumPy, Scikit-learn, Matplotlib, Seaborn.  
- **Clustering:** KMeans, DBSCAN, Gaussian Mixture Models, Bayesian GMM.  
- **Dimensionality Reduction:** t-SNE.  
- **Validation Metrics:** AIC, BIC, Silhouette Scores.  

---
