FROM composer AS builder

COPY . /var/www/app

WORKDIR /var/www/app

RUN docker-php-ext-install pdo pdo_mysql

RUN composer install

RUN cp .env.example .env

RUN chown -R www-data:www-data /var/www

FROM php:7.2-fpm

WORKDIR /var/www/app

RUN docker-php-ext-install pdo pdo_mysql

COPY --from=builder /var/www/app /var/www/app

RUN chown -R www-data:www-data /var/www

CMD ["php-fpm"]