# PSR Http Message Utilities

Utility classes and constants to provide quick reference usage for request methods and responses.

## Installation

```bash
compose require dlzer/http-util
```

## Usage

When used in conjunction with [PHP-FIG](https://github.com/php-fig/http-message-util) Status Code Interface.

```php
// Custom responder method
public function withJson(
    ResponseInterface $response,
    $statusCode, 
    $message, 
    $data = null, 
    int $options = 0
    ): ResponseInterface
{
    return $response->write(json_encode([
        "status" => $statusCode,
        "message" => $message,
        "data" => $data
    ], $options);
    );
}

// Usage
$data = ["connection" => true];
return $this->responder->withJson(
    $response, // The response interface
    StatusCodeInterface::STATUS_OK // The status code interface
    StatusCodeMessage::STATUS_OK // The status message interface: "OK"
    $data // The response data
);

```

Output:
```json
{
    "status": 200,
    "message": "OK",
    "data": {
        "connection": true
    }
}
```