# Install October CMS plugin via composer

Composer is a great way of managing dependencies for PHP. If you install a plugin via composer it allows us to specify the exact version of the plugin we require and may protect you from unnecessary issues.

## Requirements

To install a plugin via composer , we need to check whether the plugin supports installation via composer. To do that simply visit [Packagist](https://packagist.org/) and search for your extension for e.g "oc-idehelper-plugin". If you find a plugin you can install it via composer or else ask the plugin author to publish it to packagist.

## Installation

Now, you can simply add the plugin as a required dependencies to your composer.json which you will find in your website's root directory. Here is a example of how we can add the idehelper plugin.

```json
"require": {
    "php": ">=7.0.8",
    "ext-mbstring": "*",
    "ext-openssl": "*",
    "october/rain": "~1.0",
    "october/system": "~1.0",
    "october/backend": "~1.0",
    "october/cms": "~1.0",
    "laravel/framework": "~5.5.40",
    "wikimedia/composer-merge-plugin": "1.4.1",
    "flynsarmy/oc-idehelper-plugin": "*"
}
```

Once you have added the plugin to the require array. Simply run composer update and you will find the plugin in the plugins folder.

It, is also a better option to not version control packages installed via composer so you can add your plugin directory to .gitignore

### .gitignore
```
/vendor
/plugins/flynsarmy/idehelper # Add the plugin directory 
```
