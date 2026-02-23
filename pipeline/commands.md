# Docker 和数据库命令

## PostgreSQL 数据库

运行 PostgreSQL 容器在网络上：

```bash
docker run -it \
  -e POSTGRES_USER="root" \
  -e POSTGRES_PASSWORD="root" \
  -e POSTGRES_DB="ny_taxi" \
  -v ny_taxi_postgres_data:/var/lib/postgresql \
  -p 5432:5432 \
  --network=pg-network \
  --name pgdatabase \
  postgres:18
```

## pgAdmin

在同一网络上运行 pgAdmin：

```bash
docker run -it \
  -e PGADMIN_DEFAULT_EMAIL="admin@admin.com" \
  -e PGADMIN_DEFAULT_PASSWORD="root" \
  -v pgadmin_data:/var/lib/pgadmin \
  -p 8085:80 \
  --network=pg-network \
  --name pgadmin \
  dpage/pgadmin4
```

## 常用工具命令

连接到数据库：

```bash
uv run pgcli -h localhost -p 5432 -u root -d ny_taxi
```

运行 Jupyter Notebook：

```bash
uv run jupyter notebook
```