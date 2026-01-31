# Rule: Use Standard Laravel Tools

Prefer built-in Laravel features and community-standard packages over building custom solutions or using obscure third-party libraries.

## Examples
- Use **Laravel Fortify/Breeze/Jetstream** for authentication.
- Use **Laravel Socialite** for OAuth.
- Use **Laravel Media Library** for file management.
- Use **Laravel Excel** for imports/exports.

## Good
Leveraging the ecosystem.
```bash
composer require spatie/laravel-permission
```
instead of writing a custom RBAC system from scratch.
