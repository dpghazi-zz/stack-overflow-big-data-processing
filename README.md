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
![Kapture 2022-08-17 at 17 02 56](https://user-images.githubusercontent.com/94224903/185264338-9171114a-d83c-4018-bd85-8e164c3964d8.gif)
- Inserted a new folder within the same S3 bucket called “data source” that contains the CSV file
![Kapture 2022-08-17 at 17 12 50](https://user-images.githubusercontent.com/94224903/185265193-2391efaa-5f12-48a6-89c2-05a8fd609765.gif)
- Created a Spark application in a Python file called “main.py” for Spark storage job to process data
```Python
from pyspark.sql import SparkSession
from pyspark.sql.functions import col

S3_DATA_SOURCE_PATH = 's3://stackoverflow-123456/data-source/survey_results_public.csv'
S3_DATA_OUTPUT_PATH = 's3://stackoverflow-123456/data-output'

def main ():
    spark = SparkSession.builder.appName('StackoverflowApp').getOrCreate()
    all_data = spark.read.csv(S3_DATA_SOURCE_PATH, header=True)
    print('Total number of records in the source data: %s' % all_data.count())
    selected_data = all_data.where((col('Country') == 'United States') & (col('WorkWeekHrs') > 45))
    print('The number of engineers who work more than 45 hours a week in the US is: %s' % selected_data.count())
    selected_data.write.mode('overwrite').parquet(S3_DATA_OUTPUT_PATH)
    print('Selected data was was successfully saved to S3: %s' % S3_DATA_OUTPUT_PATH)

if __name__ == '__main__':
    main()
```
- Opened port 22 to SSH into the EMR cluster using IP address and spark-submitted “main.py” for data processing
![Kapture 2022-08-17 at 17 35 25](https://user-images.githubusercontent.com/94224903/185267170-3fd6b9ac-9578-4b03-abe6-f4039d36a675.gif)

- A new folder called “data output” was created in the same S3 bucket, executing commands from the “main.py” file

### Language **& Tools**

- Python
- Spark (PySpark)
- Hadoop Distribution: MapReduce (Amazon EMR)
- Shell
- AWS (EMR, EC2, S3, Amazon Linux 2)
