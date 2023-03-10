# Olympics Data Model in Qlik Cloud

## Table of Contents
1. [Introduction](#introduction)
2. [Dataset and Importing the Database](#item2)
3. [Data Preparation](#item3)
4. [Data Visualization](#item4)
   
   4.1. [Olympics Data Model - Sheet 1](#sheet1)
   
   4.2. [Athlete Medal Details - Sheet 2](#sheet2)
   
   4.3. [GDP Details - Sheet 3](#sheet3)

5. [Data Exploration](#item5)
6. [References](#item6)

  
## 1. Introduction <a name="introduction"></a>

This project is a Data Model built in Qlik App during the course "Creating Your First Qlik Sense App" in Pluralsight. 

The database used in this project is related to the Olympic Games and it includes the data from Athens 1896 to Rio 2016. We also use the countries' names and their GDP data to enhance the database.

I have used the Qlik Cloud to elaborate this dataset and here i describe the process to import, prepare and visualize the data. I also describe an example of data exploration, with a video showing how to filter data in the Dashboard and a few inferences that we can make by analyzing the filtered data in the Dashboards.

## 2. Dataset and Importing the Database <a name="item2"></a>

This model uses three databases:

1. GDP data (DP_LIVE_13102018040554424): this table contains the GDP data with the following columns:
"LOCATION","INDICATOR","SUBJECT","MEASURE","FREQUENCY","TIME","Value","Flag Codes".

2. Medals (athlete_events): this table contains the athlete data, with the following columns:
"ID","Name","Sex","Age","Height","Weight","Team","NOC","Games","Year","Season","City","Sport","Event","Medal".

3. MapCountryName (noc_regions): this table contains the countries and their names

*Please note that you are required to have a Qlik Sense account in order to view the dynamic sheets mentioned in the links below.*

## 3. Data Preparation <a name="item3"></a>

These tables were linked to each other using the fields "YEAR" and "LOCATION" as shown in the below image:

![Qlik Links](/images/qlik2.JPG)

To prepare the database and be able to perform these links, I had to:

- Load the table MapCountryName as a Mapping Load table:

![Mapping Load Table](/images/qlik3.JPG)

- Edit the name of the field NOC to LOCATION in the Medals table and link MapCountryName table as a Mapping Table:

![Medals Table](/images/qlik4.JPG)

- Edit the name of the field Time to YEAR in the GDP data table:

![GDP Table](/images/qlik5.JPG)

## 4. Data Visualization <a name="item4"></a>

After that, I could create the Olympics Data Model to be able to analyze the data contained in these three tables.

Our model is based in the following structure:

![App Structure](/images/qlik1.JPG)

### 4.1. Olympics Data Model - Sheet 1 <a name="sheet1"></a>

We can see the data in a High-Level Summary in the first sheet, that is a KPI with the following charts:

- Number of Athletes - this field counts the number of athletes (count by their ID) who participated in the Olympics

![Number of Athletes](/images/ol_id_athletes.JPG)

- Participation and Medal Winners - this chart shows the amount of medal winners per medal type: Bronze, Gold, Silver or NA (no medal)

![Medal Winners](/images/ol_medal_winners.JPG)

- Country Name - this table contains the name of all countries

- Athletes Participation over the Years - this shart shows how many athletes participated in the Olympics over the years 

![Athletes Participation](/images/ol_year_athletes.JPG)

You can find the Qlik document here: [Sheet 1](https://tmxx59gmlb7gjvt.eu.qlikcloud.com/single/?appid=75be3d5d-1823-427b-a1c5-9aa3009ea961&sheet=177547dd-dc69-4156-9909-8aafab537d1e&theme=horizon&opt=ctxmenu,currsel)

![Dashboard1](/images/qlik6.JPG)

In this sheet we are able to filter by countries and also medal type to get a more detailed scenario.

In example, here we can see a detailed visualization with the data for USA, excluding non-medals:

![Dashboard2](/images/qlik7.JPG)

And here we can see the same, but for Brazil:

![Dashboard3](/images/qlik8.JPG)

### 4.2. Athlete Medal Details - Sheet 2 <a name="sheet2"></a>

In the second sheet we are able to analyze more detailed data, as it shows the full olympic participant and medal list. In this table, you can see more details, for example the names of the athletes, which events and it also highlights the Gold medal for better visualization.

You can find the Qlik document here: [Sheet 2](https://tmxx59gmlb7gjvt.eu.qlikcloud.com/single/?appid=75be3d5d-1823-427b-a1c5-9aa3009ea961&sheet=e8f97a27-2676-4fec-8324-cf4a57bcc860&theme=horizon&opt=ctxmenu,currsel)

![Table Athlete Medal Details](/images/qlik9.JPG)

### 4.3. GDP Details - Sheet 3 <a name="sheet3"></a>

Finally, in the third table, we can see and analyze more detailed data related to the GDP (Gross Domestic Product) details. 

This table shows the count of Gold medals per year and per country, which each country's GDP per million dollars.

- To sum the GDP and show only the amounts per million dollars I applied the following formula: Sum({<MEASURE={'MLN_USD'}>}Value)
- To count the amount of gold medals I applied the following formula: Count({<Medal={'Gold'}>}ID)

You can find the Qlik document here: [Sheet 3](https://tmxx59gmlb7gjvt.eu.qlikcloud.com/single/?appid=75be3d5d-1823-427b-a1c5-9aa3009ea961&sheet=23f17ebc-d0f7-4df2-bd46-46edb1ddd754&theme=horizon&opt=ctxmenu,currsel)

![Table GDP Details](/images/qlik10.JPG)

## 5. Data Exploration <a name="item5"></a>

The below video shows an example of a data exploration that we can perform in Qlik with this Data Model. In this example, the user filters the results by Spain and considers only the Bronze, Gold and Silver medals:

https://user-images.githubusercontent.com/58880353/211905833-6a889807-7a97-4800-9193-9731fd511e4a.mp4

With these filters, we can get to some conclusions:

- The total number of athletes that participated in the Olympics in Spain from its beginning until 2016 was 5.31k
- The total number of athletes who won a medal during this period was 489
- The majority of medal winners won SILVER medals, and the minority won GOLD medals
- The proportion of medals was: 27,8% BRONZE | 49,6% SILVER | 22,4% GOLD
- There are two peak years during this period when Spain won 70 medals: in 1992 and in 2008
- However, in 1992 Spain won 48 Gold medals, versus only 7 Gold medals in 2008

## 6. References <a name="item6"></a>

[Qlik Cloud](https://www.qlik.com/)

[Creating Your First Qlik Sense App by Michael Walker on Pluralsight](https://app.pluralsight.com/library/courses/qlik-sense-first-app)

