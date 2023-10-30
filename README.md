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

## Apply custom Attribute

Where it can be applied:

- classes and anonymous classes
- properties and constants
- methods and functions (inc. closure)
- method and function parameters

### Required validation rule

```
namespace App\DTO;

use App\Validation\Rules\Required;

readonly class UserRegistration
{
    public function __construct(
        #[Required]
        public string $username,
        #[Required]
        public string $email
    ) {
    }
}
```

## Validation

Into the `attributes.php` next line after the $userRegistration = ...

```
$validator = new Validator();
$validator->validate($userRegistration);

$errors = $validator->getErrors();
```

## Validator class

### ValidationRuleInterface

Required rule must implement ut
```
namespace App\Validation\Rules;

interface ValidationRuleInterface
{
    public function getValidator():;
}
```

### Required rule

```
namespace App\Validation\Rules

use Attribute;

#[Attribute]
class Required implements ValidationRuleInterface
{
    public function getValidator()
    {
    }
}
```

### Validation itself

Into the `src\Validation`

```
<?php

namespace App\Validation;

class Validator
{
    private arrray $errors = [];
    
    public function validate(object $object): void
    {
        # instance a $reflection
        $reflector = new ReflectionClass($object);
        # loop over the reflector properties

        # get the Attributes using $property->getAttributes()

        # loop over the Attributes

        # instance a PropertyValidator

        # ask IF the property does not validate

        # add the property to errros with a message
                
    }

    public function getErrors()
    {
    }
}

```











