# Image Captioning Using a Convolutional Neural Network-Long Short-Term Memory (CNN-LSTM) Model

### **Databricks Public Link:** [CNN-LSTM](https://databricks-prod-cloudfront.cloud.databricks.com/public/4027ec902e239c93eaaa8714f173bcfc/2969901291468711/1332076956171836/8104060317816212/latest.html)

### Compute -> **Databricks Runtime Version:** 13.3 LTS ML

### Upload Flickr8k Dataset

```bash
!git clone [https://github.com/brakefieb/cs6350.git](https://github.com/brakefieb/cs6350.git)
%sh ls /databricks/driver/cs6350/flickr8k
```

```python
dbutils.fs.mkdirs("/FileStore/flickr8k_data")
dbutils.fs.mkdirs("/FileStore/flickr8k_data/images")

dbutils.fs.cp('file:/databricks/driver/cs6350/flickr8k/captions.txt', 'dbfs:/FileStore/flickr8k_data/')
dbutils.fs.cp('file:/databricks/driver/cs6350/flickr8k/images', 'dbfs:/FileStore/flickr8k_data/images/', recurse=True)
```

# Flickr8k Image Captioning Pipeline (CNN-LSTM)

[![Runtime: Databricks 13.3 LTS ML](https://img.shields.io/badge/Runtime-Databricks_13.3_LTS_ML-blue?logo=databricks)](https://databricks.com)
[![Python: 3.x](https://img.shields.io/badge/Python-3.x-green?logo=python)](https://python.org)

## 🚀 Deployment & Interactive Notebook
The full implementation, including the CNN-LSTM architecture and training logs, can be accessed via the public link:
* **Databricks Managed Notebook:** [CNN-LSTM Implementation](https://databricks-prod-cloudfront.cloud.databricks.com/public/4027ec902e239c93eaaa8714f173bcfc/2969901291468711/1332076956171836/8104060317816212/latest.html)

---

## 🛠 Environment Specifications
* **Compute:** Databricks Cluster
* **Runtime:** 13.3 LTS ML
* **Dependencies:** Apache Spark 3.4.1, Scala 2.12, TensorFlow/Keras (Pre-installed in ML Runtime)

## 📦 Data Acquisition & File System (DBFS) Setup
To optimize I/O performance, the dataset is cloned to the driver node and then migrated to the **Databricks File System (DBFS)**.

### 1. Ingest Source Data
*Note: This operation involves large binary files (images) and may take 30–60 minutes.*

```bash
# Clone source repository to local driver
!git clone [https://github.com/brakefieb/cs6350.git](https://github.com/brakefieb/cs6350.git)

# Verify local directory structure
%sh ls /databricks/driver/cs6350/flickr8k
