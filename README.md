# Olympics Data Model in Qlik Cloud

## Table of contents
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

Data Model built in Qlik App during the course "Creating Your First Qlik Sense App" in Pluralsight. I used the Qlik Cloud to elaborate this dataset.

## 2. Dataset and Importing the Database <a name="item2"></a>

This model uses three databases:

1. GDP data (DP_LIVE_13102018040554424): this table contains the GDP data with the following columns:
"LOCATION","INDICATOR","SUBJECT","MEASURE","FREQUENCY","TIME","Value","Flag Codes"

2. Medals (athlete_events): this table contains the athlete data, with the following columns:
"ID","Name","Sex","Age","Height","Weight","Team","NOC","Games","Year","Season","City","Sport","Event","Medal"
*(Note: this table could not be included in this repository due to its size)*

3. MapCountryName (noc_regions): this table contains the countries and their names

*Please note that you are required to have a Qlik Sense account in order to view the dynamic sheets mentioned in the links below.*

## 3. Data Preparation <a name="item3"></a>

These tables were linked to each other using the fields "YEAR" and "LOCATION" as shown in the below image:

![Alt text](/images/qlik2.JPG)

To prepare the database and be able to perform these links, I had to:

- Load the table MapCountryName as a Mapping Load table:

![Alt text](/images/qlik3.JPG)

- Edit the name of the field NOC to LOCATION in the Medals table and link MapCountryName table as a Mapping Table:

![Alt text](/images/qlik4.JPG)

- Edit the name of the field Time to YEAR in the GDP data table:

![Alt text](/images/qlik5.JPG)

## 4. Data Visualization <a name="item4"></a>

After that, I could create the Olympics Data Model to be able to analyze the data contained in these three tables.

Our model is based in the following structure:

![Alt text](/images/qlik1.JPG)

### 4.1. Olympics Data Model - Sheet 1 <a name="sheet1"></a>

We can see the data in a High-Level Summary in the first sheet, that is a KPI with the following charts:

- Number of Athletes - this field count the number of athletes who participated in the Olympics
- Participation and Medal Winners - this chart shows the amount of medal winners per medal type: Bronze, Gold, Silver or NA (no medal)
- Country Name - this table contains the name of all countries
- Athletes Participation over the Years - this shart shows how many athletes participated in the Olympics over the years

You can find the Qlik document here: [Sheet 1](https://tmxx59gmlb7gjvt.eu.qlikcloud.com/single/?appid=75be3d5d-1823-427b-a1c5-9aa3009ea961&sheet=177547dd-dc69-4156-9909-8aafab537d1e&theme=horizon&opt=ctxmenu,currsel)

![Alt text](/images/qlik6.JPG)

In this sheet we are able to filter by countries and also medal type to get a more detailed scenario.

In example, here we can see a detailed visualization with the data for USA, excluding non-medals:

![Alt text](/images/qlik7.JPG)

And here we can see the same, but for Brazil:

![Alt text](/images/qlik8.JPG)

### 4.2. Athlete Medal Details - Sheet 2 <a name="sheet2"></a>

In the second sheet we are able to analyze more detailed data, as it shows the full olympic participant and medal list. In this table, you can see more details, for example the names of the athletes, which events and it also highlights the Gold medal for better visualization.

You can find the Qlik document here: [Sheet 2](https://tmxx59gmlb7gjvt.eu.qlikcloud.com/single/?appid=75be3d5d-1823-427b-a1c5-9aa3009ea961&sheet=e8f97a27-2676-4fec-8324-cf4a57bcc860&theme=horizon&opt=ctxmenu,currsel)

![Alt text](/images/qlik9.JPG)

### 4.3. GDP Details - Sheet 3 <a name="sheet3"></a>

Finally, in the third table, we can see and analyze more detailed data related to the GDP (Gross Domestic Product) details. 

This table shows the count of Gold medals per year and per country, which each country's GDP per million dollars.

- To sum the GDP and show only the amounts per million dollars I applied the following formula: Sum({<MEASURE={'MLN_USD'}>}Value)
- To count the amount of gold medals I applied the following formula: Count({<Medal={'Gold'}>}ID)

You can find the Qlik document here: [Sheet 3](https://tmxx59gmlb7gjvt.eu.qlikcloud.com/single/?appid=75be3d5d-1823-427b-a1c5-9aa3009ea961&sheet=23f17ebc-d0f7-4df2-bd46-46edb1ddd754&theme=horizon&opt=ctxmenu,currsel)

![Alt text](/images/qlik10.JPG)

## 5. Data Exploration <a name="item5"></a>

The below video shows an example of a data exploration that we can perform in Qlik with this Data Model. In this example, the user filters the results by Spain and considers only the Bronze, Gold and Silver medals:

https://user-images.githubusercontent.com/58880353/211905833-6a889807-7a97-4800-9193-9731fd511e4a.mp4



## 6. References <a name="item6"></a>

