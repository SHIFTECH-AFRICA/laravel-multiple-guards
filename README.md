# <p align="center"><a href="https://github.com/SHIFTECH-AFRICA" target="_blank"><img width="400" src="https://github.com/SHIFTECH-AFRICA/avatars/blob/main/Secure.png?raw=true"></a></p>

<p align="center">
  <b>Big Things, Start Small</b><br>
  <a href="https://github.com/SHIFTECH-AFRICA/laravel-multiple-guards/issues">
  <img src="https://img.shields.io/github/issues/SHIFTECH-AFRICA/laravel-multiple-guards.svg">
  </a>
  <a href="https://github.com/SHIFTECH-AFRICA/laravel-multiple-guards/network/members">
  <img src="https://img.shields.io/github/forks/SHIFTECH-AFRICA/laravel-multiple-guards.svg">
  </a>
  <a href="https://github.com/SHIFTECH-AFRICA/laravel-multiple-guards/stargazers">
  <img src="https://img.shields.io/github/stars/SHIFTECH-AFRICA/laravel-multiple-guards.svg">
  </a>
  <a href="https://packagist.org/packages/shiftechafrica/laravel-multiple-guards">
  <img src="https://poser.pugx.org/shiftechafrica/laravel-multiple-guards/v/stable">
  </a>
  <a href="https://packagist.org/packages/shiftechafrica/laravel-multiple-guards">
  <img src="https://poser.pugx.org/shiftechafrica/laravel-multiple-guards/downloads">
  </a>
  <br><br>
  <img src="https://raw.githubusercontent.com/SHIFTECH-AFRICA/avatars/0d9c91fd61777ba4d79d7008e38729dc4ec410fd/laravel.min.svg">
</p>

## Introduction
This library helps one to handle multiple guards. Read through to understand how to use it.

## Installing

The recommended way to install laravel-multiple-guards is through
[Composer](http://getcomposer.org).

```bash
# Install package via composer
composer require shiftechafrica/laravel-multiple-guards
```

Next, run the Composer command to install the latest stable version of *shiftechafrica/laravel-multiple-guards*:

```bash
# Update package via composer
 composer update shiftechafrica/laravel-multiple-guards --lock
```

After installing, the package will be auto discovered, But if need you may run:

```php
# run for auto discovery <-- If the package is not detected automatically -->
composer dump-autoload
```

Then run this, to get the *config/laravel-multiple-guards.php* for your own configurations:

```php
# run this to get the configuration file at config/laravel-multiple-guards.php <-- read through it -->
php artisan vendor:publish --provider="LaravelMultipleGuards\LaravelMultipleGuardsServiceProvider"
```
A *config/laravel-multiple-guards.php* file will be created, follow the example below to define your guards.

```php
# set all the guards to use within the system
SYSTEM_GUARDS=admin,web
```

## Usage
Follow the steps below on how to use the laravel-multiple-guards:

#### How to use the Library
How to use the guards within your controller...

```php
class HomeController extends Controller
{
    use FindGuard;
    
        /**
         * Create a new controller instance.
         *
         * @return void
         */
        public function __construct()
        {
            $this->middleware($this->setGuardMiddleware()); //@todo this sets the middleware automatically i.e auth, auth:admin that you have defined in the config/auth.php
        }
    
        /**
         * Show the application dashboard.
         *
         * @return Renderable
         */
        public function index()
        {
            return view('home');
        }
    
        /**
         * get authenticated user
         */
        public function getUser()
        {
            return $this->findGuardType()->user();
        }
    
        /**
         * logout user
         * @return RedirectResponse
         */
        public function logout()
        {
            $this->findGuardType()->logout();
            return redirect()->route('login');
        }
}

/**
 * How to get the guard name
 * authorized
*/
 return $this->findGuardType(true); //@todo this returns the guard name i.e web , admin
```

## Version Guidance

| Version | Status     | Packagist           | Namespace    | Repo                                                                                     |
|---------|------------|---------------------|--------------|------------------------------------------------------------------------------------------|
| 1.x     | EOL     | `shiftechafrica/laravel-multiple-guards` | `LaravelMultipleGuards` | [v1.1.9](https://github.com/SHIFTECH-AFRICA/laravel-multiple-guards/releases/tag/v1.1.9) |
| 2.x     | Latest     | `shiftechafrica/laravel-multiple-guards` | `LaravelMultipleGuards` | [v2.0.1](https://github.com/SHIFTECH-AFRICA/laravel-multiple-guards/releases/tag/v2.0.1) |

[laravel-multiple-guards-repo]: https://github.com/SHIFTECH-AFRICA/laravel-multiple-guards.git

## Security Vulnerabilities
 For any security vulnerabilities, please email to [Support](mailto:bugs@shiftech.co.ke).
 
## License
 This package is open-source, licensed under the [MIT License](https://opensource.org/licenses/MIT).
