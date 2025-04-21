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

# Set proper permissions for the web server
RUN chown -R www-data:www-data /var/www/html \
    && chmod -R 777 /var/www/html

# Download the code from GitHub (or use your local files)
RUN curl -L https://github.com/MobileJC/infs3202_MJC/archive/refs/heads/main.zip -o infs3202_MJC-main.zip \
    && unzip infs3202_MJC-main.zip \
    && mv infs3202_MJC-main/* . \
    && rm -rf infs3202_MJC-main.zip infs3202_MJC-main \
    && cp -r  assets /var/www/html/public/assets  #Copy assets to public folder

# Copy custom Apache config
COPY 000-default.conf /etc/apache2/sites-available/000-default.conf

# Enable Apache mod_rewrite (required for CodeIgniter)
RUN a2enmod rewrite

RUN chmod -R 777 /var/www/html \
    && chmod -R 777 /var/www/html/writable \
    && chmod -R 777 /var/www/html/writable/cache \
    && chmod -R 777 /var/www/html/assets \
    && chmod -R 777 /var/www/html/public/assets

# Expose port 80
EXPOSE 80

# Add a health check to monitor the application
HEALTHCHECK --interval=30s --timeout=10s --start-period=5s --retries=3 \
    CMD curl -f http://localhost/login || exit 1

# Start Apache in the foreground
CMD ["apache2-foreground"]
