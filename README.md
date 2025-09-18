# Fortune500-SQL-PROJECT
This is an analysis of the Fortune 500 list of companies.
# Fortune500 Analysis SQL Project

## Project Overview

**Project Title**: Fortune500 Analysis  
**Level**: Beginner  


This project is designed to demonstrate SQL skills and techniques typically used by data analysts to explore and analyze retail sales data. The project involves setting up a data preprocessing,data cleaning and performing exploratory data analysis (EDA) through SQL queries. 

## Objectives

1. **Set up a fortune500 database**: Create and populate a database with the provided data.
2. **Data Cleaning**: Identify and remove any records with missing or null values.
3. **Exploratory Data Analysis (EDA)**: Perform basic exploratory data analysis to understand the dataset.


## Project Structure

### 1. Database Setup

- **Database Creation**: The project starts by creating a database named `fortune500`.
- **Table Creation**: The table is imported from a csv file into sql server.


### 2. Data Preprocessing & Cleaning

- **Record Count**: Determine the total number of records in the dataset.
- **Companies Count**: Find out how many unique companies are in the dataset.
- **Industry Count**: Identify all unique industries in the dataset.
- **Null Value Check**: Check for any null values in the dataset and delete records with missing data.
- **Sector Count**:Find out how many unique sectors are in the dataset.
- **Countries Count**:Find out how many unique countries in the dataset.
- **Headquarters Count**:Find out how many unique Headquarters location in the dataset.
- **Duplicate Value Check**: Check for any Duplicate values in the dataset and delete records dataset.


```sql

select * 
from fortune500 
where id is null
or    	  company is null
or        rank is null
or	  	  revenues is null
or	      revenue_change is null
or	      profits is null
or	      assets is null
or	      profit_change is null 
or	      ceo is null
or        industry is null 
or	      sector is null
or	      previous_rank is null
or	      country is null
or	      hq_location is null
or	      website is null
or	      years_on_global_500_list is null
or	      employees is null
or        total_stockholder_equity is null


select id,count(*) 
from fortune500 
group by id 
having count(*)>1

select distinct company from fortune500--500

select distinct sector from fortune500--21

select distinct industry from fortune500--58

select distinct country from fortune500--34

select distinct hq_location from fortune500--235

```

### 3. Data Exploration & Findings

The following SQL queries were developed to explore the data:

1. **SQL query to find No of companies by country**:

```sql
select country,count(company) as no_of_companies 
from fortune500
group by country
order by count(company) desc
```

2. **SQL Query to find Revenues by Industry**:
```sql
select industry,sum(revenues) as revenues
from fortune500
group by industry
order by revenues desc
```

3. **SQL Query to find Assets by Industry**:
```sql
select industry,sum(assets) as assets
from fortune500
group by industry
order by assets desc

```

4. **SQL Query to find Revenues by sector**:
```sql
		select sector,sum(revenues) as revenues
from fortune500
group by sector
order by revenues desc
```

5. **SQL Query to find Assets by sector**:
```sql
select sector,
sum(assets) as assets
from fortune500
group by sector
order by assets desc
```
6. **SQL Query to find Revenues by Country**:
```sql
select country,
sum(revenues) as revenues
from fortune500
group by country
order by revenues desc

```
7. **SQL Query to find Assets by Country**:
```sql
select country,
sum(assets) as assets
from fortune500
group by country
order by assets desc
```
8. **SQL Query to find Revenues by Hq_location**:
```sql
select hq_location,
sum(revenues) as revenues
from fortune500
group by hq_location
order by revenues desc
```
9. **SQL Query to find Assets by Hq_location**:
```sql
select sector,
sum(assets) as assets
from fortune500
group by sector
order by assets desc
```

10. **SQL Query to find Companies by number of years on the list**
```sql
select  years_on_global_500_list,
count(*) as no_of_companies
from fortune500
group by years_on_global_500_list
order by count(*) desc
```
11. **SQL Query to find 23 Yr Honor list(Creme de la Creme)**
```sql
select country,
count(*) as no_of_companies
from fortune500 
where years_on_global_500_list=23
group by country 
order by count(*) desc
```
12. **SQL Query to find 23 Yr Honor list, Top 20,companies,revenues,assets and employees columns**
```sql
select top 20 company,revenues,assets,employees
from fortune500 
where years_on_global_500_list=23
```
13. **SQL Query to find 1 Yr Honor list**
```sql
select country,count(*) as no_of_companies
from fortune500 
where years_on_global_500_list=1
group by country
order by count(*) desc
```
14. **SQL Query to find 10 Yr Honor list**
```sql
select country,count(*) as no_of_companies
from fortune500 
where years_on_global_500_list=1
group by country
order by count(*) desc
```
15. **SQL Query to find Revenues by number of years on the list**
```sql
select years_on_global_500_list,
sum(revenues) as revenues
from fortune500 
group by years_on_global_500_list
order by revenues desc

```

16. **SQL Query to find Assets by number of years on the list**
```sql
select years_on_global_500_list,
sum(assets) as assets
from fortune500 
group by years_on_global_500_list
order by assets desc


```

16. **SQL Query to find Employees by number of years on the list**
```sql
select years_on_global_500_list,
sum(employees) as employees
from fortune500 
group by years_on_global_500_list
order by employees desc


```

17. **SQL Query to find Employees by number of years on the list**
```sql
select years_on_global_500_list,
sum(employees) as employees
from fortune500 
group by years_on_global_500_list
order by employees desc
```

