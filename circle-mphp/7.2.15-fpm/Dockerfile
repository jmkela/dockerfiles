###
### UKKO.com PHP CircleCI Docker test container
###

FROM circleci/php:7.2.15-fpm-stretch-node-browsers

# Install AWS CLI
RUN apt install -y awscli

# Install common extensions
RUN apt install -y libxslt1-dev mysql-client libicu-dev zlib1g-dev libzip-dev
RUN docker-php-ext-configure intl && docker-php-ext-install intl
RUN docker-php-ext-install zip
RUN docker-php-ext-install bcmath
RUN docker-php-ext-install mbstring
RUN docker-php-ext-install pdo pdo_mysql
RUN docker-php-ext-install xsl
RUN docker-php-ext-enable bcmath

USER circleci

CMD ["/bin/sh"]

