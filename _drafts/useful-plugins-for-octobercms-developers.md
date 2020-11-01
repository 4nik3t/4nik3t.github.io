# Useful Plugins for October CMS Developers

## [IDE Helper](https://octobercms.com/plugin/flynsarmy-idehelper) 

Allows you to generate helper files for your IDE to understand. This, helps the IDE autosuggest some code instead of remembering the function names and methods.

### Installation - Using Command Line

`php artisan plugin:install flynsarmy.idehelper`

### Usage

Use `php artisan ide-helper:generate` to generate a IDE Helper file and enjoy.

## [Scaffold Translation](https://octobercms.com/plugin/bnb-scaffoldtranslation)

October CMS has certain commands to autogenerate some code for your plugins. Some of the commands are `create:plugin`, 'create:model', 'create:controller' . The files which are generated from these commands does not support translation by default. This plugin adds some commands which help you to create plugins which are translatable.

### Installation - Using Command Line

`php artisan plugin:install bnb.scaffoldtranslation`

### Usage

The plugin adds the following commands

```shell
php artisan create:plugin:translated Acme.Demo
php artisan create:controller:translated Acme.Demo Turtles
php artisan create:component:translated Acme.Demo TurtleList
php artisan create:widget:translated Acme.Plugin FooWidget
```
