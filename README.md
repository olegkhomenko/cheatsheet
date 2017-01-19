# cheatsheet
Cheatsheet for remote administration and work in conditions of complete uncertainty

# Bash & SSH

# Docker
__Go inside container__
```bash
docker exec -it %CONTAINER_NAME% /bin/bash
```

# PostgreSQL
__Run Docker container with PostgreSQL inside external volume in ```/data/postgres``` (lately you can easily backup this folder)__
```bash
docker run --name %CONTAINER_NAME% -p 5432:5432 -e POSTGRES_PASSWORD=%PASSWORD% -d -v /data/postgresql/data/:/var/lib/postgresql/data %PGSQL-IMAGE%
```
