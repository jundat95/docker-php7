FROM ubuntu:18.04

MAINTAINER Jundat95

RUN apt-get update \
    && apt-get install -y supervisor \
    && apt-get install -y nginx \
    && apt-get install -y php7.2-common php7.2-cli php7.2-fpm php7.2-opcache php7.2-gd php7.2-mysql php7.2-curl php7.2-intl php7.2-xsl php7.2-mbstring php7.2-zip php7.2-bcmath php7.2-soap \
    && apt-get install -y php-xdebug \
    && apt-get install -y vim

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

RUN mkdir -p /var/log/supervisor

ADD ./supervisord.conf /etc/supervisor/conf.d/supervisord.conf
ADD ./etc/php/xdebug.ini /etc/php/7.2/mods-available/xdebug.ini

RUN ln -sf /etc/php/7.2/mods-available/xdebug.ini /etc/php/7.2/cli/conf.d/20-xdebug.ini

WORKDIR /var/www/magento

CMD [ "/usr/bin/supervisord" ]