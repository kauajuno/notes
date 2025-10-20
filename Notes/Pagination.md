To seek for information about the configurations of some specific bundle configuration, such as the `api_platform` bundle itself, hit this command:

```bash
docker compose exec php php bin/console debug:config api_platform
```

But that command will only show whatever is set different from the defaults, if you're trying to see every possible key configuration for a bundle you're better off using this command:

```bash
docker compose exec php php bin/console config:dump api_platform
```

By running the command above you might see some information about pagination and that there is a key called `paginationItemsPerPage`. Go to your `#[ApiResource]` attribute and set this configuration to a different value than the default. You'll notice that now the number of items returned per page is whichever value you have set for your entity.