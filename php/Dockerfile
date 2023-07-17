FROM php:8.1-fpm-alpine

RUN docker-php-ext-install pdo pdo_mysql

#allow composer as a super user
ENV COMPOSER_ALLOW_SUPERUSER=1

#getting composer image and copying
COPY --from=composer:2.4 /usr/bin/composer /usr/bin/composer

#copy composer.json || composer.lock
COPY ./app/composer.* ./

#install
RUN composer install --prefer-dist --no-dev --no-scripts --no-progress --no-interaction

#copy application files to working directory
COPY ./app .

#run composer dump-autoload
RUN composer dump-autoload --optimize