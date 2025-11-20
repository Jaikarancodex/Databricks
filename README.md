# Databricks

---

## **1. Databricks Overview**
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

# 🚀 2. Workspace Navigation

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

# 🚀 3. Cluster Creation

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


