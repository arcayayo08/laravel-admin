FROM php:8.3-fpm-alpine


# Install Laravel requirements
RUN set -ex \
  && apk --no-cache add \
    postgresql-dev

RUN docker-php-ext-install pdo pdo_pgsql
RUN curl -sS https://getcomposer.org/installer | php -- \
        --install-dir=/usr/local/bin --filename=composer

# Workdir
WORKDIR /app
COPY . .
RUN composer install

RUN chown -R www-data:www-data /var/www/html/storage /var/www/html/bootstrap/cache


CMD php artisan serve --host=0.0.0.0