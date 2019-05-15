FROM php:7.1-fpm-alpine

LABEL maintainer="rrmolinet@gmail.com"

ADD wkhtmltopdf /usr/bin/wkhtmltopdf
ADD composer-uci.phar /usr/local/bin/composer-uci

RUN chmod +x /usr/bin/wkhtmltopdf \
&& chmod +x /usr/local/bin/composer-uci \
&& curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \
&& apk update \
&& apk add --no-cache --virtual .build-deps \
    autoconf \
	file \
	g++ \
	make \
    libc-dev \
	pkgconf \
	libressl-dev \
	freetype-dev \
	libjpeg-turbo-dev \
	postgresql-dev \
	imagemagick-dev \
	openldap-dev \
	curl-dev \
	libxml2-dev \
	libpng-dev \
	zlib-dev \
	libxslt-dev \
	libmcrypt-dev \
	icu-dev \
&& apk add --no-cache --virtual .persistent-deps \
    git \
    #libpng \
    #libjpeg-turbo \
	libjpeg \
	libpq \
	libldap \
	libxslt \
	libmcrypt \
	icu \
	imagemagick \
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
&& pecl install mcrypt-1.0.0 \
&& docker-php-ext-enable mcrypt \
&& pecl install imagick \
&& docker-php-ext-enable imagick \
&& pecl install redis \
&& docker-php-ext-enable redis \

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
	json \
    opcache \
    mbstring \
    tokenizer \
    xml \
    xmlrpc \

&& apk del .build-deps \
&& rm -rf /var/cache/apk/*

# bcmath bz2 calendar ctype curl dba dom enchant exif fileinfo filter ftp gd gettext gmp hash iconv imap interbase intl json ldap mbstring mcrypt mysqli oci8 odbc opcache pcntl pdo pdo_dblib pdo_firebird pdo_mysql pdo_oci pdo_odbc pdo_pgsql pdo_sqlite pgsql phar posix pspell readline recode reflection session shmop simplexml snmp soap sockets spl standard sysvmsg sysvsem sysvshm tidy tokenizer wddx xml xmlreader xmlrpc xmlwriter xsl zip
