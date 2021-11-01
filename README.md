# web-gui - UI for servers

## MongoDB

```bash
ADDR="$(docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' mongo)"
PORT="14090"
docker rm -f mongo-web
docker run -d --name mongo-web \
--link mongo \
-e ME_CONFIG_MONGODB_ENABLE_ADMIN="true" \
-e ME_CONFIG_OPTIONS_EDITORTHEME="dracula" \
-e ME_CONFIG_MONGODB_SERVER=${ADDR} \
-p $PORT:8081 mongo-express
```

## MySQL

```bash
ADDR="$(docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' mariadb)"
PORT="14091"
docker rm -f mariadb-web
docker run -d --name mariadb-web \
--link mariadb \
-e PMA_HOST=${ADDR} \
-p $PORT:80 phpmyadmin
```

## PostgreSQL

```bash
ADDR="$(docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' postgresql)"
PORT="14092"
docker rm -f postgresql-web
docker run -d --name postgresql-web \
--link postgresql \
-e ALLOW_EMPTY_PASSWORD=yes \
-e DATABASE_HOST=${ADDR} \
-p $PORT:8080 bitnami/phppgadmin
```
