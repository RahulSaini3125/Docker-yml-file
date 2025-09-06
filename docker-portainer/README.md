<div align="center">
  <img src="https://raw.githubusercontent.com/portainer/portainer/develop/app/assets/images/logo_alt.svg" alt="Portainer" width="150" />
  <h1><b>Portainer</b></h1>
  <p><i>Making Docker and Kubernetes management easy</i></p>
  
  [![Docker][docker-shield]][docker-url]
  [![Portainer][portainer-shield]][portainer-url]
  
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
8. [Accessing Portainer](#accessing-portainer)
9. [Features](#features)
10. [Troubleshooting](#troubleshooting)
11. [Security Considerations](#security-considerations)

## 🔍 Overview
This Docker setup provides Portainer, a powerful container management tool that allows you to easily manage your Docker environments through a web interface. Portainer simplifies container deployment, monitoring, and maintenance tasks.

## 📋 Prerequisites
- Docker and Docker Compose installed on your system
- Basic understanding of Docker containers
- Port 9000 available on your host machine

## ⚙️ Configuration
Create a `.env` file based on the provided `.env.example` with the following variables:

```
PORTAINER_VERSION=latest
```

### Environment Variables Explained

| Variable | Description | Default |
|----------|-------------|---------|
| PORTAINER_VERSION | Portainer image version | latest |

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

### portainer
- **Image**: portainer/portainer-ce:latest (configurable via PORTAINER_VERSION)
- **Container Name**: Docker-Portainer
- **Port**: 9000:9000
- **Restart Policy**: unless-stopped

## 🌐 Networks

### portainer
- **Driver**: bridge
- **Purpose**: Isolated network for Portainer service
- **Scope**: Local

## 💾 Volumes

### portainer_data
- **Driver**: local
- **Mount Point**: /data
- **Purpose**: Persistent storage for Portainer configuration and data
- **Type**: Named volume

### Docker Socket
- **Mount**: /var/run/docker.sock:/var/run/docker.sock
- **Purpose**: Allows Portainer to communicate with the Docker daemon

## 🖥️ Accessing Portainer

1. Open your browser and navigate to: http://localhost:9000
2. On first login, you'll be prompted to create an admin user
3. Set a strong password for the admin account
4. Select "Docker" as the environment type
5. Click "Connect"

## 🌟 Features

Portainer offers a wide range of features for Docker management:

- **Dashboard**: Overview of your Docker environment
- **Container Management**: Create, start, stop, and remove containers
- **Image Management**: Pull, build, and manage Docker images
- **Volume Management**: Create and manage persistent storage
- **Network Management**: Configure and manage Docker networks
- **Stack Deployment**: Deploy multi-container applications using Docker Compose
- **Registry Management**: Connect to Docker registries
- **User Management**: Create users with different permission levels
- **Resource Controls**: Set resource limits for containers
- **Events & Logs**: Monitor container events and logs

## ❗ Troubleshooting

### Common Issues

1. **Access Issues**
   - Problem: Cannot access Portainer UI
   - Solution: Verify port mapping and firewall settings

2. **Docker Socket Issues**
   - Problem: "Cannot connect to the Docker daemon"
   - Solution: Verify Docker socket mount and permissions

3. **Permission Issues**
   - Problem: "Permission denied" when performing actions
   - Solution: Check Docker socket permissions and user rights

## 🔒 Security Considerations

1. **Admin Password**: Use a strong password for the admin account
2. **Access Control**: Set up users with appropriate permissions
3. **Network Isolation**: Consider running Portainer behind a reverse proxy
4. **Updates**: Keep Portainer updated to the latest version

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
[portainer-shield]: https://img.shields.io/badge/Portainer-13BEF9?style=for-the-badge&logo=portainer&logoColor=white
[portainer-url]: https://www.portainer.io/