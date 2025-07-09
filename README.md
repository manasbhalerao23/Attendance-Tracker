# AttTrack

AttTrack is a full-stack role-based **Student Attendance Management System** for managing and tracking student attendance efficiently in an academic environment that tackles the persistent issue of **proxy attendance**. It features a React-based frontend and a Node.js backend, using PostgreSQL and Redis for persistent and cache storage, respectively.

---


## Problem Statement

In academic institutions, traditional attendance systems are vulnerable to **proxy attendance**, where students mark presence for their peers without being physically present. Manual processes also make it difficult to manage and audit attendance data efficiently.

This project aims to solve these issues by:
- Verifying students' **real-time physical presence** using geolocation
- Using **random time-bound attendance codes**
- Implementing **role-based access control** for security
- Managing data using a **scalable caching + DB sync mechanism**


---

## Features

- **Role-based Authentication:** Secure login for students and teachers using JWT, with session caching via Redis.
- **Attendance Management:** Teachers can generate unique attendance codes; students use codes to mark attendance.
- **Section & Subject Management:** Supports multiple academic sections (CSA, CSB, ITA, ITB, ETCA, ETCB, EI, MECH, CIVIL) and subjects.
- **Statistics & Reports:** Retrieve attendance records and analytics per student, per subject.
- **Modern Frontend:** Built with React + Vite for fast development and hot module reloading.
- **State Management:** Uses Redux Toolkit on the frontend for efficient state handling.

---

## 🔄 User Flow


### 👨‍🎓 Student Flow
1. Logs in with secure credentials.
2. Navigates to the attendance screen.
3. Enters the attendance code shared by the teacher.
4. Shares real-time location (used to verify proximity to classroom).
5. If code + location are valid:
   - Attendance is cached in Redis.
   - Periodically synced to PostgreSQL and Google Sheets.
6. Student receives attendance confirmation.

![image](https://github.com/user-attachments/assets/4b2bc7ff-85f3-4435-98b7-0628af8e4b1b)
---

### 👩‍🏫 Faculty Flow
1. Logs in as a faculty member.
2. Accesses the dashboard to:
   - Generate new attendance codes (valid for 10 mins)
   - Monitor live student submissions
3. Attendance entries are backed up to both PostgreSQL and Google Sheets.

![image](https://github.com/user-attachments/assets/9d2be99a-e6e5-4ce0-8138-1c4c7c75947f)


---

## Project Structure

```
AttTrack/
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

### Database

1.**Inside the Backend part**

 - Go to constructDB Folder
 - Run the ConstructDb.js to create a sample database (Postgresql should be running)

---
