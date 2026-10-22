# ShopEZ – Project Documentation

**Prepared by:** Aditya Kambale
**Project type:** Full-stack web application (MERN)
**Based on:** the open-source ShopEZ project by Ruturaj Misal (MIT License)

---

## 1. Introduction
ShopEZ is an online store where customers buy products and sellers manage them. It is a single-page React application backed by a REST API built with Express and MongoDB.

## 2. Problem Statement
Small sellers often lack an affordable, simple way to put a catalogue online, take orders and see how the business is doing. Shoppers, in turn, want quick search, a reliable cart and clear order status. ShopEZ addresses both sides in one system.

## 3. Objectives
- Provide secure registration and login
- Let shoppers find products quickly and place orders with few steps
- Give sellers tools to add products, control stock and process orders
- Show basic business figures (revenue, orders, products, users)
- Keep the code organised enough to extend later

## 4. Scope
**In scope:** user accounts, catalogue, cart, checkout, order tracking, admin/seller dashboard, image upload, low-stock alerts.
**Out of scope (current version):** live payment gateway, email/SMS notifications, product reviews written by users, multi-vendor accounts.

## 5. Requirements

### 5.1 Functional
| ID | Requirement |
|----|-------------|
| F1 | A visitor can register and log in |
| F2 | A user can view and edit their profile |
| F3 | A user can search, filter by category and sort products |
| F4 | A user can add, update and remove cart items |
| F5 | A user can place an order with address and payment method |
| F6 | A user can see past orders and their status |
| F7 | An admin can create, edit and delete products with images |
| F8 | An admin can change order status |
| F9 | An admin can view dashboard statistics and the user list |
| F10 | The system warns when stock is below 10 |

### 5.2 Non-functional
- **Security:** hashed passwords, token-based access, role checks on admin routes
- **Usability:** responsive layout, toast messages for feedback
- **Maintainability:** MVC separation on the server, reusable components on the client
- **Portability:** runs locally or on Vercel with a hosted MongoDB

## 6. System Architecture
Three tiers:
1. **Presentation** – React pages and components, React Router for navigation, Context API for login and cart state.
2. **Application** – Express routes call controllers; middleware validates the JWT and handles uploads.
3. **Data** – MongoDB accessed through Mongoose models.

Request flow: user action → Axios call → route → auth middleware → controller → model → database → JSON response → UI update.

## 7. Database Design
Collections (fields summarised; confirm against `Server/models`):

| Collection | Purpose | Typical data |
|-----------|---------|--------------|
| User | Customer accounts | name, email, hashed password, address details |
| Admin | Seller/admin accounts | name, email, hashed password |
| Product | Catalogue entries | title, description, category, price, discount, stock, image, rating |
| Cart | Per-user basket | user reference, list of items with quantity |
| Order | Placed orders | user reference, items, address, payment method, total, status, date |

Relationships: a User has one Cart and many Orders; an Order contains many Product line items.

## 8. API Design
REST, JSON in and out. Resources: users, products, cart, orders, admin. Reads use GET, creation POST, changes PUT, removal DELETE. Protected endpoints expect a Bearer token. See the README for the endpoint groups.

## 9. Security Measures
- Passwords hashed with bcryptjs before storage
- JWT issued at login and verified by middleware
- Separate admin check on management endpoints
- Secrets kept in environment variables, not in the repository
- Default seed admin credentials must be changed before public deployment

## 10. Testing Approach
| Area | What to check |
|------|---------------|
| Authentication | register, login, wrong password, expired or missing token |
| Catalogue | search term, category filter, price sort, empty result |
| Cart | add, change quantity, remove, totals after discount |
| Orders | placing, status transitions, visibility per user |
| Admin | non-admin blocked, product create/edit/delete, low-stock alert |
| UI | mobile and desktop widths, error messages |

Manual testing with a REST client (Postman or Thunder Client) for the API and browser testing for the UI.

## 11. Limitations
- Payment is recorded as a choice, not processed by a real gateway
- Images are stored on the server disk, which is not persistent on some hosts
- No automated test suite yet

## 12. Future Enhancements
- Payment gateway integration
- Cloud image storage
- Order confirmation emails
- Customer reviews and wishlists
- Automated unit and integration tests
- Pagination for large catalogues

## 13. Acknowledgement
This project builds on the open-source ShopEZ by Ruturaj Misal, distributed under the MIT License. His copyright notice is preserved in the repository's license file.
