php-thrift-package
==================

The repository just extracted PHP lib code from thrift code base to work better with composer. To install this lib, just add a requirement in composer.json:

```json
"require": {
    "leric/php-thrift": "0.9.*"	
}
```

Thrift Client
------------------

Generate thrift client code:

```bash
/project/root $ thrift -gen php:oop API.thrift -out thrift
```

Setup composer to autoload generated code in thrift directory:

```json
"autoload": {
    ...	
	"classmap": ["thrift/"]
}
```

Use thrift client:
```php
<?php
$socket = new TSocket('localhost', 9090);
$transport = new TBufferedTransport($socket);
$protocol = new TBinaryProtocol($transport);

$client = new ServiceClient($protocol);
$transport->open();

$client->ping();
```

better use a DI container to get rid of these boilerplate code.


Thrift Server
-----------------

TBD