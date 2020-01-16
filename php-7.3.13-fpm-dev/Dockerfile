FROM dmitriikoziuk/php-7.3.13-fpm:1.0.0

MAINTAINER Dmitrii Kozyuk <dmitrii.kozyuk@gmail.com>

RUN docker-php-ext-enable xdebug \
    && cp "$PHP_INI_DIR/php.ini-development" "$PHP_INI_DIR/php.ini"

WORKDIR /var/www

CMD ["php-fpm"]
