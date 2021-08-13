FROM dmitriikoziuk/php-8.0.9-fpm:1.0.0

MAINTAINER Dmitrii Kozyuk <dmitriikoziuk@gmail.com>

RUN pecl install xdebug-3.0.4 && docker-php-ext-enable xdebug \
    && cp "$PHP_INI_DIR/php.ini-development" "$PHP_INI_DIR/php.ini"

WORKDIR /var/www

CMD ["php-fpm"]
