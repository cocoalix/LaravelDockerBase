FROM php:8.0-fpm
COPY php.ini /usr/local/etc/php/

RUN apt-get update \
  && apt-get install -y zlib1g-dev zip libzip-dev mariadb-client \
  && docker-php-ext-configure zip \
  && docker-php-ext-install zip pdo_mysql

#composer install
COPY --from=composer /usr/bin/composer /usr/bin/composer

ENV COMPOSER_ALLOW_SUPERUSER 1

ENV COMPOSER_HOME /composer

ENV PATH $PATH:/composer/vendor/bin


WORKDIR /var/www

#laravel install
RUN composer global require "laravel/installer"
