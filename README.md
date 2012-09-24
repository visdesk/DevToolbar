# DevToolbar module for Zend Framework 2

This module provides a toolbar for your project's development to easily fetch memory usage information, tail of Apache's access and error logs as well as phpinfo(), all from their own tab in the toolbar.

Requirements:

- PHP 5.3
- Zend Framework 2
- rwoverdijk/assetmanager @ [https://github.com/RWOverdijk/AssetManager](https://github.com/RWOverdijk/AssetManager)
- jQuery
- jQuery-UI

Note: jQuery and jQuery-UI are bundled with this module and available out-of-the-box. You can override the bundled version with your own with minimal effort.

@Author: Artur Gajewski


## Installation with Composer

Go to your project directory and add the following line to "require" list in composer.json file:

```php
"artur-gajewski/dev-toolbar": "dev-master"
```

Now run the Composer:

```php
php composer.phar install
```

Then add 'DevToolbar' and 'AssetManager' modules into the Module array in APPLICATION_ROOT/config/application.config.php

```php
<?php
return array(
    'modules' => array(
        ...
        'AssetManager',
        'DevToolbar',
        ...
    ),
);
```


## Adding JS and CSS files to your layout script

DevToolbar uses it's own Javascript and CSS files to generate dynamic edit capabilities within your view script.

In order to get DevToolbar working, you need to include these files where you include all your Javascript and CSS files.

```php
echo $this->getDevToolbar('js');
echo $this->getDevToolbar('css');
```

if you want to include bundled jQuery and jQuery-UI, you need to add a boolean parameter like so:

```php
echo $this->getDevToolbar('js', true);
echo $this->getDevToolbar('css', true);
```

If you want to override the bundled package with newer version, you can override the path to Javascript and CSS files in module.config.php file:

```php
'params' => array(
    // DevToolbar settings
    'enabled'                  => true,
    'access_log'               => '/usr/local/zend/apache2/logs/access_log',
    'error_log'                => '/usr/local/zend/apache2/logs/error_log',
    'access_log_rows'          => 20,
    'error_log_rows'           => 20,
    'show_phpinfo'             => true,

    // DevToolbar related JS and CSS
    'js_source_path'           => '/js/DevToolbar.js',
    'css_source_path'          => '/css/DevToolbar.css',

    // jQuery related JS and CSS
    'jquery_js_source_path'    => '/js/jquery-1.8.0.min.js',
    'jquery-ui_js_source_path' => '/js/jquery-ui-1.8.23.custom.min.js',
    'jquery_ui_css_path'       => '/css/ui-lightness/jquery-ui-1.8.23.custom.css',
    ),
```

There are few parameters that you can configure your DevToolbar with:

enabled: wether the DevToolbar should be displayed
show_phpinfo: toggle phpinfo() tab
access_log_rows: How many rows to display from the end of access_log
error_log_rows: How many rows to display from the end of error_log


## Using DevToolbar

When you click on any of the tabs, the current information is fetched from the server. Click on the tab to show it's contents.


## Questions or comments?

Feel free to email me with any questions or comments about this module

[info@arturgajewski.com](mailto:info@arturgajewski.com)