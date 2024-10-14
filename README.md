# Maven Market Report

### Steps Followed

#### Loading and Shaping the Data
Step 1: Loaded the maven_customer file from the main dataset. Named the table "Customers" and made sure that headers have been promoted. In transform data confirmed that data types are accurate. Changed the data type of both customer_acct_num and customer_postal_code columns to text as there will be no need to perform any mathematical calculations to account number or postal code.Created two new columns full_name and birth_year. full_name by concatenating the first_name and last_name column. birth_year by extracting the last four digits from birthdate column. Added a conditional column has_children if total_children greater the zero then "Y" else "N".

Step 2: Loaded the maven_product file from the main dataset. Named the table "Products" and made sure that headers have been promoted. In transform data confirmed that data types are accurate. Added a caculated column discount_price which is 90% of original retail price. Replaced all the null values in the recyclable and low_fat colum to zero.

Step 3: Loaded the maven_stores file from the main dataset. Named the table "Stores" and made sure that headers have been promoted.
Add a calculated column named full_address, by merging store_city, store_state, and store_country, separated by a comma and space.
Add a calculated column named area_code, by extracting the characters before the dash ("-") in the store_phone field.

Step 4: Loaded the maven_product file from the main dataset. Named the table "Regions" and made sure that headers have been promoted.

Step 5: Loaded the maven_calendar file from the main dataset. Named the table "Calendar" and made sure that headers have been promoted. Used the date tools in the query editor to add the following columns:Start of Week (starting Sunday), Name of Day, Start of Month, Name of Month, Quarter of Year,Year.

Step 6: Loaded the maven_return file from the main dataset. Named the table "Return_data" and made sure that headers have been promoted.

Step 7: Loaded the maven_transactions 1997 and maven_transactions 1998 file from the main dataset. Combined the two files into a single table. Named the table "Transaction_Data" and made sure that headers have been promoted.

#### Creating the Data Model 
Step 8: In the data model section assigned primary key to customer_id in Customer table. Similarly aasigned product_id, store_id, region_id and date to Products, Store, Region and Calendar tables respectively.

Step 9: Connected Transaction_Data to Customers, Products, and Stores using valid primary/foreign keys relationship.

Step 10: Connected Transaction_Data to Calendar using both date fields, with an inactive "stock_date" relationship.

Step 11: Connected Return_Data to Products, Calendar, and Stores using valid primary/foreign keys relationship.

Step 12: Connected Stores to Regions as a "snowflake" schema using region_id.

#### Adding DAX Measures 
Step 13: In the DATA view, added the following calculated columns:

In the Calendar table, column named "Weekend"-
Equals "Y" for Saturdays or Sundays (otherwise "N")

In the Calendar table, column named "End of Month"-
Returns the last date of the current month for each row

In the Customers table, column named "Current Age"-
Calculates current customer ages using the "birthdate" column and the TODAY() function

In the Customers table, column named "Priority"-
Equals "High" for customers who own homes and have Golden membership cards (otherwise "Standard")   

In the Customers table, column named "Short_Country"-
Returns the first three characters of the customer country, and converts to all uppercase 

In the Customers table, column named "House Number"-
Extracts all characters/numbers before the first space in the "customer_address" column 

In the Products table, column named "Price_Tier"-
Equals "High" if the retail price is >$3, "Mid" if the retail price is >$1, and "Low" otherwise

In the Stores table, column named "Years_Since_Remodel"-
Calculates the number of years between the current date (TODAY()) and the last remodel date

Step 14:  In the REPORT view, added the following measures-

Created a new measure named "Quantity Sold" to calculate the sum of the quantity sold.

Created a new measure named "Quantity Returned" to calculate the sum of the quantity returned.

Created new measures named "Total Transactions" and "Total Returns" to calculate the count of rows in the transactions and returns tables.

Created a new measure named "Return Rate" to calculate the ratio of quantity returned to quantity sold, formatted as a percentage.

Created a new measure named "Weekend Transactions" to calculate the transactions that occurred on weekends.

Created a new measure named "% Weekend Transactions" to calculate the percentage of transactions that occurred on weekends, formatted as a percentage.

Created new measures named "All Transactions" and "All Returns" to calculate the grand total transactions and returns regardless of filter context.

Created a new measure named "Total Revenue" to calculate revenue based on transaction quantity and product retail price, formatted as currency.

Created a new measure named "Total Cost" to calculate the total cost based on transaction quantity and product cost, formatted as currency.

Created a new measure named "Total Profit" to calculate profit as total revenue minus total cost, formatted as currency.

Created a new measure named "Profit Margin" to calculate profit margin by dividing total profit by total revenue, formatted as a percentage.

Created a new measure named "Unique Products" to calculate the number of unique product names in the Products table.

Created a new measure named "YTD Revenue" to calculate year-to-date total revenue, formatted as currency.

Created a new measure named "60-Day Revenue" to calculate a running total revenue over a 60-day period, formatted as currency.

Created new measures named "Last Month Transactions," "Last Month Revenue," "Last Month Profit," and "Last Month Returns."

Created a new measure named "Revenue Target" based on a 5% lift over the previous month's revenue, formatted as currency.

#### Building the Report 

Step 15: Renamed the tab "Topline Performance" and inserted the Maven Market logo

Step 16: Insert a Matrix visual to show Total Transactions, Total Profit, Profit Margin, and Return Rate by Product_Brand (on rows)

Step 17: Added a KPI Card to show Total Transactions, with Start of Month as the trend axis and Last Month Transactions as the target goal.
Create two more crads: one for Total Profit (vs. Last month Profit) and one for Total Returns (vs. Last Month Returns)

Step 18: Added a Map visual to show Total Transactions by store city. Added a slicer for store country.

Step 19: Added a Treemap visual to break down Total Transactions by store country.

Step 20: Added a Column Chart to show Total Revenue by week.

Step 21: Added a Gauge Chart to show Total Revenue against Revenue Target.

Step 22: Added a notes tab with buttons to shown additional insights. 
