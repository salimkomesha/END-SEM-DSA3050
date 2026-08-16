# END-SEM-DSA3050
DSA-3050-Endsem
AMAZON SALE REPORT

# SECTION A
# 1.1. Source of the Dataset
The dataset that has been used in the current project is the Amazon Sales Report Dataset that has been sourced from Kaggle. The dataset is part of the E-Commerce Sales Dataset on Kaggle and contains a file named Amazon Sales Report.csv. Source: Kaggle – E-Commerce Sales Dataset The Amazon Sales Report dataset contains around 128,976 transactions and contains information about orders, products, quantities, sales amount, fulfillment, shipping, location of customers and status of orders. The dataset has been prepared for use in Power BI and some of the key steps involved were correction of data types, preparation of date column, handling missing data and dimensional modeling of data.

# 1.2 why I Selected This Dataset
Large number of records Multiple data types Supports time analysis Supports geographical analysis Supports product analysis Supports operational analysis

# 1.3 Main Variables Available
Order Id,Date,Status,Fulfilment,Sales Channel,Ship Service,Category,SKU,Size,Quantity,Amount,Currency,Shipping City,Shipping State,Shipping Country,Postal Code,B2B ,Courier Status

# SECTION B
# 1.REMOVED COLUMNS
Some of the columns present in the data were unnecessary for the analysis that was to be done. Therefore, to minimize the use of unwanted columns, it was necessary to remove those columns, which could have been done through the use of the Removed Columns transformation.

# 2.UPPERCASED TEXT
For some text values, it became necessary to have the text standardized before any groupings and filtering’s could take place based on these categorical values. The Uppercased Text transformation was performed B2B, resulting in the conversion of the values into all uppercase form.

# 3.REMOVED DUPLICATES
Duplicates were detected within the dataset. Removal of Duplicates transformation was performed to remove the duplicates in order to ensure that they do not affect operations like counting orders and analysing sales. Consequently, the dataset comprised unique records for analysis.

# 4.FILTERED ROWS
Some of these rows did not have any relevance with respect to the planned analysis. Therefore, the use of the Filtered Rows transformation became necessary to keep only those rows which are needed in light of the specified criteria.

# 5.RENAMED COLUMNS
There were some names that did not make sense in some columns, while others did not have consistency in their presentation. The "Renamed Columns" transformation technique was applied in order to name those fields in an easy and meaningful manner.

# 6.REMOVED TOP ROWS
The dataset had the row names and are unnecessary. The Removed Top Rows transformation was applied in order to remove the unnecessary rows so that the dataset started with the right data.

# 7.CHANGED TYPE USING LOCALE
There were also certain columns like date, where the default setting of regions in Power BI did not help in interpreting the values correctly. Thus, I employed the Changed Type with Locale option that helped me select the right data type along with the regional setting of the same.

# 8.REMOVED BLANK ROWS
There were completely empty rows in the dataset, which did not contribute any value to it. The transformation called ‘Removed Blank Rows’ was used to eliminate those empty rows from the dataset. It helped improve the quality of the dataset overall.

# SECTION C
# Why you selected your fact table.
Amazonsales has been chosen to be the fact table because it holds the transaction level sales and orders that are being analyzed. The table holds measurable data like the amount and quantity, order status, product, date, and location data. It serves as the center of the model because it is used in calculating the DAX measures like Total Revenue, Total Orders, Shipped Orders, and Cancelled Orders.

# Why each dimension was created.
DimDate was developed to aid the process of time-based analysis, including sales on annual, monthly, and daily basis. DimProduct was designed to facilitate categorization of the product's properties, like category, SKU, style, and size. This will enable performance of sales analysis based on certain product parameters. DimLocation was developed to structure geographical data, like shipping city, state, country, and postal code. It allows performing comparison of the sales based on geography. DimCustomer was developed to help separating customer-related data from transactional one.

# The relationships used.
DimDate ────────┐ DimProduct ─────┤ DimCustomer ────┤──→ Amazonsales DimLocation ────┘

# Cardinality decisions.
One-to-many (1:) cardinality was used between the dimension tables and the Amazonsales fact table. DimProduct (1) → Amazonsales ()

# Filter direction decisions.
DimProduct → Amazonsales DimDate → Amazonsales DimLocation → Amazonsales DimCustomer → Amazonsales

# Any modelling challenges encountered.
Date format: The date field in the dataset needed to be cleaned and converted to an appropriate date format to facilitate meaningful time analysis. Missing values: There were some missing values in certain fields, especially in the Amount and location fields.

# SECTION D
# 1.Total Revenue
What it measures: Calculates the total sales revenue by summing up all amounts in the Amount column. Why it’s important: It provides insight into the financial performance of the business, making comparison easy by product, location, or over different time periods. DAX formulas involved: SUM(). Context filters: The result will vary depending on which filters the user applies such as Date, Category, SKU, Location, Fulfilment etc. Where it is applied: On the Executive Overview page as one of the main KPIs.

# 2. Total Orders
What it computes: Calculates the total number of orders through the Order Id column. Why it is important: Provides the total number of orders received and prevents any order from being counted more than once. Key DAX functions: DISTINCTCOUNT() Context filters: The total number of orders depends on selected dates, product types, categories, location and order status. Where it is applied: Applied on Executive Overview and Operational Analysis pages.2. Total Orders What it computes: Calculates the total number of orders through the Order Id column. Why it is important: Provides the total number of orders received and prevents any order from being counted more than once. Key DAX functions: DISTINCTCOUNT() Context filters: The total number of orders depends on selected dates, product types, categories, location and order status. Where it is applied: Applied on Executive Overview and Operational Analysis pages.

# 3. Shipped Orders
What it calculates: The measure calculates the orders which have the status 'Shipped'. Why it is useful: It indicates how many orders have been successfully shipped. Main DAX functions used: CALCULATE() and COUNTROWS(). Filter Context: The measure reacts to filters like date, category, product, and location but counts shipped orders. Where it is used: Used on Executive Overview and Operational Analysis page.

# 4. Cancelled Orders
What it computes: Computes the number of orders whose order state is "Cancelled." Why it is useful: Useful for analyzing the quantity of failed orders and possible issues that might arise. Key DAX functions employed: CALCULATE() and COUNTROWS() Filter context: Value varies when filtering based on category, date, product, fulfillment, or location, but the number of canceled orders is always counted. Where it is used: Used in Executive Overview and Operations Analytics tabs.

# 5. Average Order Value
What it computes: Computes the average revenue earned from every order using the formula for division of total revenue by total orders. Why it is useful: It gives the value of the average order which enables you to know whether changes in revenues have been due to order volumes or order value. DAX functions that can be used: DIVIDE(), [Total Revenue], [Total Orders]. Filter context: The filter context affects the revenue and orders, and as such affects the Average Order Value. Where it is applied: It is applied on the Executive Overview page.

# 6. Cancellation Rate
What it does: The percentage of orders which have been cancelled compared to the total orders. How it is useful: It can help in identifying the areas which have a high cancellation rate and any issues in sales or order fulfillment. DAX Functions involved: DIVIDE() and [Cancelled Orders], [Total Orders]. Context: The cancellation rate varies based on the dates, categories, product type, location and fulfillment method chosen by the user. Where it is applied: This measure is applied to the Operational Analysis page.
