#Dockerize php project
#phpunit --verbose ornek1.php
#RUN curl <file_download_url> -O <copy_directory> \
#&& unzip <copy_directory>/<filename>.zip -d <copy_directory> \
#&& rm <copy_directory>/<filename>.zip

#RUN \
#apt-get update && \
#apt-get install unzip wget -y

FROM php:8.2.0beta3-apache
RUN a2enmod rewrite
RUN apt-get update \
  && apt-get install -y libzip-dev git wget --no-install-recommends \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN docker-php-ext-install pdo mysqli pdo_mysql zip;

RUN wget https://getcomposer.org/download/2.4.1/composer.phar \
    && mv composer.phar /usr/bin/composer && chmod +x /usr/bin/composer

#I copied the Apache configuration file to the appropriate place in the container, and our project files>
COPY ./apache.conf /etc/apache2/sites-enabled/000-default.conf
COPY ./entrypoint.sh /entrypoint.sh
COPY ./data/demo-2.0.2 /var/www

WORKDIR /var/www
#RUN composer update
#RUN composer install
RUN chmod +x /entrypoint.sh

RUN chown -R www-data:www-data /var/www
CMD ["apache2-foreground"]

ENTRYPOINT ["/entrypoint.sh"]


