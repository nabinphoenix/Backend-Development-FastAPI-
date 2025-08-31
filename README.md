# Backend-Development-FastAPI-

This repository contains my intern assessment project for **Arcodify Agency**.  
The goal was to create a secure, scalable, and production-ready API that demonstrates how to build a **modern FastAPI backend** with authentication, JWT authorization, admin controls, CRUD for ToDo items, PostgreSQL integration, background tasks, and Docker support.  

The project is fully compatible with **Python >=3.11**, **SQLAlchemy**, and **Pydantic V2**. If you’re aiming to build scalable and production-ready APIs with FastAPI, this project can serve as a practical reference.  

---

## Why Use This Project?

Developing a backend from scratch can be challenging. This repository provides a **ready-to-use template** with:

- **FastAPI Integration**: A modern, async-first web framework for Python.  (https://fastapi.tiangolo.com/learn/)
- **Authentication & Authorization**: JWT-based login, role-based access control (admin/user).  
- **ToDo CRUD**: Example of clean RESTful API design.  
- **Database Management**: PostgreSQL with Alembic migrations.  
- **Background Tasks**: Asynchronous email sending after user registration.  
- **Documentation**: Auto-generated Swagger/OpenAPI docs.  
- **Deployment Ready**: Dockerized setup for quick local or production use.  

---

## Table of Contents

1. [Prerequisites](#prerequisites)  
2. [Setup Environment Variables](#setup-environment-variables)  
3. [Run with Docker (Recommended)](#run-with-docker-recommended)  
4. [Run Locally without Docker](#run-locally-without-docker)  
5. [Database Setup](#database-setup)  
6. [Run Alembic Migrations](#run-alembic-migrations)  
7. [Access the API](#access-the-api)  
8. [Default Admin Credentials](#default-admin-credentials)  
9. [Architecture Overview](#architecture-overview)  
10. [Tech Stack](#tech-stack)  
11. [Notes](#notes)  
12. [Inspiration and References](#inspiration-and-references)  
13. [Author](#author)  

---

## Prerequisites

- **Windows Subsystem for Linux (WSL)**  
  - Install via Command Prompt:  
    ```sh
    wsl --install
    ```  
  - If it doesn’t work, install the latest release from:  
    [https://github.com/microsoft/WSL/releases](https://github.com/microsoft/WSL/releases)  

- **Docker Desktop** (with WSL integration enabled)  
- **Python 3.11+**  
- **PostgreSQL** (if running locally without Docker)  

Check installation:

```sh
python --version
wsl --version
docker --version
psql --version
```

---

## Setup Environment Variables

This project **already contains a `.env` file** in the root folder.  
You don’t need a `.env.example`.  

- For **Docker setup** → keep `DB_HOST=database`.  
- For **Local setup** → change `DB_HOST=localhost`.  

Example `.env` snippet:

```env
DATABASE_URL=postgresql+asyncpg://postgres:nabin@localhost:5432/ToDoAppDB
SYNC_DATABASE_URL=postgresql+psycopg2://postgres:nabin@localhost:5432/ToDoAppDB
FIRST_SUPERUSER_USERNAME=admin
FIRST_SUPERUSER_EMAIL=admin@admin.com
FIRST_SUPERUSER_PASSWORD=admin
```

---

## Run with Docker (Recommended)

This is the simplest way to start the project.

```sh
git clone https://github.com/nabinphoenix/Backend-Development-FastAPI-.git
cd Backend-Development-FastAPI-
docker compose up --build
```

Access the app:

* API → [http://localhost:8000](http://localhost:8000)  
* Swagger Docs → [http://localhost:8000/docs](http://localhost:8000/docs)  

Stop containers:

```sh
docker compose down
```

---

## Run Locally without Docker

If you prefer to set up manually:

```sh
git clone https://github.com/nabinphoenix/Backend-Development-FastAPI-.git
cd Backend-Development-FastAPI-
```

### Create a virtual environment

```sh
python -m venv venv
source venv/bin/activate   # Linux/Mac
venv\Scripts\activate      # Windows
```

### Install dependencies

```sh
pip install -r requirements.txt
```

---

## Database Setup

Create a PostgreSQL database:

```sql
CREATE DATABASE "ToDoAppDB";
CREATE USER postgres WITH PASSWORD 'nabin';
GRANT ALL PRIVILEGES ON DATABASE "ToDoAppDB" TO postgres;
```

Update `.env` (for local run):

```env
DATABASE_URL=postgresql+asyncpg://postgres:nabin@localhost:5432/ToDoAppDB
SYNC_DATABASE_URL=postgresql+psycopg2://postgres:nabin@localhost:5432/ToDoAppDB
```

---

## Run Alembic Migrations

To generate tables:

```sh
alembic upgrade head
```

---

## Access the API

* **Base URL** → [http://127.0.0.1:8000](http://127.0.0.1:8000)  
* **Swagger UI** → `/docs`  
* **ReDoc** → `/redoc`  

---

## Default Admin Credentials

By default, one superuser is created (set in `.env`):

```env
FIRST_SUPERUSER_USERNAME=admin
FIRST_SUPERUSER_EMAIL=admin@admin.com
FIRST_SUPERUSER_PASSWORD=admin
```

⚠️ **Change these before production deployment!**

---

## Architecture Overview

This project includes:

* **FastAPI app** → Core business logic  
* **PostgreSQL** → Database  
* **Alembic** → Migrations  
* **JWT Auth** → User authentication  
* **Background Tasks** → Email handling  
* **Docker Compose** → Container orchestration  

---

## Tech Stack

* [FastAPI](https://fastapi.tiangolo.com/)  
* [PostgreSQL](https://www.postgresql.org/)  
* [Alembic](https://alembic.sqlalchemy.org/)  
* [SQLAlchemy](https://www.sqlalchemy.org/)  
* [Pydantic V2](https://docs.pydantic.dev/latest/)  
* [Docker](https://www.docker.com/)  

---

## Notes

* Background tasks execute **after responses are returned**.  
* For development, Docker is strongly recommended to avoid manual DB setup.  
* For production, configure a managed PostgreSQL instance and update `.env`.  

---

## Inspiration and References

* [FastAPI Documentation](https://fastapi.tiangolo.com/)  
* [SQLAlchemy 2.0](https://docs.sqlalchemy.org/en/20/)  
* [Alembic Migrations](https://alembic.sqlalchemy.org/en/latest/)  
* [JWT Authentication in FastAPI](https://fastapi.tiangolo.com/tutorial/security/)  

---


## Author

👨‍💻 **Nabin Nepali**  
🔗 [GitHub](https://github.com/nabinphoenix)  
