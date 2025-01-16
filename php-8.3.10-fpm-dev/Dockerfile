FROM dmitriikoziuk/php-8.3.10-fpm:3.0.0

LABEL org.opencontainers.image.authors="dmitriikoziuk@gmail.com"

RUN pecl install xdebug-3.3.2 && docker-php-ext-enable xdebug \
    && cp "$PHP_INI_DIR/php.ini-development" "$PHP_INI_DIR/php.ini"

WORKDIR /var/www

CMD ["php-fpm"]
