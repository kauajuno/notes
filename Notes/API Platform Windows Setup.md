

After putting the folder inside your WSL and starting up the docker engine, start up the application with the following command.

```bash
docker compose up -d
```

This docker command runs the containers according to what's specified in the `compose.yaml` file. In this case, there will be a php instance, a frontend instance (Next.js) and a database instance (PostgreSQL). The -d flag stands for "detach" and lets you keep using that same terminal.
After this set up you may also install some Symfony bundles that will for sure be helpful for development.

```bash
docker compose exec php composer require maker debug --dev
```

This will install maker bundle, which adds some utils to the CLI that saves you some boilerplate code, and debug, which... well, it's very useful for debug.

  
