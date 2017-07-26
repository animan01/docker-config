FROM php:7-apache
COPY php.ini /usr/local/etc/php/
RUN adduser user
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN apt-get update
RUN apt-get install git -y
RUN apt-get install -y \
  mysql-client \
	libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng12-dev \
	libmcrypt-dev \
    && docker-php-ext-install -j$(nproc) mcrypt pdo pdo_mysql opcache \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd
