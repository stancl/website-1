> This document is a work in progress, it may still change, perhaps profoundly.

# What is Plus?

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

> Learn more about `[Phpstan](https://github.com/phpstan/phpstan)` and `[Psalm](https://github.com/vimeo/psalm)`.

### Drawbacks

You probably are worried about what are the drawbacks of using **Plus** today - and, on the time
of this writing, here is the list of drawbacks today:

- Missing PHPStorm plugin

## Handbook

Let’s take a look at a simple class-based example:

```php
class User {
    public readonly string $name;

    public __construct(string $name) {
        $this->name = $name;
    }

    public getName(): string => $this->name
}
```

Cool right? The syntax should look familiar if you have used PHP before - so now, let's walk thought on
what **Plus** was to offer:

### Methods signature

If you have done PHP before, you probably have used the following syntax while declaring a class method:

```php
class User
{
    public function getName(): string
    {
        return $this->name;
    }
}
```

With **Plus** you can do:

```php
class User
{
    public getName(): string
    {
        return $this->name;
    }
}
```

Notice how we dropped `function` keyword altogether and just the function name directly. Even
better, you can have one line arrow functions:

```php
class User
{
    public getName(): string => $this->name;
}
```

Keep in mind that the `return` keyword is hidden in those one-line arrow functions. So on the
example above, we are going to return the name of the user.

### `types` in class properties

> Supported by: phpstan and psalm

With **Plus** you don't need PHP 7.4 to start types in class properties. In our example, if the
property name is a `string`, you can do:

```php
class User {
    public string $name
}
```

### `readonly` in class properties

> Supported by: psalm

You can make properties readonly by using the `readonly` keyword. Readonly properties must be
initialized at their declaration or in the constructor.

```php
class User {
    public readonly string $name
}
```

## Enumerations

## Short closures

## Types

## Debuggable



