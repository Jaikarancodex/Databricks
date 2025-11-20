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

Generated automatically as requested.
