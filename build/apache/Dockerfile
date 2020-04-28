# Az image alapja debian 10
FROM debian:10

# Argumentumok beállítása, hogy ezen a UID és GID-n fusson az Apache
ARG APACHE_UID
ARG APACHE_GID

# 80-as port kinyitása
EXPOSE 80

# Apache2 szerver telepítése
RUN apt -y update
RUN apt -y upgrade
RUN apt -y install apache2

# www-data user (Apache user) GID és UID beállítása az argumentumok alapján
RUN usermod -u $APACHE_UID www-data
RUN groupmod -g $APACHE_GID www-data

# Rewrite (Drupalkoz) és proxy (PHP-FPM-hez) bekapcsolása
RUN a2enmod rewrite
RUN a2enmod proxy
RUN a2enmod proxy_http
RUN a2enmod proxy_fcgi

# Apache alapértelmezett virtualhost kikapcsolása
RUN a2dissite 000-default

# Egyedi virtualhost (Drupalhoz) bemásolása
COPY ./drupal.conf /etc/apache2/sites-enabled/

# Apache futtatása service-ként
ENTRYPOINT ["/usr/sbin/apachectl"]
CMD ["-D", "FOREGROUND"]