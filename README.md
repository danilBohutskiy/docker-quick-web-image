# Docker Image: Quick Web Environment
#### This Docker image provides a quick web environment with Apache2, PHP 8.0, xDebug 3.0.15, Postgres 15.3
### Quick start
Follow the steps below to quickly set up and configure the Docker image:
1. Rename the `.env.example` file to `.env`.
2. Configure the `.env` file with the following settings:

| Parameter            | Description                               | Default Value |
| -------------------- | ----------------------------------------- | ------------- |
| `SERVER_NAME`        | The server name. Using for Apache2 "ServerName" and xDebug IDE session                           | server_name       |
| `APACHE_DOCUMENT_ROOT` | The Apache document root directory.        | /var/www/html |
| `APACHE_SERVER_ADMIN` | The Apache server admin email address.     | admin@mail.com |
| `XDEBUG_ENABLE`      | Enable or disable xDebug.                  | true          |
| `XDEBUG_MODE`        | The xDebug mode(s) separated by commas.    | develop,debug |
| `XDEBUG_CLIENT_HOST` | The xDebug client host IP address.         | localhost    |
| `DB_NAME`            | The database name.                         | my_db       |
| `DB_USER`            | The database username.                     | root      |
| `DB_PASSWORD`        | The database password.                     | root          |
| `DB_PORT`            | The database port.                         | 5432         |

**Note:** For `XDEBUG_CLIENT_HOST`, make sure to use the IP address of your host machine
- For Linux, you can find the IP address by running the command `ip addr show | grep docker0`. Use the IP address associated with the `docker0` interface.
- For Windows, you can use the special hostname `docker.host.internal` as the value for `XDEBUG_CLIENT_HOST`. This hostname resolves to the IP address of the host machine from within a Docker container.


3. Start the Docker container:
```
docker-compose up
```
Make sure you have Docker installed and running on your system before running the commands above.