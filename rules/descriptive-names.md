# Rule: Descriptive Names over Comments

Write code that is self-explanatory by using descriptive variable and method names. Comments should explain *why* something is done, not *what* is being done.

## Bad
Cryptic names requiring comments.

```php
if ($u->st == 1) { // check if user is active
    // ...
}
```

## Good
Self-documenting code.

```php
if ($user->isActive()) {
    // ...
}
```
