# How to use Compose Watch

## Example

```yaml
...
  service-name:
    ...
    develop:
      watch:
        - action: rebuild
          path: ./src
          target: /app/src
          initial_sync: true
          ignore:
            - node_modules/
        - action: rebuild
          path: package.json
```

# Options

## action

### Sync

If action is set to sync, Compose makes sure any changes made to files on your host automatically match with the corresponding files within the service container.

sync is ideal for frameworks that support "Hot Reload" or equivalent functionality.

More generally, sync rules can be used in place of bind mounts for many development use cases.

### Rebuild

If action is set to rebuild, Compose automatically builds a new image with BuildKit and replaces the running service container.

The behavior is the same as running docker compose up --build <svc>.

Rebuild is ideal for compiled languages or as a fallback for modifications to particular files that require a full image rebuild (e.g. package.json).

### Sync + Restart

If action is set to sync+restart, Compose synchronizes your changes with the service containers and restarts them.

sync+restart is ideal when the config file changes, and you don't need to rebuild the image but just restart the main process of the service containers. It will work well when you update a database configuration or your nginx.conf file, for example.

### Tip

Optimize your Dockerfile for speedy incremental rebuilds with image layer caching and multi-stage builds.

## path and target

The target field controls how the path is mapped into the container.

For path: ./app/html and a change to ./app/html/index.html:

target: /app/html -> /app/html/index.html
target: /app/static -> /app/static/index.html
target: /assets -> /assets/index.html

## ignore

The ignore patterns are relative to the path defined in the current watch action, not to the project directory. In the following Example 1, the ignore path would be relative to the ./web directory specified in the path attribute.

## initial_sync

When using a sync+x action, the initial_sync attribute tells Compose to ensure files that are part of the defined path are up to date before starting a new watch session.


## Reference

https://docs.docker.com/compose/how-tos/file-watch/
