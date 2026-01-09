# Mart SQL Project

## Overview
This project is a **sample SQL dataset and analysis for a retail Mart**.  
It demonstrates **intermediate to advanced SQL techniques**, including:

- **Joins**: INNER, LEFT, RIGHT, FULL (via UNION), CROSS, SELF  
- **Aggregations**: SUM, COUNT, COALESCE  
- **Subqueries**  
- **Window Functions**: RANK(), running totals  
- **Grouping and filtering**  

The project is designed for **learning, practice, and portfolio purposes**.

---

## Dataset Schema

### **Customers**
| Column       | Type        | Description                  |
|--------------|------------|-----------------------------|
| customer_id  | INT        | Primary key                 |
| full_name    | VARCHAR    | Customer full name          |
| gender       | VARCHAR    | Gender of the customer      |
| city         | VARCHAR    | Customer city               |
| signup_date  | DATE       | Account creation date       |

### **Products**
| Column       | Type      | Description                     |
|--------------|----------|--------------------------------|
| product_id   | INT      | Primary key                     |
| product_name | VARCHAR  | Name of the product             |
| category     | VARCHAR  | Product category                |
| cost_price   | DECIMAL  | Cost price                      |
| selling_price| DECIMAL  | Selling price                   |

### **Orders**
| Column       | Type   | Description                       |
|--------------|--------|----------------------------------|
| order_id     | INT    | Primary key                      |
| customer_id  | INT    | Foreign key to Customers         |
| order_date   | DATE   | Date of the order                |

### **Order Items**
| Column        | Type   | Description                       |
|---------------|--------|----------------------------------|
| order_item_id | INT    | Primary key                      |
| order_id      | INT    | Foreign key to Orders             |
| product_id    | INT    | Foreign key to Products           |
| quantity      | INT    | Quantity of product in the order  |

---

## Features

This project includes **sample data** for customers, products, orders, and order items.  

It demonstrates how to perform:

1. **Inner joins** to get actual sales transactions  
2. **Left joins** to identify inactive customers  
3. **Right joins** to find orders with missing customer data  
4. **Full outer joins** using UNION  
5. **Cross joins** for marketing simulations  
6. **Self joins** to find customers in the same city  
7. **Aggregations** like total spending per customer  
8. **Subqueries** to find customers above average spend  
9. **Window functions** for running totals and ranking  

---

## Example Queries

### **Total Revenue by Product**
```sql
SELECT p.product_name,
       SUM(oi.quantity * p.selling_price) AS revenue
FROM order_items oi
JOIN products p ON oi.product_id = p.product_id
GROUP BY p.product_name;
