# Rule: Naming Conventions

Follow standard Laravel naming conventions to make the codebase predictable and easier for other developers to navigate.

- **Controllers:** `UserController` (Singular)
- **Models:** `User` (Singular)
- **Tables:** `users` (Plural)
- **Columns:** `first_name` (Snake Case)
- **Relationships:** `hasMany`, `belongsTo` (Camel Case)

## Bad
Inconsistent naming.
- Table: `UserTable`
- Model: `user_model`
- Controller: `Users`

## Good
Standard naming.
- Table: `users`
- Model: `User`
- Controller: `UserController`
