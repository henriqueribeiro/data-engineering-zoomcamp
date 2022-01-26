# Notes

## Create Conda Env
```bash
conda create -n de_zoomcamp pip
```

## Launch Postgres container
```bash
docker run -it \
  -e POSTGRES_USER="root" \
  -e POSTGRES_PASSWORD="root" \
  -e POSTGRES_DB="ny_taxi" \
  -v "$(pwd)/ny_taxi_postgres_data:/var/lib/postgresql/data" \
  -p 5432:5432 \
  postgres:13
```

## Connect to DB with pgcli
```bash
pgcli -h localhost -p 5432 -U root -d ny_taxi
```

## pgAdmin
```bash
docker run -it \
  -e PGADMIN_DEFAULT_EMAIL="admin@admin.com" \
  -e PGADMIN_DEFAULT_PASSWORD="root" \
  -p 8080:80 \
  dpage/pgadmin4
```

In order for pgAdmin and database to communicate, it's necessary to create a network

```bash
docker network create pg
```

```bash
docker run -it \
  -e POSTGRES_USER="root" \
  -e POSTGRES_PASSWORD="root" \
  -e POSTGRES_DB="ny_taxi" \
  -v "$(pwd)/ny_taxi_postgres_data:/var/lib/postgresql/data" \
  -p 5432:5432 \
  --name pgdatabase \
  --net pg \
  postgres:13
```

```bash
docker run -it \
  -e PGADMIN_DEFAULT_EMAIL="admin@admin.com" \
  -e PGADMIN_DEFAULT_PASSWORD="root" \
  -p 8080:80 \
  --name pgadmin \
  --net pg \
  dpage/pgadmin4
```

## Docker Compose
```bash
docker compose up
```

```bash
docker compose down
```
