FROM php:7.4-fpm

RUN apt-get update && apt-get install -y \
        libicu-dev \
        curl wget git \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libzip-dev zip unzip \
        libmagickwand-dev --no-install-recommends \
    && pecl install imagick \
    && docker-php-ext-enable imagick \
	&& docker-php-ext-configure zip  \
	&& docker-php-ext-install zip \
	&& docker-php-ext-configure intl \
    && docker-php-ext-install intl \
    && docker-php-ext-install pdo_mysql opcache \
    && docker-php-ext-configure gd  --with-jpeg  --with-freetype  \
    && docker-php-ext-install gd \
    && docker-php-ext-install calendar \
    && pecl install xdebug \
    && docker-php-ext-enable xdebug

#COPY --from=composer:latest /usr/bin/composer /usr/bin/composer
# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer


WORKDIR /var/www