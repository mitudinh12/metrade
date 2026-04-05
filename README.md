# METRADE 🛒
*University Community E‑Commerce Trading Platform*

## Overview
**Metrade** is a full‑stack e‑commerce trading platform designed specifically for a **Metropolia community**. It enables students and staff to **buy and sell items using an internal currency**, ensuring a safe, closed, and trusted marketplace.

The repository contains:
- A **Node.js / Express** backend API
- Two **Vite + React** frontends:
  - **E‑commerce frontend** (buyers & sellers)
  - **Admin dashboard** (platform management)

The project focuses on **secure authentication**, **role‑based access**, and **scalable backend architecture**, making it suitable both as a learning project and a production‑ready foundation.

---

## Team
- **Nhi Dinh**
- **Kim Tran Do**
- **Tu Dinh**
- **Trung Doan**

---

## Project Goals
- Build a secure internal marketplace for a university
- Apply full‑stack development best practices
- Implement JWT‑based authentication with refresh tokens and access tokens
- Support buyers, sellers, and administrators with clear role separation

---

## Key Features

### User Account Management
- University‑email registration & email verification
- Secure login with JWT (access + refresh tokens)
- Profile management (name, photo, phone, password)
- Order and purchase history

### Product Catalog
- Product browsing, searching, and filtering
- Sorting by price, rating, pickup location, and upload time
- Detailed product pages with images and descriptions
- Seller ratings and reviews

### Cart & Checkout
- Persistent shopping cart
- Quantity updates and total price calculation
- Checkout using internal university coins
- Order tracking and status updates

### Seller Features
- Create and manage product listings
- Upload product images
- Set prices, pickup locations, and inventory
- Manage discounts and promotions

### Admin Dashboard
- Transaction review and confirmation
- Refund and dispute management
- User moderation (ban, deactivate)
- Seller approval workflow
- Product and review moderation

---

## Architecture Overview

### Backend
- **Node.js + Express** REST API
- **MongoDB + Mongoose** for data persistence
- **JWT authentication** using cookies
- **Role‑based authorization middleware**
- **Swagger (OpenAPI)** for API documentation

### Frontend
- **React + Vite** for fast development
- Separate applications for:
  - `ecommerce/` – user & seller interface
  - `admin/` – admin management panel

---

## 🔐 Authentication Flow
- JWT‑based authentication
- Backend sets **HttpOnly cookies**:
  - `accessToken`
  - `refreshToken`
- Protected routes include:
  - `/api/user`
  - `/api/cart`
  - `/api/seller`
  - `/api/admin`
  - `/api/orders`

Token handling:
- Access tokens are short‑lived
- Refresh tokens renew access tokens via:
  - `POST /api/token/get-access-token`

---

## Build and Setup Instructions

### Prerequisites
- Node.js **v16+** (recommended **v18+**)
- npm or yarn
- MongoDB (local or cloud)
- Optional: Cloudinary account for image uploads

---

### Install Dependencies

#### Backend
```bash
cd backend
npm install
```

#### Admin Frontend
```bash
cd admin
npm install
```

#### Ecommerce Frontend
```bash
cd ecommerce
npm install
```

---

## Environment Variables
Create a `.env` file in `backend/` based on `.env.example`.

Required variables:
```env
MONGO_URI=
FE_URL=http://localhost:5173
SALT_ROUNDS=10
JWT_SECRET=
JWT_ACCESS_EXPIRES_IN=15m
JWT_REFRESH_EXPIRES_IN=1d
APP_PORT=3000
VERIFICATION_EXPIRES_IN=1d
EMAIL_USERNAME=
EMAIL_PASSWORD=
```

Optional (Cloudinary):
```env
CLOUDINARY_CLOUD_NAME=
CLOUDINARY_API_KEY=
CLOUDINARY_API_SECRET=
```

---

## Local Development

### Backend
Merge Swagger docs:
```bash
node backend/api-document/mergeSwagger.js
```

Run dev server:
```bash
cd backend
npm run dev
```

Run tests:
```bash
npm test
```

---

### Frontends

#### Ecommerce
```bash
cd ecommerce
npm run dev
```

#### Admin
```bash
cd admin
npm run dev
```

---

## 📚 API Documentation

Once swagger is generated, the backend serves API docs at:
```
http://localhost:<APP_PORT>/api-docs
```

Regenerate docs anytime with:
```bash
node backend/api-document/mergeSwagger.js
```

---

## 📌 Important Notes
- **CORS & Cookies**: Ensure `FE_URL` matches the frontend dev port
- **Email Verification**: Use Mailtrap or test SMTP for development
- **Cloudinary**: Optional – falls back to local storage if unset
- **Cookies**: Frontend requests must include `credentials: true`

---

## Testing
- Backend tests use **Jest + Supertest**
- Run with:
```bash
cd backend && npm test
```

---

## License
This project was developed for **educational purposes** as part of a university software project.  
Please credit the authors for reuse or extension.
