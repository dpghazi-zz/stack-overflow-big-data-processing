# AWS EMR Big Data Processing w/ Spark and Hadoop | Python, PySpark 
## **Project Description**

- Launched an Elastic MapReduce (EMR) cluster and created a Spark application written in Python.
- Implemented Python API for Apache Spark (PySpark) and performed spark-submit to process data from the [2021 Stack Overflow Annual Developer Survey](https://insights.stackoverflow.com/survey).
- Created an S3 bucket to upload a csv file so EMR can access it for data processing.
- Locally issued Linux commands (Amazon Linux 2) to the master node by connecting to Elastic Compute Cloud (EC2) instance using Secure Shell (SSH) connection.

### **Overview**

- Created an EMR cluster with cluster launch mode and first S3 bucket was created automatically to store logs
    - Software Configuration
        - emr-5.33.0
        - Spark: Spark 2.4.7 on Hadoop 2.10.1 YARN and Zeppelin 0.9.0
    - Hardware Configuration
        - m5.xlarge
        - Number of instances: 3
    - Security and access
        - EC2 key pair (used Amazon EC2 to create an ED25519 key pair)
- Set-up a new S3 bucket to upload file ("survey_results_public.csv") so EMR can access it for data processing
- Inserted a new folder within the same S3 bucket called “data source” that contains the csv file
- Created a Spark application in a Python file called “main.py” for Spark storage job to process data
- Opened port 22 to SSH into the EMR cluster using IP address and spark-submitted “main.py” for data processing
- A new folder called “data output” was created in the same S3 bucket, executing commands from the “main.py” file

### Language **& Tools**

- Python (PySpark)
- SQL 
- Shell
- AWS (EMR, EC2, S3, Amazon Linux 2)
