# Use an official PHP image with Apache
FROM php:7.4-apache

# Install required libraries and dependencies
RUN apt-get update && apt-get install -y \
    curl \
    unzip \
    libicu-dev \
    && docker-php-ext-install mysqli \
    && docker-php-ext-configure intl \
    && docker-php-ext-install intl

# Set the working directory to /var/www/html
WORKDIR /var/www/html

# Download the code from GitHub
RUN curl -L https://github.com/MobileJC/infs3202_MJC/archive/refs/heads/docker.zip -o infs3202_MJC-docker.zip \
    && unzip infs3202_MJC-docker.zip \
    && mv infs3202_MJC-docker/* . \
    && rm -rf infs3202_MJC-docker.zip infs3202_MJC-docker

# Set proper permissions for the web server
RUN chown -R www-data:www-data /var/www/html \
    && chmod -R 777 /var/www/html

# Set the document root to the public directory
RUN sed -i 's|/var/www/html|/var/www/html/public|' /etc/apache2/sites-available/000-default.conf

# Enable Apache mod_rewrite (required for CodeIgniter)
RUN a2enmod rewrite

# Expose port 80 and 8080
EXPOSE 80 8080

# Start Apache in the foreground
CMD ["apache2-foreground"]

