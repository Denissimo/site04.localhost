FROM php:8.1-fpm

RUN apt-get update && apt-get install -y \
	git \
	curl \
	libpng-dev \
	libonig-dev \
	libxml2-dev \
	zip \
	unzip \
	libpq-dev

RUN apt-get clean && rm -rf /var/lib/apt/lists/*

#RUN pecl install xdebug && docker-php-ext-enable xdebug;

RUN docker-php-ext-install pdo_pgsql exif pcntl bcmath gd

WORKDIR /var/www