# web-gui - UI for servers

## MongoDB

```bash
ADDR="$(docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' mongo)"
PORT="14090"
docker run -d --name mongo-web \
-e ME_CONFIG_MONGODB_ENABLE_ADMIN="true" \
-e ME_CONFIG_OPTIONS_EDITORTHEME="dracula" \
-e ME_CONFIG_MONGODB_SERVER=${ADDR} \
-p $PORT:8081 mongo-express
```

## MySQL

```bash
ADDR="$(docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' mariadb)"
PORT="14091"
docker run -d --name myadmin \
-e PMA_HOST=${ADDR} \
-p $PORT:80 phpmyadmin
```

## PostgreSQL

```bash
ADDR="$(docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' postgresql)"
PORT="14092"
docker run -d --name myadmin \
-e ALLOW_EMPTY_PASSWORD=yes \
-e DATABASE_HOST=${ADDR} \
-p $PORT:80 bitnami/phppgadmin
```
