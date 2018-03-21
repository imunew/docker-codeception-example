FROM php:7-apache

ENV DEBIAN_FRONTEND noninteractive

RUN a2enmod rewrite

RUN apt-get update && apt-get install -y git zlib1g-dev libicu-dev g++ vim

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin --filename=composer

RUN docker-php-ext-configure intl
RUN docker-php-ext-install intl

ADD date.ini /usr/local/etc/php/conf.d/date.ini

ADD ./symfony-demo.conf /etc/apache2/sites-available/symfony-demo.conf
RUN a2ensite symfony-demo.conf
RUN a2dissite 000-default.conf

EXPOSE 80
