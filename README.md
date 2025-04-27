# 📝 Assignment: Database Design and Normalization

## 🎯 **Learning Objectives**
* 🛠️ **Understand the principles of good database design** and **normalization**.
* 💡 **Apply normalization techniques** to improve database structure and efficiency.
* 🔍 **Learn First, Second, and Third Normal Forms** (1NF, 2NF, 3NF) to eliminate redundancy and optimize data storage.

---

## 📋 **What You'll Need**
* 💻 A computer with internet access.
* ✍️ A code editor (e.g., Visual Studio Code).
* 🖥️ MySQL Workbench or another SQL database environment.

---


## 📝 Submission Instructions  
📂 Write all your SQL queries in the **answers.sql** file.  
✍️ Answer each question concisely and make sure your queries are clear and correct.  
🗣️ Structure your responses clearly, and use comments if necessary to explain your approach.

--- 

## 📚 Assignment Questions

---

### Question 1 Achieving 1NF (First Normal Form) 🛠️
Task:
- You are given the following table **ProductDetail**:

| OrderID | CustomerName  | Products                        |
|---------|---------------|---------------------------------|
| 101     | John Doe      | Laptop, Mouse                   |
| 102     | Jane Smith    | Tablet, Keyboard, Mouse         |
| 103     | Emily Clark   | Phone                           |


- In the table above, the **Products column** contains multiple values, which violates **1NF**.
- **Write an SQL query** to transform this table into **1NF**, ensuring that each row represents a single product for an order

--- 

### Question 2 Achieving 2NF (Second Normal Form) 🧩

- You are given the following table **OrderDetails**, which is already in **1NF** but still contains partial dependencies:

| OrderID | CustomerName  | Product      | Quantity |
|---------|---------------|--------------|----------|
| 101     | John Doe      | Laptop       | 2        |
| 101     | John Doe      | Mouse        | 1        |
| 102     | Jane Smith    | Tablet       | 3        |
| 102     | Jane Smith    | Keyboard     | 1        |
| 102     | Jane Smith    | Mouse        | 2        |
| 103     | Emily Clark   | Phone        | 1        |

- In the table above, the **CustomerName** column depends on **OrderID** (a partial dependency), which violates **2NF**. 

- Write an SQL query to transform this table into **2NF** by removing partial dependencies. Ensure that each non-key column fully depends on the entire primary key.

---
Good luck 🚀

# Explanation for 1st Question
To transform the given table into **1NF**, we need to ensure that each row contains a single product for an order.

### Explanation:
1. **New Table Structure**: The new table `ProductDetail_1NF` will have three columns: `OrderID`, `CustomerName`, and `Product`.
2. **Normalization**: Each product is now represented in a separate row, ensuring compliance with **1NF**.
3. **Data Insertion**: The `Products` column values are split into individual rows for each product.

# Explanation for 2nd Question
To transform the table into **2NF**, we need to remove the partial dependency of `CustomerName` on `OrderID`. This can be achieved by splitting the table into two separate tables: one for `OrderID` and `CustomerName`, and another for `OrderID`, `Product`, and `Quantity`.

### Explanation:
1. **Orders Table**: Contains `OrderID` and `CustomerName`, removing the partial dependency of `CustomerName` on `OrderID`.
2. **OrderDetails_2NF Table**: Contains `OrderID`, `Product`, and `Quantity`, ensuring that all non-key columns fully depend on the composite primary key (`OrderID`, `Product`).
3. **Foreign Key**: Establishes a relationship between the `Orders` table and the `OrderDetails_2NF` table.