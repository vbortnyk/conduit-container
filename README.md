# Conduit

This project is a full-stack web application built with Django REST Framework for the backend and Angular for the frontend. It implements a modern, API-driven architecture inspired by the Conduit (RealWorld) specification, including features such as user authentication, article publishing, and social interactions.

The application is containerized using Docker and orchestrated with Docker Compose, enabling a consistent and reproducible development and deployment environment. An Nginx reverse proxy is used to route requests between the frontend and backend services.

## Table of Contents

- [Introduction](#introduction)
- [Prerequisites](#prerequisites)
- [Quick Start](#quick-start)
- [Usage](#usage)

Before running this project, make sure you have the following installed:

## Prerequisites
- Docker
- Docker Compose
- Node.js (for Angular development, optional if using Docker only)
- Python 3.10+ (for backend development, optional if using Docker only)
- Git

## Quick Start

### Clone the repository:
   ```bash
   $ git clone git@github.com:vbortnyk/conduit.git
   $ cd conduit
   ```

Confgurations details for each part canbe fount here:
- [Angular app README](#https://github.com/vbortnyk/conduit-frontend/blob/master/README.md)
- [Django app README](#https://github.com/vbortnyk/conduit-backend/blob/master/README.md)

The .env-template file contains all required environment variables with default values. Rename it to .env and adjust the values according to your local setup
```bash
BACKEND_PORT=
FRONTEND_PORT=

DATABASE_NAME=
DATABASE_USERNAME=
DATABASE_PASSWORD=

ALLOWED_HOSTS=
```
Make sure you use secure data.

For 

### Start the stack using Docker Compose:
```bash
$ docker compose up -d
```

### Open your browser and access Conduit:

```bash
<host-ip>:<FRONTEND_PORT>
```
`FRONTEND_PORT` must correspond the value from `.env` file

## Usage

- Open: http://<host-ip>:<FRONTEND_PORT>
- Register or log in
- Create and manage articles
- Follow users and view your feed
- Interact via comments and likes

The database (Postgres) stores its data in a Docker volume mounted to: /var/lib/postgresql/data

Additionally, the services are configures with the restart policy unless-stopped

This configuration ensures that containers automatically restart after as system reboot or Docker restart, unless they are manually stopped.

Networking
All services run on a shared network created by Docker Compose.

Containers communicate using service names as hostnames

For setting a custom port for your app:
```bash
FRONTEND_PORT=<custom-port> docker compse up -d