FROM php:5.6-apache

MAINTAINER Davi dos Santos <davi646@gmail.com>

WORKDIR /var/www

RUN apt-get update -y \
  && apt-get install -y libxml2-dev libpng-dev libcurl4-openssl-dev\
  && apt-get clean -y \
  && docker-php-ext-configure curl \
  && docker-php-ext-install soap zip gd curl

RUN php -r "readfile('http://getcomposer.org/installer');" | php -- --install-dir=/usr/bin/ --filename=composer

RUN apt-get update \
        && apt-get install -y --no-install-recommends gnupg \
        && curl -sL https://deb.nodesource.com/setup_6.x | bash - \
        && apt-get install -y nodejs \
        && npm install -g grunt-cli

COPY apache_default /etc/apache2/sites-available/000-default.conf
RUN usermod -u 1000 www-data

COPY run /usr/local/bin/run
RUN chmod +x /usr/local/bin/run
RUN a2enmod rewrite

EXPOSE 80
CMD ["/usr/local/bin/run"]
