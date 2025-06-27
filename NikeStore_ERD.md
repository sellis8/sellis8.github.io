# Nike Shoe Store Entity-Relationship Diagram

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

The 'Product' entity stores information about all of the Nike shoes available in the store. Each product includes all of the details such as name and category, and the each have a unique ID.

The 'Customer' entity contains all of the records for individuals that shop at the store. It has their contact information and their first and last names.

The 'Sale' entity shows the transaction where a customer purchases a product. Each sale is linked to a specific customer product using its foreign keys.

The 'Inventory' entity tracks the quantity and location of each product in the store.

- Customer to Sale (One to Many): Allows store to track which customers are making purchases and how often they are. 
- Product to Sale (One to Many): Helps see which products are top sellers and see supply and demand.
- Product to Inventory (One to One): Helps the store ensure accurate inventory count for each product.
