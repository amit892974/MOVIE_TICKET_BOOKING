# 🎬 BookMyScreen — Movie Ticket Booking System

A full-stack movie ticket booking application built using the MERN stack, with Redis for temporary seat locking and concurrency management.

## 📌 Overview

BookMyScreen allows users to browse movies, explore available shows, select seats, and book movie tickets. The project focuses on backend integration, seat availability, and preventing multiple users from reserving the same seat simultaneously.

## ✨ Features

- 🎥 Browse movies and available shows
- 💺 Select seats for a show
- 🎟️ Book movie tickets
- 🔐 Authentication and authorization
- ⚡ Redis-based temporary seat locking
- ⏳ Automatic lock expiration using TTL
- 🗄️ MongoDB for persistent application data
- 🔄 REST APIs built with Node.js and Express
- 🐳 Docker Compose configuration

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| React | Frontend user interface |
| Node.js | Backend runtime |
| Express.js | REST API development |
| MongoDB | Persistent data storage |
| Redis | Temporary seat locks |
| TypeScript | Backend development |
| Docker Compose | Container orchestration |

## 🏗️ Project Structure

```text
bookMyScreen-master/
├── bms-frontend/       # React frontend
├── bms-backend/        # Backend API
├── docker-compose.yml  # Docker configuration
├── README.md
└── .gitignore
```

## ⚙️ Getting Started

### Prerequisites

Install the following before running the project:

- Node.js and npm
- MongoDB
- Redis
- Git

Docker can also be used if the provided Docker Compose configuration supports your local setup.

### 1. Clone the repository

```bash
git clone https://github.com/amit892974/MOVIE_TICKET_BOOKING.git
cd MOVIE_TICKET_BOOKING
```

### 2. Configure environment variables

Check the backend and frontend directories for `.env.example` files. Create the required local `.env` files and configure the necessary values.

Never commit actual passwords, database credentials, JWT secrets, or API keys to GitHub.

### 3. Install dependencies

Backend:

```bash
cd bms-backend
npm install
```

Frontend, in a separate terminal:

```bash
cd bms-frontend
npm install
```

### 4. Start the application

Check each directory's `package.json` for the available scripts before starting the services.

For example, if the backend provides a `dev` script:

```bash
cd bms-backend
npm run dev
```

Start the frontend using the script defined in its `package.json`.

Ensure MongoDB and Redis are running and the environment variables are configured correctly.

## 🔒 Concurrency Handling with Redis

One of the key technical challenges in a ticket booking system is preventing two users from booking the same seat simultaneously.

This project uses Redis for temporary seat locking:

1. Construct a unique lock key using the show ID and seat ID.
2. Use Redis `SET` with the `NX` option to acquire the lock only if it does not already exist.
3. Apply a time-to-live (TTL) so abandoned locks can expire.
4. Verify the lock and booking state before persisting the confirmed booking in MongoDB.

This approach helps coordinate concurrent booking requests. The final booking operation must also validate seat availability and enforce appropriate database constraints or transactions to prevent duplicate bookings.

## 🚧 Future Improvements

- Online payment integration
- Booking history and cancellation
- Improved automated testing
- Deployment with production monitoring
- Enhanced seat availability updates
- More robust booking expiration and recovery

## 👨‍💻 Author

**Amit Thakur**

MCA Student | National Institute of Technology, Kurukshetra

GitHub: [amit892974](https://github.com/amit892974)

## 📄 License

No license has been specified yet. All rights are reserved by default unless a license is added to the repository.
