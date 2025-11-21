# 🌐 Databricks

---

## 💥 **Databricks Overview**
Databricks is a unified analytics platform combining data engineering, data science, and machine learning.  
The UI is designed to give easy access to compute, data, notebooks, and collaboration tools.

---

## **1.1 Workspace UI**
The Workspace UI is the main environment you see after logging in.

It contains:
- **Left Sidebar** → navigation  
- **Main Panel** → notebooks, data previews, cluster pages  
- **Top Bar** → user settings, cluster selector, search  

---

## **1.2 Overview of UI Components**
Here are the important UI sections:

### **Home**
Shows recent notebooks, experiments, and favorites.

### **Workspace**
A file-system-like area holding:
- Folders  
- Notebooks  
- Libraries  
- Projects  

### **Data**
Used to view:
- Databases  
- Tables  
- Files in DBFS  
- Upload new data  

### **Compute**
Section for managing:
- Clusters  
- SQL Warehouses (not in free edition)  

### **Workflows / Jobs**
Automated notebook runs.  
(Limited in free edition.)

### **Repos**
Git integration (not available in Community Edition).

---

## **1.3 Workspaces**
A Workspace is the organizational layer in Databricks where you store:
- Notebooks  
- Folders  
- Data files  
- Libraries  

You can group notebooks into folders to keep projects structured.

---

## **1.4 Notebooks**
Databricks Notebooks support multiple languages:
- Python  
- SQL  
- Scala  
- R  

Features:
- Markdown support  
- Visualizations  
- Export options (HTML, DBC, Source)  
- Attach to clusters  
- Revision history  

---

## **1.5 Libraries**
Libraries extend notebook functionality.

Supported types:
- **PyPI packages**
- **JAR files**
- **Wheel files (.whl)**

Installed through:  
**Compute → Cluster → Libraries**.

---

## **1.6 Data**
The Data tab allows you to:
- Upload CSV/JSON/Parquet  
- Auto-create tables  
- Preview schema  
- Run SQL queries  

Unity Catalog is **not** available in free edition.

---

## **1.7 Clusters**
Clusters are the compute resources that run your code.

You can:
- Start/Stop the cluster  
- Select runtime version  
- View Spark UI  
- Attach notebooks  

Community Edition Limit:
- Only **ONE** cluster available.

---

# 💥 Workspace Navigation

## 2.1 Creating & Managing Notebooks
- Create via: **Workspace → Create → Notebook**
- Supports Python, SQL, Scala, R
- Actions: rename, move, export, delete
- Attach to cluster, run cells, use markdown, revision history

---

## 2.2 Uploading & Managing Data
- Upload via: **Data → Add Data**
- Supports CSV, JSON, Parquet
- Auto-create Delta tables
- Data preview, schema view, profiling
- Query using SQL editor

---

## 2.3 Managing Clusters
- Path: **Compute → Select Cluster**
- Start/stop cluster
- Edit configuration
- View Spark UI (jobs, stages, executors)
- Attach/detach notebooks

---

## 2.4 Accessing Libraries
- Path: **Compute → Cluster → Libraries**
- Install from PyPI or upload JAR/Wheel
- Shows installed libs and status
- Some libraries require restart

---

## 2.5 Collaboration & Sharing
- (Paid edition) Share folders/notebooks
- Permissions: View, Run, Edit, Manage
- Commenting on cells

---

## 2.6 Sharing Notebooks
- Methods:
  - Add users (paid edition)
  - Export as HTML, DBC, or .py
  - Share link (if enabled)

---

## 2.7 Collaborative Editing
- Real-time editing (paid edition)
- See other users' cursors
- Comments + threaded discussions

---

## 2.8 Version History
- Access via clock icon in notebook
- Auto-saved checkpoints
- Compare versions
- Restore previous version

---

# 💥 Cluster Creation

## 3.1 Cluster Configuration
- Select Databricks Runtime (DBR)
- Set driver & worker node types
- Configure autoscaling
- Set termination timeout
- Attach init scripts if needed
- Add environment variables

---

## 3.2 Cluster Types
### **Standard Cluster**
- General-purpose
- Designed for single-user interactive work
- Supports libraries & custom configs

### **High Concurrency Cluster**
- Multi-user optimized
- Concurrency & security isolation
- Good for SQL/BI workloads

---

## 3.3 Worker Node Types
- **General Purpose:** balanced CPU/RAM
- **Compute Optimized:** high CPU (fast ETL)
- **Memory Optimized:** high RAM (joins, caching)
- Choose based on workload pattern

---

## 3.4 Auto Scaling Options
- Enable/disable autoscaling
- Set min/max worker nodes
- Automatically adjusts resources based on load
- Saves cost + improves performance

# 💥  4. dbutils Command

## 4.1 Overview of dbutils
`dbutils` is a Databricks utility module that provides helpers for:
- File system operations (DBFS)
- Notebook execution
- Widgets (UI inputs)
- Library installation
- Secrets and job utilities

It simplifies automation and orchestration inside Databricks notebooks.

---