18. **SQL Query to find Employees by Industry**
```sql
select industry,
sum(employees) as employees
from fortune500
group by industry
order by employees desc


```
19. **SQL Query to find Employees by Sector**
```sql
select sector,sum(employees) as employees
from fortune500
group by sector
order by employees desc


```
20. **SQL Query to find Employees by Country**
```sql
select country,
sum(employees) as employees
from fortune500
group by country
order by employees desc


```
21. **SQL Query to find Employees by hq_location**
```sql
select hq_location,
sum(employees) as employees
from fortune500
group by hq_location
order by employees desc


```
22. **SQL Query to Compare sectors between China and USA**
```sql
with china as(
select sector,count(*) as no_of_companies
from fortune500 
where country ='China'
group by sector
order by no_of_companies desc)

--USA by sector
with usa as(
select sector,count(*) as no_of_companies
from fortune500 
where country ='USA'
group by sector
order by no_of_companies desc)


with china as(
select sector,count(*) as no_of_companies
from fortune500 
where country ='China'
group by sector)
--order by no_of_companies desc)
, usa as(
select sector,count(*) as no_of_companies
from fortune500 
where country ='USA'
group by sector)
--order by no_of_companies desc)
select * from usa
left join china
on usa.sector=china.sector
order by usa.no_of_companies desc


```
23. **SQL Query to find Companies by Industry**
```sql
select top 5 industry,
count(company) as no_of_companies
from fortune500
group by industry
order by no_of_companies desc

```
24. **SQL Query to find Companies by 'Banks: Commercial and Savings'**
```sql
select country,
count(company) as no_of_companies
from fortune500
where industry ='Banks: Commercial and Savings'
group by country
order by no_of_companies desc


```
25. **SQL Query to find Companies by 'Motor Vehicles and Parts'**
```sql
select country,count(company) as no_of_companies
from fortune500
where industry ='Motor Vehicles and Parts'
group by country
order by no_of_companies desc


```
26. **SQL Query to find Companies by 'Petroleum Refining'**
```sql
select country,
count(company) as no_of_companies
from fortune500
where industry ='Petroleum Refining'
group by country
order by no_of_companies desc


```

27. **SQL Query to find Companies by Insurance: Life, Health (stock)**
```sql
select country,
count(company) as no_of_companies
from fortune500
where industry ='Insurance: Life, Health (stock)'
group by country
order by no_of_companies desc


```
28. **SQL Query to find Companies by Food and Drug Stores**
```sql
select country,
count(company) as no_of_companies
from fortune500
where industry ='Food and Drug Stores'
group by country
order by no_of_companies desc


```
29. **SQL Query to find Top 5 sector**
```sql
select top 5 sector,
count(company) as no_of_companies
from fortune500
group by sector
order by no_of_companies desc


```
30. **SQL Query to find Companies by Financial Sector**
```sql
select country,
count(company) as no_of_companies
from fortune500
where sector='Financials'
group by country
order by no_of_companies desc


```
31. **SQL Query to find Companies by Energy**
```sql
select country,
count(company) as no_of_companies
from fortune500
where sector='Energy'
group by country
order by no_of_companies desc


```
32. **SQL Query to find Companies by Technology**
```sql
select country,
count(company) as no_of_companies
from fortune500
where sector='Technology'
group by country
order by no_of_companies desc


```

33. **SQL Query to find Companies by Motor Vehicles & Parts sector**
```sql
select country,
count(company) as no_of_companies
from fortune500
where sector='Motor Vehicles & Parts'
group by country
order by no_of_companies desc


```
34. **SQL Query to find Companies by  Wholesalers sector**
```sql
select country,
count(company) as no_of_companies
from fortune500
where sector='Wholesalers'
group by country
order by no_of_companies desc


```

34. **SQL Query to find Companies by  Health Care sector**
```sql
select country,
count(company) as no_of_companies
from fortune500
where sector='Health Care'
group by country
order by no_of_companies desc


```

34. **SQL Query to find Companies by  Hq_location**
```sql
select hq_location,
count(company)  as no_of_companies
from fortune500 
group by hq_location
order by no_of_companies desc

```


## Findings

- **Analysis**:The fortune500 list is dominated by USA,Chinese and Japanese companies. Different sectors are also dominated much by companies from these countries eg Motor is dominated by Japanese,chinese and south korean companies.Much of the same can be seen in technology where America is the dominant leader however the Japanese and Chinese and Tawainese companies are in hot pursuit.China is the leader in Energy,whereas America is the leader in Health Care.Other industries such as Banking are dominated by USA AND Chinese companies.There are also some glaring differences eg Health Care,China only has two companies compared to 15 USA companies.Another striking difference is in the Food And Drug and Apparel where China has no representatives and America has a few.The other major difference is the number of Chinese companies which have been on the list for 23 years which is just two.The 23 Yr Honor list is dominated by companies from USA 57 and Japan 37 and has a total of 177 companies.These companies seem to be the top notch companies worldwide with a few exceptions.These companies are the dominant brands in our societies.The one year honor list is dominated by chinese companies(10) to Americas(4) this is a 2% change in a single year.This is a concern because China is dominating most industries and sectors already or they are in hot pursuit,this is good for the chinese people but not wise for the rest of the world as already witnessed during Covid pandemic.


## Conclusion

This project serves as an introduction to SQL for data analysts, covering database setup, data cleaning and exploratory data analysis. 

## Author - analysethatdata

This project is part of my portfolio, showcasing the SQL skills essential for data analyst roles.
