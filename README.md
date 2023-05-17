# Laravel Prod Tools

[![](http://poser.pugx.org/mohamedhk2/laravel-prod-tools/v)](https://packagist.org/packages/mohamedhk2/laravel-prod-tools)
[![Total Downloads](http://poser.pugx.org/mohamedhk2/laravel-prod-tools/downloads)](https://packagist.org/packages/mohamedhk2/laravel-prod-tools)
[![Latest Unstable Version](http://poser.pugx.org/mohamedhk2/laravel-prod-tools/v/unstable)](https://packagist.org/packages/mohamedhk2/laravel-prod-tools)
[![License](http://poser.pugx.org/mohamedhk2/laravel-prod-tools/license)](https://packagist.org/packages/mohamedhk2/laravel-prod-tools)

## Packages

|                                                                                                         |                                                                                                                                         |
|---------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| [anhskohbo/no-captcha](https://packagist.org/packages/anhskohbo/no-captcha)                             | ![](http://poser.pugx.org/anhskohbo/no-captcha/v) ![](http://poser.pugx.org/anhskohbo/no-captcha/downloads)                             |
| [cviebrock/eloquent-sluggable](https://packagist.org/packages/cviebrock/eloquent-sluggable)             | ![](http://poser.pugx.org/cviebrock/eloquent-sluggable/v) ![](http://poser.pugx.org/cviebrock/eloquent-sluggable/downloads)             |
| [ecrmnn/laravel-https](https://packagist.org/packages/ecrmnn/laravel-https)                             | ![](http://poser.pugx.org/ecrmnn/laravel-https/v) ![](http://poser.pugx.org/ecrmnn/laravel-https/downloads)                             |
| [intervention/image](https://packagist.org/packages/intervention/image)                                 | ![](http://poser.pugx.org/intervention/image/v) ![](http://poser.pugx.org/intervention/image/downloads)                                 |
| [jorenvanhocht/laravel-share](https://packagist.org/packages/jorenvanhocht/laravel-share)               | ![](http://poser.pugx.org/jorenvanhocht/laravel-share/v) ![](http://poser.pugx.org/jorenvanhocht/laravel-share/downloads)               |
| [laravel/ui](https://packagist.org/packages/laravel/ui)                                                 | ![](http://poser.pugx.org/laravel/ui/v) ![](http://poser.pugx.org/laravel/ui/downloads)                                                 |
| [mcamara/laravel-localization](https://packagist.org/packages/mcamara/laravel-localization)             | ![](http://poser.pugx.org/mcamara/laravel-localization/v) ![](http://poser.pugx.org/mcamara/laravel-localization/downloads)             |
| [morningtrain/laravel-https](https://packagist.org/packages/morningtrain/laravel-https)                 | ![](http://poser.pugx.org/morningtrain/laravel-https/v) ![](http://poser.pugx.org/morningtrain/laravel-https/downloads)                 |
| [redcenter/laravel-non-www-redirect](https://packagist.org/packages/redcenter/laravel-non-www-redirect) | ![](http://poser.pugx.org/redcenter/laravel-non-www-redirect/v) ![](http://poser.pugx.org/redcenter/laravel-non-www-redirect/downloads) |
| [spatie/laravel-medialibrary](https://packagist.org/packages/spatie/laravel-medialibrary)               | ![](http://poser.pugx.org/spatie/laravel-medialibrary/v) ![](http://poser.pugx.org/spatie/laravel-medialibrary/downloads)               |
| [spatie/laravel-translatable](https://packagist.org/packages/spatie/laravel-translatable)               | ![](http://poser.pugx.org/spatie/laravel-translatable/v) ![](http://poser.pugx.org/spatie/laravel-translatable/downloads)               |

#### Removed packages

| package                                                                                            | replaced by                                                                 | version     | reason                   |
|----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------|-------------|--------------------------|
| <del>[morningtrain/laravel-https](https://packagist.org/packages/morningtrain/laravel-https)</del> | [ecrmnn/laravel-https](https://packagist.org/packages/ecrmnn/laravel-https) | only v1.0.3 | Not support Laravel ^9.x |

## Install

The recommended way to install this is through composer:

```bash
composer require "mohamedhk2/laravel-prod-tools"
```

## Laravel Force SSL

### - using `ecrmnn/laravel-https`

- Add under ``providers`` in ``config/app.php``
  ```php
  /*
   * Package Service Providers...
   */
  \Ecrmnn\LaravelHttps\Providers\ServiceProvider::class,
  ```

- Add under ``$middleware`` in ``app/Http/Kernel.php``
  ```php
  \Ecrmnn\LaravelHttps\Http\Middleware\ForceHttps::class,
  ```

- **Update** the following in your `.env`:  
  :warning: *HTTPS will only be forced when ``env('HTTPS')`` is set to ``true``* :warning:
  ```dotenv
      HTTPS=true    # used by ecrmnn/laravel-https
      USE_SSL=false # used by morningtrain/laravel-https
  ```

### - using `morningtrain/laravel-https`

- **Deploy** the config file:

  ``` bash
  php artisan vendor:publish --provider="MorningTrain\Laravel\Https\LaravelHttpsServiceProvider"
  ``` 

- **Update** the following in your `.env`:

  ```dotenv
      USE_SSL=true # used by morningtrain/laravel-https
      HTTPS=false  # used by ecrmnn/laravel-https
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
          ...
          \MorningTrain\Laravel\Https\Http\Middleware\ForceSSL::class,
      ];
  }
  ```

## Laravel non-WWW Redirect

- Add the middleware class to your Kernel.php in App\Http:

  ``` php
      protected $middlewareGroups = [
          'web' => [
              ...
              \LaravelNonWwwRedirect\LaravelNonWwwRedirectMiddleware::class,
          ],
      ];
  ```

## License

The Laravel Prod Tools is open-sourced software licensed under the [MIT license](http://opensource.org/licenses/MIT)
