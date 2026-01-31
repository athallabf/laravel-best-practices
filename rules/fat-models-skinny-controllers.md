# Rule: Fat Models, Skinny Controllers

Controllers should only handle request parsing and response returning. Business logic and database interactions should be moved to Models or Services.

## Bad
The controller contains database logic and property assignment.

```php
public function store(Request $request)
{
    $request->validate(['title' => 'required|unique:posts|max:255']);

    $post = new Post;
    $post->title = $request->title;
    $post->slug = Str::slug($request->title);
    $post->user_id = Auth::id();
    $post->save();

    return redirect()->route('posts.index');
}
```

## Good
The controller delegates logic to the model or a service.

```php
// PostController.php
public function store(StorePostRequest $request)
{
    Post::createWithSlug($request->validated());
    return redirect()->route('posts.index');
}

// Post.php
public static function createWithSlug(array $data)
{
    $data['slug'] = Str::slug($data['title']);
    $data['user_id'] = Auth::id();
    return self::create($data);
}
```
