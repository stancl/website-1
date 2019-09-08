> This document is a work in progress, it may still change, perhaps profoundly.

# Get Started

You may install install by issuing the [Composer](https://getcomposer.org) `require` command in your terminal:

```bash
composer require php-plus/engine
```

After installing **Plus**, you need to a `declare(plus=1);` to each file you want use the new
syntax that **Plus** has to offer. Here is an example:

```php
<?php

declare(plus=1);

Route::get('/', () => view('welcome');
```
