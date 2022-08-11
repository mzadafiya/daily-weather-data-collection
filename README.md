# Problem Statement

Subscribe to https://rapidapi.com/community/api/open-weather-map/

Use the docker container to create airflow and postgres instances.

1. Create the first task to use endpoint /Current Weather Data for at least 10 states of India and fill up the csv file with details of State, Description, Temperature, Feels Like Temperature, Min Temperature, Max Temperature, Humidity, Clouds.
2. Create a second task to create a postgres table “Weather” that would have columns same as the csv file.
3. Create a third task that should fill the columns of the table while reading the data from the csv file.
4. Schedule the DAG in AirFlow to run every day at 6:00 am and update the daily weather detail in csv as well as the table.

# Solution

## Start airflow
"sh restart.sh"

Open hhttp://localhost:8080/connection/list/ in browser

username = airflow
passwrod = airflow

## Create below connectction

* Conn Id: rapid_api_connection
* Conn Type: HTTP
* Host: community-open-weather-map.p.rapidapi.com
* Schema: https
* Extra: {"X-RapidAPI-Key": "**your secret**"}

## Update below connection

* Conn Id: postgres_default
* Conn Type: Postgres
* Host: postgres
* Schema: airflow_db
* Login: airflow
* Password: airflow
* Port: 5432

## Enable weather dag

## Check psql table

* docker ps
* docker exec -it <docker_id> /bin/bash
* psql -U airflow  -d airflow_db
* SELECT * FROM weather_data;
