# Stack Overflow Data Processing
## **Project Description**

- Spun an Elastic MapReduce cluster (based on Apache Hadoop) and created a Spark application written in Python.
- Implemented Python API for Apache Spark (PySpark) and performed spark-submit to process data from the [2020 Stack Overflow Annual Developer Survey](https://insights.stackoverflow.com/survey).
- Created an S3 bucket to upload a CSV file so EMR can access it for data processing.
- Locally issued Linux commands (Amazon Linux 2) to the master node by connecting to Elastic Compute Cloud (EC2) instance using Secure Shell (SSH) connection.

### **Overview**

- Created an EMR cluster with cluster launch mode and initial S3 bucket was created automatically to store logs
    - Software Configuration
        - emr-5.36.0
        - Spark: Spark 2.4.8 on Hadoop 2.10.1 YARN and Zeppelin 0.10.0
    - Hardware Configuration
        - m5.xlarge
        - Number of instances: 3
    - Security and access
        - EC2 key pair (used Amazon EC2 to create a RSA key pair)
![Kapture 2022-08-17 at 16 07 08](https://user-images.githubusercontent.com/94224903/185259581-10e86439-fb22-48de-8593-f423cd1e2079.gif)
- Set-up a new S3 bucket to upload file ("survey_results_public.csv") so EMR can access it for data processing
![Kapture 2022-08-17 at 16 45 30](https://user-images.githubusercontent.com/94224903/185263036-71f3576e-9504-4e3b-a30d-fffa6b0b4ee0.gif)






- Inserted a new folder within the same S3 bucket called “data source” that contains the CSV file
- Created a Spark application in a Python file called “main.py” for Spark storage job to process data
- Opened port 22 to SSH into the EMR cluster using IP address and spark-submitted “main.py” for data processing
- A new folder called “data output” was created in the same S3 bucket, executing commands from the “main.py” file

### Language **& Tools**

- Python
- Spark (PySpark)
- Hadoop Distribution: MapReduce (Amazon EMR)
- Shell
- AWS (EMR, EC2, S3, Amazon Linux 2)
