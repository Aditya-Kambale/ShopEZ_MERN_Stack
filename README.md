# ShopEZ – MERN Stack E-Commerce Platform

**Author:** Aditya Kambale ([@Aditya-Kambale](https://github.com/Aditya-Kambale))

ShopEZ is a full-stack online shopping application built on the MERN stack (MongoDB, Express.js, React, Node.js). Customers can browse and buy products; sellers/admins get a separate dashboard to run the catalogue, process orders and watch sales numbers.

> **Acknowledgement:** This project is based on the open-source ShopEZ project by [Ruturaj Misal](https://github.com/ruturaj1804/-ShopEZ), released under the MIT License. The original copyright and license notice are retained in `LICENSE`. Documentation in this repository was written separately for this version.

## Table of Contents
1. [Highlights](#highlights)
2. [Tech Stack](#tech-stack)
3. [How It Works](#how-it-works)
4. [Folder Layout](#folder-layout)
5. [Quick Start](#quick-start)
6. [Environment Variables](#environment-variables)
7. [API Overview](#api-overview)
8. [Application Routes](#application-routes)
9. [More Documentation](#more-documentation)
10. [License](#license)

## Highlights

**Shoppers**
- Sign up, log in and edit a profile, secured with JSON Web Tokens
- Search products, filter by category and sort by price
- Product pages with images, description, rating, discount and stock status
- Cart with live totals, quantity changes and item removal
- Checkout with shipping address and payment method
- Order history with status (Processing, Shipped, Delivered, Cancelled)

**Sellers / Admins**
- Dashboard with totals for revenue, orders, products and users
- Create products with image upload, pricing, discount, category and stock
- Edit price and stock in place from the product list
- Automatic low-stock warning when quantity drops under 10
- View every order and change its status
- View registered users

## Tech Stack

| Area | Tools |
|------|-------|
| Frontend | React 18, Vite, React Router, Axios, React Icons, React Toastify |
| Backend | Node.js, Express.js |
| Database | MongoDB, Mongoose |
| Auth & security | JWT, bcryptjs |
| Uploads | Multer |
| Pattern | MVC on the server |
| Hosting | Vercel (see `vercel.json`) |

## How It Works

The React client talks to the Express API over HTTP using Axios. The API checks the JWT on protected routes, runs the logic in controllers, and reads or writes MongoDB through Mongoose models. Product images are stored in the server's `uploads` folder and served as static files. React Context holds login state and cart state so every page stays in sync.

```
Browser (React + Vite)  <-->  Express API  <-->  MongoDB
        |                        |
   Auth/Cart context      JWT middleware, Multer
```

## Folder Layout

```
ShopEZ/
├── Client/                  React app
│   └── src/
│       ├── components/      Navbar, Footer, ProductCard
│       ├── context/         Auth and cart state
│       ├── pages/           Shopper pages
│       │   └── admin/       Seller and admin pages
│       └── services/        API client and helpers
├── Server/                  Express API
│   ├── config/              Database connection
│   ├── controllers/         Request handling and business rules
│   ├── middleware/          JWT check, file upload
│   ├── models/              Mongoose schemas
│   ├── routes/              Route definitions
│   ├── uploads/             Product images
│   ├── index.js             Entry point
│   └── seed.js              Sample data loader
├── Documentation/           Project report
├── Phase Wise/              Development phases
├── package.json
└── vercel.json
```

## Quick Start

**Requirements:** Node.js 16+, npm, and MongoDB (local or Atlas).

```bash
# 1. Clone
git clone https://github.com/Aditya-Kambale/ShopEZ_MERN_Stack.git
cd ShopEZ_MERN_Stack

# 2. Backend
cd Server
npm install
# create .env (see below), then load sample data
node seed.js
npm run dev        # http://localhost:8000

# 3. Frontend (new terminal)
cd Client
npm install
npm run dev        # http://localhost:5173
```

The seed script creates sample products and an admin account. Check `Server/seed.js` for the admin credentials and **change them before deploying anywhere public**.

## Environment Variables

Create `Server/.env`:

```
MONGO_URI=mongodb://localhost:27017/shopez
JWT_SECRET=choose_a_long_random_string
PORT=8000
```

Never commit `.env` files.

## API Overview

| Group | Base path | What it covers |
|-------|-----------|----------------|
| Users | `/api/users` | register, login, read/update own profile |
| Products | `/api/products` | list (search, category, sort), view one, and admin-only create/update/delete |
| Cart | `/api/cart` | view cart, add item, change quantity, remove item |
| Orders | `/api/orders` | place order, own orders, admin: all orders and status updates |
| Admin | `/api/admin` | dashboard statistics, user list, site settings |

Routes marked protected need an `Authorization: Bearer <token>` header; admin routes also require an admin account.

## Application Routes

| Route | Page |
|-------|------|
| `/` | Home with banner, categories, featured items |
| `/products`, `/products/:id` | Catalogue and product detail |
| `/cart` | Cart and checkout |
| `/profile` | Account details and orders |
| `/login`, `/register` | Authentication |
| `/admin` | Admin dashboard |
| `/admin/sell` | Seller dashboard |
| `/admin/orders` | Order management |
| `/admin/products`, `/admin/products/new` | Product list and creation form |

## More Documentation
- [Project Documentation](Documentation/Project-Documentation.md)
- [Phase-wise development](Phase%20Wise/)

## License
MIT. See `LICENSE`. The original work is copyright its respective author, Ruturaj Misal, and that notice must stay in the license file.
