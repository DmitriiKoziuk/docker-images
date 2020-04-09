FROM php:7.4.4-fpm

MAINTAINER Dmitrii Kozyuk <dmitriikoziuk@gmail.com>

RUN apt-get update && apt-get install -y \
        g++ \
        curl \
        wget \
        git \
        libfreetype6-dev \
        libjpeg-dev \
        libmcrypt-dev \
        libpng-dev \
        zip \
        libzip-dev \
        imagemagick \
        libmagickwand-dev \
        zlib1g-dev libicu-dev \
        graphviz \
        && docker-php-ext-configure zip \
        && docker-php-ext-install -j$(nproc) mysqli pdo_mysql zip \
        && docker-php-ext-configure intl \
        && docker-php-ext-install intl \
        && pecl install mcrypt-1.0.3 \
        && pecl install redis-5.2.1 \
        && pecl install xhprof-2.1.4 \
        && pecl install imagick-3.4.4 \
        && docker-php-ext-enable mcrypt redis xhprof imagick opcache \
        && cp "$PHP_INI_DIR/php.ini-production" "$PHP_INI_DIR/php.ini" \
        && curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \
        && chown www-data:www-data /usr/local/bin/composer \
        && mkdir /tmp/xhprof \
        && chown www-data:www-data /tmp/xhprof

WORKDIR /var/www

CMD ["php-fpm"]
