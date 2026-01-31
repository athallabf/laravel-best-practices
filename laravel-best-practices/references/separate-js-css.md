# Rule: Separate JS and CSS from Blade

Keep JavaScript and CSS in dedicated files within the `resources` directory and use a bundler (like Vite) instead of inlining them in Blade templates.

## Bad
Inlining scripts and styles in Blade.

```html
<!-- index.blade.php -->
<script>
    function handleClick() {
        alert('Clicked!');
    }
</script>
<style>
    .btn-custom { color: red; }
</style>
```

## Good
Importing external assets.

```html
<!-- index.blade.php -->
@vite(['resources/css/app.css', 'resources/js/app.js'])
```
