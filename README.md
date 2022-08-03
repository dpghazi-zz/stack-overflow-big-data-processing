# AWS EMR Big Data Processing w/ Spark and Hadoop | Python, PySpark 
## **Project Description**

- Spun an EMR cluster and do a spark submit job on it to process data from [2021 Stack Overflow Annual Developer Survey](https://insights.stackoverflow.com/survey).
- Wrote codes (Python & PySparkSQL) for the spark storage job to to process the data.
- Connected to the EMR master node using SSH to run interactive queries, examine log files, and submit Linux commands via Amazon Linux 2.

### **Overview**

- Created an EMR cluster with a cluster launch mode where a S3 bucket was created automatically to store the logs
    - Software Configuration
        - emr-5.33.0
        - Spark: Spark 2.4.7 on Hadoop 2.10.1 YARN and Zeppelin 0.9.0
    - Hardware Configuration
        - m5.xlarge
        - Number of instances: 3
    - Security and access
        - EC2 key pair (used Amazon EC2 to create an ED25519 key pair)
- Created a S3 bucket to upload the file (survey_results_public.csv) so the EMR can access it for data processing
- Created a new folder within the bucket called data-source which contains the csv file
- Wrote codes (Python & PySparkSQL) for the spark storage job to to process the data.
- Opened port 22 to SSH into EMR cluster using my IP address.

### Language **& Tools**

- Python
- SQL (PySparkSQL)
- Shell
- AWS (EMR, EC2, S3, Amazon Linux 2)
