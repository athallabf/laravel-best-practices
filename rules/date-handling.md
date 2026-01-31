# Rule: Standard Date Handling

Store all dates in the database using the standard UTC format. Use Eloquent `$casts` or accessors/mutators to handle formatting for the frontend.

## Bad
Storing formatted date strings or manually formatting dates in every view.

```php
// In view
{{ date('m/d/Y', strtotime($user->created_at)) }}
```

## Good
Casting the attribute to a datetime and using it as a Carbon instance.

```php
// Model
protected $casts = [
    'published_at' => 'datetime',
];

// In view
{{ $post->published_at->format('M d, Y') }}
```
