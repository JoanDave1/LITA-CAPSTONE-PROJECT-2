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
- *Relevant Computations and Data Summary*: Using pivot tables, I was able to identify the popular subscriptions based on the number of customers and revenue generated as well as the cancellation of each subscription type based on total number of customers.
  
 The table below shows the count of customers that subscribed for each subscription type.
 
![image](https://github.com/user-attachments/assets/dc763878-fdd5-43a2-8c46-29b012ae93fc)

The pivot table below shows the amount of revenue generated from each region.

![image](https://github.com/user-attachments/assets/2f192059-3d29-4980-8f30-9700cc99bd2e)

This table below shows the cancellation count by customer ID for each subscription type.

![image](https://github.com/user-attachments/assets/042bcb18-13f5-4141-85c3-26dac3aec691)



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

#### Power BI: 
Power BI (BI meaning Business Intelligence) is a data visualization tool that allows users to connect to various data sources, create interactive visualizations and business intelligence dashboards. I made use of power bi to viaualize my data and extract meaningful insights.

The images below are visual representations of some of the relavant computations in this dataset. I inserted slicers for the years 2023 and 2024 and for different regions to show specific information.

------
The image below gives a proper visualication of relevant information from this data set. 
It reveals the following:

- Total number of customers from various regions, different subscription types and years 

![Screenshot (186)](https://github.com/user-attachments/assets/249308b7-a84e-413a-9350-918b0c693b3f)

***
This image below shows all the information for the subscription type "basic".

![Screenshot (183)](https://github.com/user-attachments/assets/d9e02439-876e-48b7-8a50-cd694bcee3f7)

***
This image below shows all the information for the subscription type "premium".

![Screenshot (188)](https://github.com/user-attachments/assets/0f64c75b-e713-4a9f-b7cd-a0dd0a973a83)

***
This image below shows all the information for the subscription type "standard". 

![Screenshot (185)](https://github.com/user-attachments/assets/9acfea37-d270-4d08-bd2d-f3c253a796af)

***
This image below shows all the information for the year "2023".

![Screenshot (180)](https://github.com/user-attachments/assets/2b8a2b2c-1b63-4616-aec2-254f4b84d1e8)

***
This image below shows all the information for the year "2024".

![Screenshot (179)](https://github.com/user-attachments/assets/a021f5bc-8f54-4a10-907c-b70d34ec4eb5)

------------
### 2.3 Results

OVERALL CUSTOMER SUBSCRIPTION PERFORMANCE 

SUBSCRIPTION TYPE

- Insights:
  
     1. The "Basic" subscription type is the most popular among customers indicating that it might be a cost effective option.
     2. "Basic" subscription type generates a signifiacnt portion of the total revenue indicating a large customer base.

- Recommendations:

     1. Analyze consumer behaviour and preferences to better understand the reasons they prefer the Basic subscription type.
     2. Develop targeted campaigns to upgrade "Basic" subscribers to higher level subscriptions highlighting the additional benefits and value.

CANCELLATION STATUS

- Insights:
     1. There were more active subscriptions than inactive ones indicating a relatively high retention rate.
     2. The East region is the only region with a 100% active subscription rate. Other regions have a mix of active and cancelled subscriptions.

- Recommendations:
     1. Analyze the east region's strategies, customer demographics and satisfactory levels to identify best practices that can be applied to other regions.
     2. Gather feedback from customers with cancelled subscriptions to understand reasons for cancellation and improve services.
     3. 
  
  
  













