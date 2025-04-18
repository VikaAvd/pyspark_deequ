# Deequ + PySpark Data Quality Checks

### 📊 Homework Task for EPAM DQE Intermediate Course

This project demonstrates how to use **PySpark** with **AWS Deequ** to perform data profiling, constraint suggestions, and constraint verification on a **Microsoft SQL Server** database.

## 🚀 What’s inside
- 🔗 Connection to **MS SQL Server** using JDBC
- 📊 Data Analyzing section with `AnalysisRunner`
- 📈 Data Profiling with `ColumnProfilerRunner`
- 🧠 Constraint Suggestions based on actual data patterns
- ✅ Constraint Verification using `VerificationSuite`
- 📄 Check reports in **CSV** and **HTML** formats

## 📂 Folder Structure
```bash
├── 📒 Deequ_pySpark_skeleton.ipynb        # Completed notebook with results and explanations
├── 📄 constraint_verification_report.csv  # Exported test report (CSV format)
├── 🌐 constraint_verification_report.html # Exported test report (HTML format)
└── 📝 README.md                           # Project description and instructions
```

## ⚙️ Environment Setup
1. Install Docker on Windows https://docs.docker.com/desktop/windows/install/
2. Clone the Jupyter Docker Stacks repository https://github.com/jupyter/docker-stacks
    ```cd docker-stacks```
3. Download ***spark-3.5.5-bin-hadoop3.tgz*** here ```https://spark.apache.org/downloads.html```
4. Update the Dockerfile to use Spark 3.5.5 (in the ```docker-stacks/pyspark-notebook/Dockerfile```) if needed.
5. Rebuild docker "pyspark-notebook" image to support spark 3.5.5 version for PyDeequ according to instructions: https://jupyter-docker-stacks.readthedocs.io/en/latest/using/specifics.html    
    Note: Generate ***SHA256*** for your file 'spark-3.5.5-bin-hadoop3.tgz' to add a checksum (e.g.: ```SHA256 hash of spark-3.5.5-bin-hadoop3.tgz:8daa3f7fb0af2670fe11beb8a2ac79d908a534d7298353ec4746025b102d5e31``` )

6. Run the rebuilt docker Image:
    ```docker run -v ${PWD}:/home/jovyan/work -p 8888:8888 -p 4040:4040 --user root -e JUPYTER_ENABLE_LAB=yes --name pyspark jupyter/pyspark-notebook:spark-3.5.5```    
7. After the container starts, find and open one of the tokenized URLs in the terminal. It will look like:
    - http://localhost:8888/lab?token={your_token}
    - http://127.0.0.1:8888/lab?token={your_token}
8. Copy the JDBC Driver to the Container.
    You’ll need a Microsoft SQL Server JDBC driver (e.g. mssql-jdbc-12.10.0.jre11.jar).
    Run this from PowerShell (adjust the path and versions as needed):
    ```docker cp "C:\path\to\mssql-jdbc-{your_version}}.jre{version}.jar" pyspark:/opt/spark/jars/```
9. Install PyDeequ inside the container:
    ```pip install git+https://github.com/awslabs/python-deequ.git```


## 💡 How to run
1. Access Jupyter at localhost:8888 and open **Deequ_pySpark_skeleton.ipynb**
2. Follow along the notebook steps:
    - Run `%env SPARK_VERSION=3.5.5`
    - Initialize session with PyDeequ and JDBC Support
    - Connect to DB (**adjust connection properties with your values**)
    - Run Analysis and Profiling sections
    - Generate Constraint Suggestions
    - Run Constraint Verifications
    - Export Final Reports
