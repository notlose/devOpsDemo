FROM ubuntu:16.04

RUN apt-get update && \
    apt-get dist-upgrade -y && \
    apt-get install -y \
      apache2 \
      php7.0 \
      php7.0-cli \
      libapache2-mod-php7.0 \
      php7.0-gd \
      php7.0-json \
      php7.0-mbstring \
      php7.0-mysql \
      curl

RUN /usr/sbin/a2enmod rewrite

ADD laravel.conf /etc/apache2/sites-available/
RUN /usr/sbin/a2dissite '*' && /usr/sbin/a2ensite laravel

RUN /usr/bin/curl -sS https://getcomposer.org/installer |php
RUN /bin/mv composer.phar /usr/local/bin/composer

EXPOSE 80
EXPOSE 443


CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]