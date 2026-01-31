# Rule: Prevent N+1 Problem with Eager Loading

When iterating over a collection and accessing a relationship, use eager loading (`with()`) to fetch all related data in a single query.

## Bad
Accessing a relationship in a loop without eager loading triggers a database query for every item.

```php
// Controller
$posts = Post::all();

// View
@foreach ($posts as $post)
    {{ $post->user->name }} <!-- Query executed for EACH post -->
@endforeach
```

## Good
Eager loading the relationship reduces the number of queries to just two.

```php
// Controller
$posts = Post::with('user')->get();

// View
@foreach ($posts as $post)
    {{ $post->user->name }}
@endforeach
```
