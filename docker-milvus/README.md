# Milvus Standalone Docker Compose

This configuration sets up a standalone instance of Milvus, the world's most advanced open-source vector database, along with its management tools.

## Components
- **Milvus Standalone**: The core vector database engine.
- **etcd**: Used for metadata storage and service discovery.
- **MinIO**: Object storage for large-scale data persistence.
- **Attu**: Official GUI for Milvus collection and vector management.

## Prerequisites
- Docker and Docker Compose V2.
- CPU with AVX2 or SSE4.2 support.
- Minimum 8GB RAM (16GB recommended).

## Getting Started
1. Copy `.env.example` to `.env`:
   ```bash
   cp .env.example .env
   ```
2. Start the services:
   ```bash
   docker compose up -d
   ```
3. Access the tools:
   - **Milvus (RPC)**: `localhost:19530`
   - **Attu (GUI)**: [http://localhost:8000](http://localhost:8000)
   - **MinIO Console**: [http://localhost:9001](http://localhost:9001) (Credentials: `minioadmin`/`minioadmin`)
