# Requirement Analysis: Solution Requirements (Functional & Non-Functional)

| Meta Attribute | Value |
| :--- | :--- |
| **Date** | 12 August 2026 |
| **Team ID** | N/A |
| **Project Name** | ShopEZ Ecommerce Application |
| **Author / Repo** | Aditya Kamble ([https://github.com/Aditya-Kambale/ShopEZ_MERN_Stack](https://github.com/Aditya-Kambale/ShopEZ_MERN_Stack)) |
| **Maximum Marks** | 4 Marks |

---

## 1. Functional Requirements (FR)

| FR No. | Functional Epic | Detailed Sub-Requirements & Acceptance Criteria |
| :--- | :--- | :--- |
| **FR-1** | User Authentication | User registration with email/password; secure login with JWT token; password hashing using bcryptjs (10 rounds); persistent session in localStorage; role differentiation (`user`/`admin`). |
| **FR-2** | Product Catalog | Display all active products in a responsive grid; support category filtering (Electronics, Clothing, Footwear, Books, Home); support keyword search; sort by price and rating. |
| **FR-3** | Product Details | Single product view displaying high-res image, price, discount percentage, category, stock availability indicator, and customer reviews/ratings. |
| **FR-4** | Customer Reviews | Authenticated users can submit 1-5 star ratings and textual comments on product pages; average rating and review count recalculation. |
| **FR-5** | Shopping Cart | Add to cart from catalog or detail page; modify quantity directly in cart; auto-recalculate line items and total amount; remove individual items or clear entire cart. |
| **FR-6** | Checkout & Orders | Enter shipping address (street, city, state, zip, country); select payment method (COD); create order; deduct purchased quantity from product stock. |
| **FR-7** | Order Tracking | Users view order history under Profile; real-time order status tracking: `Processing` -> `Shipped` -> `Delivered` -> `Cancelled`. |
| **FR-8** | Seller Central | Dedicated seller interface (`/admin/sell`) displaying all catalog items, current stock, price, and direct action triggers. |
| **FR-9** | Inline Inventory Edit | Sellers can click on price or stock cells to edit values inline with immediate backend persistence via REST API (`PUT /api/products/:id`). |
| **FR-10** | Low Stock Alerts | Automatic visual alert banner displayed when any product inventory drops below 10 units to prevent stockouts. |
| **FR-11** | Product Management | Admins/sellers can add new products with image upload (Multer), name, description, price, category, discount, and initial stock. |
| **FR-12** | Admin Governance | Admin dashboard with total revenue, total orders, product count, and user count; order status updates; customer deletion. |
