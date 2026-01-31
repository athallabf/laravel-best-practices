# Rule: Eloquent Scopes for DRY Queries

Encapsulate common query logic into Eloquent scopes to keep your code DRY and improve readability.

## Bad
Repeating the same query logic across multiple controllers.

```php
$posts = Post::where('active', 1)->where('published_at', '<=', now())->get();
```

## Good
Defining a scope in the model.

```php
// Post.php
public function scopePublished($query)
{
    return $query->where('active', 1)->where('published_at', '<=', now());
}

// Usage
$posts = Post::published()->get();
```
