FROM php:8.3.10-fpm

LABEL org.opencontainers.image.authors="dmitriikoziuk@gmail.com"

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
        && docker-php-ext-install opcache mysqli pdo_mysql sockets \
        && docker-php-ext-configure zip && docker-php-ext-install zip \
        && docker-php-ext-configure intl && docker-php-ext-install intl \
        && docker-php-ext-configure pcntl --enable-pcntl && docker-php-ext-install pcntl \
        && pecl install mcrypt-1.0.7 && docker-php-ext-enable mcrypt \
        && pecl install redis-5.3.7 && docker-php-ext-enable redis \
        #&& pecl install imagick-3.4.4 \
        && cd ~ && git clone https://github.com/Imagick/imagick && cd imagick && phpize && ./configure \
        && make && make install && cd ~ && rm -rf ./imagick && cd /var/www \
        && docker-php-ext-enable imagick \
        && cp "$PHP_INI_DIR/php.ini-production" "$PHP_INI_DIR/php.ini" \
        && curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \
        && chown www-data:www-data /usr/local/bin/composer \
        # php-spx install
        && git clone https://github.com/NoiseByNorthwest/php-spx.git && cd php-spx && git checkout release/latest \
        && phpize && ./configure && make && make install && docker-php-ext-enable spx

WORKDIR /var/www

CMD ["php-fpm"]
