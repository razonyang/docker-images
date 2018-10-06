FROM php:7.2-fpm
MAINTAINER razonyang@gmail.com

ENV PHP_EXTRA_CONFIGURE_ARGS --enable-fpm --with-fpm-user=www-data --with-fpm-group=www-data --disable-cgi --enable-maintainer-zts

RUN apt-get update

# Supervisor
RUN apt-get install -y supervisor
COPY supervisord.conf /etc/supervisord.conf

# Cron
RUN apt-get install -y cron
COPY crontab /etc/crontab
RUN chmod 644 /etc/crontab
RUN crontab /etc/crontab

CMD ["/usr/bin/supervisord", "-c", "/etc/supervisord.conf"]
