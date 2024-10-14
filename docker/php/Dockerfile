FROM php:8.1-fpm

# Installer les extensions PHP nécessaires
RUN docker-php-ext-install pdo pdo_mysql

# Installer Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Définir le répertoire de travail
WORKDIR /var/www/symfony

# Installer les dépendances Symfony
COPY ../symfony/composer.json ../symfony/composer.lock ./
RUN composer install --no-dev --optimize-autoloader

# Copier le reste de l'application
COPY ../symfony ./

# Donner les permissions nécessaires
RUN chown -R www-data:www-data /var/www/symfony/var
