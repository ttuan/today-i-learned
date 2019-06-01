# Create default MySQL user and MySQL database on Docker

From: [Docker Hub](https://hub.docker.com/_/mysql)

When you start the `mysql` image, you can pass some environment variables. MySql
image will read those variables and do some job. See [docker-entrypoint.sh](https://github.com/docker-library/mysql/blob/master/5.6/docker-entrypoint.sh) file.

If you want to create user/password, you can specify `MYSQL_USER` and
`MYSQL_PASSWORD` on `docker-compose.yml` file, environment section.

If you want to create a new database, you just need put a value for `MYSQL_DATABASE`.

If you put 3 above variables on .env file, the user/password above will be granted superuser access to this database.

