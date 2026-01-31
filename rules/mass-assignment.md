# Rule: Mass Assignment and Fillable

Use mass assignment methods like `create()` or `update()` combined with `$fillable` or `$guarded` properties on the model for cleaner and more secure code.

## Bad
Manually assigning every property before saving.

```php
$post = new Post;
$post->title = $request->title;
$post->body = $request->body;
$post->save();
```

## Good
Using mass assignment with validated data.

```php
// Post.php
protected $fillable = ['title', 'body'];

// Controller
Post::create($request->validated());
```
