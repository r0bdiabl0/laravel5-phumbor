# DEPRECATED - Use r0bdiabl0/php-thumbor instead

> **This package has been replaced by [`r0bdiabl0/php-thumbor`](https://github.com/r0bdiabl0/php-thumbor).**
>
> The new package offers:
> - Zero dependencies (no longer requires 99designs/phumbor)
> - Works standalone OR with Laravel (Laravel is optional)
> - Modern PHP 8.2+ with strict types
> - Full Thumbor 7.7.7 support (AVIF, WebP, HEIC formats)
> - Laravel 10, 11, 12, and 13 support

## Migration

```bash
# Remove old package
composer remove r0bdiablo/laravel5-phumbor

# Install new package
composer require r0bdiabl0/php-thumbor
```

### Update your code:

```php
// Old
use R0bdiabl0\Laravel5Phumbor\Facades\Phumbor;

// New
use R0bdiabl0\Thumbor\Laravel\Facades\Thumbor;
```

### Update config:

- Old config file: `config/laravel5-phumbor.php`
- New config file: `config/thumbor.php`

Run `php artisan vendor:publish --tag=thumbor-config` after installing.

### Update .env:

```env
THUMBOR_SERVER=https://your-thumbor-server.com
THUMBOR_KEY=your-secret-key
```

The API methods (`url()`, `fitIn()`, `addFilter()`, etc.) remain the same.

---

# Original README (Legacy)

This Laravel package adds support for [the 99designs PHP interface](https://github.com/99designs/phumbor) to the [globocom Thumbor thumbnail service](https://github.com/globocom/thumbor).

It is compatible with Laravel 5+.

Requires PHP 7.1+.

## Installation

Simply run this command in your project root:

    composer require r0bdiablo/laravel5-phumbor

or require the package in your `composer.json` file:

    "r0bdiablo/laravel5-phumbor": "^1.0"

Run `composer install` to download the package and have the autoloader updated.

Once installed, register the service provider with your Laravel application. Update the `providers` section of `config/app.php`:

    'providers' = array(
    	// existing providers
    	R0bdiabl0\Laravel5Phumbor\Laravel5PhumborServiceProvider::class,
    );

and register the facade in the `aliases` section:

    'aliases' => array(
    	// existing aliases
    	'Phumbor'   => R0bdiabl0\Laravel5Phumbor\Facades\Phumbor::class,
    );

Now, publish the package's config file:

    php artisan vendor:publish

which will publish the default configuration file to `config/laravel5-phumbor.php`.

You should modify this file to reflect your Thumbor installation's URL and secret key.

## Usage

The `Phumbor` facade exposes the API from [the 99designs PHP interface](https://github.com/99designs/phumbor).

For example:

    Phumbor::url('http://images.example.com/llamas.jpg')
        ->fitIn(640, 480)
    	->addFilter('fill', 'green');

## License

Licensed under the MIT license. See <https://github.com/r0bdiablo/laravel5-phumbor/blob/master/LICENSE>
