## Test Cloud Native with Monolith Architecture

repository ini digunakan untuk peserta maggang DevOps Engineer. Soal / Quis dibagi jadi 3

1. Containerize web framework (docker)
2. Continues Integration (CI) (gitlab-ci)
3. Orchestration container system (kubernetes)
4. Kubernetes cluster administration

### Containerize web framework

Salah satu pilar Cloud Native adalah container, contohnya disini kita sudah develop aplikasi bisnis kemudian buat containernya dengan spesifikasi

- Web framework
    - PHP 8.1
    - Laravel 8
    - Node 16  (frontend laramix)

- Dependency
    - mysql 8.0

- OS package
    - git 
    - mysql-client
    - openssl
    - zip 

- php-extension
    - fileinfo 
    - exif 
    - pcntl 
    - bcmath 
    - gd 
    - mysqli 
    - pdo_mysql

Build script:

- Install dependency `composer install`
- Install frontend dependency `npm install`
- Build frontend `npm build production`

Run application:
- Copy `.env` file: `php -r "file_exists('.env') || copy('.env.example', '.env');"`
- Generate key: `php artisan package:discover --ansi && php artisan key:generate --ansi --force`
- Refresh config key: `php artisan optimize`

Task:
1. Buat `Dockerfile` untuk buat docker image
2. Buat `docker-compose.yaml` untuk mempermudah mejalankan container `webapps` dan dependency seperti `mysql` database dan lain-lain
3. Push ke docker registry (docker hub)