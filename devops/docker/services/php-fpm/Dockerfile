FROM php:7.2-fpm

ENV WORKDIR_PROJECT $

RUN pecl install apcu

RUN echo "extension=apcu.so" > /usr/local/etc/php/conf.d/apcu.ini

RUN apt-get update \
    && docker-php-ext-install bcmath mbstring \
    && docker-php-ext-install pdo_mysql \
    && docker-php-ext-install pdo \
    && docker-php-ext-install opcache \
    && apt-get install -y libpq-dev \
    && apt-get install -y git \
    && pecl install xdebug \
    && docker-php-ext-enable xdebug

RUN apt-get install -y p7zip \
    p7zip-full \
    unace \
    zip \
    unzip \
    xz-utils \
    sharutils \
    uudeview \
    mpack \
    arj \
    cabextract \
    file-roller \
    && rm -rf /var/lib/apt/lists/*

# Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer


WORKDIR WORKDIR_PROJECT