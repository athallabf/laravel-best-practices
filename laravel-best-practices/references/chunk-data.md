# Rule: Chunk Large Datasets

When processing large amounts of data, use `chunk()` or `cursor()` to prevent memory exhaustion by loading only a small portion of the data at a time.

## Bad
Loading all records into memory at once.

```php
$users = User::all();
foreach ($users as $user) {
    // Process user
}
```

## Good
Processing records in chunks.

```php
User::chunk(100, function ($users) {
    foreach ($users as $user) {
        // Process user
    }
});
```
