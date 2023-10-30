# ed-php-attributes
PHP Attributes by https://youtu.be/oSo4xbP6ZYo

# First usage - DTO (data transfer objects)

## Require package
`composer require --dev symfony/var-dumper`

## DTO class

Into the src/DTO

```
namespace App\DTO;

class UserRegistration
{
    public function __construct(
        public string $username,
        public string $email
    ) {
    }
}
```

## Readonly (protect properties)

to protectd our properties

```
readonly public string $username,
readonly public string $email
```

## attributes.php file

```
<?php

use App\DTO\UserRegistration;

require_once 'vendor/autoload.php';

$userRegistration = new UserRegistration('test', 'test@test.com');
```

It's acceptable to set

```
readonly class UserRegistration
```

and don't write it to each or property












