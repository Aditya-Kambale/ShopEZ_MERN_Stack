# Project Design Phase: Solution Architecture

| Meta Attribute | Value |
| :--- | :--- |
| **Date** | 12 August 2026 |
| **Team ID** | N/A |
| **Project Name** | ShopEZ Ecommerce Application |
| **Author / Repo** | Aditya Kamble ([https://github.com/Aditya-Kambale/ShopEZ_MERN_Stack](https://github.com/Aditya-Kambale/ShopEZ_MERN_Stack)) |
| **Maximum Marks** | 4 Marks |

---

## 1. High-Level Architecture
ShopEZ implements a 3-tier layered architecture adhering to the Model-View-Controller (MVC) pattern.

```mermaid
flowchart TD
    subgraph Client ["Client Layer (React 18 / Vite)"]
        UI["React Pages (Landing, Products, Cart, Profile, Admin)"]
        Context["Context API (AuthContext, CartContext)"]
        Axios["Axios Interceptor (Bearer JWT)"]
        UI --> Context
        Context --> Axios
    end

    subgraph Server ["Server Layer (Node.js & Express.js)"]
        Routes["Express Routers (/api/users, /products, /cart, /orders, /admin)"]
        MW["Middleware (protect, adminOnly, upload)"]
        Controllers["Controllers (user, product, cart, order, admin)"]
        Axios -->|REST / JSON| Routes
        Routes --> MW
        MW --> Controllers
    end

    subgraph Database ["Data Persistence Layer (MongoDB Atlas)"]
        Models["Mongoose Models (User, Product, Cart, Order, Admin)"]
        DB[(MongoDB Database)]
        Controllers --> Models
        Models --> DB
    end
```
