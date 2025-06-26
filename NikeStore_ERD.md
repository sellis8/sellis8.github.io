# Nike Shoe Store Entity-Relationship Diagram

This ERD models the database structure for a Nike shoe retail store, capturing key entities and their relationships using Mermaid syntax.

```mermaid
erDiagram
  PRODUCT {
    int product_id PK
    string name
    string category
    string size
    float price
  }

  CUSTOMER {
    int customer_id PK
    string first_name
    string last_name
    string email
    string phone
}

  SALE {
    int sale_id PK
    date sale_date
    int customer_id FK
    int product_id FK
    int quantity
    float total_price
  }

  INVENTORY {
    int inventory_id PK
    int product_id FK
    int stock_quantity
    string warehouse_location
  }

  CUSTOMER ||--o{ SALE : places
  PRODUCT ||--o{ SALE : includes
  PRODUCT ||--|| INVENTORY : tracked_by
