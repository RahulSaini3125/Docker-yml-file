<div align="center">
  <img src="https://www.portainer.io/hubfs/portainer-logo-black.svg" alt="Portainer" width="150" />
  <h1><b>Portainer</b></h1>
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
This Docker setup provides Portainer, a powerful container management tool that allows you to easily manage your Docker environments through a web interface.

## 📋 Prerequisites
- Docker and Docker Compose installed on your system
- Basic understanding of Docker containers

## ⚙️ Configuration
Create a `.env` file based on the provided `.env.example` with the following variables:

```
PORTAINER_VERSION=latest
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

### Access Portainer
Open your browser and navigate to: http://localhost:9000

On first login, you'll be prompted to create an admin user.

## 🔧 Services

### portainer
- **Image**: portainer/portainer-ce:latest (configurable via PORTAINER_VERSION)
- **Container Name**: Docker-Portainer
- **Port**: 9000:9000
- **Restart Policy**: unless-stopped

## 🌐 Networks

### portainer
- **Driver**: bridge
- **Purpose**: Isolated network for Portainer service

## 💾 Volumes

### portainer_data
- **Driver**: local
- **Mount Point**: /data
- **Purpose**: Persistent storage for Portainer configuration and data
- **Additional Volume**: /var/run/docker.sock:/var/run/docker.sock (allows Portainer to communicate with the Docker daemon)
