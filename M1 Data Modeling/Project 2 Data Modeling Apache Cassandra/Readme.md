# Project - Data Modeling with Cassandra

In this project, we need analyze the data we have been collecting on songs and user activity on their new music streaming app. The analysis team is particularly interested in understanding what songs users are listening to. Currently, there is no easy way to query the data to generate the results, since the data reside in a directory of CSV files on user activity on the app.

# Project Overview

In this project, you'll apply what you've learned on data modeling with Apache Cassandra and complete an ETL pipeline using Python. To complete the project, you will need to model your data by creating tables in Apache Cassandra to run queries. You are provided with part of the ETL pipeline that transfers data from a set of CSV files within a directory to create a streamlined CSV file to model and insert data into Apache Cassandra tables.

# Datasets

For this project, you'll be working with one dataset: event_data. The directory of CSV files partitioned by date. 
s
- event_data/2018-11-08-events.csv
- event_data/2018-11-09-events.csv

# Project Steps

## Below are steps you can follow to complete each component of this project.

- Modeling your NoSQL database or Apache Cassandra database
- Design tables to answer the queries outlined in the project template
- Write Apache Cassandra CREATE KEYSPACE and SET KEYSPACE statements
- Develop your CREATE statement for each of the tables to address each question
- Load the data with INSERT statement for each of the tables
- Include IF NOT EXISTS clauses in your CREATE statements to create tables only if the tables do not already exist. We recommend you also include DROP TABLE statement for each table, this way you can run drop and create tables whenever you want to reset your database and test your ETL pipeline
- Test by running the proper select statements with the correct WHERE clause

## Build ETL Pipeline

- Implement the logic in section Part I of the notebook template to iterate through each event file in event_data to process and create a new CSV file in Python
- Make necessary edits to Part II of the notebook template to include Apache Cassandra CREATE and INSERT statements to load processed records into relevant tables in your data model
- Test by running SELECT statements after running the queries on your database

## Reviews by Mentor -

<img width="1076" alt="Screen Shot 2021-05-05 at 2 58 23 PM" src="https://user-images.githubusercontent.com/900824/117216233-4a778f00-adb4-11eb-9393-9a94944b2432.png">

<img width="1040" alt="Screen Shot 2021-05-05 at 2 58 45 PM" src="https://user-images.githubusercontent.com/900824/117216244-4e0b1600-adb4-11eb-88e6-89c83c28e4cc.png">

<img width="1059" alt="Screen Shot 2021-05-05 at 2 58 58 PM" src="https://user-images.githubusercontent.com/900824/117216256-51060680-adb4-11eb-9997-2becb5acb2d9.png">
