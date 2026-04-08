# 📦 Instagram Thrift Creator Store - Database Design
Eraser Link https://app.eraser.io/workspace/x9dBbRPJQioQCYD4U5UQ?origin=share

## 🎯 Overview

A production-ready database design for a hybrid e-commerce platform that sells **thrifted secondhand items** and **handmade creator products**. Built for scalability, uniqueness tracking, and order management.

**Key Challenge Solved**: Handling both unique thrift items (quantity = 1) and batch-produced handmade items (quantity >= 1) in a single normalized schema.

---

## 📊 Database Schema

### Entity Relationship Diagram

```mermaid
erDiagram
    Customer ||--o{ Order : places
    Order ||--|| Payment : has
    Order ||--|| Shipment : has
    Order ||--o{ OrderItem : contains
    OrderItem }o--|| Inventory : references
    Inventory }o--|| Product : tracks
    Product ||--|| ThriftProduct : "is a"
    Product ||--|| HandmadeProduct : "is a"
    
    Customer {
        int customer_id PK
        string email UK
        string full_name
        text shipping_address
        string phone
        date registered_date
    }
    
    Order {
        int order_id PK
        int customer_id FK
        datetime order_date
        decimal total_amount
        enum order_status
    }
    
    Payment {
        int payment_id PK
        int order_id FK
        string payment_method
        datetime payment_date
        decimal amount_paid
        string transaction_id
    }
    
    Shipment {
        int shipment_id PK
        int order_id FK
        string tracking_number
        string carrier
        date shipped_date
        date estimated_delivery
        date delivered_date
    }
    
    Product {
        int product_id PK
        enum product_type
        string name
        decimal base_price
        text description
        string category
        string size
        string color
    }
    
    ThriftProduct {
        int product_id PK,FK
        enum condition
        boolean is_unique
        string original_brand
        int estimated_year
    }
    
    HandmadeProduct {
        int product_id PK,FK
        string batch_id
        int total_batch_size
        text materials
        int production_time_days
    }
    
    Inventory {
        int inventory_id PK
        int product_id FK
        string stock_keeping_unit
        int quantity_available
        int reserved_quantity
    }
    
    OrderItem {
        int order_item_id PK
        int order_id FK
        int inventory_id FK
        int quantity
        decimal unit_price_at_sale
        string product_name_snapshot
    }