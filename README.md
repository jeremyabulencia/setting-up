# Setting-Up a Laravel Environment
#### Download and Install PHP (Non Thread Safe)
```link
    https://windows.php.net/download/
```
#### Enabling pdo_mysql
```bash
    php -i | findstr "php.ini"
```
```bash
    $ php.exe -i | findstr "php.ini"
    Configuration File (php.ini) Path =>
    Loaded Configuration File => C:\php8\php.ini
```
`php.ini`
```comment
    uncomment
    ;extension=pdo_mysql
```
### Download and Install composer
```link
    https://getcomposer.org/download/
```

### Download and Install Docker
```link
    https://www.docker.com/get-started/
```

### Download and Install NodeJs
```link
    https://nodejs.org/en/download
```

## Running MySQL database using Docker
`docker-compose.yml`
```yml
    version: "3.9"
    services:
    mysql:
        image: mariadb:10.8.3
        # Uncomment below when on Mac M1
        # platform: linux/arm64/v8
        command: --default-authentication-plugin=mysql_native_password
        restart: always
        environment:
        MYSQL_ROOT_PASSWORD: root
        ports:
        - 3306:3306
    adminer:
        image: adminer
        restart: always
        ports:
        - 8080:8080

```
#### run docker service
```bash
    docker compose up
```

### Adding Mailpit
```yml
    mailpit:
        image: axllent/mailpit
        container_name: mailpit
        restart: always
        volumes:
        - ./data:/data
        ports:
        - 8025:8025
        - 1025:1025
        environment:
        MP_MAX_MESSAGES: 5000
        MP_DATA_FILE: /data/mailpit.db
        MP_SMTP_AUTH_ACCEPT_ANY: 1
        MP_SMTP_AUTH_ALLOW_INSECURE: 1
```