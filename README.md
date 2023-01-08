# QLIK_Olympics_Data_Model
Data Model built in Qlik App during the course "Creating Your First Qlik Sense App" in Pluralsight

This model uses three databases:

1. Medals table (DP_LIVE_13102018040554424): this table contains the GDP data with the following fields:
Location, indicator, subject, measure, frequency, year, value and flag codes

2. GDP data (athlete_events): this table contains the athlete data, with the following fields:
ID, name, sex, age, height, weight, team, location, games, year, season, city, sport, event and medal
(Note: this table is not included in this repository due to its size)

3. MapCountryName (noc_regions): this table contains the countries and their names

## Data Model

These tables are linked to each other using the fields "YEAR" and "LOCATION" as shown in the below image:

![Alt text](/images/qlik2.JPG)

To enable these links, I had to:

- Load the table MapCountryName as a Mapping Load table:

![Alt text](/images/qlik3.JPG)

- Edit the name of the field NOC to LOCATION in the Medals table and link MapCountryName table as a Mapping Table:

![Alt text](/images/qlik4.JPG)

- Edit the name of the field Time to YEAR in the GDP data table:

![Alt text](/images/qlik5.JPG)

After that, we could create the Olympics Data Model to be able to analyze the data contained in these three tables.

Our model is based in the following structure:

![Alt text](/images/qlik1.JPG)

We can see the data in a High-Level Summary in the first sheet, that is a KPI with the following charts:

- Number of Athletes - this field count the number of athletes who participated in the Olympics
- Participation and Medal Winners - this chart shows the amount of medal winners per medal type: Bronze, Gold, Silver or NA (no medal)
- Country Name - this table contains the name of all countries
- Athletes Participation over the Years - this shart shows how many athletes participated in the Olympics over the years

![Alt text](/images/qlik6.JPG)

In this sheet we are able to filter by countries and also medal type to get a more detailed scenario.

In example, here we can see a detailed visualization with the data for USA, excluding non-medals:

![Alt text](/images/qlik7.JPG)

And here we can see the same, but for Brazil:

![Alt text](/images/qlik8.JPG)

[Sheet 1](https://tmxx59gmlb7gjvt.eu.qlikcloud.com/single/?appid=75be3d5d-1823-427b-a1c5-9aa3009ea961&sheet=177547dd-dc69-4156-9909-8aafab537d1e&theme=horizon&opt=ctxmenu,currsel)

[Sheet 2](https://tmxx59gmlb7gjvt.eu.qlikcloud.com/single/?appid=75be3d5d-1823-427b-a1c5-9aa3009ea961&sheet=e8f97a27-2676-4fec-8324-cf4a57bcc860&theme=horizon&opt=ctxmenu,currsel)

[Sheet 3](https://tmxx59gmlb7gjvt.eu.qlikcloud.com/single/?appid=75be3d5d-1823-427b-a1c5-9aa3009ea961&sheet=23f17ebc-d0f7-4df2-bd46-46edb1ddd754&theme=horizon&opt=ctxmenu,currsel)
