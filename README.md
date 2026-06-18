OrderDetails Table
Overview

The OrderDetails table stores information about the products included in each order. It acts as a bridge between the Orders and Products tables, allowing a single order to contain multiple products and a single product to appear in multiple orders.

Fields
Field	Description
OrderDetailID	Unique identifier for each order detail record.
OrderID	References the order in the Orders table.
ProductID	References the product in the Products table.
Quantity	Number of units of the product ordered.
SubTotal	Total amount for the product in the order (Price × Quantity).
Relationships
OrderID is a foreign key linked to the Orders table.
ProductID is a foreign key linked to the Products table.

This design helps maintain data integrity and supports a many-to-many relationship between orders and products.

Operations Performed
1. Insert Sample Records

Inserted sample order detail records to demonstrate how products are associated with orders.

INSERT INTO OrderDetails VALUES (...);
2. Retrieve Order Details for a Specific Order

Displays all products associated with a particular order.

SELECT * FROM OrderDetails
WHERE OrderID = 201;
3. Calculate Total Revenue

Uses the SUM() aggregate function to calculate the total revenue generated from all order details.

SELECT SUM(SubTotal) AS Total_Revenue
FROM OrderDetails;
4. Retrieve Top 3 Most Ordered Products

Groups products by ProductID, calculates the total quantity sold, sorts the results, and returns the top three products.

SELECT ProductID,
SUM(Quantity) AS Total_Ordered
FROM OrderDetails
GROUP BY ProductID
ORDER BY Total_Ordered DESC
LIMIT 3;
5. Count Product Sales

Counts the number of times a specific product appears in the order details.

SELECT COUNT(*)
FROM OrderDetails
WHERE ProductID = 2;
SQL Concepts Used
Primary Key: Uniquely identifies each order detail.
Foreign Key: Maintains relationships with Orders and Products tables.
SUM(): Calculates total revenue.
COUNT(): Counts occurrences of a product.
GROUP BY: Groups records by product.
ORDER BY: Sorts results in descending order.
LIMIT: Restricts the number of returned rows.
Purpose

The OrderDetails table provides detailed information about the items in each order, enabling revenue analysis, product sales tracking, and order management while maintaining a normalized database structure.
