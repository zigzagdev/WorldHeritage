FROM php:7.3.12-fpm

# install library
RUN apt-get update --fix-missing
RUN apt-get install -y curl
RUN apt-get install -y build-essential libssl-dev zlib1g-dev libpng-dev libjpeg-dev libfreetype6-dev zip unzip vim less

RUN apt-get update && apt-get install libmagickwand-dev -y --no-install-recommends \
    && pecl install imagick-3.4.3 \
    && docker-php-ext-enable imagick \
    && apt-get install -y libzip-dev \
    && docker-php-ext-install zip

RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install gd

RUN docker-php-ext-install pdo pdo_mysql mysqli bcmath exif

RUN apt-get install -y nodejs npm && npm install n -g && n 14.15.3


# install composer
RUN cd /usr/bin && curl -s http://getcomposer.org/installer | php && ln -s /usr/bin/composer.phar /usr/bin/composer



#composer create-project --prefer-dist "laravel/laravel=8.*" .
#install project



#node install error fix
#curl -sL https://deb.nodesource.com/setup_15.x | bash -
#apt-get update
#apt-get install nodejs
#apt autoremove