## 4.2 Accessing dbutils in Notebooks
Inside Databricks, dbutils is already available:
```python
dbutils
```

Outside Databricks (e.g., local PySpark):
```python
from pyspark.dbutils import DBUtils
dbutils = DBUtils(spark)
```

---

## 4.3 Common dbutils Commands
| Area | Command |
|------|---------|
| File System | `dbutils.fs.*` |
| Notebooks | `dbutils.notebook.*` |
| Widgets | `dbutils.widgets.*` |
| Libraries | `dbutils.library.*` |
| Secrets | `dbutils.secrets.*` |

---

## 4.4 dbutils.fs (File System Operations)
```python
dbutils.fs.ls("/mnt")
dbutils.fs.mkdirs("/mnt/new_folder")
dbutils.fs.rm("/mnt/old_folder", recurse=True)
dbutils.fs.cp("/mnt/a.txt", "/mnt/b.txt")
dbutils.fs.put("/mnt/test.txt", "Hello World", overwrite=True)
```

---

## 4.5 dbutils.notebook (Notebook Operations)
Execute another Databricks notebook:
```python
dbutils.notebook.run("/Users/NotebookPath", timeout=120, arguments={"param": "value"})
```

---

## 4.6 dbutils.library (Library Operations)
```python
dbutils.library.installPyPI("pandas", "1.5.3")
dbutils.library.restartPython()
```

---

## 4.7 dbutils.widgets (Widget Operations)
Create widgets:
```python
dbutils.widgets.text("name", "default")
dbutils.widgets.dropdown("dept", "IT", ["IT","HR","Finance"])
```

Read widget value:
```python
value = dbutils.widgets.get("name")
```

Remove widgets:
```python
dbutils.widgets.removeAll()
```

---

# 💥 5. Example Usages

## 5.1 Uploading & Downloading Files
Upload via UI:  
**Data → DBFS → Upload**

Download file:
```python
dbutils.fs.cp("dbfs:/FileStore/data.csv", "file:/tmp/data.csv")
```

---

## 5.2 Running External Notebooks
```python
result = dbutils.notebook.run("/Repos/ProcessSales", 120, {"region": "EU"})
print(result)
```

---

## 5.3 Installing & Managing Libraries
```python
dbutils.library.installPyPI("numpy")
dbutils.library.restartPython()
```

---

## 5.4 Interacting with Widgets
```python
dbutils.widgets.dropdown("country", "India", ["India","USA","UK"])
selected = dbutils.widgets.get("country")
print(selected)
```

---

# 💥 6. Read and Write in DBFS Path

## 6.1 Introduction to DBFS
DBFS = Databricks File System  
Virtual filesystem layer over cloud storage (S3/ADLS/GCS).

---

## 6.2 Overview of DBFS
| Path | Description |
|------|-------------|
| `/dbfs` | Local FS mount |
| `dbfs:/` | Native DBFS prefix |
| `/mnt` | Mounted cloud storage |
| `/FileStore` | Publicly accessible files |
| `/databricks-datasets` | Sample datasets |

---

## 6.3 Mount Points
Mount ADLS/S3:
```python
dbutils.fs.mount(
  source="wasbs://container@storage.blob.core.windows.net",
  mount_point="/mnt/data",
  extra_configs={"fs.azure.account.key.storage.blob.core.windows.net": "<KEY>"}
)
```

---

## 6.4 Reading Data from DBFS
```python
df = spark.read.csv("dbfs:/FileStore/data.csv", header=True, inferSchema=True)
```

---

## 6.5 Reading CSV/Parquet Files
```python
df = spark.read.csv("dbfs:/mnt/data/file.csv", header=True)
df = spark.read.parquet("dbfs:/mnt/parquet/data.parquet")
```

---

## 6.6 Reading Other File Formats
```python
spark.read.json("dbfs:/data/data.json")
spark.read.format("delta").load("dbfs:/delta/events")
spark.read.orc("dbfs:/orc/data.orc")
```

---

## 6.7 Writing Data to DBFS
```python
df.write.csv("dbfs:/mnt/output/csv_out")
```

---

## 6.8 Writing CSV/Parquet Files
CSV:
```python
df.write.mode("overwrite").option("header", True).csv("dbfs:/mnt/output/sales_csv")
```

Parquet:
```python
df.write.mode("overwrite").parquet("dbfs:/mnt/output/sales_parquet")
```

---

## 6.9 Commands for Writing CSV and Parquet
```python
df.write.csv("dbfs:/path/csv")
df.write.parquet("dbfs:/path/parquet")
```

---

## 6.10 Writing Other File Formats
```python
df.write.json("dbfs:/output/json")
df.write.format("delta").save("dbfs:/output/delta")
df.write.orc("dbfs:/output/orc")
```

---

## 6.11 Summary Table
| Format | Write Command |
|--------|---------------|
| CSV | `df.write.csv()` |
| Parquet | `df.write.parquet()` |
| JSON | `df.write.json()` |
| Delta | `df.write.format("delta").save()` |
| ORC | `df.write.orc()` |

---



