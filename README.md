# Auction House

CSI-300 project with a Node.js app and local PostgreSQL, MongoDB, Redis, and Kafka services.

## Requirements

- Docker Desktop
- Node.js LTS

## Set up

1. Copy `.env.example` to `.env` and replace the placeholder values with local-only credentials.
   - PowerShell: `Copy-Item .env.example .env`
   - Git Bash/macOS/Linux: `cp .env.example .env`
2. Install Node dependencies: `npm install`
3. Start the databases and dashboards: `docker compose up -d`
4. Check their status: `docker compose ps`
5. Start the Node app: `npm run dev` or `npm start`.

Keep `.env` on your machine. It is ignored by Git; commit changes to `.env.example` only.

## Services

| Service | Local address | Purpose |
|---|---|---|
| PostgreSQL | `localhost:5432` | Relational database |
| MongoDB | `localhost:27017` | Document database |
| Redis | `localhost:6379` | Cache and key/value store |
| Kafka | `localhost:9092` | Message broker |
| pgAdmin | `http://localhost:5050` | PostgreSQL dashboard |
| Adminer | `http://localhost:8084` | PostgreSQL dashboard |
| Mongo Express | `http://localhost:8082` | MongoDB dashboard |
| Redis Commander | `http://localhost:8081` | Redis dashboard |
| Kafka UI | `http://localhost:8083` | Kafka dashboard |

The dashboards that require credentials use the values in your local `.env`. In pgAdmin, register a server named `auction-house` and use the Docker service name `postgres` as its host.

## Common commands

```bash
docker compose up -d       # start services
docker compose ps          # check status
docker compose logs <name> # inspect a service
docker compose stop        # stop without deleting data
docker compose down        # stop and remove containers
docker compose down -v     # also delete saved database volumes
npm run dev                # run the Node app with watch mode
npm start                  # run the Node app
```

`docker compose down -v` permanently removes the local database volumes. Use it only when you want to reset the data.

See [docs.md](docs.md) for database-client documentation.
