FROM php:7.4.21-apache

# UPDATE APT
RUN apt-get update -y

# INSTALL EXTENSION DEPENDENCIES
RUN apt-get install -y libcurl3-dev && apt-get clean -y
RUN apt-get install -y libzip-dev
RUN apt-get install -y openssl

# INSTALL IMAGICK
RUN apt-get install -y --no-install-recommends libmagickwand-dev
RUN pecl install imagick
RUN docker-php-ext-enable imagick

# PHP EXTENSIONS
RUN docker-php-ext-configure zip
RUN docker-php-ext-install zip
RUN docker-php-ext-install curl
RUN docker-php-ext-install mysqli
RUN docker-php-ext-install gd
RUN docker-php-ext-install pdo
RUN docker-php-ext-install pdo_mysql
RUN docker-php-ext-install soap

#MEMCACHED PHP7
RUN apt-get install -y git
RUN apt-get install -y libmemcached-dev libmemcached11
RUN apt-get update && apt-get install --no-install-recommends -y memcached libmemcached-tools libzip-dev zlibc zlib1g \
    && git clone https://github.com/php-memcached-dev/php-memcached /usr/src/php/ext/memcached \
    && cd /usr/src/php/ext/memcached && git fetch && git checkout master \
    && docker-php-ext-configure memcached \
    && docker-php-ext-install memcached

# VIRTUAL HOSTS
COPY ./vhosts/legacy.localdev.conf /etc/apache2/sites-available/legacy.localdev.conf
COPY ./vhosts/staff.legacy.localdev.conf /etc/apache2/sites-available/staff.legacy.localdev.conf
COPY ./vhosts/portal.legacy.localdev.conf /etc/apache2/sites-available/portal.legacy.localdev.conf

# Maybe, maybe this is needed? I dunno.
#RUN echo "ServerName localhost" >> /etc/apache2/apache2.conf

RUN a2dissite 000-default
RUN a2ensite legacy.localdev
RUN a2ensite staff.legacy.localdev
RUN a2ensite portal.legacy.localdev

# APACHE SETUP
#WORKDIR /var/www/html
RUN a2enmod rewrite
RUN service apache2 restart
