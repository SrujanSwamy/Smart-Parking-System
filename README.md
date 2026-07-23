# Smart Parking System

A full-stack smart parking management system with a Node.js/Express backend and a Vite + React frontend. The app supports vehicle parking, exit flow, slot management, reservations, analytics, pricing, payments, and voice-assisted actions.

## Tech Stack

- Backend: Node.js, Express, MongoDB, Mongoose
- Frontend: React, Vite, Axios
- Auth and security: JWT, Helmet, CORS, rate limiting
- Integrations: Razorpay, SMTP email, Google Speech API

## Project Structure

- `backend-node/` - API server, models, controllers, routes, and services
- `frontend-new/` - Vite React app for the operator/admin UI
- `readme/` - Legacy project notes and proposal documents

## Features

- User and admin authentication
- Vehicle park and exit workflows
- Slot allocation and live parking status
- Reservation management
- Pricing estimates and billing
- Analytics dashboard
- Payment order and verification flow
- Voice command and transcription endpoints

## Requirements

- Node.js 18 or later
- npm
- MongoDB connection string
- Razorpay credentials if payments are enabled

## Setup

### 1. Backend

Create a `.env` file inside `backend-node/` with at least these values:

```env
PORT=8080
NODE_ENV=development
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret
FRONTEND_URL=http://localhost:3000
```

Optional variables used by the backend:

```env
RATE_LIMIT_WINDOW_MS=900000
RATE_LIMIT_MAX=100
RAZORPAY_KEY_ID=your_razorpay_key_id
RAZORPAY_KEY_SECRET=your_razorpay_key_secret
SMTP_HOST=smtp.gmail.com
SMTP_PORT=465
SMTP_SECURE=true
SMTP_USER=your_email
SMTP_PASS=your_email_password
SMTP_FROM=your_email
NOTIFY_SCHEDULER_ENABLED=true
NOTIFY_RESERVATION_UPCOMING_MINUTES=30
NOTIFY_RESERVATION_EXPIRY_MINUTES=10
NOTIFY_RESERVATION_EXPIRED_WINDOW_MINUTES=5
NOTIFY_SCHEDULER_INTERVAL_MINUTES=5
```

Install dependencies and start the API server:

```bash
cd backend-node
npm install
npm start
```

The backend runs on `http://localhost:8080` by default.

### 2. Frontend

Create a `.env` file inside `frontend-new/` if you want to override the API URL:

```env
VITE_API_URL=http://localhost:8080/api
```

Install dependencies and start the UI:

```bash
cd frontend-new
npm install
npm run dev
```

The frontend runs on `http://localhost:3000` and opens automatically in the browser.

## Development Flow

1. Start MongoDB.
2. Start the backend server from `backend-node/`.
3. Start the frontend from `frontend-new/`.
4. Use the UI to manage vehicles, slots, reservations, and reports.

## Useful Endpoints

- `GET /api` - API info
- `POST /api/auth/login` - Authentication
- `POST /api/vehicles/park` - Park a vehicle
- `POST /api/vehicles/exit` - Exit a vehicle
- `GET /api/slots` - List slots
- `GET /api/analytics/dashboard` - Dashboard metrics

## Notes

- The frontend uses `VITE_API_URL` if it is set, otherwise it falls back to `http://localhost:8080/api`.
- The backend enables CORS for `http://localhost:3000` and `http://localhost:3001`.
- The manual commands above are the reliable way to run the current codebase.

