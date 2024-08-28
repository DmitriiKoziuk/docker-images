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
        && docker-php-ext-install opcache mysqli pdo_mysql \
        && docker-php-ext-configure zip && docker-php-ext-install zip \
        && docker-php-ext-configure intl && docker-php-ext-install intl \
        && docker-php-ext-configure pcntl --enable-pcntl && docker-php-ext-install pcntl \
        && pecl install mcrypt-1.0.7 && docker-php-ext-enable mcrypt \
        && pecl install redis-5.3.7 && docker-php-ext-enable redis \
        #&& pecl install xhprof-2.2.3 \
        && cd ~ && git clone https://github.com/longxinH/xhprof.git && cd ./xhprof/extension/ \
        && phpize && ./configure --with-php-config=/usr/local/bin/php-config && make && make install && cd ~ && rm -rf ./xhprof \
        && cd /var/www && docker-php-ext-enable xhprof \
        && docker-php-ext-enable xhprof \
        #&& pecl install imagick-3.4.4 \
        && cd ~ && git clone https://github.com/Imagick/imagick && cd imagick && phpize && ./configure \
        && make && make install && cd ~ && rm -rf ./imagick && cd /var/www \
        && docker-php-ext-enable imagick \
        && cp "$PHP_INI_DIR/php.ini-production" "$PHP_INI_DIR/php.ini" \
        && curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \
        && chown www-data:www-data /usr/local/bin/composer \
        && mkdir /tmp/xhprof \
        && chown www-data:www-data /tmp/xhprof

WORKDIR /var/www

CMD ["php-fpm"]
