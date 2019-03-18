# Weather-Company-Wind-Alerts
Here you'll find Python code you can schedule to check for wind and wind gust alerts every hour that leverages The Weather Company's wind and wind gust Forecast, a DB2 Database on IBM Cloud to store thresholds with delivery information once tresholds are exceeded, a GMail account to email the alerts, and a Weather Company Data Package key.

REQUIRES: 
1) DB2 DATABASE ON IBM CLOUD
Go to IBM Cloud and create a DB2 Databsse instance(https://console.bluemix.net/catalog/services/db2-warehouse)
Required Fields in DB2 Database: NAME (VARCHAR), LATITUDE (DECIMAL), LONGITUDE (DECIMAL), WIND_THRESHOLD (SMALLINT), WIND_GUST_THRESHOLD (SMALLINT), EMAIL (VARCHAR)
Within the Python code you'll edit the following with your information:
...ibm_db.connect("DATABASE=YOUR_DB2_DB_NAME_HERE;HOSTNAME=YOUR_DB2_HOST_NAME_HERE;PORT=YOUR_DB2_PORT_HERE;PROTOCOL=TCPIP;UID=YOUR_DB2_USERNAME_HERE;PWD=YOUR_DB2_PASSWORD_HERE", "YOUR_DB2_USERNAME_HERE", "YOUR_DB2_PASSWORD_HERE")...

2) GMAIL ACCOUNT TO SEND EMAILS
Also using gmail to email alerts.  You'll need a database and a Gmail account prior to using this script as it requires these two.
Within the Python Code, you'll need to update the following:
...send_email('GMAIL_USERNAME_HERE', 'GMAIL_PASSWORD_HERE', email, sub, bod) ...

3) WEATHER COMPANY TRIAL KEY
We're using The Weather Company Enhanced Forecast - Forecast On Demand.  
Within the Python Code, you'll need to update the following:
...url = url + '&format=json&units=e&language=en-US&apiKey=YOUR_WEATHER_COMPANY_KEY_HERE}'...

Once you have these working parts in order, use something like iBM Watson Studio to schedule and send emails once thresholds have been exceeded. 
