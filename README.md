# Cost-of-Living-Project
## Project Summary

Dashboard analyzing the ability to save money in various American cities. 

I've always had an interest in Economics, and I have heard that there are natural mechanisms in the economy that adjust cost of living for the salaries in a given city. 
As a result, I wanted to look into the data myself, and see if there are cities where people are able to save more of their income relative to average costs of living.
I found the following dataset on kaggle, which presented a unique opportunity to dig into the data: https://www.kaggle.com/datasets/mvieira101/global-cost-of-living 

**Skills Used:**
* SQL to clean and format the dataset
* Tableau for Visualization

**Desired Insights:**
* Which cities have the lowest costs of living, relative to incomes?
* Which cities have the highest costs for housing?
* Which cities lead the way in other categories (car payment, utilities, food, etc)?

## Preparing the project data
The dataset:
<img width="1464" alt="Screenshot 2024-07-30 at 1 44 33 PM" src="https://github.com/user-attachments/assets/dd5bd269-759d-4565-bf0a-a4f9b448a083">

 **Changes Made:**
 After importing the CSV file from Kaggle using the Import Wizard, I made the following set of changes to modify the dataset:

 1. Renaming Indexes. The Indexes were clearly named to save from including long strings in column names, but for our purposes this was not sufficient.
    <img width="1346" alt="Screenshot 2024-07-30 at 1 51 43 PM" src="https://github.com/user-attachments/assets/10e195d6-0d33-4276-96e4-9563f625619c">
    I created the following script to rename the column indexes:
    <img width="991" alt="Screenshot 2024-07-30 at 1 54 57 PM" src="https://github.com/user-attachments/assets/9c61ebd8-5aaf-438e-9f15-60f970ac58cd">

2. Dropping Unneccessary Columns. Because there are so many columns there were a few which I didn't think were necessary like imported beer, cigarrettes, monthly pass, etc.
   I created the following script to drop the columns     which I hadn't included in the script renaming the indexes I wanted to keep:

   <img width="496" alt="Screenshot 2024-07-30 at 1 58 02 PM" src="https://github.com/user-attachments/assets/de28f0e8-83f5-4167-a2c7-874ab42d77e0">

3. The last change that I made in the dataset revolved around columns which measured price per square meter for real estate, inside and outside of the city center.
   I am from the US and am not too familiar with the metric system, so I decided to change these two columns to Square Feet.

   <img width="1005" alt="Screenshot 2024-07-30 at 2 06 50 PM" src="https://github.com/user-attachments/assets/5480b704-79e7-4dd4-832d-b70acf5c24ec">

   **Here's the script:**
   
   <img width="1032" alt="Screenshot 2024-07-30 at 2 09 51 PM" src="https://github.com/user-attachments/assets/3c407959-f0a6-4431-8a69-4d034f6e3fc3">

   **Here's what the new DB looks like**
   
   <img width="1340" alt="Screenshot 2024-07-30 at 2 11 05 PM" src="https://github.com/user-attachments/assets/05a6ebda-f926-460b-abc2-cae64d452034">

## Creating Views:

**In order to filter American cities that I was interested in, I created this initial view:**

<img width="627" alt="Screenshot 2024-07-30 at 2 40 15 PM" src="https://github.com/user-attachments/assets/d1ce09a5-1564-4138-bc4d-08febe687cdc">

**Here is what the view looks like:**


<img width="1249" alt="Screenshot 2024-07-30 at 2 43 26 PM" src="https://github.com/user-attachments/assets/22e23c2b-267d-464b-bdc1-d99e7c6c12a9">


After this, I began creating a number of other views which I might be able to use directly in Tableau to create different visuals... I created views such as one showing a city and cost to income ratio,
utilities costs, car payment, food costs, etc per city. I used the cost to income ratio directly in a bar chart and object map chart, and the amounts for different areas of cost of living to create a 
pie chart where I display each segment of the cost of living in each city.

**Here are some examples:**

<img width="1200" alt="Screenshot 2024-07-30 at 2 49 31 PM" src="https://github.com/user-attachments/assets/11cdb5a6-debc-4ad8-81e5-50021395a50a">

<img width="727" alt="Screenshot 2024-07-30 at 2 53 18 PM" src="https://github.com/user-attachments/assets/2f2da53f-8a39-461a-b767-49fc5ac3751e">

## Using Tableau:

After cleaning the data, and creating views, the next step was to connect the database to Tableau. I did this by downloading the Azure SQL drivers, and connecting live to the database directly. 

Here was my main thought process behind creating the dashboard:

* My goal was to create a one-sheet dashboard that tells the whole story
* I wanted to create a few simple insights that would answer my questions
* I wanted to create pie chart that allowed me to drill down into the specific costs that make up each city's cost of living

The first two visuals I created using the Cost to Income View that I had created in SQL. The first visual was a line chart, and which I added an AVG line to. 

<img width="1152" alt="Screenshot 2024-07-30 at 3 04 43 PM" src="https://github.com/user-attachments/assets/a95b56b2-c078-4157-9b82-23bd5a959eaa">


The second visual was a map chart, which I was a bit less familiar with. I needed to edit the latitude and longitude for 10 of the cities, because there are cities in other states with the same names. I then created a new view called CostToIncomeWithRank where I used a window function to add a rank column into the CostToIncomeView. This allowed me to edit the label, and put it directly in the bubble for each city. Then I was able to display the rankings of each cities cost to income ratio directly on a map of the US.


<img width="1217" alt="Screenshot 2024-07-30 at 3 07 22 PM" src="https://github.com/user-attachments/assets/de676703-9b68-476f-a87d-c86bf975eba9">





