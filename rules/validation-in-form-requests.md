# Rule: Validation in Form Requests

Validation logic should be extracted into dedicated Form Request classes to keep controllers clean and promote reusability.

## Bad
Validation is performed directly inside the controller method.

```php
public function store(Request $request)
{
    $request->validate([
        'title' => 'required|unique:posts|max:255',
        'body' => 'required',
    ]);
    
    // ...
}
```

## Good
Validation is handled by a custom `StorePostRequest` class.

```php
// app/Http/Requests/StorePostRequest.php
public function rules()
{
    return [
        'title' => 'required|unique:posts|max:255',
        'body' => 'required',
    ];
}

// app/Http/Controllers/PostController.php
public function store(StorePostRequest $request)
{
    // Logic here is only reached if validation passes
    Post::create($request->validated());
}
```
