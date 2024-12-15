FROM php:8.3-fpm-alpine

WORKDIR /tmp

RUN apk add wget git iputils-ping net-tools vim nano nodejs npm figlet

# Install additional packages
RUN apk --no-cache add \
    supervisor \
    && docker-php-ext-enable opcache

# installing required extensions
RUN apk add bash build-base gcc autoconf libmcrypt-dev libzip-dev zip  g++ make openssl-dev

RUN docker-php-ext-install mysqli pdo pdo_mysql

# Install Composer 2.5
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer --version=2.5.5

COPY ../laravel /opt/html

WORKDIR /opt/html

#RUN composer install

#RUN npm install

#RUN npm install -dev typescript@5.6.3

#RUN npm install -dev vue-tsc@2.1.10

#RUN npm run dev
CMD ["php-fpm"]

EXPOSE 8000
EXPOSE 9000
EXPOSE 5173