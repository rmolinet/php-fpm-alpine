FROM php:7.4-fpm-alpine

LABEL maintainer="rrmolinet@gmail.com"

ADD wkhtmltopdf /usr/bin/wkhtmltopdf
RUN chmod +x /usr/bin/wkhtmltopdf \
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
    libzip-dev \
    libxslt-dev \
    libmcrypt-dev \
    icu-dev \
    oniguruma-dev \
&& apk add --no-cache --virtual .persistent-deps \
    git \
	libjpeg \
    libpq \
    libldap \
    libxslt \
    libmcrypt \
    libzip \
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
&& pecl install mcrypt-1.0.3 \
&& docker-php-ext-enable mcrypt \
&& pecl install imagick \
&& docker-php-ext-enable imagick \
&& pecl install redis \
&& docker-php-ext-enable redis \

&& docker-php-ext-configure gd --with-freetype=/usr/include/ --with-jpeg=/usr/include/ \

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
    calendar \
    exif \
&& apk del .build-deps \
&& rm -rf /var/cache/apk/*

# bcmath bz2 calendar ctype curl dba dom enchant exif fileinfo filter ftp gd gettext gmp hash iconv imap interbase intl json ldap mbstring mcrypt mysqli oci8 odbc opcache pcntl pdo pdo_dblib pdo_firebird pdo_mysql pdo_oci pdo_odbc pdo_pgsql pdo_sqlite pgsql phar posix pspell readline recode reflection session shmop simplexml snmp soap sockets spl standard sysvmsg sysvsem sysvshm tidy tokenizer wddx xml xmlreader xmlrpc xmlwriter xsl zip
