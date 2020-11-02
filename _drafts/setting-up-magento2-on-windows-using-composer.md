# Setting up Magento on Windows using Composer

## Requirements

You can take a look at the [requirements](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements-tech.html) for magento 2 before moving forward.

## Create Project

To create a magento website, run the following the following command in your webroot . This will create a folder as specified in the command with all the necessary files.

` composer create-project --repository-url=https://repo.magento.com/ magento/project-community-edition <install-directory-name> `

## Install Magento

Now move into your project folder and run the below command for installing magento and configure it as per your need
```shell
php bin/magento setup:install --base-url=https://magento2.app --db-host=localhost --db-name=magento2 --db-user=root --db-password= --admin-firstname=admin --admin-lastname=admin --admin-email=admin@admin.com --admin-user=admin --admin-password=admin123 --language=en_US --currency=INR --timezone=Asia/Kolkata --use-rewrites=1 --search-engine=elasticsearch7 --elasticsearch-host=https://127.0.0.1:9200 --elasticsearch-port=9200 --elasticsearch-enable-auth=1 --elasticsearch-username=elastic --elasticsearch-password=@el++++++++++++++gar#
```

## Common Installation Issues

**Unable to apply data patch Magento\Theme\Setup\Patch\Data\RegisterThemes for module Magento_Theme. Original exception message: Wrong file**

To resolve this issue, navigate to vendor\magento\framework\Image\Adapter\Gd2.php and replace the validateURLScheme function with the below code

```php
private function validateURLScheme(string $filename): bool
{
    $allowed_schemes = ['ftp', 'ftps', 'http', 'https'];
    $url = parse_url($filename);
    if ($url && isset($url['scheme']) && !in_array($url['scheme'], $allowed_schemes) && !file_exists($filename)) {
        return false;
    }

    return true;
}
```

[Source](https://magento.stackexchange.com/questions/311806/installation-at-51-module-magento-theme-error-in-magento-2)

**Admin Black & Gray Screen Issue**

To resolve this issue, navigate to vendor/magento/framework/View/Element/Template/File/Validator.php. Replace the code in the isPathInDirectories method with the following code.

```php
protected function isPathInDirectories($path, $directories)
{
    if (!is_array($directories)) {
        $directories = (array)$directories;
    }
    $realPath = $this->fileDriver->getRealPath($path);
    foreach ($directories as $directory) {
        $realDirectory = $this->fileDriver->getRealPath($directory);
        if ($realDirectory && 0 === strpos($realPath, $realDirectory)) {
            return true;
        }
    }
    return false;
}
```

