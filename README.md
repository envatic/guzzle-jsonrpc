# Guzzle JSON-RPC

**Master build:** [![Master branch build status][travis-master]][travis]

This library implements [JSON-RPC 2.0][jsonrpc] for the [Guzzle v3 HTTP client][guzzle].<br/>
It can be installed in whichever way you prefer, but we recommend [Composer][packagist].
```json
{
    "require": {
        "graze/guzzle-jsonrpc": "*"
    }
}
```

## Documentation
```php
<?php
use Graze\Guzzle\JsonRpc\JsonRpcClient;

// Create the client
$client = new JsonRpcClient('http://localhost:8000');

// Prepare and send a notification
$request = $client->notification('method', array('key' => 'value'));
$request->send();

// Prepare and send a request that expects a response
$request  = $client->request('method', 123, array('key' => 'value'));
$response = $request->send();

// Prepare and send a batch of requests
$request = $client->batch(array(
    $client->request('method', 123, array('key' => 'value')),
    $client->request('method', 124, array('key' => 'value')),
    $client->notification('method', array('key' => 'value'))
));
$response = $request->send();
```

### Contributing ###

We accept contributions to the source via Pull Request,
but passing unit tests must be included before it will be considered for merge.

```bash
$ make deps
$ make lint test
```

### License ###
The content of this library is released under the **MIT License** by **Nature Delivered Ltd**.<br/>
You can find a copy of this license at http://www.opensource.org/licenses/mit or in [`LICENSE`][license]

<!-- Links -->
[travis]: https://travis-ci.org/graze/guzzle-jsonrpc
[travis-master]: https://travis-ci.org/graze/guzzle-jsonrpc.png?branch=master
[packagist]: https://packagist.org/packages/graze/guzzle-jsonrpc
[vagrant]: http://vagrantup.com
[jsonrpc]: http://jsonrpc.org/specification
[guzzle]: https://github.com/guzzle/guzzle3
[license]: /LICENSE
