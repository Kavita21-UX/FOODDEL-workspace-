# 🍕 Tomato - Full Stack Food Delivery Web Application

A full-stack, production-ready Food Delivery Web Platform built using **React 19**, **Node.js / Express**, **MongoDB / Mongoose**, **JWT Authentication**, and **Stripe Integration**.

---

## 🌟 Architecture & Key Features

### 1. 🚀 Backend API (`backend/` - Port `4000`)
- **Authentication**: JWT-based user registration & login with password hashing via `bcryptjs` and email validation.
- **Menu Management**: CRUD endpoints to add dishes with image file upload handling via `multer`, list items, and remove items.
- **Cart Synchronization**: Persistent user cart storage in database.
- **Order Lifecycle & Payments**:
  - Cash on Delivery (COD) checkout.
  - Stripe Checkout Session creation and verification callback handler.
  - Live order tracking and administrative status updates (*Food Processing* ➔ *Out for delivery* ➔ *Delivered* ➔ *Cancelled*).
- **Static Asset Serving**: Serves all uploaded and catalog images under `/images/<filename>`.

### 2. 🍔 Customer Web Application (`frontend/` - Port `5173`)
- **Modern Hero Section**: Appealing banner with call-to-action to explore dishes.
- **Interactive Menu Category Filter**: Scrollable category pills (Salad, Rolls, Deserts, Sandwich, Cake, Pure Veg, Pasta, Noodles) with real-time dish filtering.
- **Live Search**: Instant keyword search by dish name and description.
- **Add / Remove Cart Counter**: Smooth animated badges on food cards with real-time quantity controls.
- **Cart Page**: Itemized summary, subtotal calculation, delivery fee rules, and promo code support (e.g. `SAVE20`, `FREE5`).
- **Checkout Page**: Comprehensive delivery information form and payment method selector (COD / Stripe).
- **My Orders Page**: Real-time order tracking dashboard showing parcels, items ordered, total amounts, and colored live status indicators.
- **Auth Modal**: Seamless Login and Sign Up modal with token storage.

### 3. 🛡️ Admin Dashboard (`admin/` - Port `5174`)
- **Add Food Page**: Form with drag-and-drop / file image preview, title, description, category selector, and price.
- **Food List Page**: Complete catalog table with dish images, categories, prices, and delete actions.
- **Orders Management**: Real-time order cards with customer address, phone number, payment details, ordered food items, and live status dropdown selector.

---

## 📁 Project Structure

```
FOODDEL/
├── package.json                 # Root orchestrator (concurrently runner)
├── backend/                     # Node.js + Express + Mongoose API
│   ├── config/db.js             # Database connection
│   ├── controllers/             # Food, User, Cart, Order controllers
│   ├── middleware/auth.js       # JWT auth middleware
│   ├── models/                  # Food, User, Order schemas
│   ├── routes/                  # Food, User, Cart, Order routes
│   ├── uploads/                 # Uploaded & default food images
│   ├── scripts/seed.js          # Database seeding script (32 food items)
│   ├── .env                     # Environment variables
│   └── server.js                # Server entrypoint
├── frontend/                    # Customer React App
│   ├── src/
│   │   ├── assets/              # Icons, badges, food images
│   │   ├── components/          # Navbar, Header, ExploreMenu, FoodDisplay, FoodItem, AppDownload, Footer, LoginPopup
│   │   ├── context/StoreContext # Global Cart, Auth, Food, Price state
│   │   ├── pages/               # Home, Cart, PlaceOrder, MyOrders, Verify
│   │   ├── App.jsx & main.jsx
│   │   └── index.css
└── admin/                       # Restaurant Admin React App
    ├── src/
    │   ├── components/          # Admin Navbar, Sidebar
    │   ├── pages/               # Add Dish, List Dishes, Orders Manager
    │   ├── App.jsx & main.jsx
    │   └── index.css
```

---

## 🚀 Quick Start Guide

### 1. Install All Dependencies
Run from the root directory:
```bash
npm run install:all
```

### 2. Configure Environment Variables
Verify or update `backend/.env`:
```env
PORT=4000
MONGO_URI=mongodb://127.0.0.1:27017/food-delivery
JWT_SECRET=supersecret_food_delivery_jwt_key_2025
STRIPE_SECRET_KEY=sk_test_placeholder_key_for_stripe
FRONTEND_URL=http://localhost:5173
ADMIN_URL=http://localhost:5174
```
*(You can paste your MongoDB Atlas connection string in `MONGO_URI`)*.

### 3. Seed Initial Menu Data (Optional)
```bash
npm run seed
```

### 4. Run Everything in Development Mode
Start Backend, Customer Frontend, and Admin Panel concurrently with one command:
```bash
npm run dev
```

- **Customer Frontend**: [http://localhost:5173](http://localhost:5173)
- **Admin Dashboard**: [http://localhost:5174](http://localhost:5174)
- **Backend API**: [http://localhost:4000](http://localhost:4000)

---

## 🧪 Verification & Build Status
- `frontend`: Vite Production Build **Passed** (0 errors)
- `admin`: Vite Production Build **Passed** (0 errors)
- `backend`: API Health Check & Routes **Verified**
