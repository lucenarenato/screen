# Demo

This is just a demonstration of how you can use this library

## index.html

Here you can find a basic form that requests the `shot.php` file to screenshot the websites.

## shot.php

You can directly render the taken screen-shot with the `shot.php` file

You can render any link by passing it as `url` parameter: `shot.php?url=google.com`

You can specify height and width: `shot.php?url=google.com&w=300&h=100`

If you want to crop/clip the screen shot, you can do so like this: `shot.php?url=google.com&w=800&h=600&clipw=800&cliph=600`

You can also set a user agent string to be used on the request: `shot.php?url=google.com&user-agent=some-random-user-agent-string`

**Note**: You should `urlencode` the values in case there is any space or tricky character.

## clean-jobs.php

Here you can se an example on how to delete the job files that are generated automatically.


## Commands
```
composer require microweber/screen
composer require jakoch/phantomjs-installer microweber/screen

php -S localhost:8001
```

## Caso tenha algum problema
```
sudo apt-get install -y php7.2-bz2
composer require jakoch/phantomjs-installer microweber/screen
php -d memory_limit=4G $(which composer) install 
php -d memory_limit=4G $(which composer) update
```

<p align="center"><img src="captura.png"></p>

## Uso no Laravel 6

```php
use Screen\Capture;
public function iframeType($src) 
    {
        $url = $src;
        $screenCapture = new Capture($url);
        $screenCapture->setWidth(1024);
        $screenCapture->setHeight(768);
        $screenCapture->setImageType('png');

        //$fileLocation = Storage::disk('temp')->put('screenshot_iframe.png', Storage::disk('temp')->get('screenshot_iframe.png')); 
        $fileLocation =storage_path('/app/public/screenshot.png');

        $screenCapture->save($fileLocation); // Will automatically determine the extension type
        //echo $screenCapture->getImageLocation();
        
        return $screenCapture->getImageLocation();
    }
```    
- Renato Lucena 
- [Renato Lucena](https://github.com/lucenarenato)