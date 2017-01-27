# cheatsheet
Cheatsheet for remote administration and work in conditions of complete uncertainty

# Bash & SSH
__tmux may help you to run a command and continue to work with bash via ssh__
```
tmux
```
__to deattach a session__

`C-b` then `d`

__to attach to a session__

`tmux a -p #`

__List of currently working sessions__

`tmux ls`

# Docker
__If docker repository has unvalidated certificate__

In `/etc/default/docker`
```
DOCKER_OPTS=”--insecure-registry domain.com:port”
```
__Go inside container__
```bash
docker exec -it %CONTAINER_NAME% /bin/bash
```

# PostgreSQL
__Run Docker container with PostgreSQL inside external volume in ```/data/postgres``` (lately you can easily backup this folder)__
```bash
docker run --name %CONTAINER_NAME% -p 5432:5432 -e POSTGRES_PASSWORD=%PASSWORD% -d -v /data/postgresql/data/:/var/lib/postgresql/data %PGSQL-IMAGE%
```

__Migrate from ```HOST1``` to ```HOST2```__
```bash
pg_dump.exe -h %HOST1% -U %USER% -t %TABLENAME% %DBNAME% | pgsql -U %USER% -h %HOST2% %DBNAME%
```
__Dump and restore DB__
```bash
pg_dump -U %USERNAME% %DBNAME% | gzip -9 > /var/lib/postgresql/data/postgres.sql.gz
```

```bash
gunzip -c /data/postgresql/data/postgres.sql.gz | psql -U %USERNAME% %DBNAME%
```
