FROM ubuntu:16.04
MAINTAINER Davi dos Santos <davi646@gmail.com>

VOLUME ["/var/www"]

RUN apt-get update && apt-get install -y --no-install-recommends \
		apache2 \
		software-properties-common \
		git \
	&& apt-get clean \
	&& rm -fr /var/lib/apt/lists/*

RUN LC_ALL=C.UTF-8 add-apt-repository ppa:ondrej/php

RUN apt-get update && apt-get install -y --no-install-recommends \
		libapache2-mod-php7.2 \
		php7.2 \
		php7.2-cli \
		php7.2-curl \
		php7.2-dev \
		php7.2-gd \
		php7.2-imap \
		php7.2-mbstring \
		php7.2-zip \
		php7.2-mysql \
		php7.2-pgsql \
		php7.2-pspell \
		php7.2-xml \
		php7.2-xmlrpc \
		php-apcu \
		php-memcached \
		php-pear \
		php-redis \
	&& apt-get clean \
	&& rm -fr /var/lib/apt/lists/*

RUN php -r "readfile('http://getcomposer.org/installer');" | php -- --install-dir=/usr/bin/ --filename=composer

RUN apt-get update && apt-get install -y xvfb libfontconfig wkhtmltopdf

RUN a2enmod rewrite

EXPOSE 80

COPY apache_default /etc/apache2/sites-available/000-default.conf
COPY run /usr/local/bin/run
RUN chmod +x /usr/local/bin/run
RUN a2enmod rewrite

EXPOSE 80
CMD ["/usr/local/bin/run"]
