FROM php:fpm-alpine

LABEL maintainer="macias@uci.cu, rmolinet@uci.cu"

ADD wkhtmltopdf /usr/bin/wkhtmltopdf

RUN chmod +x /usr/bin/wkhtmltopdf \
&& apk update \
&& apk add --no-cache --virtual .build-deps \
    autoconf \
	file \
	g++ \
	make \
    libc-dev \
	pkgconf \
	openssl-dev \
	curl-dev \
&& apk add --no-cache --virtual .persistent-deps \
	freetype-dev \
	libjpeg-turbo-dev \
	libpq \
	postgresql-dev \
	libldap \
	openldap-dev \
	libxslt-dev \
	libmcrypt-dev \
	icu-dev \
	libxml2-dev \
	libpng-dev \
	zlib-dev \
	libxrender \
	fontconfig \
	libx11 \
	libxext \
	libintl \
	glib \
	libgcc \
	libstdc++ \
	ttf-freefont \
	ttf-dejavu \
	ttf-droid \
	ttf-freefont \
	ttf-liberation \
	ttf-ubuntu-font-family \

&& pecl install xdebug \
&& docker-php-ext-enable xdebug \

&& docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \

&& docker-php-ext-install \
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

&& apk del .build-deps \
&& rm -rf /var/cache/apk/*
