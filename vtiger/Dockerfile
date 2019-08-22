FROM alpine:3.10
LABEL maintainer='Nilesh <nilesh@cloudgeni.us>'

# Add basics first
RUN apk update && apk upgrade && apk add \
  bash \
  apache2 \
  php7-apache2 \
  curl \
  ca-certificates \
  openssl \
  openssh \
  git \
  php7 \
  php7-phar \
  php7-json \
  php7-iconv \
  php7-openssl \
  tzdata \
  openntpd \
  vim \
  mysql-client \
  tzdata

# Add Composer
RUN curl -sS https://getcomposer.org/installer | php && mv composer.phar /usr/local/bin/composer

# Setup apache and php
RUN apk add \
  php7-ftp \
  php7-xdebug \
  php7-mcrypt \
  php7-mbstring \
  php7-soap \
  php7-gmp \
  php7-pdo_odbc \
  php7-dom \
  php7-pdo \
  php7-zip \
  php7-mysqli \
  php7-sqlite3 \
  php7-pdo_pgsql \
  php7-bcmath \
  php7-gd \
  php7-odbc \
  php7-pdo_mysql \
  php7-pdo_sqlite \
  php7-gettext \
  php7-imap \
  php7-xml \
  php7-xmlreader \
  php7-xmlwriter \
  php7-tokenizer \
  php7-xmlrpc \
  php7-bz2 \
  php7-pdo_dblib \
  php7-curl \
  php7-ctype \
  php7-session \
  php7-redis \
  php7-exif \
  php7-intl \
  php7-fileinfo \
  php7-ldap \
  php7-apcu \
  php7-zlib \
  php7-simplexml

WORKDIR /var/www/localhost/htdocs

#COPY php.ini /usr/local/etc/php/
COPY php.ini /etc/php7/conf.d/50-setting.ini

# ENV VT_VERSION=7.1.0 \
#   VT_DOWNLOAD=http://sourceforge.net/projects/vtigercrm/files/vtiger%20CRM%207.1.0/Core%20Product/vtigercrm7.1.0.tar.gz \
#   COMPOSER_ALLOW_SUPERUSER=1 \
#   PATH=/root/.composer/vendor/bin:$PATH \
#   VT_ADMIN_USER='Nilesh' \
#   VT_ADMIN_PASSWORD='123' \
#   VT_ADMIN_EMAIL='nilesh@cloudgeni.us' \
#   VT_CURRENCY_NAME='USA, Dollars' \
#   MYSQL_HOST='mysql' \
#   MYSQL_DATABASE='vtiger'

# RUN rm -rf /var/www/localhost/htdocs/index.html
# COPY index.php /var/www/localhost/htdocs/index.php

# RUN rm -rf /var/www/localhost/htdocs/ && \
#   cd /var/www/localhost && \
#   wget https://phoenixnap.dl.sourceforge.net/project/vtigercrm/vtiger%20CRM%207.1.0/Core%20Product/vtigercrm7.1.0.tar.gz && \
#   tar xzf vtigercrm7.1.0.tar.gz --directory /var/www/localhost/ && \
#   chown -R apache:apache /var/www/localhost/vtigercrm && \
#   mv /var/www/localhost/vtigercrm /var/www/localhost/htdocs && \
#   rm vtigercrm7.1.0.tar.gz

ADD sourcecode /var/www/localhost/sourcecode
RUN rm -rf /var/www/localhost/htdocs/ && \
  chown -R apache:apache /var/www/localhost/sourcecode && \
  mv /var/www/localhost/sourcecode /var/www/localhost/htdocs

COPY vtiger-foreground /usr/local/bin/
RUN chmod +x /usr/local/bin/vtiger-foreground
CMD ["vtiger-foreground"]
