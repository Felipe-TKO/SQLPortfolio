Hello and welcome!
This Project is to show the average median list price of homes listed on zillow for the year 2018-2022

The following will be covered:
* The business task
* Description of all data sources used
* Documentation of Data Cleaning and manipulation
* Visuals
* Top recommendations based on analysis

# Topic 1: The Business Task #

How has the past 5 years impacted the average home list price in the U.S.?
Which cities saw a negative percent change in avg list price?
Which cities saw over 100% increase in avg list price?

# Topic 2: Description of all data sources used #

All data was obtained directly from Zillow Research:
link: https://www.zillow.com/research/data/ 
The data came from the Median List and Sale price section
Obtained November 2022 for the years Jan 2018 - Oct 2022

The files were downloaded as CSV files, saved as xlsx files and stored/uplaoded in Google Sheets and used in Tablaue and Googles BigQuery SQL Sandbox

https://docs.google.com/spreadsheets/d/1ei5VYA4JCTH9KtYCprJMhGZ-LMtkX_sx/edit?usp=sharing&ouid=108080808687006532923&rtpof=true&sd=true

# Topic 3: Documentation of Data Cleaning and Manipulation #
All Documentation and version history is readily available in Google Sheets
Example of functions/formulas used:
=Split() to split the RegionName column into City and State
=Average() to obtain the average of each city by year

Nulls were kept to display no/empty data in Tablaue
The average columns were added manually and calculated

SQL Querys used:

`SELECT state_Name, city_name, the_Avg_2018, the_Avg_2022, ((the_Avg_2022 - the_Avg_2018)/the_Avg_2018) * 100 as percentChange
FROM us-median-sale-and-list-price.median_list_price.onlyAvgforAll

/* Return Percent change in Avg median list price from 2018 to 2022 to show either in increase or decrease in list price */ `

Table was saved from this query in order to isolate negative and postive percent changes. This table was then queried:

`SELECT *
FROM us-median-sale-and-list-price.median_list_price.percentChangefrom2018-2022
Where percentChange > 100
Order by percentChange desc `

and

`SELECT *
FROM us-median-sale-and-list-price.median_list_price.percentChangefrom2018-2022
Where percentChange < 0
Order by percentChange asc `

# Topic 4: Visuals #
Visuals can be seen in the Tableau Public here:
https://public.tableau.com/app/profile/khristian.rodriguez/viz/ZillowMedianListSalePrice-MetroU_S_/Story1#1

# Topic 5: Top Recommendations based on analysis #
Investigate why there are cities that saw a negative percent change in avg median Home list price.
Texas has a 263% increase in avg median list price from 2018-2022. Best place for investors to sell homes.



