# Bookstore-SQL-Project
# Bookstore SQL Analysis Project

## 📖 Overview
This project demonstrates **relational database analysis using SQL** with three interconnected datasets:
- **Book Dataset** → Book details (Book ID, Title, Author, Genre, Price, Stock)
- **Customer Dataset** → Customer information (Customer ID, Name, Age, Location, Membership)
- **Order Dataset** → Transaction records (Order ID, Customer ID, Book ID, Quantity, Order Date, Payment Mode)

The project replicates a **bookstore management system**, focusing on customer behavior, sales performance, and revenue insights.

---

## 🗂️ Dataset Description
### 1. Book Dataset
- **Fields:** Book_ID, Title, Author, Genre, Price, Stock  
- **Size:** ~500 records  

### 2. Customer Dataset
- **Fields:** Customer_ID, Name, Age, Gender, Location, Membership  
- **Size:** ~300 records  

### 3. Order Dataset
- **Fields:** Order_ID, Customer_ID, Book_ID, Quantity, Order_Date, Payment_Mode  
- **Size:** ~1,000 records  

---

## 🔍 SQL Queries Performed
- **Customer Analytics:** Most frequent buyers, age group trends, membership-wise sales  
- **Sales Insights:** Best-selling books, revenue by genre, author performance  
- **Order Analysis:** Monthly/seasonal trends, average order value, payment mode distribution  
- **Inventory Management:** Fast-moving vs. slow-moving books, stock requirements  

---

## 🛠️ Tools & Technologies
- **SQL** (MySQL / PostgreSQL / SQLite) → Database creation, joins, aggregations, analytical queries  

---

## 📊 Sample SQL Queries
```sql
-- 1. Top 5 best-selling books
SELECT b.Title, SUM(o.Quantity) AS Total_Sold
FROM Orders o
JOIN Book b ON o.Book_ID = b.Book_ID
GROUP BY b.Title
ORDER BY Total_Sold DESC
LIMIT 5;

-- 2. Revenue by genre
SELECT b.Genre, SUM(o.Quantity * b.Price) AS Revenue
FROM Orders o
JOIN Book b ON o.Book_ID = b.Book_ID
GROUP BY b.Genre
ORDER BY Revenue DESC;

-- 3. Top customers by total spend
SELECT c.Name, SUM(o.Quantity * b.Price) AS Total_Spend
FROM Orders o
JOIN Customer c ON o.Customer_ID = c.Customer_ID
JOIN Book b ON o.Book_ID = b.Book_ID
GROUP BY c.Name
ORDER BY Total_Spend DESC
LIMIT 10;
