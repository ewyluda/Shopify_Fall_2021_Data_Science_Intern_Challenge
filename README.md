# Shopify_Fall_2021_Data_Science_Intern_Challenge
# Shopify Fall 2021 Data Science Intern Challenge

## Please complete the following questions, and provide your thought process/work. You can attach your work in a text file, link, etc. on the application page. Please ensure answers are easily visible for reviewers!


## Question 1: Given some sample data, write a program to answer the following: click here to access the required data set

On Shopify, we have exactly 100 sneaker shops, and each of these shops sells only one model of shoe. We want to do some analysis of the average order value (AOV). When we look at orders data over a 30 day window, we naively calculate an AOV of $3145.13. Given that we know these shops are selling sneakers, a relatively affordable item, something seems wrong with our analysis. 

### Think about what could be going wrong with our calculation. Think about a better way to evaluate this data. 
  ***The calculation used is wrong because it is averaging the total order amount, some orders included more than one pair of shoes which is skewing the AOV value calculated.***
### What metric would you report for this dataset?
  ***I would report what I defined as average unit price, being the 'order_amount' divided by the 'total_items'.***
### What is its value?
  ***The AOV price is $387.74***


## Question 2: For this question you’ll need to use SQL. Follow this link to access the data set required for the challenge. Please use queries to answer the following questions. Paste your queries along with your final numerical answers below.

### How many orders were shipped by Speedy Express in total?
SELECT COUNT ( DISTINCT OrderID ) AS "Number of Orders" 
FROM orders
WHERE ShipperID=1;

Number of Orders
54

### What is the last name of the employee with the most orders?

SELECT EmployeeID, COUNT(DISTINCT OrderID)
FROM Orders
GROUP BY EmployeeID
ORDER BY COUNT(DISTINCT OrderID) desc;

Peacock is the last name of the employee with the most orders.


### What product was ordered the most by customers in Germany?
SELECT 
	Customers.CustomerID, 
    Customers.Country,
    OrderDetails.ProductID
FROM Customers
JOIN Orders
	ON Customers.CustomerID = Orders.CustomerID
JOIN OrderDetails
	ON OrderDetails.OrderID = Orders.OrderID
WHERE Country = 'Germany'
ORDER BY ProductID;

The product ordred the most by customers in Germany is productID 31, Gorgonzola Telino
