FROM php:fpm

WORKDIR /
RUN apt update && apt upgrade -y && \
	apt install -y  unzip libzip-dev libicu-dev && \
	apt clean && \
	docker-php-ext-install -j$(nproc) zip iconv intl mbstring pdo_mysql opcache && \
	pecl install xdebug && \
	docker-php-ext-enable xdebug

COPY php.ini /usr/local/etc/php/conf.d
COPY www.conf /usr/local/etc/php-fpm.d/www.conf
#COPY .. /var/www

EXPOSE 9000

CMD ["php-fpm"]
