# docker-all-database

This folder contains a docker-compose stack that launches three local database containers for development and testing: MySQL, PostgreSQL and MongoDB.

Files
- `docker-compose.yml` — Compose file that defines the services.
- `.env.example` — Example environment file (copy to `.env` and edit before starting).

Quick summary
- MySQL: port 3306 (bound to `127.0.0.1:3306`)
- PostgreSQL: port 5432 (bound to `127.0.0.1:5432`)
- MongoDB: port 27017 (bound to `127.0.0.1:27017`)

Prerequisites
- Docker (desktop or engine) installed
- Docker Compose (v2) or `docker-compose` available

Usage

1. Copy the example file and edit secrets:

```powershell
Copy-Item .env.example .env
# Then edit .env with your editor and replace placeholder passwords
``` 

2. Start the stack:

```powershell
# Using Docker Compose v2
docker compose -f docker-compose.yml up -d

# Or, if you use the older `docker-compose` binary
docker-compose -f docker-compose.yml up -d
```

3. Check status and logs:

```powershell
docker compose ps
docker compose logs -f
```

4. Stop and remove containers:

```powershell
docker compose down
```

Environment variables (in `.env`)

- `MYSQL_PASSWORD` — root password for MySQL. Required for MySQL healthcheck.
- `MYSQL_VERSION` — MySQL image tag (default: `latest`)
- `POSTGRES_PASSWORD` — password for the default `postgres` user
- `POSTGRES_VERSION` — Postgres image tag (default: `latest`)
- `MONGO_USERNAME` — MongoDB root username
- `MONGO_PASSWORD` — MongoDB root password
- `MONGODB_VERSION` — MongoDB image tag (default: `latest`)

Security notes
- This repository previously included real sample passwords in `.env`. Never commit a `.env` with real credentials to a public repo. Use `.env.example` as the template and keep the actual `.env` private.
- The compose file binds database ports to `127.0.0.1` (localhost) to reduce exposure — still avoid running this on a public network without additional protections.

Connecting examples

- MySQL (CLI):

```powershell
# You will be prompted for the root password
mysql -h 127.0.0.1 -P 3306 -u root -p
```

- PostgreSQL (psql):

```powershell
psql -h 127.0.0.1 -p 5432 -U postgres
```

- MongoDB (mongo shell):

```powershell
mongo --host 127.0.0.1 --port 27017 -u <your_user> -p <your_password> --authenticationDatabase admin
```

Healthchecks and behavior
- Each service includes a healthcheck in `docker-compose.yml`. Containers are configured with `restart: unless-stopped`.

Troubleshooting
- If a container fails its healthcheck, inspect the logs for that service:

```powershell
docker compose logs <service-name>
# e.g. docker compose logs mysql
```
- If ports are already in use, ensure nothing else binds to 127.0.0.1:3306/5432/27017.

Further improvements (optional)
- Add initialization scripts or sample databases as needed.
- Consider using Docker secrets or a vault for production-grade secret management.

License / Attribution
- This README is provided as a short usage document for local development.
