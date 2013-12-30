# Fork

A Laravel PHP library that allows you to "faux fork" processes into the background.  It uses a new ability in Laravel to serialize closures, which can then be executed in the command line in the background.

## Install

You'll need to install the service provider in your ``app/config/app.php`` file:

```php
'Travis\Fork\Provider',
```

You may also wish to add an alias to remove the namespace:

```php
'Fork' => 'Travis\Fork'
```

Also, you'll need to register the command in your ``app/start/artisan.php`` file:

```php
Artisan::add(new ForkCommand);
```

## Usage

Just fork the code you want to run in the background:

```php
Fork::run(function() use($foobar)
{
    // do stuff
});
```

If you want to test for errors, you can run your code synchronously with output:

```php
Fork::test(function() use($foobar)
{
    // do stuff
});
```

## Notes

Executing code via command line can be dangerous and may require ``safe mode`` to ``off`` for it to work properly.