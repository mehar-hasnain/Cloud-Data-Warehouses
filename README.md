# Introduction

Sparikfy a music streaming startup wants to perform analysis on song play. Using their song and event datasets we have designed and implemented star schema on AWS redshift.

Star schema include the following tables:

### Fact Tables
**songplays** - records in event data associated with song plays 
`songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent`

### Dimension Tables
 **users** - users in the app
`user_id, first_name, last_name, gender, level`
 **songs** - songs in music database
`song_id, title, artist_id, year, duration`
**artists** - artists in music database
 `artist_id, name, location, lattitude, longitude`
**time** - timestamps of records in songplays broken down into specific units
`start_time, hour, day, week, month, year, weekday`

# ETL Process

Before inserting data into dimensions and fact tables we have created staging schema to ingest data from S3 source. 

Staging Schema include the following tables:

**staging_events** - records in log data associated with song plays i.e. records with page NextSong

`event_id, artist_name, auth, user_first_name, user_gender, item_in_session, user_last_name, song_length, user_level, location, method, page, registration, session_id, song_title, status, ts, user_agent, user_id`
    

**staging_songs** 

`song_id, num_songs, artist_id, artist_latitude, artist_longitude, artist_location, artist_name, title, duration, year`

# How to run

Run the following Python files in given order:

1. `create_tables.py`
2. `etl.py`
