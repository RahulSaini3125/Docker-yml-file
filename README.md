<div align="center">
  <img src="https://www.docker.com/wp-content/uploads/2022/03/Moby-logo.png" alt="Docker" width="200" />
  <h1><b>Docker Services Collection</b></h1>
  <p><i>A collection of essential Docker services for development environments</i></p>
  
  [![Docker][docker-shield]][docker-url]
  [![PostgreSQL][postgresql-shield]][postgresql-url]
  [![pgAdmin][pgadmin-shield]][pgadmin-url]
  [![Portainer][portainer-shield]][portainer-url]
  
  <p align="center">
    <a href="#overview">Overview</a> •
    <a href="#services">Services</a> •
    <a href="#getting-started">Getting Started</a> •
    <a href="#usage">Usage</a> •
    <a href="#structure">Structure</a>
  </p>
</div>

## 📑 Table of Contents
1. [Overview](#overview)
2. [Services](#services)
3. [Getting Started](#getting-started)
4. [Usage](#usage)
5. [Structure](#structure)
6. [Common Commands](#common-commands)
7. [Networks](#networks)
8. [Volumes](#volumes)
9. [Customization](#customization)
10. [Troubleshooting](#troubleshooting)

## 🔍 Overview

This repository contains a collection of Docker services configured with Docker Compose, designed to provide essential development tools and databases. Each service is organized in its own directory with a consistent structure, making it easy to deploy and manage independently.

## 🛠️ Services

| Service | Description | Port | Documentation |
|---------|-------------|------|---------------|
| **PostgreSQL** | Powerful, open-source relational database | 5432 | [PostgreSQL README](./docker-postgres/README.md) |
| **pgAdmin** | Web interface for PostgreSQL management | 8080 | [pgAdmin README](./docker-pgadmin/README.md) |
| **Portainer** | Docker container management UI | 9000 | [Portainer README](./docker-portainer/README.md) |

## 🚀 Getting Started

### Prerequisites
- Docker Engine installed
- Docker Compose installed
- Basic understanding of Docker concepts

### Quick Start
1. Clone this repository
2. Navigate to the service directory you want to use
3. Create a `.env` file based on the `.env.example` provided
4. Run `docker-compose up -d` to start the service

## 📋 Usage

Each service can be used independently or in combination with others. For example, you might want to run PostgreSQL with pgAdmin for database management.

### Running Multiple Services

To run PostgreSQL with pgAdmin:

1. Start PostgreSQL:
```bash
cd docker-postgres
docker-compose up -d
```

2. Start pgAdmin:
```bash
cd ../docker-pgadmin
docker-compose up -d
```

3. Connect pgAdmin to PostgreSQL by adding a server in pgAdmin UI:
   - Host: `host.docker.internal` (for macOS/Windows) or your host IP (for Linux)
   - Port: `5432`
   - Username: as configured in PostgreSQL .env
   - Password: as configured in PostgreSQL .env

## 📁 Structure

Each service follows a consistent directory structure:

```
docker-service-name/
  ├── .env.example       # Example environment variables
  ├── docker-compose.yml # Service configuration
  └── README.md          # Service documentation
```

## 🔄 Common Commands

### Start a service
```bash
cd docker-service-name
docker-compose up -d
```

### Stop a service
```bash
cd docker-service-name
docker-compose down
```

### View logs
```bash
cd docker-service-name
docker-compose logs -f
```

### Remove a service (including volumes)
```bash
cd docker-service-name
docker-compose down -v
```

## 🌐 Networks

Each service creates its own isolated Docker network. If you need services to communicate with each other, you have two options:

1. **Host Network**: Services can communicate through the host using `host.docker.internal` (macOS/Windows) or host IP (Linux)
2. **Shared Network**: Modify the docker-compose files to use a common external network

### Creating a Shared Network

```bash
# Create a shared network
docker network create shared_network

# Add to docker-compose.yml for each service:
networks:
  service_network:
    external: true
    name: shared_network
```

## 💾 Volumes

Each service creates named volumes for data persistence. These volumes will persist even if you remove the containers.

To list all volumes:
```bash
docker volume ls
```

To remove a specific volume:
```bash
docker volume rm volume_name
```

## ⚙️ Customization

Each service can be customized through:

1. **Environment Variables**: Edit the `.env` file
2. **Docker Compose**: Modify the `docker-compose.yml` file
3. **Volume Mounts**: Add additional volume mounts for custom configurations

## ❗ Troubleshooting

### Common Issues

1. **Port Conflicts**
   - Error: "port is already allocated"
   - Solution: Change the host port in docker-compose.yml

2. **Network Issues**
   - Problem: Services can't communicate
   - Solution: Ensure proper network configuration or use host.docker.internal

3. **Permission Issues**
   - Problem: "Permission denied" errors
   - Solution: Check volume permissions and ownership

4. **Container Not Starting**
   - Problem: Container exits immediately
   - Solution: Check logs with `docker-compose logs`

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
[postgresql-shield]: https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white
[postgresql-url]: https://www.postgresql.org/
[pgadmin-shield]: https://img.shields.io/badge/pgAdmin-336791?style=for-the-badge&logo=postgresql&logoColor=white
[pgadmin-url]: https://www.pgadmin.org/
[portainer-shield]: https://img.shields.io/badge/Portainer-13BEF9?style=for-the-badge&logo=portainer&logoColor=white
[portainer-url]: https://www.portainer.io/
