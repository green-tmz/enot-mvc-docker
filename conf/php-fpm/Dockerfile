FROM php:8.1-fpm

WORKDIR /srv/www/enot

RUN apt-get update && apt-get install -y \
    build-essential \
    libpng-dev \
    libjpeg62-turbo-dev \
    libfreetype6-dev \
    locales \
    zip \
    htop \
    jpegoptim optipng pngquant gifsicle \
    vim \
    unzip \
    git \ 
    curl \
    libpq-dev \
    libonig-dev libzip-dev mc libxml2-dev libcurl4-openssl-dev pkg-config

RUN apt-get clean && rm -rf /var/lib/apt/lists/*

RUN docker-php-ext-install pgsql mysqli pdo_mysql pdo_pgsql iconv mbstring opcache zip exif pcntl xml curl
RUN docker-php-ext-configure gd
RUN docker-php-ext-install gd

RUN groupadd -g 1000 www
RUN useradd -u 1000 -ms /bin/bash -g www www

COPY --chown=www:www . /srv/www

USER www

CMD ["php-fpm"]