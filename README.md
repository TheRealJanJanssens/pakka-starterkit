<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400"></a></p>

<p align="center">
<a href="https://travis-ci.org/laravel/framework"><img src="https://travis-ci.org/laravel/framework.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/dt/laravel/framework" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/v/laravel/framework" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/l/laravel/framework" alt="License"></a>
</p>

## Install

```
cp .env.example .env

fill .env

composer install
npm install

php artisan key:generate 
php artisan pakka-install
```

## Autogit
When not using autogit remove /storage from .gitignore to save all files in the repo.

1. put everything in a www folder
2. Copy .autogit.yml in root
3. Put .env and /storage folder in /checkout/master/shared

## Bug Fixing
```
php artisan config:clear
php artisan cache:clear
php artisan view:clear
php artisan route:clear
composer dump-autoload
```

## Notes
Tfile Caching:
This method of caching has created alot of problems during the install of the pakka package. The main reason for causing these problems is the order the service providers are called. Pakka uses the auto discover to register itself but the tfile package doesn't and get manually called withing config/app.php. Auto discover packages are registered before any manual registered service providers causing the tfile package being called after the Pakka package. This resulted in Pakka not knowing tfile driver existed. The solution for this is forcing the pakka package to manually load in app.php behind the tfile package using the 'dont-discover' feature in the main composer file. Might be changed in the future to clean up the code and composer file.