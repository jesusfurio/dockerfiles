FROM composer AS builder

COPY src/ /var/www/app

WORKDIR /var/www/app

RUN docker-php-ext-install pdo pdo_mysql

RUN composer install

RUN chown -R www-data:www-data /var/www

FROM nginx:1.17.4

WORKDIR /var/www/app

COPY --from=builder /var/www/app /var/www/app

COPY vhost /etc/nginx/conf.d/default.conf

CMD [ "nginx","-g","daemon off;" ] 