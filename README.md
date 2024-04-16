## Raspberry Pi Sensor Data Display Webpage

This Raspberry Pi project involves displaying sensor data over a webpage using NGINX and UWSGI servers. The project utilizes Flask for web framework, NGINX as the web server, and UWSGI for serving Python web applications.

### Installation

1. **Install Required Packages:**
   Use the following command to install Flask, NGINX, and UWSGI on your Raspberry Pi:
   ```
   sudo apt-get install python3-flask nginx uwsgi
   ```

2. **Switch to Root User:**
   Sign in as the root user to gain necessary access:
   ```
   sudo su
   ```

3. **Set Up Root Password:**
   Set up a password for the root user by executing:
   ```
   passwd root
   ```

4. **Create Directories:**
   Create the directory `/var/www/lab_app` for easier code execution. This directory structure is assumed to be set up within the project files.

5. **SQLite Database Setup:**
   - Install SQLite3 and create the database:
     ```
     sqlite3 lab_app.db
     ```
   - Create tables for temperatures and humidities:
     ```sql
     sqlite> begin;
     sqlite> create table temperatures (rDatetime datetime, sensorID text, temp numeric);
     sqlite> insert into temperatures values (datetime(CURRENT_TIMESTAMP), "1", 25);
     sqlite> commit;
     ```
   - Repeat the same process for the `humidities` table.

6. **Crontab Configuration:**
   - Open the crontab editor:
     ```
     crontab -e
     ```
   - Add the following line to execute a script for adding values to the database every 10 minutes:
     ```
     */10 * * * * /var/www/lab_app/python /var/www/lab_app/bin/env_log.py
     ```
   - Use a crontab generator like `crontab.guru` to define the desired recurring time format.

### Additional Notes
- Ensure Python3 is installed as the project is based on Python3.
- Adjust file paths and permissions as necessary for your setup.
- Modify and enhance the code according to your requirements.
- For any issues or suggestions, open an issue in the project repository.
