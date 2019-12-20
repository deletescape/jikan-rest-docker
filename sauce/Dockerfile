FROM php:7.3.11-apache-buster

ENV COMPOSER_ALLOW_SUPERUSER 1

RUN apt-get update && apt-get install -y \
    openssl \
    git \
    unzip \
    redis-tools \
 && curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \
 && composer --version \
 && a2enmod rewrite \
 && service apache2 restart \
 && git clone https://github.com/deletescape/jikan-rest.git . \
 && git checkout ad685f735322e3a60c6908425a68c1c1a08f8bb7 \
 && composer install --prefer-dist --no-progress --no-suggest --classmap-authoritative  --no-interaction

ADD .env /run-jikan.sh ./

ENTRYPOINT ["./run-jikan.sh"]