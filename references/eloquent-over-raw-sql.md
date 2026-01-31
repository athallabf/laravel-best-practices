# Rule: Use Eloquent over Raw SQL

Always prefer Eloquent ORM or Query Builder over raw SQL queries to ensure code readability, maintainability, and built-in protection against SQL injection.

## Bad
Using raw SQL queries for simple data retrieval.

```php
$users = DB::select('select * from users where active = 1');
```

## Good
Using Eloquent to perform the same task.

```php
$users = User::where('active', 1)->get();
```
