[![Latest Stable Version](https://img.shields.io/packagist/v/walker-development/ldap-auth.svg?style=flat-square)](https://packagist.org/packages/walker-development/ldap-auth)
[![License](https://img.shields.io/packagist/l/walker-development/ldap-auth.svg?style=flat-square)](https://packagist.org/packages/walker-development/ldap-auth)

# ldap-auth

Very basic **READ ONLY** LDAP authentication driver for [Laravel 5.5+](http://laravel.com/)

Look [**HERE**](https://github.com/krenor/ldap-auth/tree/1.1.0) for the package for Laravel 5.1.
Look [**HERE**](https://github.com/krenor/ldap-auth/tree/master) for the package for Laravel 5.2.
However, only the 5.2 Version will be maintained.

## Installation

### Step 1: Install Through Composer

Add to your root composer.json and install with `composer install` or `composer update`

    {
      require: {
        "walker-development/ldap-auth": "~2.3"
      }
    }

or use `composer require walker-development/ldap-auth` in your console.

### Step 2: Add the Service Provider

Modify your `config/app.php` file and add the service provider to the providers array.

    WalkerDevelopment\LdapAuth\LdapAuthServiceProvider::class,

### Step 3: Publish the configuration file by running:

`php artisan vendor:publish`

Now you're all set!

## Configuration

### Step 1: Tweak the basic authentication


Update your `config/auth.php` to use **ldap** as authentication and the **LdapUser** Class.

```php
'guards' => [
  	'web' => [
  		'driver'   => 'session',
  		'provider' => 'ldap-users',
	],
],

'providers' => [
	'users'      => [
		'driver' => 'eloquent',
		'model'  => App\User::class,
	],

	'ldap-users' => [
		'driver' => 'ldap',
		'model'  => \WalkerDevelopment\LdapAuth\Objects\LdapUser::class,
	],
]
```


### Step 2: Adjust the LDAP config to your needs

If you have run `php artisan vendor:publish` you should see the
ldap.php file in your config directory. Adjust the values as you need them.
If your admin user has a different baseDN, include that option as admin_base_dn, otherwise it will use the base_dn set.

## Usage

### Authentication
Look up here for an [Example](https://github.com/WalkerDevelopment/ldap-auth/blob/master/EXAMPLE.md) or
Look up here for all [Guard methods](https://github.com/neoascetic/laravel-framework/blob/master/src/Illuminate/Auth/Guard.php) using `$this->auth`.


## Contributing

### Pull Requests

- **[PSR-2 Coding Standard](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md)**

- **Add tests** - Your patch won't be accepted if it doesn't have tests.

- **Document any changes** - Make sure the `README.md` and any other relevant documentation are kept up-to-date.

- **Create feature branches** - Use `git checkout -b my-new-feature`

- **One pull request per feature** - If you want to do more than one thing, send multiple pull requests.

- **Send coherent history** - Make sure each individual commit in your pull request is meaningful. If you had to make multiple intermediate commits while developing, please [squash them](http://www.git-scm.com/book/en/v2/Git-Tools-Rewriting-History#Changing-Multiple-Commit-Messages) before submitting.


## Licence

ldap-auth is distributed under the terms of the [MIT license](https://github.com/WalkerDevelopment/ldap-auth/blob/master/LICENSE.md)
