# Car_prices_analysis
Analysis of Vechicle data set.
**Vehicle Sales Data**

****About Data **:**
The "Vehicle Sales and Market Trends Dataset" provides a comprehensive collection of information pertaining to the sales transactions of various vehicles. This dataset encompasses details such as the year, make, model, trim, body type, transmission type, VIN (Vehicle Identification Number), state of registration, condition rating, odometer reading, exterior and interior colors, seller information, Manheim Market Report (MMR) values, selling prices, and sale dates. The dataset was obtained from the **Kaggle Datasets.**

### **Key Features:**
**Vehicle Details:** Includes specific information about each vehicle, such as its make, model, trim, and manufacturing year.

**Transaction Information:** Provides insights into the sales transactions, including selling prices and sale dates.

**Market Trends:** MMR values offer an estimate of the market value of each vehicle, allowing for analysis of market trends and fluctuations.

**Condition and Mileage:** Contains data on the condition of the vehicles as well as their odometer readings, enabling analysis of how these factors influence selling prices.

**### Potential Use Cases:**


**Market Analysis:** Researchers and analysts can utilize this dataset to study trends in the automotive market, including pricing fluctuations based on factors such as vehicle condition and mileage.

**Predictive Modeling:** Data scientists can employ this dataset to develop predictive models for estimating vehicle prices based on various attributes.

**Business Insights:** Automotive industry professionals, dealerships, and financial institutions can derive insights into consumer preferences, market demand, and pricing strategies.

**Format:** The dataset is typically presented in tabular format (e.g., CSV) with rows representing individual vehicle sales transactions and columns representing different attributes associated with each transaction.

**Data Integrity:** Efforts have been made to ensure the accuracy and reliability of the data; however, users are encouraged to perform their own validation and verification processes.

**Update Frequency:** The dataset may be periodically updated to include new sales transactions and market data, providing fresh insights into ongoing trends in the automotive industry.

-----------------------------------------------------------------------------------------------------------------
|Column         |Description                                                                          |Datatype |
|---------------|-------------------------------------------------------------------------------------|---------|
|year           |The manufacturing year of the vehicle.                                               |int      |
|make           |The brand or manufacturer of the vehicle.                                            |text     |
|model          |The specific model of the vehicle.                                                   |text     |
|trim           |Additional designation for the vehicle model.                                        |text     |
|body           |The body type of the vehicle (e.g., SUV, Sedan).                                     |text     |
|transmission   |The type of transmission in the vehicle (e.g., automatic).                           |text     |
|vin            |Vehicle Identification Number, a unique code for each vehicle.                       |text     |
|state          |The state where the vehicle is registered.                                           |text     |
|condition      |Condition of the vehicle, possibly rated on a scale.                                 |int      |
|odometer       |The mileage or distance traveled by the vehicle.                                     |int      |
|color          |Exterior color of the vehicle.                                                       |text     |
|interior       |Interior color of the vehicle.                                                       |text     |
|seller         |The entity selling the vehicle.                                                      |text     |
|mmr            |Manheim Market Report, possibly indicating the estimated market value of the vehicle.|int      |
|sellingprice   |The price at which the vehicle was sold.                                             |int      |
|saledate       |The date and time when the vehicle was sold.                                         |text     |
-----------------------------------------------------------------------------------------------------------------

**Analysis List:**

1.Product Analysis

Identify the most popular vehicle makes, models, trims, and body types.
Analyze trends in transmission types, odometer readings, and condition ratings to understand preferences and market demand.

2.Sales Analysis:

This analysis aims to answer the question of the selling price of the vehicles. The results of this can help use measure the effectiveness of each sales.

**Approach Used :**

**Data Wrangling :** This is the first step where inspection of data is done to make sure **Null** values and missing values are detected and there is no **Null** or missing values are dedected in the data.

       1. Build a Database
       2. Create table and insert data.
       3. Select columns with null values in them. There are no null values in our database as in creating the table, we set NOT NULL for each field, hence null values are filtered out.
   
   **Exploratory Data Analysis(EDA):** Exploratory data analysis is done to answer the listed questions and aims of this project.

   1. Conclusion:

**### Business questions to answer**

**Generic Question **

   1.How many unique brands does the data have?
   2.In which state is each vechicle registered?

