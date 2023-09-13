# PDF version converter 
PHP library for converting the version of PDF files (for compatibility purposes).

## Requirements

- PHP 5.3+
- Ghostscript (gs command on Linux)

## Installation

Run `composer require imaginativeimpact/pdf-version-converter dev-master` or add the follow lines to your composer.json and run `composer install`:

```
{
    "require": {
        "imaginativeimpact/pdf-version-converter": "^2.0"
    }
}
```

## Usage

Guessing a version of PDF File:

```php
<?php

// import the composer autoloader
require_once __DIR__.'/vendor/autoload.php'; 

// import the namespaces
use ImaginativeImpact\PDFVersionConverter\Guesser\RegexGuesser;
// [..]

$guesser = new RegexGuesser();
echo $guesser->guess('/path/to/my/file.pdf'); // will print something like '1.4'
```

Converting file to a new PDF version:

```php
<?php

// import the composer autoloader
require_once __DIR__.'/vendor/autoload.php'; 

// import the namespaces
use Symfony\Component\Filesystem\Filesystem,
    ImaginativeImpact\PDFVersionConverter\Converter\GhostscriptConverterCommand,
    ImaginativeImpact\PDFVersionConverter\Converter\GhostscriptConverter;

// [..]

$command = new GhostscriptConverterCommand();
$filesystem = new Filesystem();

$converter = new GhostscriptConverter($command, $filesystem);
$converter->convert('/path/to/my/file.pdf', '1.4');
```

## Running unit tests

**Important:** *Tests are currently not working and need to be updated*

Run `./vendor/bin/phpunit -c tests`
