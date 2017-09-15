FROM php:5-fpm

LABEL maintainer="macias@uci.cu, rmolinet@uci.cu"

ADD wkhtmltopdf /usr/bin/wkhtmltopdf

RUN chmod +x /usr/bin/wkhtmltopdf \
&& apt-get update \
&& apt-get install -y --force-yes --no-install-recommends \
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
	libxrender1 \
	libfontconfig1 \
	
&& pecl install xdebug \
&& docker-php-ext-enable xdebug \

&& docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
&& docker-php-ext-configure ldap --with-libdir=lib/x86_64-linux-gnu/ \

&& docker-php-ext-install -j$(nproc) \
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
	json \

&& apt-get autoremove -y \
&& apt-get clean all \
&& rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
