# Polling System - Backend

A backend server for a real-time polling application. It manages teacher actions, student participation, and communicates live poll updates via Socket.io.

## 🎯 Project Overview

This backend powers the following core functionality:

* Teachers create questions/polls.
* Students submit answers.
* Both teacher and students receive **live updates** using WebSockets.
* Poll states, timing, and transitions are controlled from the backend.

Designed for the *Intervue.io Assignment — Live Polling System*.

---

## 🛠 Tech Stack

* **Node.js**
* **Express.js** — HTTP API framework
* **Socket.io** — real-time communication
* **MongoDB (Mongoose)** — database for storing poll data
* **dotenv** — environment variable management

---

## 📁 Project Structure

```
assignment-intrv-backend/
├── src/
│   ├── server.js            # Entry point — Express + Socket.io setup
│   ├── app.js               # Express app configuration
│   ├── config/              # DB connection
│   ├── controllers/         # Business logic
│   ├── models/              # Mongoose models
│   ├── routes/              # API routes
│   ├── socket/              # Socket.io event handlers
│   └── utils/               # Helper functions
├── package.json
└── README.md
```

---

## ⚙️ Environment Variables

Create a `.env` file with:

```
PORT=5000
MONGO_URI=your_mongodb_connection_string
```

Add these variables manually in Render/Vercel since `.env` is not uploaded.

---

## 🚀 Getting Started

### Install dependencies

```
npm install
```

### Run locally

```
npm start
```

Server runs at:

```
http://localhost:5000
```

---

## 📦 Scripts

| Command       | Description                        |
| ------------- | ---------------------------------- |
| `npm start`   | Start server using Node            |
| `npm run dev` | Start server in dev mode (nodemon) |

---

## 📡 API Endpoints (Brief)

### Authentication / Teacher

```
POST /teacher-login
```

Body:

```json
{
  "email": "teacher@example.com",
  "password": "123456"
}
```

### Polling

```
POST /create-question
GET /current-question
POST /submit-answer
GET /poll-results
```

> (Route names based on project analysis — update if you add more.)

---

## 🔌 WebSocket Events (Socket.io)

* `connect` — new user connects
* `new-question` — teacher broadcasts new question
* `submit-answer` — student sends answer
* `poll-results` — server emits updated results
* `disconnect` — user leaves

---

## 🌐 Deployment Notes

### Render Deployment

* Set **Root Directory** = repository root
* Start Command:

```
npm start
```

* Ensure `process.env.PORT` is used in `server.js`
* Add environment variables under **Render → Environment**

### Vercel Deployment (Frontend Only)

> Vercel cannot host an Express server directly.
> Use Vercel for frontend + Render for backend.

---

## ⚠️ Troubleshooting

### 404 Errors

If API returns:

```
Cannot POST //teacher-login
```

Fix your frontend `.env`:

```
VITE_API_URL=https://your-backend.onrender.com
```

(no trailing slash!)

### Socket Not Connecting

Ensure CORS setup:

```js
origin: ["http://localhost:5173", "https://your-frontend.vercel.app"]
```

---

## 👨‍💻 Author

**Vishal Maurya**
GitHub: [https://github.com/vishal28d](https://github.com/vishal28d)

---

This backend forms the core logic and communication layer of the Live Polling System. Extend it with logging, authentication guards, performance improvements, and additi
