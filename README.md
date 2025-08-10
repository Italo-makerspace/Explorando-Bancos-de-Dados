***Exploring Databases***
=========================

***Database***
--------------

`Definition:` An organized collection of information, stored and structured in a way that facilitates efficient access, management, and updating.

This concept can be broadly divided into two categories:

-   *Relational*

-   *Non-Relational*

### ***Relational Database***

A relational database is a type of database that stores and provides access to data points that are related to one another. Fundamentally, they are based on the **relational model**, an intuitive and straightforward method of representing data in tables. These tables consist of rows and columns, with each row possessing a unique identifier (a **primary key**), which facilitates the establishment of relationships between data points across different tables.

#### **Use Case Example:**

Consider a pharmacy managing its inventory. It would use **foreign keys** (e.g., a `Medication_ID` in a `Sales` table) to reference the **primary key** in a `Medications` table. In essence, a specific medication's record is located through the intersection of rows and columns that contain information about the product and its available quantity.

### ***Non-Relational Database***

A non-relational database (often called **NoSQL**) is a database that does not use the traditional tabular schema of rows and columns. Instead, it employs a storage model optimized for the specific requirements of the data being stored. This makes it highly effective for handling data with complex structures or high update rates, such as **graph data** or **JSON documents**.

#### **Use Case Example:**

A streaming platform needs to analyze user preferences to provide recommendations. For this purpose, the data can be structured as a **graph**, where users and content are nodes, and their interactions (e.g., "likes," "watched") are edges. This model efficiently represents complex relationships and supports constant, rapid data updates.

***The Normalization Process***
-------------------------------

Data normalization is the process of structuring a relational database to **reduce data redundancy** and **improve data integrity**. Its primary goal is to eliminate duplicate and inconsistent information, thereby simplifying data manipulation and analysis.

### ***Normalizing:***

`Unnormalized Table`

|Order_ID|Customer_Name|Customer_Address|Product_ID|Quantity|Total_Price|
|---------|------------|----------------|----------|----------|-----------|
  |1|     João Silva    |   St A, 123         |   10             | Pen          |   2       |   4,00         |
  |1|     João Silva    |   St A, 123         |   11             | Pencil         |   1       |   2,00         |
  |2|     Maria Souza   |   St. B, 456         |   10             | Pen         |   5       |  10,00         |

  ---

`1st Normal Form (1NF)` By creating a `Customers` table, we extract the attributes: `Customer_ID`, `Name`, and `Address`.

| Customers_ID | Name       | Address  |
|------------|-------------|-----------|
| 1          | João Silva  | St A, 23 |
| 2          | Maria Souza | St. B,456 |

-   **Objective:** Eliminate repeating groups and ensure all data values are atomic (indivisible).

---

`2nd Normal Form (2NF)` By creating a `Products` table, we extract: `Product_ID` and `Product_Name`.

| Product_ID| Product_Name |
|-------------|-----------|
|10  | Pen |
|11  | Pencil  |

-   **Objective:** Remove partial dependencies. This ensures that all non-key attributes are fully dependent on the entire primary key (which is especially relevant for composite keys).

---

`3rd Normal Form (3NF)` By creating an `Order_Items` table, we extract: `Product_ID`, `Order_ID`, `Quantity`, and `Total_Price`.

| Order_ID | Product_ID | Quantity | Total_Price |
|-----------|------------|------------|-------------|
| 1         | 10         | 2          | 4,00        |
| 1         | 11         | 1          | 2,00        |
| 2         | 10         | 5          | 10,00       |

-   **Objective:** Remove transitive dependencies. This ensures that no non-key attribute is dependent on another non-key attribute.

***Non-Relational Structure (MongoDB Example)***
------------------------------------------------

This type of structure is widely utilized due to its inherent **flexibility, speed, and scalability**. The absence of a rigid, predefined schema accelerates development and optimizes performance for specific data models. This flexibility is crucial for handling vast and varied datasets, a cornerstone of **Big Data**, where traditional manual data management becomes infeasible.

```
[
  {
    "order_id": 1,
    "customer": {
      "customer_id": 1,
      "name": "João Silva",
      "address": "Rua A, 123"
    },
    "items": [
      {
        "product_id": 10,
        "product_name": "Pen",
        "quantity": 2,
        "total_price": 4.00
      },
      {
        "product_id": 11,
        "product_name": "Pencil",
        "quantity": 1,
        "total_price": 2.00
      }
    ]
  },
  {
    "order_id": 2,
    "customer": {
      "customer_id": 2,
      "name": "Maria Souza",
      "address": "Av. B, 456"
    },
    "items": [
      {
        "product_id": 10,
        "product_name": "Pen",
        "quantity": 5,
        "total_price": 10.00
      }
    ]
  }
]

```
