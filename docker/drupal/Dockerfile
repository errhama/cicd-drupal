# Use the official PHP image with Apache
# Use the latest Ubuntu image
FROM ubuntu:latest

# Set environment variables to non-interactive (avoid prompts during installation)
ENV DEBIAN_FRONTEND=noninteractive

# Update package list and install necessary packages
RUN apt-get update && \
    apt-get install -y \
    apache2 \
    php \
    php-gd \
    php-mysql \
    php-xml \
    php-mbstring \
    curl \
    vim \
    git \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

    # Set the working directory
WORKDIR /var/www/html

# Copy the local code to the container
COPY ../  /var/www/html

# Enable Apache mod_rewrite (useful for Drupal)
RUN a2enmod rewrite

# Copy Apache configuration file (if needed, you can create a custom Apache configuration file)
# COPY apache2.conf /etc/apache2/apache2.conf

# Expose port 80
EXPOSE 80

# Start Apache in the foreground
CMD ["apache2ctl", "-D", "FOREGROUND"]


