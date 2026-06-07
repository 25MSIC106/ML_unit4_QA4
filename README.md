# QA 4 — Clustering Implementation and Visualization

> Unit 4 Assignment | Unsupervised Machine Learning | K-Means & DBSCAN

---

## 📌 Overview

This project implements and compares two popular clustering algorithms — **K-Means** and **DBSCAN** — on a synthetic customer dataset with features: *Annual Income* and *Spending Score*. Results are visualized in 2D scatter plots and analyzed in depth.

---

## 📂 Repository Structure

```
📦 QA4-Clustering/
├── clustering_QA4.ipynb        # Jupyter Notebook (code + manual steps)
├── QA4_Clustering_Report.docx  # Word document explaining all steps
└── README.md                   # This file
```

---

## 🗃️ Dataset

- **Type:** Synthetic customer data (generated via `sklearn.datasets.make_blobs`)
- **Samples:** 320 points (300 clustered + 20 random noise)
- **Features:**
  - `Annual Income (k$)` — customer yearly income (0–100)
  - `Spending Score (1–100)` — purchase behavior score

---

## ⚙️ Algorithms Used

### 🔵 K-Means Clustering
- Partitions data into **k = 5** clusters by minimizing inertia (WCSS)
- Optimal k selected using the **Elbow Method** and **Silhouette Score**
- All 320 points are assigned to a cluster (no outlier handling)
- **Silhouette Score: 0.7373**

### 🟢 DBSCAN
- Density-based algorithm — auto-detects clusters from data density
- Parameters: `eps = 0.35`, `min_samples = 8`
- Detects **4 clusters** and flags **6 noise/outlier points** (label = −1)
- **Silhouette Score: 0.7286** (measured on non-noise points)

---

## 📊 Results

| Property              | K-Means                    | DBSCAN                        |
|-----------------------|----------------------------|-------------------------------|
| Clusters Found        | 5 (user-defined)           | 4 (auto-detected)             |
| Noise Handling        | None (assigns all points)  | Yes (labels outliers as −1)   |
| Cluster Shape         | Spherical / convex         | Arbitrary shapes              |
| Silhouette Score      | **0.7373**                 | 0.7286                        |
| Sensitive to Outliers | Yes                        | No                            |
| Parameters Needed     | k (number of clusters)     | eps, min_samples              |

### Customer Segment Interpretation (K-Means)

| Cluster | Income | Spending | Segment Label       |
|---------|--------|----------|---------------------|
| 1       | Low    | High     | Impulsive Buyers    |
| 2       | Mid    | Mid      | Standard Customers  |
| 3       | High   | Low      | Conservative Buyers |
| 4       | Low    | Low      | Budget-Conscious    |
| 5       | High   | High     | VIP / Premium       |

---

## 🖼️ Visualizations

The notebook generates two plots:

1. **Elbow Method & Silhouette Score** — confirms k=5 as the optimal number of clusters
2. **K-Means vs DBSCAN Side-by-Side** — 2D scatter plots of cluster assignments

---

## 🏁 Conclusion

- **K-Means performed better** on this dataset because the clusters are spherical and well-separated — exactly what K-Means is optimized for.
- **DBSCAN is superior** at identifying outliers and works well on irregularly-shaped clusters. It correctly isolated noise points that K-Means silently absorbed.
- Neither algorithm is universally best — the choice depends on data structure and business context.

---

## 🛠️ Libraries & Tools

| Library       | Purpose                          |
|---------------|----------------------------------|
| `numpy`       | Numerical computing              |
| `pandas`      | Data manipulation                |
| `matplotlib`  | Plotting and visualization       |
| `seaborn`     | Statistical visualization        |
| `scikit-learn`| KMeans, DBSCAN, StandardScaler   |
| `jupyter`     | Interactive notebook environment |

---

## 🚀 How to Run

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/QA4-Clustering.git
   cd QA4-Clustering
   ```

2. **Install dependencies**
   ```bash
   pip install numpy pandas matplotlib seaborn scikit-learn jupyter
   ```

3. **Launch the notebook**
   ```bash
   jupyter notebook clustering_QA4.ipynb
   ```

4. **Run all cells** — plots and analysis will be generated automatically.

---

## 📄 Submission Contents

- [x] `clustering_QA4.ipynb` — Jupyter notebook with manual + code
- [x] `ML_QA4.docx` — Word document explaining all steps
- [x] `README.md` — Project overview and instructions
