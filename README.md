# Raspberry-Pi-Programs
A web-server to display sensor data in table format which is stored in a SQLite database. 

This is Raspberry Pi project of dispalying the sensor data over a webpage via NGINX and UWSGI server.

install Flask, NGINX and UWSGI on Pi.

The data is stored in SQLite database and accessed by Python webpage code.

The corresponidng file for UWSGI server that is, the ini file is also uploaded alongside.

The project is based on Python3.

The addidtional directories that need to be created are: /var/www/lab_app
(to run the code more easily as the location and extensions are already settled inside)

Currently the project is still under progress, as im trying to add Google charts to display the data more precisely and effectively.

install sqlite3 then at the command line type : sqlite3 lab_app.db
sqlite> begin;
sqlite> create table temperatures (rDatetime datetime, sensorID text, temp numeric);
sqlite> insert into temperatures values (datetime(CURRENT_TIMESTAMP), "1", 25)
sqlite>commit;

to see the values in the database
sqlite> select * from temperatures

sqlite>.exit

do the same for the humdities table

for adding values every 10 minutes open the command line and type crontab -e
then from there choose nano
then at last paste 
*/10 * * * * /var/www/lab_app/python /var/www/lab_app/bin/env_log.py

for chossing the recurring time go to: crontab.guru
