# Raspberry-Pi-Programs
This is Raspberry Pi project of displaying the sensor data over a webpage via NGINX and UWSGI server.

Install Flask, NGINX and UWSGI on Pi by “sudo-apt get install” command.

Sign in with root user as it would give much greater access so type “sudo su” and set up a password for root user and remember it.

The corresponding file for UWSGI server that is, the ini file is also uploaded alongside.

The project is based on Python3 so you would have to install te

The additional directories that need to be created are: /var/www/lab_app (to run the code more easily as the location and extensions are already settled inside the different file uploaded on my GitHub).

Install sqlite3 then at the command line type : 
i.	“sqlite3 lab_app.db 
ii.	 sqlite> begin; 
iii. sqlite> create table temperatures (rDatetime datetime, sensorID text, temp numeric); 
iv.	 sqlite> insert into temperatures values (datetime(CURRENT_TIMESTAMP), "1", 25);
v.	 sqlite> commit;”

To see the values stored in the database, type the following command 
“sqlite> select * from temperatures” then 
“sqlite>.exit” 
Repeat the same process for the humidities table.

For automatically adding values to the database, we can use crontab. 
i.	Open the command line and type “crontab -e” then from there choose nano then at the last of the page paste the below code for taking values every 10 minutes.
ii.	“*/10 * * * * /var/www/lab_app/python  /var/www/lab_app/bin/env_log.py”
iii.	For choosing the recurring time format i.e., ”*/10 * * * *”, Go to: “crontab.guru”
