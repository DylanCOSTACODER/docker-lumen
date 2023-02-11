FROM php:8.2-fpm

# Set the working directory
WORKDIR .

# Copy the composer.json and composer.lock
COPY composer*.json ./

# Install the dependencies
RUN apt-get update && apt-get install -y \
    libpq-dev \
    libzip-dev \
    unzip \
    && docker-php-ext-install pdo pdo_pgsql zip \
    && rm -rf /var/lib/apt/lists/*

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

ENV PATH="/usr/local/bin:$PATH"

RUN composer install

# Copy the rest of the application's files
COPY . .

# Expose the port
EXPOSE 8000

# Start the application
CMD ["php", "artisan", "serve", "--host=0.0.0.0"]