# Ahrmerd/TestGenerator

Ahrmerd/TestGenerator is a command-line tool for generating test files for Laravel models. It helps you quickly generate feature tests for your Eloquent models to facilitate automated testing in your Laravel application.

## Features

- Generate test files for individual models or all models in your Laravel application
- Automatically generate test methods for common CRUD operations (create, read, update, delete)
- Provides a template for writing custom test methods for additional testing scenarios
- Automatically generates test file names based on the model name
- Supports Laravel Form Request classes for extracting validation rules
- Option to overwrite existing test files with a `--force` flag

## Installation

You can install Ahrmerd/TestGenerator via Composer using the following command:

```sh 
composer require ahrmerd/laravel-test-generator --dev
```
the tests generated by the package requires the Pest's Laravel plugin to work. To start using Pest's Laravel plugin, you need to require this plugin via Composer.
```sh 
composer require pestphp/pest-plugin-laravel --dev 
```

Once installed, run the following Artisan command to publish the configuration file:
```sh
php artisan vendor:publish --tag=TestGenerator-config 
```

## Compatibility
This package is compatible with Laravel 10 and above.
## Configuration
You can configure the behavior of the TestGenerator package using the laravel-TestGenerator.php config file. Here are the available options:
### - ignore_models
An array of models that should be ignored when generating tests when --all option is passed. Models listed in this array will not have tests generated for them. by default, it ignores creating test test for the user model. For example:
```php 
    'ignore_models' => [
        'User', 'Post'
    ],
```
### default
The default type of tests to generate. You can specify either 'api', 'web', 'both', or null (default). If set to 'api', only API tests will be generated by default. If set to 'web', only web tests will be generated by default. If set to 'both', both API and web tests will be generated by default.
## Usage

Once installed, you can use Ahrmerd/TestGenerator via the command-line interface (CLI). Here are some examples:

### - Generate tests for a specific model:

```sh
 php artisan generate:tests ModelName
```

This command will generate test files for the ModelName model in your Laravel application. The test files will contain test methods for common CRUD operations such as create, read, update, and delete, based on the --api or --web options provided (default is --api). You can also add custom test methods in the generated test files.

### - Generate tests for all models:
```sh 
php artisan generate:tests --all
```
This command will generate test files for all models in your Laravel application. Each test file will contain test methods for common CRUD operations, based on the --api or --web options provided (default is --api), as well as a template for writing custom test methods for additional testing scenarios.

### - Overwrite existing test files:
```sh 
php artisan generate:tests ModelName --force
```
By default, Ahrmerd/TestGenerator will not overwrite existing test files. However, you can use the --force flag to overwrite existing test files if needed. Please use this option with caution, as it will overwrite any existing test files for the specified model.

### - Specify type of tests to generate:
```sh
php artisan generate:tests ModelName --api
```
This command will generate test files for the ModelName model with test methods specifically for testing API routes and functionality. You can also use the --web option to generate test methods for testing web routes and functionality (default will generate for both api and web).

## Note: 
-You can use any combination of options (--api, --web, --force) to customize the generated test files as per your requirements.
-You can customize the generated test methods or add your own custom test methods in the generated test files to suit your specific testing needs.
-Pest PHP is required for the generated tests to work. Make sure you have Pest PHP installed and configured in your Laravel project before running the generate:tests command
## Contributing

Contributions to Ahrmerd/TestGenerator are welcome! If you would like to contribute, please follow the standard GitHub Fork & Pull Request workflow.

