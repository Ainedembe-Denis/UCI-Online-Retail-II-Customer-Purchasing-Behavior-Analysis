# Assignment Alignment Analysis
## Question 2: Customer Purchasing Behavior Analysis

### Overall Assessment: ✅ **WELL ALIGNED** with minor recommendations

---

## PART A: Data Cleaning and Clustering (15 marks)

### ✅ 1. Load dataset
**Status: COMPLETE**
- Cell 6: Dataset loaded from `dataset/online_retail_II.csv`
- Proper encoding (ISO-8859-1) used
- Shape and preview displayed

### ✅ 2. Remove missing descriptions, negative quantities, cancelled invoices
**Status: COMPLETE**
- Cell 12 (A2): Data cleaning performed
  - Missing descriptions removed: `df_clean = df_clean.dropna(subset=["Description"])`
  - Negative quantities removed: `df_clean = df_clean[df_clean["Quantity"] > 0]`
  - Cancelled invoices removed: `df_clean = df_clean[~df_clean["Invoice"].astype(str).str.startswith("C")]`

### ✅ 3. Create customer-level features
**Status: COMPLETE** (Enhanced with Recency)
- Cell 13 (A3): Customer-level aggregation
  - ✅ Total spending: `TotalSpending`
  - ✅ Transaction count: `TransactionCount`
  - ✅ Average basket size: `AvgBasketSize`
  - ✅ **BONUS**: Recency feature added (days since last purchase)

### ✅ 4. Apply k-Means and DBSCAN/Hierarchical clustering
**Status: MOSTLY COMPLETE** (Minor issue)
- ✅ k-Means: Cell 17 - Implemented with parameter tuning (k=2-10)
- ✅ DBSCAN: Cell 18 - Implemented with parameter tuning (eps grid search)
- ⚠️ **ISSUE**: Hierarchical clustering is imported but NOT applied
  - `AgglomerativeClustering` is imported in Cell 3
  - But no code cell applies hierarchical clustering
  - **RECOMMENDATION**: Add hierarchical clustering or remove from imports

### ✅ 5. Compute silhouette scores; visualize with PCA/t-SNE
**Status: COMPLETE**
- ✅ Silhouette scores computed for both k-Means and DBSCAN
- ✅ PCA visualization: Cell 20 - Side-by-side plots for k-Means and DBSCAN
- ✅ t-SNE visualization: Cell 24 - Side-by-side plots for k-Means and DBSCAN
- ✅ Interpretation provided: Cell 21

**Part A Score Estimate: 14/15** (Missing hierarchical clustering)

---

## PART B: Deep Embedding Clustering (15 marks)

### ✅ 1. Autoencoder latent embeddings clustered with k-Means
**Status: COMPLETE**
- Cell 28 (B1.1): Autoencoder architecture defined
- Cell 29 (B1.2): Autoencoder trained
- Cell 30 (B2): Embeddings extracted and clustered with k-Means
  - Encoder model created
  - Latent embeddings extracted
  - k-Means applied to embeddings

### ✅ 2. Provide embedding plots and compare cluster quality with PCA clusters
**Status: COMPLETE**
- ✅ Embedding plots: Cell 30 includes visualization of autoencoder clusters
- ✅ Comparison with PCA: Cell 30 includes comparison
  - PCA-based k-Means clustering
  - Autoencoder-based clustering
  - Cluster quality comparison

**Part B Score Estimate: 15/15** ✅

---

## PART C: Association Rule Mining (10 marks)

### ✅ 1. Convert data into basket format: Invoice to list of Description items
**Status: COMPLETE**
- Cell 37 (C1): Basket format conversion
  - Invoice → list of Description items
  - Proper grouping implemented

### ✅ 2. Build binary matrix with Invoice as rows and Description as columns
**Status: COMPLETE**
- Cell 37 (C1): Binary matrix created
  - `basket_bool` matrix: Invoice × Description (0/1)
  - Verification output included

### ✅ 3. Apply Apriori or FP-Growth
**Status: COMPLETE**
- Cell 41 (C3): FP-Growth algorithm applied
  - `fpgrowth()` function used
  - Minimum support = 0.01

### ✅ 4. Extract 10 strongest rules sorted by lift
**Status: COMPLETE**
- Cell 42 (C4): Top 10 rules extracted
  - Sorted by lift (descending)
  - Displayed in table format
  - Visualizations included (bar chart + scatter plot)

