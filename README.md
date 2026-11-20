# ShelfWise - Library Management System (LMS)

A full-stack, modern Library Management System (LMS) built with **Node.js, Express, MongoDB, React, Vite, and Tailwind CSS**.

---

## Features

- **Authentication & Security**: Student registration with OTP email verification, 3-step profile onboarding, JWT auth headers, role-based protection (Student vs Admin).
- **Student Portal**: View active borrowed books, track due dates, live fine calculation, and student profile management.
- **Admin Command Center**: Institutional dashboard, student search by Roll Number, multi-book manual issuing form, returns processing, manual fine management, and institution fine settings.

---

## Project Structure

```
LMS/
├── backend/
│   ├── config/          # Database configuration
│   ├── controller/      # Auth, Book, and Student API logic
│   ├── middleware/      # JWT auth and Role verification middleware
│   ├── models/          # User, Issue, FineSetting Mongoose models
│   ├── routes/          # Express route definitions
│   ├── utils/           # JWT and OTP generator helpers
│   ├── server.js        # Express app entry point
│   ├── .env.example     # Environment variable template
│   └── package.json
└── frontend/
    ├── src/
    │   ├── components/  # Navbar, Sidebar, ProtectedRoute
    │   ├── context/     # AuthContext state manager
    │   ├── pages/       # Home, Login, Signup, Student & Admin pages
    │   ├── utils/       # API fetch wrapper
    │   ├── App.jsx      # Router configuration
    │   └── index.css    # Tailwind CSS theme
    ├── public/
    │   └── _redirects   # SPA routing fallback for Netlify / Render
    ├── .env.example     # Frontend environment variable template
    └── package.json
```

---

## Local Development Setup

### 1. Backend Setup
```bash
cd backend
npm install
# Copy .env.example to .env and configure your MongoDB URI & JWT_SECRET
npm run dev
```
Backend runs on `http://localhost:8080`.

### 2. Frontend Setup
```bash
cd frontend
npm install
# Copy .env.example to .env and configure VITE_API_URL=http://localhost:8080/api
npm run dev
```
Frontend runs on `http://localhost:5173`.

---

## Production Deployment Guide

### Option 1: Render / Railway / Heroku (Backend & Frontend)

#### Backend Deployment (Render / Railway):
1. Create a **Web Service** pointing to `backend/`.
2. **Build Command**: `npm install`
3. **Start Command**: `npm start` (runs `node server.js`).
4. Set Environment Variables:
   - `PORT`: (Auto-assigned or `8080`)
   - `MONGODB_URI`: `mongodb+srv://...`
   - `JWT_SECRET`: `your_secure_secret`
   - `CLIENT_URL`: `https://your-frontend.vercel.app`

#### Frontend Deployment (Vercel / Netlify / Cloudflare Pages):
1. Create a new site pointing to `frontend/`.
2. **Framework Preset**: Vite
3. **Build Command**: `npm run build`
4. **Output Directory**: `dist`
5. Set Environment Variable:
   - `VITE_API_URL`: `https://your-backend.onrender.com/api`
