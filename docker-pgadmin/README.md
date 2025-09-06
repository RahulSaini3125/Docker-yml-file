<div align="center">
  <img src="https://raw.githubusercontent.com/docker-library/docs/b449be7df57e9ed9086bb5821bfb5d6cdc5d67a4/postgres/logo.png" alt="pgAdmin" width="150" />
  <h1><b>pgAdmin</b></h1>
  <p><i>The most popular and feature rich PostgreSQL administration platform</i></p>
  
  [![Docker][docker-shield]][docker-url]
  [![pgAdmin][pgadmin-shield]][pgadmin-url]
  
  <p align="center">
    <a href="#overview">Overview</a> •
    <a href="#prerequisites">Prerequisites</a> •
    <a href="#configuration">Configuration</a> •
    <a href="#usage">Usage</a> •
    <a href="#services">Services</a>
  </p>
</div>

## 📑 Table of Contents
1. [Overview](#overview)
2. [Prerequisites](#prerequisites)
3. [Configuration](#configuration)
4. [Usage](#usage)
5. [Services](#services)
6. [Networks](#networks)
7. [Volumes](#volumes)
8. [Accessing pgAdmin](#accessing-pgadmin)
9. [Connecting to PostgreSQL](#connecting-to-postgresql)
10. [Troubleshooting](#troubleshooting)

## 🔍 Overview
This Docker setup provides pgAdmin, a feature-rich open-source administration and development platform for PostgreSQL. It provides a web interface to manage and interact with your PostgreSQL databases.

## 📋 Prerequisites
- Docker and Docker Compose installed on your system
- Basic understanding of PostgreSQL and pgAdmin
- Port 8080 available on your host machine

## ⚙️ Configuration
Create a `.env` file based on the provided `.env.example` with the following variables:

```
PGADMIN_VERSION=latest
PGADMIN_DEFAULT_EMAIL=admin@example.com
PGADMIN_DEFAULT_PASSWORD=admin
```

### Environment Variables Explained

| Variable | Description | Default |
|----------|-------------|---------|
| PGADMIN_VERSION | pgAdmin image version | latest |
| PGADMIN_DEFAULT_EMAIL | Default admin email for login | admin@example.com |
| PGADMIN_DEFAULT_PASSWORD | Default admin password | admin |

## 🚀 Usage

### Start the service
```bash
docker-compose up -d
```

### Stop the service
```bash
docker-compose down
```

### Remove the service (including volumes)
```bash
docker-compose down -v
```

### View logs
```bash
docker-compose logs -f
```

### Check container status
```bash
docker-compose ps
```

## 🔧 Services

### pgadmin
- **Image**: dpage/pgadmin4:latest (configurable via PGADMIN_VERSION)
- **Container Name**: Docker-Pgadmin
- **Port**: 8080:80
- **Environment Variables**:
  - PGADMIN_DEFAULT_EMAIL
  - PGADMIN_DEFAULT_PASSWORD
- **Restart Policy**: unless-stopped

## 🌐 Networks

### pgadmin
- **Driver**: bridge
- **Purpose**: Isolated network for pgAdmin service
- **Scope**: Local

## 💾 Volumes

### pgadmin_data
- **Driver**: local
- **Mount Point**: /data
- **Purpose**: Persistent storage for pgAdmin configuration and data
- **Type**: Named volume

## 🖥️ Accessing pgAdmin

1. Open your browser and navigate to: http://localhost:8080
2. Login with the credentials specified in your `.env` file:
   - Email: admin@example.com (or as configured)
   - Password: admin (or as configured)

## 🔌 Connecting to PostgreSQL

To connect pgAdmin to a PostgreSQL server:

1. After logging in, right-click on "Servers" in the left panel and select "Create" > "Server..."
2. In the "General" tab, enter a name for your server connection
3. In the "Connection" tab, enter:
   - Host name/address: postgresql (if using the companion PostgreSQL service)
   - Port: 5432
   - Maintenance database: postgres
   - Username: postgres (or as configured)
   - Password: admin (or as configured)
4. Click "Save"

### Network Configuration

If your PostgreSQL server is running in a different Docker network, you'll need to:
1. Add the pgAdmin service to that network in your docker-compose.yml
2. Use the PostgreSQL service name as the hostname

## ❗ Troubleshooting

### Common Issues

1. **Login Issues**
   - Problem: Cannot login to pgAdmin
   - Solution: Verify PGADMIN_DEFAULT_EMAIL and PGADMIN_DEFAULT_PASSWORD in .env

2. **Connection Issues**
   - Problem: Cannot connect to PostgreSQL server
   - Solution: Ensure both services are in the same network or properly configured

3. **Permission Issues**
   - Problem: "Permission denied" errors
   - Solution: Check volume permissions and ownership

---

<div align="center">
  <p>Maintained by <a href="https://github.com/RahulSaini3125">Rahul Saini</a></p>
  <p>
    <a href="mailto:rahulsaini5123@outlook.com">Contact</a> •
    <a href="https://github.com/RahulSaini3125">GitHub</a>
  </p>
</div>

<!-- MARKDOWN LINKS & BADGES -->
[docker-shield]: https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white
[docker-url]: https://www.docker.com/
[pgadmin-shield]: https://img.shields.io/badge/pgAdmin-336791?style=for-the-badge&logo=postgresql&logoColor=white
[pgadmin-url]: https://www.pgadmin.org/