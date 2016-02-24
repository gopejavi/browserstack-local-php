# browserstack-local-php

## Setup

Installation is possible using [Composer](https://getcomposer.org/).

If you don't already use Composer, you can download the `composer.phar` binary:

    curl -sS https://getcomposer.org/installer | php

Then install the library:

    `php composer.phar require browserstack/local:dev-master`

Install all depenedencies:
    `php composer.phar install`

Test the installation by running a simple test file:

```
<?php
  require_once "vendor/autoload.php";
  use BrowserStack\Local;

  $me = new Local();
  $args = array("v" => 1);
  print $me->isRunning();
  $me->start($args);
  print $me->isRunning();
  $me->stop();

?>
```

## API

### Constructor

* `new Local()`: creates an instance of Local

### Methods

* `start(options)`: starts Local instance with options. The options available are detailed below.
* `stop()`: stops the Local instance
* `isRunning()`: checks if Local instance is running

### Options

* `key`: BrowserStack Access Key
* `v`: Provides verbose logging
* `f`: If you want to test local folder rather internal server, provide path to folder as value of this option
* `force`: Kill other running Browserstack Local
* `only`: Restricts Local Testing access to specified local servers and/or folders
* `forcelocal`: Route all traffic via local machine
* `onlyAutomate`: Disable Live Testing and Screenshots, just test Automate
* `proxyHost`: Hostname/IP of proxy, remaining proxy options are ignored if this option is absent
* `proxyPort`: Port for the proxy, defaults to 3128 when -proxyHost is used
* `proxyUser`: Username for connecting to proxy (Basic Auth Only)
* `proxyPass`: Password for USERNAME, will be ignored if USERNAME is empty or not specified
* `localIdentifier`: If doing simultaneous multiple local testing connections, set this uniquely for different processes
* `hosts`: List of hosts and ports where Local must be enabled for eg. localhost,3000,1,localhost,3001,0
* `logfile`: Path to file where Local logs be saved to
* `binarypath`: Optional path to Local binary

## Test

Testing is possible using [PHPUnit](https://phpunit.de/).

To run the tests, run the command:
  `phpunit tests/LocalTest.php`


