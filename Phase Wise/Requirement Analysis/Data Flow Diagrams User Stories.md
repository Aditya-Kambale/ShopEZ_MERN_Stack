# Requirement Analysis: Data Flow Diagrams & User Stories

| Meta Attribute | Value |
| :--- | :--- |
| **Date** | 12 August 2026 |
| **Team ID** | N/A |
| **Project Name** | ShopEZ Ecommerce Application |
| **Author / Repo** | Aditya Kamble ([https://github.com/Aditya-Kambale/ShopEZ_MERN_Stack](https://github.com/Aditya-Kambale/ShopEZ_MERN_Stack)) |
| **Maximum Marks** | 4 Marks |

---

## 1. Data Flow Diagrams (DFD)

### DFD Level 0 (Context Diagram)
```mermaid
flowchart LR
    Customer((Shopper)) <-->|Browse Products / Place Orders / View Status| ShopEZ[ShopEZ E-Commerce Platform]
    Seller((Seller / Merchant)) <-->|Add Products / Edit Stock & Prices| ShopEZ
    Admin((Administrator)) <-->|Manage Users / Update Order Status / View Analytics| ShopEZ
```

### DFD Level 1 (Subsystems)
```mermaid
flowchart TD
    Customer((Shopper)) -->|1. Register / Login| AuthSys[1.0 Authentication Subsystem]
    AuthSys -->|JWT Token| Customer
    Customer -->|2. Browse / Search / Filter| CatalogSys[2.0 Product Catalog Subsystem]
    CatalogSys -->|Product List & Details| Customer
    Customer -->|3. Add to Cart / Modify Quantity| CartSys[3.0 Cart Management Subsystem]
    CartSys -->|Compute Total| CartStore[(Carts DB)]
    Customer -->|4. Checkout & Address| OrderSys[4.0 Order & Checkout Subsystem]
    OrderSys -->|Create Order & Decrement Stock| OrderStore[(Orders DB)]
    OrderSys -->|Update Inventory| ProductStore[(Products DB)]
    Seller((Seller / Admin)) -->|5. Inline Edit Price & Stock| AdminSys[5.0 Admin & Seller Operations]
    AdminSys -->|Update Stock & Price| ProductStore
    AdminSys -->|Update Order Status| OrderStore
```
