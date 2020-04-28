FROM debian:10

ARG APACHE_UID
ARG APACHE_GID

EXPOSE 80

RUN apt -y update
RUN apt -y upgrade
RUN apt -y install apache2

RUN usermod -u $APACHE_UID www-data
RUN groupmod -g $APACHE_GID www-data

RUN a2enmod rewrite
RUN a2enmod proxy
RUN a2enmod proxy_http
RUN a2enmod proxy_fcgi

RUN a2dissite 000-default

COPY ./drupal.conf /etc/apache2/sites-enabled/

ENTRYPOINT ["/usr/sbin/apachectl"]
CMD ["-D", "FOREGROUND"]