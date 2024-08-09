# Use the latest Ubuntu image
FROM ubuntu:latest

# Set environment variables to non-interactive (avoid prompts during installation)
ENV DEBIAN_FRONTEND=noninteractive

# Install systemd and other necessary packages
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
    systemd \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Create necessary directories for systemd
RUN mkdir -p /run/systemd && \
    mkdir -p /run/systemd/journal

# Set the working directory
WORKDIR /var/www/html

# Copy the local code to the container
COPY ../  /var/www/html

# Enable Apache mod_rewrite (useful for Drupal)
RUN a2enmod rewrite

# Expose port 80
EXPOSE 80

# Start systemd as the init system
CMD ["/lib/systemd/systemd"]
