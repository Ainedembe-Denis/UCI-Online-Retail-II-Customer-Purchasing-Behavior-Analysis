# UCI Online Retail II – Customer Purchase Behavior Analysis

## Project Overview
This project analyzes customer purchasing behavior for a UK-based online retailer using data mining and machine learning techniques. The objective is to extract meaningful customer segments, identify purchasing patterns, and generate actionable marketing recommendations that support data-driven business decisions.

The analysis combines traditional clustering, deep embedding representations, and association rule mining to uncover both high-level customer groups and detailed product-level insights.

---

## Author
**Ainedembe Denis**
- Master’s student in Information Systems (2024/2026)
- LinkedIn: https://www.linkedin.com/in/ainedembe-denis-2b329615a/

---

## Objectives
- Understand customer purchasing behavior using transaction data
- Segment customers based on spending and buying patterns
- Compare traditional clustering with deep embedding-based clustering
- Discover frequently co-purchased product combinations
- Provide actionable business and marketing recommendations

---

## Dataset
- **Title :** Online Retail II UCI (A real online retail transaction data)
- **Link / Source:** https://www.kaggle.com/datasets/mashlyn/online-retail-ii-uci
- **Description:** All Transactional data for a UK-based and registered, non-store online retail between 01/12/2009 and 09/12/2011.The company mainly sells unique all-occasion gift-ware. Many customers of the company are wholesalers.
- **Content:** Attribute Information:
  - `InvoiceNo`, `StockCode`, `Description`, `Quantity`, `InvoiceDate`,`UnitPrice`, `CustomerID`, `Country`

---

## Methodology

### **Part A: Data Cleaning and Customer Clustering**
1. Load the Online Retail II dataset
2. Data cleaning:
   - Remove missing product descriptions
   - Remove negative quantities (returns)
   - Remove cancelled invoices
3. Feature engineering at customer level:
   - Total spending (log-transformed)
   - Transaction count (log-transformed)
   - Average basket size
   - Recency (days since last purchase)
4. Apply clustering techniques:
   - k-Means clustering (with parameter tuning: k=2-10)
   - DBSCAN clustering (with eps parameter tuning)
5. Evaluate clustering performance using silhouette scores
6. Visualize customer clusters using PCA and t-SNE

---

### **Part B: Deep Embedding Clustering**
1. Train an **Autoencoder** to learn latent representations of customer features
2. Extract low-dimensional embedding space
3. Apply k-Means clustering on latent embeddings
4. Visualize embedding-based clusters
5. Compare cluster separation and quality against PCA-based clustering

---

### **Part C: Association Rule Mining**
1. Transform transactional data into basket format (Invoice → list of products)
2. Construct binary transaction matrix (40,301 invoices × 5,469 products)
3. Apply **FP-Growth** algorithm to identify frequent itemsets (1,056 itemsets found)
4. Generate association rules (848 rules generated)
5. Extract and rank the top 10 rules based on lift
6. Interpret 4 strong association rules with business relevance

---

### **Part D: Interpretation and Business Insights**
- Interpret customer clusters and define customer types
- Identify high-value and loyal customer segments
- Compare traditional clustering vs deep embedding clustering
- Provide three actionable business and marketing recommendations

---

## Technologies & Tools used
- Python
- Pandas, NumPy
- Scikit-learn
- TensorFlow / Keras
- mlxtend (FP-Growth)
- Matplotlib, Seaborn

---

## Repository Structure
```
Retail-II-UCI-Customer-Purchase-Behavior-Analysis/
├── dataset/
│ └── online_retail_ii.csv
├── Retail-Customer-Analysis.ipynb
├── results/
│ ├── report/
│ └── screenshots/
├── README.md
└── requirements.txt
```

---

## Key Outcomes
- **Customer Segmentation**: Identified 3 k-Means clusters (Medium-value: 46.1%, Low-value: 53.8%, Bulk buyers: 0.05%)
- **Clustering Performance**: 
  - k-Means silhouette score: 0.4144
  - DBSCAN silhouette score: 0.3186 (2 clusters, 101 noise points)
  - Autoencoder embedding silhouette: 0.5768 (best performance)
- **Association Rules**: Discovered 848 rules, top 10 with lift values 45-52
- **Product Insights**: Strong associations in "Poppy's Playhouse" product line

## Business Recommendations
1. **Cross-selling**: Bundle frequently co-purchased products (e.g., Poppy's Playhouse sets)
2. **Loyalty Programs**: Target high-value customers (Cluster 0: 2,714 customers, £5,848 avg spending)
3. **Targeted Discounts**: Segment-specific promotions based on cluster characteristics

---

## License
This project is for academic purposes only.
