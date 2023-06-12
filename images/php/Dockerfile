FROM php:8-fpm

RUN apt-get update && apt-get install -y \
	git \
	curl \
	libpng-dev \
	libonig-dev \
	libxml2-dev \
	zip \
	unzip \
	libpq-dev \
    libgd3 \
    libgd-dev

RUN apt-get clean && rm -rf /var/lib/apt/lists/*

RUN pecl install xdebug && docker-php-ext-enable xdebug;

RUN docker-php-ext-configure gd --with-freetype
RUN docker-php-ext-configure pgsql -with-pgsql=/usr/local/pgsql

RUN docker-php-ext-install pdo pdo_pgsql pgsql

RUN docker-php-ext-enable pdo_pgsql
RUN pecl install -o -f redis && rm -rf /tmp/pear && docker-php-ext-enable redis

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

WORKDIR /var/www
