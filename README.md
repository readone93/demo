# Project README

## Overview

This project is a full-stack application with three main components:

- **Frontend** – built with Next.js, accessible on port `5000`.
- **Backend** – Node.js/Express API, accessible on port `3001`.
- **Database** – PostgreSQL database, accessible on port `5432`.

Docker Compose is used to manage and run all services together.

---

## Prerequisites

Make sure you have the following installed:

- [Docker](https://www.docker.com/products/docker-desktop)
- [Docker Compose](https://docs.docker.com/compose/install/)

---

## Project Structure

```
├── backend
│   └── ... (backend code)
├── frontend
│   └── ... (frontend code)
├── docker-compose.yml
└── README.md
```

---

## Environment Variables

### Frontend

| Variable                  | Description                                  | Example                        |
|----------------------------|----------------------------------------------|--------------------------------|
| NEXTAUTH_SECRET            | Secret key for NextAuth authentication       | `changeme`                     |
| NEXTAUTH_URL               | URL of the frontend                           | `http://62.171.177.16:5000`   |
| NEXT_PUBLIC_API_URL        | Backend API URL                               | `http://backend:3001`          |
| CLOUDINARY_CLOUD_NAME      | Cloudinary cloud name for media uploads      | `changeme`                     |
| CLOUDINARY_API_KEY         | Cloudinary API key                            | `changeme`                     |
| CLOUDINARY_API_SECRET      | Cloudinary API secret                         | `changeme`                     |

### Backend

| Variable                  | Description                                  | Example                                     |
|----------------------------|----------------------------------------------|---------------------------------------------|
| PORT                       | Port the backend server runs on              | `3001`                                      |
| DATABASE_URL               | PostgreSQL connection string                 | `postgresql://USER:PASSWORD@db:5432/DATABASE?schema=public` |
| NEXTAUTH_SECRET            | Secret key for NextAuth authentication       | `changeme`                                  |
| NEXTAUTH_URL               | URL of the frontend                           | `http://62.171.177.16:5000`               |
| CLOUDINARY_CLOUD_NAME      | Cloudinary cloud name for media uploads      | `changeme`                                  |
| CLOUDINARY_API_KEY         | Cloudinary API key                            | `changeme`                                  |
| CLOUDINARY_API_SECRET      | Cloudinary API secret                         | `changeme`                                  |

### Database

| Variable                  | Description          | Example       |
|----------------------------|--------------------|---------------|
| POSTGRES_USER             | Database username   | `USER`        |
| POSTGRES_PASSWORD         | Database password   | `PASSWORD`    |
| POSTGRES_DB               | Database name       | `DATABASE`    |

---

## Running the Application

1. Clone the repository:

```bash
git clone <repository-url>
cd <repository-folder>
```

2. Build and start all services using Docker Compose:

```bash
docker-compose up --build
```

3. Access the application:

- Frontend: `http://62.171.177.16:5000`
- Backend API: `http://62.171.177.16:3001`
- PostgreSQL DB: `localhost:5432`

4. Stop the services:

```bash
docker-compose down
```

---

## Persistent Storage

The PostgreSQL database data is persisted using a Docker volume:

```yaml
volumes:
  postgres_data:
```

This ensures data remains intact even if containers are restarted.

---

## Notes

- Make sure to replace all `changeme`, `USER`, `PASSWORD`, and `DATABASE` placeholders with actual values.
- The frontend depends on the backend, and the backend depends on the database, so Docker Compose will handle the startup order automatically.
- For production deployment, consider securing environment variables and using a reverse proxy for HTTPS.
