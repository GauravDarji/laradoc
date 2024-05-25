# Laravel Docker Setup

This repository contains the Docker setup for a Laravel application with the following services:

- PHP
- Nginx
- MySQL
- phpMyAdmin
- Adminer
- Redis

## Prerequisites

Make sure you have Docker and Docker Compose installed on your system.

## Getting Started

### First-Time Setup

1. Clone the repository and navigate to the project directory:

    ```sh
    git clone <repository-url> laradoc
    cd laradoc
    ```

2. Build and start the Docker containers:

    ```sh
    docker compose up -d --build
    ```

3. Set permissions for phpMyAdmin sessions:

    ```sh
    docker compose exec phpmyadmin chmod 777 /sessions
    ```

4. Access the PHP container:

    ```sh
    docker compose exec -it php bash
    ```

5. Inside the PHP container, set the necessary permissions for Laravel:

    ```sh
    chown -R www-data:www-data /var/www/storage /var/www/bootstrap/cache
    chmod -R 775 /var/www/storage /var/www/bootstrap/cache
    ```

6. Install Composer dependencies:

    ```sh
    composer install
    ```

### Subsequent Starts

To start the Docker containers after the initial setup, simply run:

```sh
docker compose up -d
```

## Accessing the Services
### Laravel Application

    URL: http://localhost

## Database

    phpMyAdmin: 8080
    Adminer   : 9090
    MySQL     : 3306

- Note: This setup is intended for development purposes only. For production use, please review and adjust the configurations as needed.