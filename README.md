PHP interface to OpenProvider API
=================================

This package contains a small PHP interface to make use of the OpenProvider API (https://doc.openprovider.eu/index.php/Main_Page).

The files as found in this package are almost identical to the ones as distributed by OpenProvider. So why bother
creating a package for it? The __distribution__ of OpenProvider consists of a single file and does not make use
of Composer and it's autoload features.

Example
-------

```php
include 'vendor/autoload.php';

$api = new OP_API ('https://api.openprovider.eu');

$request = new OP_Request;
$request
    ->setCommand('checkDomainRequest')
    ->setAuth(array('username' => '[username]', 'password' => '[password]'))
    ->setArgs(array(
        'domains' => array(
            array(
                'name' => 'openprovider',
                'extension' => 'nl'
            ),
            array(
                'name' => 'jouwweb',
                'extension' => 'nl'
            )
        )
    ));

$reply = $api->setDebug(1)->process($request);
echo "Code: " . $reply->getFaultCode() . "\n";
echo "Error: " . $reply->getFaultString() . "\n";
echo "Value: " . print_r($reply->getValue(), true) . "\n";
echo "\n---------------------------------------\n";

echo "Finished example script\n\n";
```
