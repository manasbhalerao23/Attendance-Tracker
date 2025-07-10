# Attendance Tracker

Attendance Tracker is a full-stack web application designed for managing and tracking student attendance efficiently in an academic environment. It features a React-based frontend and a Node.js backend, using PostgreSQL and Redis for persistent and cache storage, respectively.

---

## Features

- **Role-based Authentication:** Secure login for students and teachers using JWT, with session caching via Redis.
- **Attendance Management:** Teachers can generate unique attendance codes; students use codes to mark attendance.
- **Section & Subject Management:** Supports multiple academic sections (CSA, CSB, ITA, ITB, ETCA, ETCB, EI, MECH, CIVIL) and subjects.
- **Statistics & Reports:** Retrieve attendance records and analytics per student, per subject.
- **Modern Frontend:** Built with React + Vite for fast development and hot module reloading.
- **State Management:** Uses Redux Toolkit on the frontend for efficient state handling.

---

## Project Structure

```
Attendance Tracker/
│
├── BE/                 # Backend (Node.js + Express)
│   ├── constructDB/    # Database initialization and scripts
│   ├── src/
│   │   ├── config/     # Database and Redis configs
│   │   ├── controllers/# Route controllers for Student/Teacher
│   │   ├── middlewares/# Auth middlewares
│   │   └── models/     # DB query logic
│   └── ...
├── FE/                 # Frontend (React + Vite)
│   ├── src/
│   │   ├── Utilities/  # Redux store and slices
│   │   └── ...
│   └── ...
└── README.md
```

---

## Dependencies

### Backend

- Node.js
- Express.js
- PostgreSQL (`pg`)
- Redis (`redis`)
- JWT (`jsonwebtoken`)
- dotenv

### Frontend

- React
- Vite
- Redux Toolkit
- ESLint

---

## Setup Instructions

### Prerequisites

- [Node.js](https://nodejs.org/)
- [PostgreSQL](https://www.postgresql.org/)
- [Redis](https://redis.io/)
- [Docker](https://www.docker.com/) (optional, for running Redis/Postgres easily)

### Backend

1. **Database Setup:**

   - Create a PostgreSQL database (default: `sample-db`).
   - Edit credentials in `BE/constructDB/ConstructDb.js` if needed.
   - From the `BE/constructDB` directory, run:
     ```sh
     node ConstructDb.js
     ```
     This will create all required tables and seed initial data.

2. **Start Redis:**

   - Using Docker:
     ```sh
     docker run -d --name redis-db -p 127.0.0.1:6379:6379 redis
     ```
   - Or install Redis locally and start the server.

3. **Configure Environment Variables:**

   - Create a `.env` file in `BE/` with appropriate DB and JWT credentials.

4. **Install Backend Dependencies:**
   ```sh
   cd BE
   npm install
   ```

5. **Run the Backend Server:**
   ```sh
   npm start
   ```

---

### Frontend

1. **Install Frontend Dependencies:**
   ```sh
   cd FE
   npm install
   ```

2. **Start the Frontend Dev Server:**
   ```sh
   npm run dev
   ```

---

## Usage

- Teachers can log in, generate attendance codes for their classes, and view class attendance.
- Students log in and use the code to mark their attendance.
- Roles are validated and sessions are managed via Redis for efficient authentication.

---
