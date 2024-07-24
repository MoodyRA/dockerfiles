FROM php:8.3-fpm-alpine

RUN apk --no-cache add bash openssh-client ca-certificates \
    git curl nginx wget \
    libxml2-dev libzip-dev libpng-dev libjpeg-turbo-dev \
    ldb-dev \
    $PHPIZE_DEPS


RUN docker-php-ext-install pdo_mysql \
	&& docker-php-ext-install zip \
	&& pecl install xdebug-3.3.1 \
    && docker-php-ext-enable xdebug \
	&& docker-php-source extract \
	&& docker-php-source delete

COPY --from=composer:latest /usr/bin/composer /usr/local/bin/composer

WORKDIR /home

# xdebug
EXPOSE 9003
