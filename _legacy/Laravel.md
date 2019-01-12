## Installation

### Install with Composer

- **Create project**: `composer create-project --prefer-dist laravel/laravel project-name`

### Configure Vue HTML5 History Mode

- Configure router properties

  ```js
  export default new Router({
    mode: 'history',
    routes: [...]
  })
  ```

- Configure routes/web.php

  ```php
  Route::get('/', 'HomeController@index');
  Route::get('/{route}', 'HomeController@index')->where('route', '.*');

  # laravel 5.5+
  Route::view('/', 'home');
  Route::view('/{route}', 'home')->where('route', '.*');
  ```

## Command

- **Local Development Server**: `php artisan serve`
- **Defining Models**

  ```sh
  # Create an Eloquent model
  php artisan make:model Model

  # Generate a database migration
  php artisan make:model Model --migration
  # or
  php artisan make:model Model -m
  ```

- **Running Migrations**: `php artisan migrate`
- **Defining Controllers**: `php artisan make:controller ModelController`

## Link

- [**Laravel**](https://laravel.com/)
