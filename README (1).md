# 🔐 Zero Trust Architecture — Security Dashboard

A full-stack web application implementing Zero Trust security principles with real-time event monitoring, user authentication, and device-aware access control.

---

## 🌐 Live Demo

| Service | URL |
|---|---|
| Frontend | https://zerotrustarchitecturee.netlify.app |
| Backend API | https://zero-trust-io4h.onrender.com/api/health |

---

## 🧱 Tech Stack

| Layer | Technology |
|---|---|
| Frontend | React 19, React Router v6, Recharts |
| Backend | Node.js, Express.js |
| Database | MongoDB Atlas (Mongoose) |
| Auth | JWT (JSON Web Tokens), bcryptjs |
| Device Detection | ua-parser-js |
| Containerization | Docker, Docker Compose |
| Hosting (Frontend) | Netlify |
| Hosting (Backend) | Render |

---

## 📁 Project Structure

```
zero_trust_fixed/
├── docker-compose.yml          # Orchestrates all containers
├── client/                     # React frontend
│   ├── Dockerfile
│   ├── .dockerignore
│   ├── public/
│   │   ├── index.html
│   │   ├── manifest.json
│   │   └── _redirects          # Netlify SPA routing fix
│   └── src/
│       └── utils/
│           └── api.js          # Axios API config
└── server/                     # Express backend
    ├── Dockerfile
    ├── .dockerignore
    ├── server.js               # Main entry point
    └── routes/
        ├── auth.js             # Login / Register routes
        └── events.js           # Security event routes
```

---

## ⚙️ Environment Variables

### `server/.env`
```env
MONGO_URI=your_mongodb_atlas_uri
JWT_SECRET=your_jwt_secret
PORT=5000
```

### `client/.env`
```env
REACT_APP_API_URL=http://localhost:5000/api
```

---

## 🐳 Running with Docker (Local)

### Prerequisites
- [Docker Desktop](https://www.docker.com/products/docker-desktop/) installed and running

### Steps

```bash
# 1. Clone the repository
git clone https://github.com/your-username/zero_trust_fixed.git
cd zero_trust_fixed

# 2. Build Docker images
docker compose build

# 3. Start all containers
docker compose up

# 4. Open in browser
# Frontend → http://localhost:3000
# Backend  → http://localhost:5000/api/health
```

### Useful Docker Commands

```bash
# Run in background
docker compose up -d

# View live logs
docker compose logs -f

# Stop containers
docker compose down

# Rebuild after code changes
docker compose up --build
```

---

## 💻 Running Locally (Without Docker)

### Backend
```bash
cd server
npm install
npm run dev       # Runs with nodemon (hot reload)
```

### Frontend
```bash
cd client
npm install
npm start         # Runs on http://localhost:3000
```

---

## 🚀 Deployment

### Backend — Render
| Setting | Value |
|---|---|
| Root Directory | `server` |
| Build Command | `npm install` |
| Start Command | `npm start` |
| Environment Variables | `MONGO_URI`, `JWT_SECRET`, `PORT` |

### Frontend — Netlify
| Setting | Value |
|---|---|
| Base Directory | `client` |
| Build Command | `npm run build` |
| Publish Directory | `client/build` |
| Environment Variable | `REACT_APP_API_URL=https://your-render-url.onrender.com/api` |

---

## 🔑 API Endpoints

### Auth Routes (`/api/auth`)

| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/auth/register` | Register a new user |
| POST | `/api/auth/login` | Login and receive JWT token |

### Events Routes (`/api/events`)

| Method | Endpoint | Description |
|---|---|---|
| GET | `/api/events` | Get all security events |
| POST | `/api/events` | Log a new security event |

### Health Check

| Method | Endpoint | Description |
|---|---|---|
| GET | `/api/health` | Check if server is running |

---

## 🔒 Zero Trust Principles Implemented

- **Verify Explicitly** — Every request requires JWT authentication
- **Device Awareness** — User agent parsing to detect device type and OS
- **Least Privilege** — Role-based access to security events
- **Assume Breach** — All access attempts are logged as security events


