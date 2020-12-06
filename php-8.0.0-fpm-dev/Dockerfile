FROM dmitriikoziuk/php-8.0.0-fpm:1.0.0

MAINTAINER Dmitrii Kozyuk <dmitriikoziuk@gmail.com>

RUN pecl install xdebug-3.0.1 && docker-php-ext-enable xdebug \
    && cp "$PHP_INI_DIR/php.ini-development" "$PHP_INI_DIR/php.ini"

WORKDIR /var/www

CMD ["php-fpm"]
