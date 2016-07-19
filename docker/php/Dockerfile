FROM php:5.6-apache

ENV DEBIAN_FRONTEND noninteractive

RUN a2enmod rewrite

RUN apt-get update && apt-get install -y git zlib1g-dev libicu-dev g++ vim

RUN docker-php-ext-configure intl
RUN docker-php-ext-install intl

RUN mkdir -p /var/www/symfony.demo
WORKDIR /var/www/symfony.demo

RUN usermod -u 1000 www-data

ADD date.ini /usr/local/etc/php/conf.d/date.ini
ADD vhosts.conf /etc/apache2/sites-enabled/vhosts.conf

EXPOSE 80
