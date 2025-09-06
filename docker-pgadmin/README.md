<div align="center">
  <img src="https://www.pgadmin.org/static/COMPILED/assets/img/logo.svg" alt="pgAdmin" width="150" />
  <h1><b>pgAdmin</b></h1>
</div>

## 📑 Table of Contents
1. [Overview](#overview)
2. [Prerequisites](#prerequisites)
3. [Configuration](#configuration)
4. [Usage](#usage)
5. [Services](#services)
6. [Networks](#networks)
7. [Volumes](#volumes)

## 🔍 Overview
This Docker setup provides pgAdmin, a feature-rich open-source administration and development platform for PostgreSQL. It provides a web interface to manage and interact with your PostgreSQL databases.

## 📋 Prerequisites
- Docker and Docker Compose installed on your system
- Basic understanding of PostgreSQL and pgAdmin

## ⚙️ Configuration
Create a `.env` file based on the provided `.env.example` with the following variables:

```
PGADMIN_VERSION=latest
PGADMIN_DEFAULT_EMAIL=admin@example.com
PGADMIN_DEFAULT_PASSWORD=admin
```

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

### Access pgAdmin
Open your browser and navigate to: http://localhost:8080

Login with the credentials specified in your `.env` file.

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

## 💾 Volumes

### pgadmin_data
- **Driver**: local
- **Mount Point**: /data
- **Purpose**: Persistent storage for pgAdmin configuration and data
