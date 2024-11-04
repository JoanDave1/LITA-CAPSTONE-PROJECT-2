# LITA-CAPSTONE-PROJECT-2

## Introduction
This is the second half of the final project for the Ladies in Tech Africa(LITA)- Data Analysis Track. We have a dataset containing Sales Data and Customer Data for TV subscription of which we are to conduct and visualize our analysis. For project 2, we will be working on the Customer data which contains 75,000+ records of sales transactions, including order ID, customer ID, product, region, order date, quantity ordered, unit price and total sales revenue.

---------
### 2.1 Objectives 

The purpose of this analysis is to:

1. Calculate the average subscription duration and identify the most popular subscription types.   
2. retrieve the total number of customers from each region. 
3. find the most popular subscription type by the number of customers. 
4. find customers who cancelled their subscription within 6 months. 
5. find customers with subscriptions longer than 12 months. 
6. calculate total revenue by subscription type. 
7. find the top 3 regions by subscription cancellations. 
8. find the total number of active and canceled subscriptions.

### 2.2 Methodology
#### Microsoft Excel: 
- *Data Source*: This dataset was provided by the facilitators of Ladies in Tech Africa(LITA) for Data Analysis track.
- *Data Cleaning*: I imported the dataset into Microsoft Excel. Afterwards, I proceeded to claen my dataset using the "Remove Duplicates" feature available on the "Data" tab to remove values occurring more than once. My dataset of about 75,000+ records was reduced to 33,788 records of sales. There were no other errors present in this dataset. 
- *Relevant Computations*: Using pivot tables, I was able to identify the popular subscriptions based on the number of customers and revenue generated as well as the cancellation of each subscription type based on total number of customers.

#### SQL: 

Using SQL queries, I was able to find:

- Total number of customers from each region
  
      SELECT Region, COUNT(CustomerID) AS  CustomerPerRegion,

      SUM(Revenue) AS Total_Revenue

      FROM CustomerData

      GROUP BY Region
  
- Most popular subscription type by the number of customers

      SELECT TOP 3 SubscriptionType,

      COUNT (CustomerID) AS popular_sub_type

      FROM CustomerData

      GROUP BY SubscriptionType

      ORDER BY popular_sub_type
  
- Customers who cancelled their subscription within 6 months

      SELECT COUNT (CustomerID) AS Cancelled_in_6_months

      FROM CustomerData

      WHERE SubscriptionEnd <= DATEADD (month, 6, SubscriptionStart)

      AND SubscriptionEnd IS NOT NULL
  
- Customers with subscription longer than 12 months

      SELECT COUNT(CustomerID) AS Long_Term_Customers

      FROM CustomerData

      WHERE DATEDIFF(MM, SubscriptionStart, SubscriptionEnd) > 12

      AND SubscriptionEnd IS NOT NULL
  
- Total revenue by subscription type

      SELECT SubscriptionType
  
      SUM(Revenue) AS Total_Revenue
  
      FROM CustomerData
  
      GROUP BY SubscriptionType
  
- Top 3 regions by subscription cancellation

      SELECT Region, COUNT (CustomerID) AS Cancellation_Count

      FROM CustomerData

      WHERE Canceled = '1'

      GROUP BY Region

      ORDER BY Cancellation_Count desc
  
- Total number of active and cancelled subscriptions

      SELECT
   
      SUM (CASE WHEN Canceled = '0' THEN 1 ELSE 0 END) AS Active_Subscriptions,
  
      SUM(CASE WHEN Canceled = '1' THEN 1 ELSE 0 END) AS Cancelled_Subscriptions
  
      FROM CustomerData
