# How to use Docker

```yaml
...
  service-name:
    ...
    develop:
      watch:
        - action: rebuild # sync | rebuild | sync+restart
          path: ./src # Local sorce path
          target: /app/src # Container path
```

Reference: https://docs.docker.com/compose/how-tos/file-watch/
