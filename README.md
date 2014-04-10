# ImageProxy  

Laravel 4 package for image cropping and resizing on the fly. It uses Timthumb nder the hood.

## Installation  

Add in `composer.json`  
```
"require": {
    "psimone/imgproxy": "1.0.*"
},
"repositories": {
    {
        "type": "vcs",
        "url": "git@bitbucket.org:psimone/imgproxy.git"
    }
}
```

Run `composer update`  

Add the service provider in the `app/config/app.php` file  
```
"Psimone\Imgproxy\ImgproxyServiceProvider"
```

Publish the package assets running `php artisan asset:publish psimone/imgproxy`

## Usage

Use the package facade to generate the resource url
```
ImgProxy::link("path/to/image.jpg", 100, 80)
```
This will generate a link like this
```
http://www.yourdomain.com/packages/psimone/imgproxy/100/80/path/to/image.jpg
```
that generates an image with dimensions 100 x 80 using the original `image.jpg` stored in the `public/path/to` folder.  

## Config

After publishing the assets it's possible to edit package config in the `public/packages/psimone/imgproxy/timthumb-config.php` file.  

These, at the moment, are the default values
```
define ("DEBUG_ON", false);

define ("DEBUG_LEVEL", 3);

define ("FILE_CACHE_MAX_FILE_AGE", 86400);

define ("FILE_CACHE_SUFFIX", ".imgproxy.cache");

define ("FILE_CACHE_PREFIX", "");

define ("FILE_CACHE_DIRECTORY", "../../../../app/storage/cache/imgproxy");

define ("NOT_FOUND_IMAGE", "./nophoto.gif");

define ("ERROR_IMAGE", "./nophoto.gif");

define ("PNG_IS_TRANSPARENT", FALSE);

define ("DEFAULT_Q", 90);
```