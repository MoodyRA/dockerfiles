FROM php:8.1-fpm-alpine

RUN apk --no-cache add bash openssh-client ca-certificates \
    git curl nginx wget \
    libxml2-dev libzip-dev libpng-dev libjpeg-turbo-dev \
    ldb-dev \
    $PHPIZE_DEPS


RUN docker-php-ext-install pdo_mysql \
	&& docker-php-ext-install pdo_pgsql \
	&& docker-php-ext-install soap \
	&& docker-php-ext-install zip \
	&& docker-php-ext-install gd \
	&& pecl install xdebug-3.1.3 \
    && docker-php-ext-enable xdebug \
    && docker-php-ext-configure gd --with-jpeg-dir=/usr/include/ \
	&& docker-php-source extract \
	&& docker-php-source delete

COPY --from=composer:latest /usr/bin/composer /usr/local/bin/composer

WORKDIR /home

# xdebug
EXPOSE 9003
