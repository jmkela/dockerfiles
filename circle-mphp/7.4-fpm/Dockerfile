###
### UKKO.com PHP CircleCI Docker test container
###

FROM circleci/php:7.4-fpm-buster-node-browsers

USER root

# Install AWS CLI
RUN apt-get -y install awscli

# Install common extensions
RUN apt-get -y install mariadb-client-10.3 \
    libxslt1-dev libicu-dev zlib1g-dev libzip-dev \
    libpng-dev libjpeg-dev
RUN wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -
RUN echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb stable main" >> /etc/apt/sources.list.d/google.list
RUN apt-get update
RUN apt-get --only-upgrade install google-chrome-stable
RUN pecl install pcov
RUN rm /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini
RUN docker-php-ext-configure intl && docker-php-ext-install intl
RUN docker-php-ext-install json xml calendar
RUN docker-php-ext-configure gd --with-gd --with-png-dir=/usr/include/ --with-jpeg-dir=/usr/include/
RUN docker-php-ext-install gd
RUN docker-php-ext-install zip
RUN docker-php-ext-install bcmath
RUN docker-php-ext-install mbstring
RUN docker-php-ext-install pdo pdo_mysql
RUN docker-php-ext-install xsl
RUN docker-php-ext-install soap
RUN docker-php-ext-enable bcmath gd
RUN docker-php-ext-enable pcov

USER circleci

CMD ["/bin/sh"]

