<div align="center">
  <img src="https://www.postgresql.org/media/img/about/press/elephant.png" alt="PostgreSQL" width="150" />
  <h1><b>PostgreSQL</b></h1>
  <p><i>A powerful, open-source object-relational database system</i></p>
  
  [![Docker][docker-shield]][docker-url]
  [![PostgreSQL][postgresql-shield]][postgresql-url]
  
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
8. [Connecting to PostgreSQL](#connecting-to-postgresql)
9. [Troubleshooting](#troubleshooting)
10. [Maintenance](#maintenance)

## 🔍 Overview
This Docker setup provides a PostgreSQL database server, which is a powerful, open-source object-relational database system with a strong reputation for reliability, feature robustness, and performance.

## 📋 Prerequisites
- Docker and Docker Compose installed on your system
- Basic understanding of PostgreSQL
- Port 5432 available on your host machine

## ⚙️ Configuration
Create a `.env` file based on the provided `.env.example` with the following variables:

```
POSTGRES_VERSION=latest
POSTGRES_USER=postgres
POSTGRES_PASSWORD=admin
POSTGRES_DB=postgres
TZ=Asia/Kolkata
```

### Environment Variables Explained

| Variable | Description | Default |
|----------|-------------|---------|
| POSTGRES_VERSION | PostgreSQL image version | latest |
| POSTGRES_USER | Username for PostgreSQL | postgres |
| POSTGRES_PASSWORD | Password for PostgreSQL user | admin |
| POSTGRES_DB | Default database name | postgres |
| TZ | Timezone | Asia/Kolkata |

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
- **Scope**: Local

## 💾 Volumes

### postgres_data
- **Mount Point**: /var/lib/postgresql/data
- **Purpose**: Persistent storage for database files
- **Type**: Named volume

## 🔌 Connecting to PostgreSQL

### Using psql CLI
```bash
docker exec -it PostgreSQL psql -U postgres
```

### Using a connection string
```
postgresql://postgres:admin@localhost:5432/postgres
```

### Connection Parameters
- **Host**: localhost
- **Port**: 5432
- **Username**: postgres (or as configured in .env)
- **Password**: admin (or as configured in .env)
- **Database**: postgres (or as configured in .env)

## ❗ Troubleshooting

### Common Issues

1. **Port Conflict**
   - Error: "port is already allocated"
   - Solution: Change the host port in docker-compose.yml

2. **Authentication Failure**
   - Error: "password authentication failed"
   - Solution: Verify credentials in .env file

3. **Data Persistence Issues**
   - Problem: Data lost after container restart
   - Solution: Verify volume configuration

## 🔄 Maintenance

### Backup Database
```bash
docker exec -t PostgreSQL pg_dumpall -c -U postgres > dump_$(date +%Y-%m-%d_%H_%M_%S).sql
```

### Restore Database
```bash
cat your_dump.sql | docker exec -i PostgreSQL psql -U postgres
```

### Update PostgreSQL Version
1. Update POSTGRES_VERSION in .env
2. Run `docker-compose down && docker-compose up -d`

---

<div align="center">
  <p>Maintained by <a href="https://github.com/yourusername">Your GitHub Username</a></p>
  <p>
    <a href="mailto:your.email@example.com">Contact</a> •
    <a href="https://github.com/yourusername">GitHub</a>
  </p>
</div>

<!-- MARKDOWN LINKS & BADGES -->
[docker-shield]: https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white
[docker-url]: https://www.docker.com/
[postgresql-shield]: https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white
[postgresql-url]: https://www.postgresql.org/