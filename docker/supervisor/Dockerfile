FROM php:8.1-cli

LABEL maintainer="contact@simon-micheneau.fr"

RUN apt-get update && apt-get upgrade -yqq

RUN apt-get update \
    &&  apt-get install -y --no-install-recommends \
        locales apt-utils git libicu-dev g++ libpng-dev libxml2-dev libzip-dev libonig-dev libxslt-dev unzip libpq-dev nodejs npm wget \
        apt-transport-https lsb-release ca-certificates supervisor

RUN echo "en_US.UTF-8 UTF-8" > /etc/locale.gen  \
    &&  echo "fr_FR.UTF-8 UTF-8" >> /etc/locale.gen \
    &&  locale-gen

ADD https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions /usr/local/bin/

RUN chmod +x /usr/local/bin/install-php-extensions && sync && \
    install-php-extensions amqp apcu bz2 dba \
    decimal excimer gd gettext \
    gmagick igbinary imap intl ldap memcache \
    memcached msgpack mysqli oauth opcache \
    pdo_mysql redis shmop smbclient snmp \
    tidy xdebug xlswriter xmldiff xsl zip

RUN install-php-extensions @composer

RUN curl -sS https://get.symfony.com/cli/installer | bash \
    &&  mv /root/.symfony/bin/symfony /usr/local/bin

RUN git config --global user.email "contact@simon-micheneau.fr" \
    && git config --global user.name "SimonDevelop"
