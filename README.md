# Project: Database Creation and Business Analysis
A project focused on database creation and querying for business purposes using SQL.
# Project Overview
This is a project completed for my Database Management class, in which I was presented with the data of a hypothetical business and was tasked with building a database for them. The ultimate goal was to query the database in order to provide relevant information used to answer important questions posed by the business.

- ERD showing entities and relationships was created in Lucidchart.
- ERD was imported into SQL in order to create the framework of a database.
- Using SQL, data entries were then imported into the database.
- Using SQL, three simple form queries and two complex queries were written to address business questions.

## Relational ERD to Form Database
![](Images/Screen%20Shot%202023-07-27%20at%2012.04.37%20AM.png)

## SQL Queries
Normal
1. What are the names of the truck drivers who live in Collegetown, Tallahassee, FL?
- Select DriverFName, DriveLName from Driver where ZipCode = 32304
2. How many red products are stored in warehouses from Tallahassee, FL?
- Select Count(ProductColor) as Red Product Count, WarehouseID, WarehouseCity from Product join Warehouse on Product.ProductID = Warehouse.WarehouseID Where ProductColor = Red and   WarehouseCity = Tallahassee
3. What are the customer orders that were paid for with debit cards?
- Select * from CustomerOrder where CustomerPaymentType = debit card

Complex
1. List the phone numbers of suppliers that operate out of Tallahassee, FL and employ drivers with last names starting with “Z”
- Select Supplier.SupplierPhoneNumber, ZipCode.City, ZipCode.State, Driver.DriverLName from Supplier join ZipCode on Supplier.ZipCode = ZipCode.ZipCode join Driver on ZipCode.ZipCode = Driver.ZipCode Where ZipCode.City = Tallahassee and ZipCode.State = Florida and Driver.DriverLName like Z%
2. How much money in total is warehouse 1234 paying hourly to truck drivers from Seattle, Washington?
- Select Sum(DriverHourlyRate), Warehouse.WarehouseID, ZipCode.City, ZipCode.State from Driver join ZipCode on Driver.ZipCode = ZipCode.ZipCode join Warehouse on ZipCode.ZipCode = Warehouse.WarehouseID where ZipCode.City = Seattle and ZipCode.State = Washington and Warehouse.WarehosueID = 1234
