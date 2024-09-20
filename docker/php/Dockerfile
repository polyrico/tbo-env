FROM php:8.1-fpm

# Necessary dependencies
RUN apt-get update && pecl install apcu uploadprogress xdebug && apt-get install -y \
    build-essential \
    libzip-dev \
    libpng-dev \
    libjpeg62-turbo-dev \
    libfreetype6-dev \
    libonig-dev \
    locales \
    zip \
    jpegoptim optipng pngquant gifsicle \
    vim \
    git \
    curl

# Necessary PHP extentions
RUN docker-php-ext-install pdo_mysql zip exif pcntl bcmath calendar
RUN docker-php-ext-configure gd --with-freetype --with-jpeg
RUN docker-php-ext-install gd
RUN docker-php-ext-enable apcu uploadprogress
RUN docker-php-ext-enable xdebug

# Dependency manager
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Expose the ports
EXPOSE 9000

# Define the workdir
WORKDIR /var/www

# Execute the php-fpm command
CMD ["php-fpm"]
