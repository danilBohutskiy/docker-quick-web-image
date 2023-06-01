FROM php:8.0-apache

RUN a2enmod rewrite

# ServerName
ARG SERVER_NAME
ENV PHP_IDE_CONFIG="serverName=$SERVER_NAME"

# Apache2 config
ARG APACHE_DOCUMENT_ROOT
ARG APACHE_SERVER_NAME
ARG APACHE_SERVER_ADMIN

ENV APACHE_DOCUMENT_ROOT=$APACHE_DOCUMENT_ROOT
ENV APACHE_SERVER_NAME=$SERVER_NAME
ENV APACHE_SERVER_ADMIN=$APACHE_SERVER_ADMIN

# Install packages
RUN apt-get update && apt-get install -y \
    libzip-dev \
    unzip \
    curl \
    git \
    && docker-php-ext-install zip

# xDebug config
ARG XDEBUG_ENABLE
ARG XDEBUG_CLIENT_HOST
ARG XDEBUG_MODE

RUN if [ "$XDEBUG_ENABLE" = "true" ]; then \
    pecl install xdebug-3.0.4 && \
    docker-php-ext-enable xdebug && \
    echo "xdebug.mode=${XDEBUG_MODE}" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini && \
    echo "xdebug.client_host=$XDEBUG_CLIENT_HOST" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini && \
    echo "xdebug.start_with_request=yes" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini; \
fi

# Установка Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

COPY . /var/www/html
RUN chown -R www-data:www-data /var/www/html
WORKDIR /var/www/html

EXPOSE 80