FROM php:5-fpm
#FROM nexus.prod.uci.cu/php:5.6-apache

#COPY sources.list /etc/apt/sources.list

RUN apt-get update
#RUN apt-get upgrade -y
RUN apt-get install -y --force-yes \
	unzip \
	libssl-dev \
	libfreetype6-dev \
	libjpeg62-turbo-dev \
	libpq-dev \
	libzip-dev \
	libldap2-dev \
	libxslt-dev \
	libcurl4-openssl-dev \
	libmcrypt-dev \
	libicu-dev \
	wkhtmltopdf
	
RUN pecl install xdebug \
&& docker-php-ext-enable xdebug

RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
&& docker-php-ext-configure ldap --with-libdir=lib/x86_64-linux-gnu/

RUN docker-php-ext-install -j$(nproc) \
	pdo \
	pgsql \
	pdo_pgsql \
	soap \
	gd \
	bcmath \
	json \
	xsl \
	zip \
	ldap \
	intl \
	curl \
	mcrypt \
	json

RUN apt-get autoremove -y && apt-get clean all \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*



