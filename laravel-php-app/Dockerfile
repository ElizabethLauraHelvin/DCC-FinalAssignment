#Stage 1
FROM composer:2 AS vendor
RUN mkdir -p /var/www/laravel
WORKDIR /var/www/laravel
COPY database/ ./database/
COPY composer.* ./
RUN composer install \
   --ignore-platform-reqs \
   --no-interaction \
   --no-plugins \
   --no-scripts \
   --prefer-dist

#Stage 2
FROM node:18 AS asset
RUN mkdir -p /var/www/laravel/public
WORKDIR /var/www/laravel
COPY package*.json ./ 
RUN npm install
COPY vite.config.js ./
COPY resources/ resources/
RUN npm run build

#Stage 3
FROM php:8.2-apache
ENV APACHE_DOCUMENT_ROOT=/var/www/laravel/public
RUN sed -ri -e 's!/var/www/html!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/sites-available/*.conf
RUN sed -ri -e 's!/var/www/!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/apache2.conf /etc/apache2/conf-available/*.conf

RUN mkdir -p /var/www/laravel && chown www-data:www-data /var/www/laravel
WORKDIR /var/www/laravel
COPY --chown=www-data:www-data . .
COPY --chown=www-data:www-data --from=vendor /var/www/laravel/vendor/ ./vendor/
COPY --chown=www-data:www-data --from=asset /var/www/laravel/public/build/ ./public/build/
USER www-data:www-data