FROM php:8.1-fpm

RUN apt update \
    && apt install -y zlib1g-dev g++ git libicu-dev zip libzip-dev zip \
    && docker-php-ext-install intl opcache pdo pdo_mysql \
    && pecl install apcu \
    && docker-php-ext-enable apcu \
    && docker-php-ext-install zip \
    && docker-php-ext-configure zip

COPY php.ini $PHP_INI_DIR/conf.d/php.ini
COPY ./scripts/wait-for-it.sh /usr/bin/wait-for-it.sh
RUN chmod +x /usr/bin/wait-for-it.sh

# Change the default fpm port
#RUN sed -i 's/9000/9100/' /usr/local/etc/php-fpm.d/www.conf
#RUN echo 'listen = 127.0.0.1:9100' >> /usr/local/etc/php-fpm.d/docker.conf

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN curl -sS https://get.symfony.com/cli/installer | bash
RUN mv /root/.symfony/bin/symfony /usr/local/bin/symfony

WORKDIR /var/www/html/symfony5-app

RUN /usr/bin/wait-for-it.sh database_sym5:3306 -- echo "Database is set up";

CMD ["php-fpm"]
