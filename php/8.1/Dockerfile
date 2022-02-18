FROM php:8.1-fpm-alpine

RUN pecl install xdebug-3.1.3\
&& docker-php-ext-enable xdebug

COPY --from=composer:latest /usr/bin/composer /usr/local/bin/composer