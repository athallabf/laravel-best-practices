# Rule: Do Not Access .env Directly

Configuration values should be accessed through the `config()` helper, never via `env()` directly in the application logic. This ensures values are available even when configuration is cached.

## Bad
Accessing environment variables directly in controllers or services.

```php
$apiKey = env('STRIPE_KEY');
```

## Good
Defining the value in a config file and accessing it via `config()`.

```php
// config/services.php
return [
    'stripe' => [
        'key' => env('STRIPE_KEY'),
    ],
];

// In your code
$apiKey = config('services.stripe.key');
```
