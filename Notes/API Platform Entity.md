# Entity definition

In API Platform with Symfony, you define entities as PHP classes annotated (or attributed) with `#[ApiResource]`. Each entity represents a data model exposed as a REST or GraphQL resource.
# Creating an entity

To create your first entity, let's say `DragonTreasure`, run the following command:

```bash
docker compose exec php php bin/console make:entity DragonTreasure
```

This will auto-generate your entity and prompt you to enter its properties. Depending on the version it will also ask you if you want to expose the new entity as an `ApiResource`. Mark it as no for now. It will also create a `DragonTreasureRepository.php` file on `src/Repository`. More on repositories later.

After doing so, you'll end up with a `DragonTreasure.php` with your properties and their pairs of getters and setters.

Run the following commands in your WSL to create a migration and run it to be able to interact with your database through the application.

```bash
docker compose exec php php bin/console make:migration
docker compose exec php php bin/console doctrine:migrations:migrate
```  

However, as soon as you get to your docs you'll notice that there is nothing there, even though you just created an entity just like the `Greeting` that you had before... or did you? In order to expose that entity to your API, you may give it the following attribute right above the class:

```php
#[ApiResource]
```
