FROM dmitriikoziuk/php-7.4.4-fpm:1.0.0

MAINTAINER Dmitrii Kozyuk <dmitriikoziuk@gmail.com>

RUN pecl install xdebug-2.9.4 \
    && docker-php-ext-enable xdebug \
    && cp "$PHP_INI_DIR/php.ini-development" "$PHP_INI_DIR/php.ini"

WORKDIR /var/www

CMD ["php-fpm"]
