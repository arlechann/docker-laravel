FROM php:fpm

# php
WORKDIR /
RUN apt-get update && apt-get upgrade -y && \
	apt-get install -y  unzip libzip-dev libpng-dev libicu-dev libonig-dev && \
	apt-get clean && \
	docker-php-ext-install -j$(nproc) zip iconv intl mbstring pdo_mysql opcache gd && \
	pecl install xdebug && \
	docker-php-ext-enable xdebug && \
	apt-get update && \
	apt-get clean

COPY php.ini /usr/local/etc/php/conf.d
COPY www.conf /usr/local/etc/php-fpm.d/www.conf
#COPY .. /var/www
EXPOSE 9000

# composer
COPY --from=composer /usr/bin/composer /usr/bin/composer

ENV COMPOSER_ALLOW_SUPERUSER 1
ENV COMPOSER_HOME /composer
ENV PATH /composer/vendor/bin:$PATH

WORKDIR /var/www/public

CMD ["php-fpm"]

