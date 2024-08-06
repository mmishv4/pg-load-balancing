PostgreSQL Replication Environment с одним мастером и двумя репликами 
с полным выводом логов для удобства отладки. Включает базовые конфигурации 
для Pgpool-II + PgBouncer и HAProxy + PGBouncer.

Статистика HAProxy: http://localhost:8404/

```shell
docker network create postgres_net
docker-compose up --build
```
```shell
docker-compose -f haproxy/docker-compose.yml up --build
```
или
```shell
docker-compose -f pgpool/docker-compose.yml up --build
```
```python
HAPROXY_WRITE_READ_URL = "postgresql+asyncpg://user:password@localhost:6432/write_db"
HAPROXY_READ_URL = "postgresql+asyncpg://user:password@localhost:6432/read_db"
PGPOOL_URL = "postgresql+asyncpg://user:password@localhost:6432/postgres"
```