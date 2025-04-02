# BI Platform
## 1. Overview
### 1.1 Guidebook Introduction
This documentation is intended to introduce the basic instructions for using the retail people counting and footfall analytics BI (Business Intelligence) platform of Beijing Vion Technology Inc, including how to login to the system correctly on the PC, how to configure organizational relationships in the early stage of the system establishment, how to create user relationships within a retail conglomerate, how to view the data reports, and the specific meanings of each report.

## 2. Platform Specifications
### 2.1 Explanation of Nouns
Cloud Platform: refers to the people counting and footfall analytics BIplatform which is operated and maintained by our company and provides footfall analytics data query and export services.Atpresent,the cloud platform maintained by our company is divided into commercial platform and retail chain/franchise platform.
Group: refers to the highest resource leve lof aproject,generally corresponding to a commercial group or retail chain/franchise group.Its dataauthority is generally open to the group 
headquarters operations department.There can be multiple shops under it.
Shop: a single retail shop.

### 2.2 Precautions
The people counting and footfall analytics BI platform’s access requires authorization. Before using the system, first ensure that you have obtained a legitimate account and password.

## 3. System Functionalities
### 3.1 Data Dashboard
#### 3.1.1 Group Homepage
Group is the highest resource level of project data. On the Group Homepage, you can view the summary and ranking of all stores traffic in the country. This functionality is provided to the administrators of the group/conglomerate category of the multi-store project, and can be ignored by the users of a single store in general.
- Support switching time to view the group data in different time ranges;
- Switch the card indicators to view the trend graph of different indicators.
![](http://doc.vionyun.com:4999/server/index.php?s=/api/attachment/visitFile&sign=f8ccdc30059a80a505038341ab7da1cc)

#### 3.1.2 Store Homepage
The store homepage is a summary page of single store’s footfall analytics data. It mainly includes basic information such as core index data, customer flow trend, and customer/group percentage, etc..
- Support switching time to view store data in different time ranges;
- Switch the card indicators to view the trend graph of different indicators.
![](http://doc.vionyun.com:4999/server/index.php?s=/api/attachment/visitFile&sign=18f15e67e12fc8869ad46c3476bd76cb)

### 3.2 Data Reports
#### 3.2.1 Group Data
- Group data summarizes the footfall analytics data of the stores in each regional city under the group;
- It supports to view by regional grouping, and support to view the details of the footfall analytics data by store;
- Action Path: Login to the Platform - Report - Basic Analysis - Group Data and find the corresponding menu;
- Operation Methodology: select the grouping object of query and time, time granularity, click the Search button;
- Click the Download button, to extract the report data (excel format) or images.
![](http://doc.vionyun.com:4999/server/index.php?s=/api/attachment/visitFile&sign=bd2c416ab7a2911532e0951394830777)

#### 3.2.2 Store data
- Store data summarizes the passers-by traffics, entry traffics, number of unique customers, staff quantity, entry rate, long-dwelled customer traffics, long-dwelled rate, and other indicators of a single store;
- Action Path: Login to the Platform - Reports - Basic Analysis - Store Data and find the corresponding menu;
- Operation Methodology: select the store, time and time granularity of the Search and click the Search button;
- Support chart switching;
- Click the Download button, then extract the report data (excel format) or pictures.
- Select different time granularity to display different statistical dimensions. Hourly level displays the number of new customers per hour; minute level displays the number of new customers per ten minutes.
![](http://doc.vionyun.com:4999/server/index.php?s=/api/attachment/visitFile&sign=f2e346cb9e1746044cce96a094bb62a8)

- Traffic Funnel
 1. The Customer Traffic Funnel Analysis measures the visitor counts that have been converted into each stage of the consumption stages from passers-by to the paid conversion.
 1. Action Path: Login to the Platform - Reports - Basic Analysis - Conversion Funnel and find the corresponding menu;
 1. Operation Methodology: select the store, time and time granularity of the Search and click the Search button;
 1. Support funnel visualization;
![](http://doc.vionyun.com:4999/server/index.php?s=/api/attachment/visitFile&sign=b4eeffda2cd115b9ced6b368045c6f27)

 1. And able to view the detailed infos as in the KPI Comparsion, Counts Detials, Weekly Avg. Counts by Hourly/Monthly Data, Entry Rate and Data Report in the same column under Basic Analysis.
![](http://doc.vionyun.com:4999/server/index.php?s=/api/attachment/visitFile&sign=d7e5afe9f16458487081af05c7d87dec)
#### 3.2.3 Cross-store Comparison
- Cross-store Comparison is to compare the footfall analytics data of multiple stores, supporting such indicators as passers-by traffics, entry traffics, number of unique customers, staff quantity, entry rate, long-dwelled customer traffics, long-dwelled rate, and other indicators of multiple stores;
- Action Path: Login to the Platform - Reports - Contrast Analysis - Comparison Analysis, and find the corresponding menu;
- Operation method: select the store, time and time granularity of the Search and click the Search button;
- Support chart switching;
- Click the Download button, then extract the report data excel format;
- Select different time granularity to display different statistical dimensions. Hourly level displays the number of new customers per hour; minute level displays the number of new customers per ten minutes.
![](http://doc.vionyun.com:4999/server/index.php?s=/api/attachment/visitFile&sign=feebd56bb5b0a1aa277080b1ce9ef7c1)

#### 3.2.4 Store Ranking
- Store Ranking is a ranking of the footfall anlytics data of multiple stores, supporting such indicators as passers-by traffics, entry traffics, number of unique customers, staff quantity, entry rate, long-dwelled customer traffics, long-dwelled rate, and other indicators of multiple stores;
- Action Path: Login to the Platform - Reports - Basic Analysis - Store Ranking and find the corresponding menu;
- Operation Methodology: select the Group and time of the Search and click the Search button;
- Click the Filtering button next to the indicators to support the ranking of stores according to different indicators in positive and reverse order;
- Click Details button to jump to the home page of store data.
![](http://doc.vionyun.com:4999/server/index.php?s=/api/attachment/visitFile&sign=29cf3ba71f0163d555f9a848d25c9755)

#### 3.2.5 Dwell Time Distribution and Statistics
- The dwell time period that traffic distribution shows the average traffics heat of each hour from Monday to Sunday;
- Action Path: Login to the Platform - Reports - Basic Analysis - Dwell Time, and find the corresponding menu;
- Operation Methodology: select the object of query, time, and click the Search button;
- Click the Download button, then extract the report data (excel format) or pictures;
- The darker the color, the higher the passenger flow during the time.
![](http://doc.vionyun.com:4999/server/index.php?s=/api/attachment/visitFile&sign=622d99f9b0302518942e2ba2f6d98b70)

#### 3.2.7 Store Index Analysis
- Display the percentage of customers in the store at different dwell times according to the store dwell time period settings;
- Indicator growth analysis page displays year-on-year and retail chain/franchise comparison data of indicators in different time ranges, and supports data export;
- Action Path: Login to the Platform - Reports - Contrast Analysis - Store Index Analysis, and find the corresponding menu;
- Operation Methodology: select the query object, indicator and time, and click the Search button;
- Support customized filtering according to time;
- Support data export through Download button.
![](http://doc.vionyun.com:4999/server/index.php?s=/api/attachment/visitFile&sign=0704e576a3ccaffee828e0f4a04050e5)

#### 3.2.8 In&out Traffic Comparison
- In&out Traffic Comparison page displays the data comparison of incoming and outgoing customer flow of the store in each hour of the day;
- Action Path: Login to the Platform - Reports - Contrast Analysis - In&out Traffic Comparison, and find the corresponding menu;
- Operation Methodology: select the store, index and time of query, and click the Search button;
- Support multi-selection of stores;
- Support chart switching;
- Click the Download button, then extract the report data (excel format).
![](http://doc.vionyun.com:4999/server/index.php?s=/api/attachment/visitFile&sign=794a9c1b762f641bb23ef5c2c0527114)

#### 3.2.9 Weekday and Weekend Comparison
- Store traffic fluctuates regularly between weekdays and weekends. In order to understand the time pattern of potential customers and the active situation on weekends, the weekly growth of weekend traffic will be counted.
- Support any weekly query through Filtering and Search;
- Support icon and excel export through Download.
![](http://doc.vionyun.com:4999/server/index.php?s=/api/attachment/visitFile&sign=2689d249f8640156edd31c96ca23cc98)

#### 3.2.10 Holiday and Festive Analysis
- Holiday and Festive Analysis page shows the average customer flow and growth rate during the holiday/festival/activity period and supports data export;
- Activity holidays are set in the background management - holiday/festive/activity management, supporting the import of traditional holidays and customized activity cycle;
- Action Path: Login to the Platform - Reports - Holiday Comparison - Holiday Comparison or Festive Analysis, and find the corresponding menu;
- Operation Methodology: select the query store, time (year), click the Search button;
- Activity holidays are set in the background management - activity management;
- Click the Download button, then extract the report data (excel format) or pictures.
![](http://doc.vionyun.com:4999/server/index.php?s=/api/attachment/visitFile&sign=8d206d968a4d7136993d23f0fdfa3db8)

#### 3.2.11 Demographics (ReID) in Age/Gender Segmentations
- Through the non-biometric ReID analysis of the store customers, it derives the age and gender distribution of the store's customer base, as well as information related to the store staff.
- Supports multi-store, daily, weekly, monthly, yearly, and customized date data view.
- Support switching between summary data and day-level data (weekly, monthly, yearly, customized date).
- Supports table and image switching and exporting through Filtering, Search and Download.
- Support to view multi-day data.
![](http://doc.vionyun.com:4999/server/index.php?s=/api/attachment/visitFile&sign=c368e2105a8c650a1ac8d0fd62b883d6)

#### 3.2.12 Store Heatmap (ReID)
- Through the wide application of our non-biometric ReID tehcnology, combined with the area covered by the extisting/AIoT camera irradiation can be derived the number of people in each area at different times. By way of heat distribution presents the length of time customers dwelled in different locations of the store.
- Support switching between different stores and dates to view the data.
- Support to present heat effect on store plan and 3D map
![](http://doc.vionyun.com:4999/server/index.php?s=/api/attachment/visitFile&sign=4e9aca30ae39359a9dd9fc3f964f6dea)

#### 3.2.13 Zone Analysis (ReID)
- Through the wide application of our non-biometric ReID tehcnology, combined with the area covered by the extisting/AIoT camera irradiation can be derived the number of people in each area at different times.
- According to the division of the store partition, statistics on the number of customers in each area, the number of people dwelled, the dwell time, and other information;
- Support switching between different stores and dates to view the data.
- Support to present heat effect on store plan and 3D map.
![](http://doc.vionyun.com:4999/server/index.php?s=/api/attachment/visitFile&sign=fd62de7dc81701e1040e426c6a6a0d1f)
