FROM php:8.2-apache
MAINTAINER stuart reeves
#RUN a2enmod rewrite
#RUN sed -i 's/AllowOverride None/AllowOverride FileInfo/' /etc/apache2/apache2.conf
RUN docker-php-ext-install pdo pdo_mysql mysqli

