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
