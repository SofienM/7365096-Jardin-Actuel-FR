FROM php:8.1-fpm
WORKDIR .
ENV COMPOSER_ALLOW_SUPERUSER=1
RUN apt-get update && apt-get install -y \
    curl \
    libicu-dev \
    libpq-dev \
    libzip-dev \
    && docker-php-ext-install -j$(nproc) intl pdo pdo_mysql zip

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
COPY . .
RUN composer install --prefer-dist --no-progress --no-interaction

EXPOSE 8081
CMD php -S 0.0.0.0:8081 -t public/


