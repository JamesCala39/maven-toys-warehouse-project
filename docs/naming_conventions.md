# **Naming Conventions**

This document outlines the naming conventions used for schemas, tables, views, columns, and other objects in the data warehouse.

## **General Principles**

- **Naming Conventions**: Use snake_case, with lowercase letters and underscores (`_`) to separate words.
- **Language**: Use English for all names.

## **Table Naming Conventions**

### **Bronze Rules**
- All names must start with the 'raw' tag, and table names must match their original names without renaming.
- **`raw_<entity>`**  
  - `raw`: Specifies that the data is from the bronze table and is unfiltered.  
  - `<entity>`: Exact table name from the source system.  
  - Example: `raw_orders` → Order information from the source system.

### **Silver Rules**
- All table names must match their original names without renaming.
- **`<entity>`**  
  - `<entity>`: Exact table name from the source system.  
  - Example: `orders` → Cleaned order information from the source system.

### **Gold Rules**
- All names must use meaningful, business-aligned names for tables, starting with the category prefix.
- **`<category>_<entity>`**  
  - `<category>`: Describes the role of the table, such as `dim` (dimension) or `fact` (fact table).  
  - `<entity>`: Descriptive name of the table, aligned with the business domain (e.g., `customers`, `products`, `sales`).  
  - Examples:
    - `dim_sessions` → Dimension table for website sessions data.  
    - `fact_orders` → Fact table containing orders.
   
## **Loading Procedure**

- All Python function loading procedures used for loading data must follow the naming pattern:
- **`load_<layer>`**.
  
  - `<layer>`: Represents the layer being loaded, such as `bronze`, `silver`, or `gold`.
  - Example: 
    - `load_bronze` → Stored procedure for loading data into the Bronze layer.
    - `load_silver` → Stored procedure for loading data into the Silver layer.
