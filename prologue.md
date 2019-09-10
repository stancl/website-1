# Prologue

> This document is a work in progress, it may still change, perhaps profoundly.

**Plus is a runtime compiler that adds features to PHP** - It's also a package that you can
require using `composer`, and is mainly used to add features and syntactic sugar to existant PHP
code. Of course, those features arrive in PHP using runtime source code transformations.

Here is an example:
```php
$names = array_map(($user) => $user->name, $users);

// The short closure above is transformed in runtime to:
$names = array_map(function ($user) {
    return $user->name;
}, $users);
```

### Static analysis

Keep in mind that **Plus** is not a static analysis tool; you'll still have
to install and use `Phpstan` or `Psalm` to that. But, indeed, **Plus** works better
combined with those static analysis tools.

Here is an example where `psalm` static analysis will be able to tell you that `name` can't
be modified outside of the class constructor:

```php
class User {
    public readonly string $name;
}

$user = new User();
$user->name = 'Nuno'; // psalm error: property `name` can be modified
```

Of course, you can still **Plus** without any static analysis tool and enjoy all the syntactic
sugar such as `short closures` and others.

> Learn more about [Phpstan](https://github.com/phpstan/phpstan) and [Psalm](https://github.com/vimeo/psalm).

### Drawbacks

You probably are worried about what are the drawbacks of using **Plus** today - and, on the time
of this writing, here is the list of drawbacks today:

- Missing PHPStorm plugin
