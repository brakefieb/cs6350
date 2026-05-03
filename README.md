# Image Captioning Using a Convolutional Neural Network-Long Short-Term Memory (CNN-LSTM) Model

**Databricks Public Link:** [View Notebook](https://databricks-prod-cloudfront.cloud.databricks.com/public/4027ec902e239c93eaaa8714f173bcfc/2969901291468711/1332076956171836/8104060317816212/latest.html)

### Compute
* **Databricks Runtime Version:** 13.3 LTS ML (includes Apache Spark 3.4.1, Scala 2.12)

### Upload Flickr8k Dataset
*(This step can take ~30min-1hr)*

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
