# Real-Time Financial Performance Dashboard Documentation
## Project Overview
This project is designed to showcase my skills in data analysis, automation, and data visualization by building a real-time financial performance dashboard. The dashboard integrates data from Google Sheets, Power BI, and Excel to provide actionable insights into financial performance, sales, profits, and more, updated every minute.

## Key Features:
* Real-Time Data Updates: The dashboard fetches data from Google Sheets every minute, ensuring the dashboard always reflects the latest figures.
* Data Automation: Scripts were written in Google Apps Script to automatically populate and update the Google Sheet with new data.
* Interactive Visualizations: The dashboard was built using Power BI for interactive visualizations such as charts and graphs.
* Comprehensive Analysis: Includes detailed metrics like total sales, total costs, profit margins, and more

## 1. Step-by-Step Process
 * Data Preparation in Google Sheets: To simulate the data needed for the dashboard, a synthetic dataset was created in Google Sheets. This data includes:
 * Invoice ID: Generated in the format INV001, INV002, etc.
 * Date: Randomly selected dates between January 1, 2020, and January 31, 2025.
 * Product Names: Random products such as mobile, tablet, laptop, etc.
 * Quantity, Sale Price, Cost Price: Random values for the quantity of products sold, sale price, and cost price.
 * Total Sales: Calculated as Quantity * Sale Price.
 * Total Cost: Calculated as Quantity * Cost Price.
 * Total Profit: Calculated as Total Sales - Total Cost.
 * Profit Percentage: Calculated as (Total Profit / Total Sales) * 100.

## Automation of Data Updates:
 - Google Apps Script was used to automate data updates in Google Sheets, adding new data every minute using a trigger.
 - The "Last Updated" timestamp was automatically inserted in a separate column using new Date() to reflect when the data was last updated.
 ## 2. Power BI Dashboard Creation
  - The data was imported into Power BI for interactive visualizations:

## Data Import: 
Imported the Google Sheets data using a Web Connector in Power BI.
## Visualizations:
- Bar Charts: To show total sales, total profit by country.
- Pie Chart: To display the distribution of sales by product.
- Line Chart: To visualize the trend of sales over time.
- Map Visualization: To show which country has the highest sales for each product.

## The Power BI dashboard was designed to allow the user to:
- Filter data by country, product, or time period.
- Get insights into sales performance across regions.
  
## 3. Data Automation & Real-Time Updates
  The real-time data update functionality was achieved through Google Apps Script and Power BI: 
                              - Google Sheets automatically receives new data every minute through the Apps Script.
                              - Power BI updates by connecting directly to Google Sheets, ensuring that the dashboard is always displaying the most recent data.
## 4. Final Adjustments & Visual Enhancements
* Date Formatting: Dates were formatted to Month/Day/Year to ensure readability and consistency.
* Profit %: The profit percentage was formatted as a percentage to make it easier to interpret.
* Consistent Branding: Used consistent colors, fonts, and layout styles to make the dashboard visually appealing.
## 5. Tools & Technologies Used:
* Google Sheets: For real-time data storage and manipulation.
* Power BI: For creating interactive and insightful visualizations.
* Google Apps Script: For automating data insertion and updates.
* GitHub: For hosting and sharing static snapshots of data.
* LinkedIn: To share the completed project with professionals for feedback and advice.
## Conclusion:
This project allowed me to apply data analysis, automation, and data visualization techniques to a real-world scenario. The final dashboard provides insights into financial performance, such as sales, profits, and cost analysis, all updated in real time.
