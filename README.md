# Docker Image: Quick Web Environment
#### This Docker image provides a quick web environment with Apache2, PHP 8.0, and xDebug 3.0.15.
### Quick start
Follow the steps below to quickly set up and configure the Docker image:
1. Rename the .env.example file to .env.
2. Configure the .env file with the following settings:
```
# Path to the project
# Directory DocumentRoot in 000-default.conf

APACHE_DOCUMENT_ROOT=/var/www/html

# ServerAdmin

APACHE_SERVER_ADMIN=admin@mail.com

# Apache2 - ServerName
# Set a custom name for xDebug to work correctly!
# Use it for PhpStorm's "Name" (Servers) from the incoming xDebug connection.

SERVER_NAME=ServerName

# You can set XDEBUG_ENABLE to false if you don't need to use xDebug.

XDEBUG_ENABLE=true

# You can set any xDebug modes here, separated by commas.

XDEBUG_MODE=debug

# If you use Windows or macOS, set it to "docker.host.internal".
# For Linux, use the docker0 IP (for example, use 'ip addr show | grep docker0' command to find it).

XDEBUG_CLIENT_HOST=localhost

```
3. Start the Docker container:
```
docker-compose up
```
Make sure you have Docker installed and running on your system before running the commands above.