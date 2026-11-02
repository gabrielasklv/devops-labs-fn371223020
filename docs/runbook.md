# Runbook

> Fill in every TODO with exact commands. / Попълнете всяко TODO с точни команди.

## Start locally / Локално стартиране

TODO

## Check that it works / Проверка, че работи

TODO: which address do you open and what should you see? / кой адрес отваряте и какво трябва да видите?

## Run the tests / Тестове

TODO

## When something breaks / Когато нещо се счупи

TODO: the first three things you check. / първите три неща, които проверявате.
## Run with Docker

### Build
```bash
docker build -t notes-api:0.3.0 .
```

### Run
```bash
docker run -d --name notes -p 8000:8000 notes-api:0.3.0
```
Check that it works: open port 8000 and go to `/health`. It should return `{"status": "ok"}`.

Health status (after about 15 seconds):
```bash
docker inspect --format '{{.State.Health.Status}}' notes   # healthy
```

### Logs
```bash
docker logs -f notes      # Ctrl+C to stop watching
```

### Stop
```bash
docker stop notes         # stop the container
docker rm notes           # delete the container
```

## Run with Compose

Prerequisite: copy `.env.example` to `.env` and set a real password.

| Task | Command |
|---|---|
| Start (build if needed) | `docker compose up -d --build` |
| Status / health | `docker compose ps` |
| Follow app logs | `docker compose logs -f app` |
| Start with Adminer (port 8081) | `docker compose --profile tools up -d` |
| Stop, **keep data** | `docker compose down` |
| Stop, **delete data** | `docker compose down -v` |

**Important:** `down` keeps the `db-data` volume, so notes survive.
`down -v` deletes the volume, and all notes are lost.