FROM php:7.2-fpm

RUN apt-get update
RUN apt-get install -y autoconf pkg-config libssl-dev

RUN docker-php-ext-install mbstring mysqli pdo_mysql

RUN pecl install -o -f mongodb redis \
	&& rm -rf /tmp/phar \
	&& docker-php-ext-enable mongodb redis

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
	&& php composer-setup.php \
	&& php -r "unlink('composer-setup.php');" \
	&& mv composer.phar /usr/local/bin/composer
