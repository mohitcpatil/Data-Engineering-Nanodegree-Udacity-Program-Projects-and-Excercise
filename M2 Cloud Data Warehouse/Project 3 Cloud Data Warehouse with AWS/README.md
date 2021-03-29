# Project Summary - Data Warehouse 

A music streaming company Sparkify has grown their user and songs database and wants to move the data and involved processes to the cloud.The company data resides in S3 having directory of JSON log files of the user activity on the app and directory of JSON metadata of songs in the app.

The task is to build an ETL pipeline that extracts their data from S3, stages them in Redshift, and transforms data into a set of dimensional tables for their analytics team to run the analysis queries i.e. what songs users are listening to

# Project Description
 
 We are going to implement the AWS and Data warehouse concepts to build an ETL pipeline by hosting the database on redshift. Data from S3 will be loaded into staging tables created on redshift. After which run the SQL statements to create  
 analytics tables such as Fact and dimension tables from the data stores in staging tables. Analytics tables then used for analysis on user activity.

# Project Datasets

Their are two sets of Datasets to complete this project Songs and User logs.
-  Here are the S3 links for each:
     - **Song data:** `s3://udacity-dend/song_data`
     - **Log data:** `s3://udacity-dend/log_data`
     - **Log data json path:** `s3://udacity-dend/log_json_path.json`
    
### Song Dataset
This dataset contains million songs metadata i.e. data about songs and artists.The files are partitioned by the first three letters of each song's track ID.

**For example, here are filepaths to two files in this dataset.**
- `song_data/A/B/C/TRABCEI128F424C983.json`
- `song_data/A/A/B/TRAABJL12903CDCF1A.json`

**Below example of what a single song file, TRAABJL12903CDCF1A.json, looks like.**

{"num_songs": 1, "artist_id": "ARJIE2Y1187B994AB7", "artist_latitude": null, "artist_longitude": null, "artist_location": "", "artist_name": "Line Renaud", "song_id": "SOUPIRU12A6D4FA1E1", "title": "Der Kleine Dompfaff", "duration": 152.92036, "year": 0}

### Log Dataset
This dataset contain the log files of the user activity on the songs of above dataset. This data is partitioned by Year and Month.

**For example, here are filepaths to two files in this dataset.**
log_data/2018/11/2018-11-12-events.json
log_data/2018/11/2018-11-13-events.json


# Database Schema Design 

Creating Staging, Fact and Dimensions tables 

#### Staging Tables
   - **Staging_Events**
   - **Staging_songs**
   
#### Fact Table

-  **songplays** - records in event data associated with song plays 
    -  songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent

#### Dimension Tables

   -  **users** - users in the app
       -  user_id, first_name, last_name, gender, level
    
   -  **songs** - songs in music database
        - song_id, title, artist_id, year, duration
    
   -  **artists** - artists in music database
        - artist_id, name, location, lattitude, longitude

  -   **time** - timestamps of records in songplays broken down into specific units
        - start_time, hour, day, week, month, year, weekday

# How to Run Project 

###### 1. Configure the dwh.config file
- Add the AWS access and secret keys in dwh.config file 
- Specify the IAM_ROLE link in after creating the redshift cluster
- For cluster provide the endpoint address as host
            
###### 2. Run the Create_Redshift_Cluster file `python create_redshift_cluster.ipynb`. Below are the steps are followed in redshift cluster file.
-   Import the libraries required to use AWS SDK 
-   Using configparser read the AWS cluster configuration file to access the parameters 
- Configure the AWS SDK boto3 to use in python 
- Check for the files present in directory using bucket
- Create an IAM Role for providing the suitable permission required to create redshift cluster (This allows redshift clusters to run AWS services on behalf)
- Attach the role to the newly created redshift cluster
- Edit the cluster and add Redshift_security_group in Network and security group name
Note : I assume you have already created the Redshift_security_group 
- Note down the ARN and Endpoint to mention it in dwh.config
- Authenticate the security access group 
- Connect to the database 

###### 3. Run the create_tables.py file using termianl `python create_tables.py`
- This files calls the drop_table and create_table functions defined in `sql_queries.py` which creates all fact,dimensional and staging tables

###### 4. Run the etl.py file using termianl `python etl.py`
- This file calls the function load_staging_table function which loads the data from S3 to staging tables and insert the data from staging to dimensional tables.

###### 5. Run the queries written in `Create_redshift_cluster.ipynb` file to check the data has been loaded into fact and dimensional tables 

# Description of each file

* **sql_queries.py** - contains sql queries for dropping and creating fact and dimension and staging tables. Also, contains insertion query template. 

* **create_tables.py** - contains code for setting up database. Running this file creates and drops fact and dimension tables.

* **Create redshift cluster.ipynb** - a jupyter notebook to create a IAM Role and Redshift cluster database to load the data from S3.

* **etl.py** - By running this file we load the data from S3 to staging tables and also insert the data into fact and dimensional tables

* **dwh.cfg** - This configuration file contains all the keys for database,IAM roles and clusters.=

# Steps Followed to create project 

- **Create Table Schemas**

  -  Design schemas for your fact and dimension tables
  -  Write a SQL CREATE statement for each of these tables in sql_queries.py
  - Complete the logic in create_tables.py to connect to the database and create these tables
  -  Write SQL DROP statements to drop tables in the beginning of create_tables.py 
  -  if the tables already exist. This way, you can run create_tables.py whenever you want to reset your database and test your ETL pipeline.
   -  Launch a redshift cluster and create an IAM role that has read access to S3.
   - Add redshift database and IAM role info to dwh.cfg.
   - Test by running create_tables.py and checking the table schemas in your redshift database. You can use Query Editor in the AWS Redshift console for this.

- **Build ETL Pipeline**

    - Implement the logic in etl.py to load data from S3 to staging tables on Redshift.
    - Implement the logic in etl.py to load data from staging tables to analytics tables on Redshift.
    - Test by running etl.py after running create_tables.py and running the analytic queries on your Redshift database to compare your results with the expected results.
    - Delete your redshift cluster when finished.


