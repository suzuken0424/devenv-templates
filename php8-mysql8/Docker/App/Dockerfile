FROM php:8-apache

ADD php.ini /usr/local/etc/php/
ADD 000-default.conf /etc/apache2/sites-enabled/

RUN cd /usr/bin && curl -s http://getcomposer.org/installer | php && ln -s /usr/bin/composer.phar /usr/bin/composer

RUN apt update \
    && apt install -y \
    git \
    zip \
    unzip \
    vim \
    libpng-dev \
    libpq-dev \
    default-mysql-client \
    zlib1g-dev libpng-dev \
    && docker-php-ext-install pdo_mysql

RUN apt install -y nodejs npm
RUN npm install -g n
RUN n 16.17.0
RUN apt purge -y nodejs npm
RUN mv /etc/apache2/mods-available/rewrite.load /etc/apache2/mods-enabled
RUN /bin/sh -c a2enmod rewrite
