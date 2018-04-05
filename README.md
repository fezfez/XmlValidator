# PHP Xml validator

[![Build Status](https://travis-ci.org/vrbata/XmlValidator.svg)](https://travis-ci.org/vrbata/XmlValidator)
[![Packagist](https://img.shields.io/packagist/dt/vrbata/xml-validator.svg)](https://packagist.org/packages/vrbata/xml-validator)

Validate Xml against a xsd schema.

## Installation

### Library

    $ git clone https://github.com/vrbata/XmlValidator.git

### Composer

    $ composer require vrbata/xml-validator:dev-master

## Usage

```php
<?php
require "./vendor/autoload.php";
use XmlValidator\XmlValidator;

$xml = "<sample>my xml string</sample>";
$xsd = "path_to_xsd.xsd";

// Validate based on xsd file
$xmlValidator = new XmlValidator($xml, $xsd, XsdSource::FILE);
try{
    $xmlValidator->validate($xml,$xsd);
    
    // Check if is valid
    if(!$xmlValidator->isValid()){
        
        // Do whatever with the errors.
        foreach ($xmlValidator->errors as $error) {
            /*echo sprintf('[%s %s] %s (in %s - line %d, column %d)',
                $error->level, $error->code, $error->message, 
                $error->file, $error->line, $error->column
            ); */
        }
    }
} catch (\InvalidArgumentException $e){
    // catch InvalidArgumentException
}

// Validate based on xsd as string
$xmlValidator = new XmlValidator($xml, $xsd, XsdSource::STRING);
try{
    $xmlValidator->validate($xml,$xsd);
    
    // Check if is valid
    if(!$xmlValidator->isValid()){
        
        // Do whatever with the errors.
        foreach ($xmlValidator->errors as $error) {
            /*echo sprintf('[%s %s] %s (in %s - line %d, column %d)',
                $error->level, $error->code, $error->message, 
                $error->file, $error->line, $error->column
            ); */
        }
    }
} catch (\InvalidArgumentException $e){
    // catch InvalidArgumentException
}

```

Based on [XmlUtils](https://github.com/symfony/symfony/blob/master/src/Symfony/Component/Config/Util/XmlUtils.php) from Symfony config component.