# Testing October CMS plugins using PHPUnit and Github Actions

## Creating a phpunit.xml file 

Create a file within your plugin root directory with the following content

###phpunit.xml
```xml
<?xml version="1.0" encoding="UTF-8"?>
<phpunit backupGlobals="false"
         backupStaticAttributes="false"
         bootstrap="../../../tests/bootstrap.php"
         colors="true"
         convertErrorsToExceptions="true"
         convertNoticesToExceptions="true"
         convertWarningsToExceptions="true"
         processIsolation="false"
         stopOnFailure="false"
>
    <testsuites>
        <testsuite name="Plugin Name Test Suite">
            <directory>./tests</directory>
        </testsuite>
    </testsuites>
    <php>
        <env name="APP_ENV" value="testing"/>
        <env name="CACHE_DRIVER" value="array"/>
        <env name="SESSION_DRIVER" value="array"/>
    </php>
</phpunit>
```
## Make sure you have the tests folder

If you have installed October CMS via composer then you will already find a tests directory in the root folder. This tests directory contains a class called **PluginTestCase** which should be used as a base class for plugin testing. If you don't have this folder you can copy the directory from the octobercms [repo](https://github.com/octobercms/october/tree/develop/tests).

## Create your First Test Case

Once you have made sure you have the tests directory, you can now create your first test case. Create a new directory called tests inside your plugin directory and create a file called ExampleTest.php

### tests/ExampleTest.php
```php
<?php

namespace Author\Plugin\Tests;

use PluginTestCase;

class ExampleTest extends PluginTestCase
{
    public function testExample()
    {
        $this->assertTrue(true);
    }
}

```

## Running your tests locally

To run your test cases navigate to your plugin's root directory and run the following command.

`../../../vendor/bin/phpunit` OR If you are on windows

`..\..\..\vendor\bin\phpunit`.

This will run the phpunit executable which is included in the installation with octobercms. Make sure you are green or else get the bug solved :-)

### Creating a Github Action for Testing the plugin


