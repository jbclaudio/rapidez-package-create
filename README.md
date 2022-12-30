# Rapidez Package Create
This package adds a command to easily generate packages for Rapidez and install them using composer.
This is taken from [indykoning/laravel-module-create](https://github.com/indykoning/laravel-module-create) and further developed especially for Rapidez packages. Credits go to https://github.com/indykoning 🚀

## Installation
Simply install the package using composer:
`composer require rapidez/package-create --dev`

Since this package uses composer to install and autoload the created packages, this package can be removed while still keeping created packages functional.

## Usage
`php artisan rapidez:package:create {package} {--json-vendor=} {--json-package=} {--stub=}`

if json-vendor and json-package are not defined, we will make assumptions based on the vendor and package name

The possible values of stub are:
 - default (the VERY basics of what you need for an install)

## Configuration
If you wish to change the folder where the new packages will be installed to you can publish the config:
```
php artisan vendor:publish --provider="Rapidez\PackageCreate\PackageCreateServiceProvider" --tag="config"
```

and change the `package-folder`

NOTE: `package-folder` is assumed to be relative from the Rapidez installation, so do not attempt to use an absolute path. Subfolders are fine though.

## Internals
1. We very simply create the required folders for the vendor and package name
2. Then we add the repository path to the composer.json
3. Then we install the repository from that path
4. Rapidez should now auto discover your newly created package and you can get to work
