<div align="center">
  <img src="https://www.postgresql.org/media/img/about/press/elephant.png" alt="PostgreSQL" width="150" />
  <h1><b>PostgreSQL</b></h1>
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
This Docker setup provides a PostgreSQL database server, which is a powerful, open-source object-relational database system with a strong reputation for reliability, feature robustness, and performance.

## 📋 Prerequisites
- Docker and Docker Compose installed on your system
- Basic understanding of PostgreSQL

## ⚙️ Configuration
Create a `.env` file based on the provided `.env.example` with the following variables:

```
POSTGRES_VERSION=latest
POSTGRES_USER=postgres
POSTGRES_PASSWORD=admin
POSTGRES_DB=postgres
TZ=Asia/Kolkata
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

## 🔧 Services

### postgresql
- **Image**: postgres:latest (configurable via POSTGRES_VERSION)
- **Container Name**: PostgreSQL
- **Port**: 5432:5432
- **Environment Variables**:
  - POSTGRES_USER
  - POSTGRES_PASSWORD
  - POSTGRES_DB
  - TZ
- **Health Check**: Configured to verify database availability
- **Restart Policy**: unless-stopped

## 🌐 Networks

### postgresql
- **Driver**: bridge
- **Purpose**: Isolated network for PostgreSQL service

## 💾 Volumes

### postgres_data
- **Mount Point**: /var/lib/postgresql/data
- **Purpose**: Persistent storage for database files
