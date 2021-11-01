# web-gui
UI for servers

## MongoDB

```bash
ADDR="$(docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' mongo)"
docker run -d --name mongo-web \
-e ME_CONFIG_MONGODB_ENABLE_ADMIN="true" \
-e ME_CONFIG_OPTIONS_EDITORTHEME="dracula" \
-e ME_CONFIG_MONGODB_SERVER=${ADDR} \
-p 8081:8081 mongo-express
```

## MySQL

```bash
ADDR="$(docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' mariadb)"
docker run -d --name myadmin \
-e PMA_HOST=${ADDR} \
-p 8080:80 phpmyadmin
```

## PostgreSQL

```bash
ADDR="$(docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' postgresql)"
docker run -d --name myadmin \
-e ALLOW_EMPTY_PASSWORD=yes \
-e DATABASE_HOST=${ADDR} \
-p 8080:80 bitnami/phppgadmin
```
