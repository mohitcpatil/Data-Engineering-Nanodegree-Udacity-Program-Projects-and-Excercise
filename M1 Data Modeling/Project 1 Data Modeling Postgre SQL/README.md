# Project Summary 

Sparkify startup wants to analyze the data they have been collecting on songs and user activity. Analytics team is particularly interested in what songs users are interested in listening. Currently, they don't have an easy way to query their data, which resides in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.

# How to Run python scripts -

To create database tables run the command in python terminal - python create_tables.py

To create ETL pipeline and load the data into tables run - python etl.py 



# Schema for Song Play Analysis -  

* **Fact Table** -

      songplays records in log data associated with song plays


* **Dimension Tables** - 

      users in the app

      songs in music database

      artists in music database

      time timestamps of records in songplays broken down into specific units


# Projects files -

* **sql_queries.py** - contains sql queries for dropping and creating fact and dimension tables. Also, contains insertion query template.

* **create_tables.py** - contains code for setting up database. Running this file creates sparkifydb and also creates the fact and dimension tables.

* **etl.ipynb** - a jupyter notebook to analyse dataset before loading.

* **etl.py** - read and process song_data and log_data

* **test.ipynb** - a notebook to connect to postgres db and validate the data loaded.



