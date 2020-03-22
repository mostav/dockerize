# https://hub.docker.com/_/php?tab=tags
FROM php:7.4-alpine3.11

# Needed packages (apache2, php packages)
RUN apk add --update nano bash apache2 php7-apache2 php7-mbstring php7-pdo php7-pdo_mysql php7-json \
    php7-soap php7-zip php7-curl php7-mysqli php7-xml php7-session php7-gd  \
    && mkdir -p /run/apache2 \
    && rm -rf /tmp/* && rm -rf /var/cache/apk/* && rm -rf /run/apache2/*
    
# Install NodeJS 8.14
RUN apk add --no-cache --repository=http://dl-cdn.alpinelinux.org/alpine/v3.8/main/ nodejs=8.14.0-r0 npm

# setup your project
# ....

# Apache configuration & launch setup
COPY cfg/httpd.conf /etc/apache2/httpd.conf
COPY cfg/entrypoint.sh /opt/entrypoint.sh
RUN chmod +x /opt/entrypoint.sh

EXPOSE 80

# Launch httpd service
ENTRYPOINT [ "/opt/entrypoint.sh" ]