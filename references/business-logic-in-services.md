# Rule: Business Logic in Services

Complex business logic that doesn't belong in a controller or a model should be encapsulated in a Service class.

## Bad
The controller handles file uploads and complex processing logic.

```php
public function store(Request $request)
{
    if ($request->hasFile('image')) {
        $path = $request->file('image')->store('posts');
        // more image processing logic...
    }
    
    // ... extensive business logic ...
}
```

## Good
The controller delegates the work to a specialized Service.

```php
public function store(StorePostRequest $request, PostService $postService)
{
    $postService->createPost($request->validated(), $request->file('image'));
    return redirect()->route('posts.index');
}
```
