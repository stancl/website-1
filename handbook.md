> This document is a work in progress, it may still change, perhaps profoundly.

# Handbook

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

## Methods signature

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

## Typed properties

> Supported by: phpstan and psalm

With **Plus** you don't need PHP 7.4 to start types in class properties. In our example, if the
property name is a `string`, you can do:

```php
class User {
    public string $name
}
```

## Readonly properties

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



