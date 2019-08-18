**Instructions**

1. Business case
Sparkify startup company  needs to organise and analyse the information about it's users who subscribe and play online music on its company web portal. Users can subscibe for free or pay a subscription fee.

2. Data extraction , transformation and loading
A python script file etl.py has been developed to extract, transform and load user activity information from website log files into fact and dimension tables

3. Execute ETL pipeline
i. Open the Execute.ipynb notebook
ii. Run the first line of code to reset the database tables
iii. Run the second line of code to  read data from log files into the tables
iv. Open the test.ipynb notebook and run the lines of codes to verify  that data has been imported into the database

4. Sample songs analysis

To get the top 5 most listened-to songs you need to execute the line of code below in your test.ipynb notebook

%sql SELECT song_id, sum(duration) FROM songs GROUP BY songs.song_id ORDER BY sum(duration) DESC LIMIT 5

5. Database design

**Fact table**

**i. songplays table : play records from the log data**

columns:

songplay_id int
start_time timestamp NOT NULL -> foreign key to reference the time table which contains specific date and time units
user_id int NOT NULL
level varchar NOT NULL
song_id varchar
artist_id varchar
session_id int NOT NULL
location varchar NOT NULL
user_agent varchar NOT NULL

PRIMARY KEY (songplay_id, start_time, user_id, session_id, location, user_agent)


**Dimension tables**

**i. users : user records showing personal details**

columns:

user_id int PRIMARY KEY
first_name varchar NOT NULL
last_name varchar NOT NULL
gender char
level varchar NOT NULL


**ii.  songs : records of available songs for playing**

columns: 

song_id varchar NOT NULL
title varchar NOT NULL
artist_id varchar  NOT NULL  -> foreign key to reference the artists table based on the artist_id
year int
duration numeric NOT NULL


**iii. artists : artists in the music database**

columns:

artist_id varchar PRIMARY KEY
name varchar NOT NULL
location varchar
latitude numeric
longitude numeric

**iv: time : timestamps of records in songplays broken down into specific units**


columns:

start_time timestamp   PRIMARY KEY
hour int NOT NULL
day int NOT NULL
week int NOT NULL
month int NOT NULL
year int NOT NULL
weekday int NOT NULL