**Product **

1. What are the top 10 most frequently occurring vehicle brands?
2. Show the brand with mmr greater than 10000;
3. Which is the top brand according to the condition rating?
4. Which color sold the most?
5. Selct top 5 most prefered interior color?
6. Which brand sells the most by the seller?
7. Which model has the highest condition rating?
8. Which vehicle has the greater travel distance?
9. How many body types in the dataset?
10. Which state has the highest number of vehicle registrations?
11. What is the average market value of each brands?

**Sales**

1.  Which year produced the most vehicles?
2.  Which brand has the highest selling price?
3.  Which brand has the lowest selling price?
4.  Which seller has the highest sales value?
5.  Show the Expensive, Medium and lowest price of cars (use Case function)
   
**Code:**
--Create database
Create Database Vechicle;

--Create table 
Create table Car_prices(
   Year int NOT NULL,
   Make Varchar(50) NOT NULL,
   Model Varchar(50) NOT NULL,
   Trim Varchar(50) NOT NULL,
   Body Varchar(50) NOT NULL,
   Transmission Varchar(50) NOT NULL,
   Vin int NOT NULL,
   State Varchar(50) NOT NULL,
   Condition int NOT NULL,
   Odometer int NOT NULL,
   Color Varchar(50),
   Interior Varchar(50),
   Seller Varchar(50),
   MMR int NOT NULL,
   Sellingprice int NOT NULL,
   Saledate Varchar(100) NOT NULL
);

**General Questions;**

----1.How many unique brands does the data have?
Ans : Select count(distinct make) from car_prices;

----2.In which state each vehicle registered?
Ans : Select state from car_prices;

**Product Analysis:**

----1.What are the top 10 most frequently occuring vehicle brand?
Ans : Select make, count(*) as frequency from car_prices
group by make
order by frequency desc
limit 10;

----2.Show the brand and MMR where MMR greater than 10000;
Ans : Select make, mmr from car_prices where mmr>10000;

----3.Which is the top brand according to the condition rating?
Ans : Select make, condition from car_prices
      order by condition desc
      limit 1;

----4.Which color is sold most of the times?
Ans : Select color, count(*) as count from car_prices
      group by color
      order by count desc
      limit 1;     

----5.Select top 5 most prefered interior color?
Ans : Select interior, count(*) as count from car_prices
      group by interior
      order by count desc
      limit 5; 

----6.Which brand is the most solded by seller?
Ans : Select make, seller, count (*) as count from car_prices
      group by make, seller
      order by count desc
      limit 1;

----7.Which model has the highest condtion rating?
Ans : Select model, max(condition) as highest_rating
      from car_prices
      group by model;

----8.Which vehicle has the greater travel distance?
Ans : Select make, max(odometer) as highest_travel_distance
      from car_prices
      group byb make
      limit 1;

----9.How many body types are in the dataset?
Ans : Select count(distinct body) from car_prices.

----10. Which state has the highest number of vehicle registration?
Ans : Select state, count(*) as registration_count
      from car_prices
      group by state
      order by registration_count desc
      limit 1;

----11.What is the avg market value of each brand?
Ans : Select avg(mmr) as average_market_value, make from car_prices
group by make;

**Sales Analysis:**

----1.Which year produced the most vehicles?
Ans : Select year, count(*) as vehicle_count from car_prices
group by year
order by vehicle_count desc
limit 1;

----2.Which brand has the highest selling price?
Ans : Select make, max(sellingprice) as highest_sellingprice 
      from car_prices
      group by make
      order by highest_sellingprice
      limit 1;

----3.Which brand has the lowest selling price?
Ans : Select make, min(sellingprice) as lowest_sellingprice 
      from car_prices
      group by make
      order by lowest_sellingprice
      limit 1;

----4.Which seller has the highest sales value?
Ans : Select seller, sum(sellingprice) as top_seller
from car_prices
group by seller
order by top_seller desc
limit 1;

----5.Show the expensive, medium, lowest brands(use case function)
Ans : Select distinct make, 
      case
      when sellingprice>100000 then 'Expensive_brand'
      when sellingprice between 50000 and 90000 then 'Medium_brand'
      else 'lowest brand'
      end as car_status
      from car_prices;

---------------------------------------------------------------------------
