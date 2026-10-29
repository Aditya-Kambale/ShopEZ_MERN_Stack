# Project Design Phase: Problem - Solution Fit

| Meta Attribute | Value |
| :--- | :--- |
| **Date** | 11 August 2026 |
| **Team ID** | N/A |
| **Project Name** | ShopEZ Ecommerce Application |
| **Author / Repo** | Aditya Kamble ([https://github.com/Aditya-Kambale/ShopEZ_MERN_Stack](https://github.com/Aditya-Kambale/ShopEZ_MERN_Stack)) |
| **Maximum Marks** | 2 Marks |

---

## Problem-Solution Fit Analysis

| Identified Customer / Merchant Problem | Root Cause | ShopEZ Technical Solution | Validation Metric / Outcome |
| :--- | :--- | :--- | :--- |
| **High shopping cart abandonment due to complex checkout** | Multi-step redirects and mandatory unnecessary fields | Single-screen streamlined checkout with auto-filled profile address and Cash on Delivery (COD) default | 100% test completion of checkout flow in under 30 seconds |
| **Customer uncertainty regarding stock availability and delivery state** | Outdated catalog inventory and opaque fulfillment stages | Real-time stock deduction upon order creation, low-stock warnings, and transparent status tracking (Processing, Shipped, Delivered) | Clear status indicators visible on both user profile and seller orders view |
| **Seller fatigue managing prices and stock across multiple catalog pages** | Clunky traditional admin portals requiring page reload per product edit | Seller Central (`/admin/sell`) with inline editable table cells that trigger asynchronous PUT requests | Zero page reloads required to modify prices and quantities |
| **Unorganized product discovery across varying merchandise** | Poor category taxonomy and slow server-rendered search queries | Fast client-side routing with instant category tabs (Electronics, Fashion, Home) and regex MongoDB search | Search and filter query execution in < 150ms |
