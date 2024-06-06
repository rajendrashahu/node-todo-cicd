FROM php:8.3.2-fpm

# Update package lists and install required dependencies
RUN apt-get update && \
    apt-get install -y \
        libpng-dev \
        libjpeg-dev \
        libfreetype6-dev \
        zlib1g-dev \
        libzip-dev \
        libxml2-dev \
        libmagickwand-6.q16-dev --no-install-recommends

# Install GD extension
RUN docker-php-ext-configure gd --with-freetype --with-jpeg && \
    docker-php-ext-install -j$(nproc) gd

# Additional PHP extensions
RUN docker-php-ext-install mysqli pdo pdo_mysql zip

# Install Git
RUN apt-get install -y git

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Expose port
EXPOSE 81