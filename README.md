# Laravel Prod Tools

[![Latest Stable Version](http://poser.pugx.org/mohamedhk2/laravel-prod-tools/v)](https://packagist.org/packages/mohamedhk2/laravel-prod-tools)
[![Total Downloads](http://poser.pugx.org/mohamedhk2/laravel-prod-tools/downloads)](https://packagist.org/packages/mohamedhk2/laravel-prod-tools)
[![Latest Unstable Version](http://poser.pugx.org/mohamedhk2/laravel-prod-tools/v/unstable)](https://packagist.org/packages/mohamedhk2/laravel-prod-tools)
[![License](http://poser.pugx.org/mohamedhk2/laravel-prod-tools/license)](https://packagist.org/packages/mohamedhk2/laravel-prod-tools)

## Packages

1. [anhskohbo/no-captcha](https://packagist.org/packages/anhskohbo/no-captcha)
1. [cviebrock/eloquent-sluggable](https://packagist.org/packages/cviebrock/eloquent-sluggable)
1. [intervention/image](https://packagist.org/packages/intervention/image)
1. [jorenvanhocht/laravel-share](https://packagist.org/packages/jorenvanhocht/laravel-share)
1. [laravel/ui](https://packagist.org/packages/laravel/ui)
1. [mcamara/laravel-localization](https://packagist.org/packages/mcamara/laravel-localization)
1. [morningtrain/laravel-https](https://packagist.org/packages/morningtrain/laravel-https)
1. [redcenter/laravel-non-www-redirect](https://packagist.org/packages/redcenter/laravel-non-www-redirect)
1. [spatie/laravel-medialibrary](https://packagist.org/packages/spatie/laravel-medialibrary)
1. [spatie/laravel-translatable](https://packagist.org/packages/spatie/laravel-translatable)

## Install
The recommended way to install this is through composer:
```bash
composer require "mohamedhk2/laravel-prod-tools"
```
- **Laravel Force SSL**  
  - **Deploy** the config files:
  ``` bash
  $ php artisan vendor:publish
  ```
  - and **chose:**  
    `[ ] Provider: MorningTrain\Laravel\Https\LaravelHttpsServiceProvider`  
  - **Update** the following in your `.env`:
  ```dotenv
      USE_SSL=true
  ```
  - **Register the ForceSSL middleware as a global middleware in your `App\Http\Kernel` class:**  
  ``` php
  class Kernel extends HttpKernel
  {
      /**
       * The application's middleware stack.
       *
       * @var array
       */
      protected $middleware = [
          \MorningTrain\Laravel\Https\Http\Middleware\ForceSSL::class,
      ];
  }
  ```
- **Laravel non-WWW Redirect**  
Add the middleware class to your Kernel.php in App\Http:
```
    protected $middlewareGroups = [
        'web' => [
            ...
            \LaravelNonWwwRedirect\LaravelNonWwwRedirectMiddleware::class,
            ...
        ],
    ];
```
## License
The Laravel Prod Tools is open-sourced software licensed under the [MIT license](http://opensource.org/licenses/MIT)
