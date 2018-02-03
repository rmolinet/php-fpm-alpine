FROM php:7.1-fpm-alpine

LABEL maintainer="macias@uci.cu, rmolinet@uci.cu"

ADD wkhtmltopdf /usr/bin/wkhtmltopdf
ADD composer.phar /usr/local/bin/composer

RUN chmod +x /usr/bin/wkhtmltopdf \
&& chmod +x /usr/local/bin/composer \
&& apk update \
&& apk add --no-cache --virtual .build-deps \
    autoconf \
	file \
	g++ \
	make \
    libc-dev \
	pkgconf \
&& apk add --no-cache --virtual .persistent-deps \
	openssl-dev \
	curl-dev \
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
	mysqli \
	pdo_mysql \
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
    opcache \
    mbstring \
    tokenizer \
    xml \
    xmlreader \
    xmlrpc \
    xmlwriter\

&& apk del .build-deps \
&& rm -rf /var/cache/apk/*

# bcmath bz2 calendar ctype curl dba dom enchant exif fileinfo filter ftp gd gettext gmp hash iconv imap interbase intl json ldap mbstring mcrypt mysqli oci8 odbc opcache pcntl pdo pdo_dblib pdo_firebird pdo_mysql pdo_oci pdo_odbc pdo_pgsql pdo_sqlite pgsql phar posix pspell readline recode reflection session shmop simplexml snmp soap sockets spl standard sysvmsg sysvsem sysvshm tidy tokenizer wddx xml xmlreader xmlrpc xmlwriter xsl zip