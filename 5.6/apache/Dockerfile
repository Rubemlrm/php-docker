FROM php:5.6-apache
LABEL Rubem Mota <rubemmota89@gmail.com>

#enable mcrypt iconv and gd extensions
RUN apt-get update && apt-get install -y \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libmcrypt-dev \
    libpq-dev \
    libpng-dev \
    && rm -rf /var/lib/apt/lists/* \
    && docker-php-ext-install -j$(nproc) iconv mcrypt \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd pdo_pgsql pdo pdo_mysql

RUN pecl install xdebug-2.5.0 \
    && docker-php-ext-enable xdebug
