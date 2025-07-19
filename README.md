
# Wellness Scheduler

A full-stack appointment scheduling app with real-time updates using Redis and ActionCable.

---
## Tech Stack Used

- **Frontend:** React + Vite + HTML/CSS
- **Backend:** Ruby on Rails (REST API)
- **Database:** PostgreSQL
- **Real-Time Sync:** Redis + ActionCable (`@rails/actioncable`)
- **Containerization:** Docker + Docker Compose

---

## Installation

> Recommended for reviewers: clone this repo and run the Docker setup below.

### 1. Clone the Repo
```bash
git clone https://github.com/mahaboobk/wellness-app.git
cd wellness-app
```

### 2. Build and Run Services
```bash
docker-compose build
docker-compose up

```
This spins up:
- `wellness-ui` → React + Vite frontend (`http://localhost:5173`)
- `wellness-api` → Rails backend API (`http://localhost:3000`)
- `wellness-db` → PostgreSQL database
- `redis` → WebSocket message broker

---

## API Endpoints (Rails)

- `GET    /clients` → List all clients  
- `GET    /appointments` → Fetch all appointments  
- `POST   /appointments` → Create a new appointment  
- `PUT    /appointments/:id` → Edit an appointment  
- `DELETE /appointments/:id` → Remove an appointment  

Supports real-time broadcast on CRUD via Redis.

---

## UI Overview

- **Left Pane** → Client List  
- **Right Pane** → Appointment form with time-picker  
- Select a client to view/edit/delete their upcoming appointments  
- Creating, editing, or deleting instantly syncs across browsers  

> Test by opening **two browser windows** and performing create/edit/delete — changes will reflect live using WebSockets.

---

## Development Notes

- Used **Postman mock APIs** initially before integrating with PostgreSQL
- Learned and implemented **Redis WebSocket broadcasting** for real-time syncing
- Ensured responsive design and smooth UX with basic HTML/CSS styling
- Time spent: ~12 hours over 3 days (4 hours/day)

---

## Docker Container Summary

| Service         | Port   | Role                   |
|----------------|--------|-------------------------|
| `wellness-ui`  | 5173   | React Vite frontend     |
| `wellness-api` | 3000   | Rails backend API       |
| `wellness-db`  | 5432   | PostgreSQL database     |
| `redis`        | 6379   | ActionCable broker      |

---

## Cleanup

To stop and remove containers:

```bash
docker-compose down
```

To remove volumes:
```bash
docker-compose down -v
```

## Pending Tasks & Features

- Application works locally via `localhost`
- Working on deploying to AWS for Demo.
- Enhancing the UX for Mobile View
- Developing optional features
