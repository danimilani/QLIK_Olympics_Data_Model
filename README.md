# QLIK_Olympics_Data_Model
Data Model built in Qlik App during the course "Creating Your First Qlik Sense App" in Pluralsight

This model uses three databases:

1. DP_LIVE_13102018040554424: this table contains the GDP data with the following fields:
Location, indicator, subject, measure, frequency, year, value and flag codes

2. athlete_events: this table contains the athlete data, with the following fields:
ID, name, sex, age, height, weight, team, location, games, year, season, city, sport, event and medal
(Note: this table is not included in this repository due to its size)

3. noc_regions: this table contains the countries and their names

## Data Model

These tables are related to each other using the fields YEAR and LOCATION as shown in the below image:

![Alt text](/screenshots/qlik2.JPG)


[Sheet 1](https://tmxx59gmlb7gjvt.eu.qlikcloud.com/single/?appid=75be3d5d-1823-427b-a1c5-9aa3009ea961&sheet=177547dd-dc69-4156-9909-8aafab537d1e&theme=horizon&opt=ctxmenu,currsel)

[Sheet 2](https://tmxx59gmlb7gjvt.eu.qlikcloud.com/single/?appid=75be3d5d-1823-427b-a1c5-9aa3009ea961&sheet=e8f97a27-2676-4fec-8324-cf4a57bcc860&theme=horizon&opt=ctxmenu,currsel)

[Sheet 3](https://tmxx59gmlb7gjvt.eu.qlikcloud.com/single/?appid=75be3d5d-1823-427b-a1c5-9aa3009ea961&sheet=23f17ebc-d0f7-4df2-bd46-46edb1ddd754&theme=horizon&opt=ctxmenu,currsel)
