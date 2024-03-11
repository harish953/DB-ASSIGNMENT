### Read the diagram carefully and answer the below questions.

![ecommerce table](https://raw.githubusercontent.com/iAmritMalviya/DB-Assignment/main/product-management-ecommerce-table-.webp)

**Questions**

### 1. Explain the relationship between the "Product" and "Product_Category" entities from the above diagram.

as we can see in product table , it has a column named as category_id which is a foreign key to the product_category table.
it is one to many relationship.This means that one product category can have multiple products associated with it, but each product belongs to only one category.

---

### 2. How could you ensure that each product in the "Product" table has a valid category assigned to it?

By defining a foreign key relationship between the "category_id" column in the "Product" table and the primary key column in the "Product_Category" table.
it ensures that every value in the "category_id" column of the "Product" table must exist as a primary key in the "product_category" table

---

### 3. Create schema in any Database script or any ORM (Object Relational Mapping).

CREATE TABLE product_category (
id INT PRIMARY KEY,
name VARCHAR(255) NOT NULL,
description TEXT,
created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
modified_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
deleted_at TIMESTAMP DEFAULT NULL
);

CREATE TABLE product (
id INT PRIMARY KEY,
name VARCHAR(255) NOT NULL,
description TEXT,
SKU VARCHAR(255) NOT NULL,
category_id INT,
inventory_id INT,
FOREIGN KEY (category_id) REFERENCES product_category(id),
FOREIGN KEY (inventory_id) REFERENCES product_inventory(id),
price DECIMAL(10, 2) NOT NULL, -- Lowercased column name
discount_id INT,
FOREIGN KEY (discount_id) REFERENCES discount(id),
created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
modified_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
deleted_at TIMESTAMP DEFAULT NULL
);

CREATE TABLE product_inventory (
id INT PRIMARY KEY,
quantity INT NOT NULL,
product_id INT,
FOREIGN KEY (product_id) REFERENCES product(id),
created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
modified_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
deleted_at TIMESTAMP DEFAULT NULL
);

CREATE TABLE discount (
id INT PRIMARY KEY,
name VARCHAR(255) NOT NULL,
description TEXT,
discount_percent DECIMAL(5, 2) NOT NULL,
active BOOLEAN DEFAULT 0,
created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
modified_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
deleted_at TIMESTAMP DEFAULT NULL
);

---

Steps:

1. create the new public repository called DB-Assignment and make a file called Answers.md
   <br> for help: [How to create the repository in gitgub](https://www.geeksforgeeks.org/creating-repository-in-github/)
2. Answers to the 1st and 2nd questions will go to the Answer.md
3. The answer to the 3rd question will go to the schema.<language_extenstion> eg(schema.js, schema.java, schema.py, schema.sql etc)
4. upload it to the GitHub.
5. insert the link in the form.
# DB-ASSIGNMENT