### ✅ 5. Interpret at least 3 rules
**Status: COMPLETE**
- Cell 45 (C5): 4 rules interpreted (exceeds requirement)
  - Randomly sampled 4 rules
  - Each rule includes:
    - Antecedents and consequents
    - Support, Confidence, Lift values
    - Business interpretation

**Part C Score Estimate: 10/10** ✅

---

## PART D: Interpretation and Presentations (10 marks)

### ✅ 1. Cluster meanings and customer types
**Status: COMPLETE**
- Cell 47 (D1): Cluster profiles generated
  - k-Means cluster profiles with mean values
  - Autoencoder cluster profiles with mean values
  - Customer counts per cluster
- Cell 48 (D2): Detailed cluster interpretations
  - k-Means clusters described with customer types
  - Autoencoder clusters described with customer types
  - Brief explanations provided

### ✅ 2. High-value segments
**Status: COMPLETE**
- Cell 49 (D2): High-value segments identified
  - Highest-value segments from k-Means
  - Highest-value segments from Autoencoder
  - Detailed characteristics provided

### ✅ 3. Differences between PCA and deep embedding clusters
**Status: COMPLETE**
- Cell 50 (D3): Comparison provided
  - Cluster profiles comparison
  - Differences explained
  - Quality metrics compared

### ✅ 4. Three actionable business recommendations
**Status: COMPLETE**
- Cell 51 (D4): Three recommendations provided
  1. Cross-selling based on association rules
  2. Loyalty programs for high-value customers
  3. Targeted discounts based on cluster characteristics
- Cell 52 (D5): Additional detailed recommendations

**Part D Score Estimate: 10/10** ✅

---

## RECENT CHANGES VERIFICATION

### ✅ Log Transformation
- **Status**: IMPLEMENTED
- Cell 16: Feature preparation uses log-transformed features
  - `TotalSpending_log`
  - `TransactionCount_log`
  - `AvgBasketSize` (original)
  - `Recency` (original)

### ✅ Recency Feature
- **Status**: IMPLEMENTED
- Cell 16: Recency calculated and included
  - Days since last purchase
  - Statistics displayed
  - Merged with customer_df

---

## ISSUES FOUND

### ⚠️ Issue 1: Hierarchical Clustering Not Applied
- **Location**: Part A, Requirement 4
- **Severity**: Minor (1 mark deduction possible)
- **Status**: `AgglomerativeClustering` imported but never used
- **Recommendation**: 
  - Option 1: Add hierarchical clustering cell
  - Option 2: Remove from imports if not required
  - **Note**: Assignment says "k-Means and DBSCAN/Hierarchical" - the "/" suggests OR, not AND

### ✅ Issue 2: Feature Alignment
- **Status**: RESOLVED
- Log transformation and Recency now properly implemented

---

## RECOMMENDATIONS

### 1. **CRITICAL**: Clarify Hierarchical Clustering Requirement
   - The assignment says "k-Means and DBSCAN/Hierarchical"
   - This likely means: k-Means + (DBSCAN OR Hierarchical)
   - Currently: k-Means + DBSCAN ✅
   - **Action**: If hierarchical is required, add it. Otherwise, current approach is correct.

### 2. **OPTIONAL**: Add Brief Summary Section
   - Consider adding a summary cell at the end
   - Highlight key findings from each part
   - Makes it easier for graders to see all requirements met

### 3. **OPTIONAL**: Verify All Outputs Are Visible
   - Ensure all cells have been executed
   - Check that visualizations display correctly
   - Verify statistics are printed

---

## FINAL SCORE ESTIMATE

| Part | Requirements | Status | Estimated Score |
|------|-------------|--------|----------------|
| Part A | 5 requirements | 4.5/5 complete | 14/15 |
| Part B | 2 requirements | 2/2 complete | 15/15 |
| Part C | 5 requirements | 5/5 complete | 10/10 |
| Part D | 4 requirements | 4/4 complete | 10/10 |
| **TOTAL** | **16 requirements** | **15.5/16** | **49/50** |

---

## CONCLUSION

✅ **The notebook is WELL ALIGNED with the assignment requirements.**

**Strengths:**
- All major requirements met
- Excellent visualizations
- Comprehensive interpretations
- Good code organization
- Recent improvements (log transformation, Recency) enhance quality

**Minor Issue:**
- Hierarchical clustering imported but not applied (likely not required based on "/" in assignment)

**Overall Assessment: EXCELLENT** - Ready for submission with minor clarification on hierarchical clustering requirement.

