## Bike Data Project

##  Project description 

This project explores a real-world Bike Sales Dataset to perform end-to-end data analysis using PostgreSQL and Python.
The goal was to design a structured SQL database, execute insightful analytical queries, and visualize key business metrics to better understand sales performance, customer behavior, and store efficiency. Created as a training for SQL queries creation.  

The project demonstrates strong skills in SQL querying, database design, and data visualization — a practical example of how data analysts use relational databases to derive insights from large datasets. Data was obtained from the Kaggle platform : (https://www.kaggle.com/datasets/dillonmyrick/bike-store-sample-database)

## Tech Stack

Database: PostgreSQL

Querying: SQL (Postgresql)

Data Manipulation: Pandas

Visualization: Matplotlib & Seaborn

Environment: Jupyter Notebook

Dataset Source: Kaggle Bike Sales Dataset (https://www.kaggle.com/datasets/dillonmyrick/bike-store-sample-database)

## Key Analyses

The analysis focuses on answering the following business questions:

Which products and brands generate the highest sales revenue?

What is the monthly trend of orders throughout the year?

Which stores and states receive the most orders?

Who are the top customers by number of purchases and total spending?

How does the average order value vary by store or region?




### Author
Anna Furgała-Wojas

https://www.linkedin.com/in/anna-furga%C5%82a-wojas-5869a6a9/












```mermaid
erDiagram
    CUSTOMERS {
        INT customer_id PK
        VARCHAR first_name
        VARCHAR last_name
        VARCHAR street
        VARCHAR city
        VARCHAR state
        VARCHAR zip-code
        VARCHAR email
        VARCHAR phone
        INT store_id FK
    }

    ORDERS {
        INT order_id PK
        INT customer_id FK
        INT store_id FK
        INT order_status
        DATE order_date
        DATE required_date
        DATE shipped_date
        INT staff_id
    }

    ORDER_ITEMS {
        INT item_id PK
        INT order_id FK
        INT product_id FK
        INT quantity
        DECIMAL list_price
        DECIMAL discount
    }

    PRODUCTS {
        INT product_id PK
        VARCHAR product_name
        INT brand_id FK
        INT category_id FK
        INT model_year
        DECIMAL list_price
    }

    BRANDS {
        INT brand_id PK
        VARCHAR brand_name
    }

    CATEGORIES {
        INT category_id PK
        VARCHAR category_name
    }

    STORES {
        INT store_id PK
        VARCHAR store_name
        VARCHAR phone
        VARCHAR email
        VARCHAR street
        VARCHAR city
        VARCHAR state
        VARCHAR zip_code
    }

    CUSTOMERS }|..|| STORES : "from"
    ORDERS }|..|| CUSTOMERS : "placed by"
    ORDERS }|..|| STORES : "processed at"
    ORDER_ITEMS }|..|| ORDERS : "contains"
    ORDER_ITEMS }|..|| PRODUCTS : "includes"
    PRODUCTS }|..|| BRANDS : "made by"
    PRODUCTS }|..|| CATEGORIES : "classified as"
