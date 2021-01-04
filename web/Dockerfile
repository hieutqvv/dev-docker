FROM php:7.4.13-apache

RUN apt-get update
RUN apt-get install -y vim zlib1g-dev libjpeg-dev libpng-dev libfreetype6-dev mysql-client-*

# install PHP extensions
RUN docker-php-ext-install pdo_mysql
RUN docker-php-ext-configure gd --with-freetype=/usr/include/ --with-jpeg=/usr/include/
RUN docker-php-ext-install gd
RUN docker-php-ext-install mysqli

# install SSL Self-signed certificate
COPY entrypoint.sh /opt/entrypoint.sh
RUN chmod a+x /opt/entrypoint.sh
RUN /bin/bash -c "source /opt/entrypoint.sh /etc/apache2/ssl_keys *.localhost"

RUN a2enmod ssl
RUN a2enmod rewrite

RUN a2dissite *
RUN rm -f /etc/apache2/sites-available/*
COPY ./apache-conf /etc/apache2/sites-available
RUN a2ensite *

COPY php.ini /usr/local/etc/php
COPY ./dotfiles /root
