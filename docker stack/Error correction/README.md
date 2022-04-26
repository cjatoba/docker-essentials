### ...deploy.resources.limits.cpus must be a string

This error occurs because the output of the docker-compose config command removes the quotes in the cpus parameter, it is necessary to use the sed command to add the quotes again
```
docker stack deploy -c <(docker-compose -f stack.yml config|sed -E "s/cpus: ([0-9\.]+)/cpus: '\1'/") stack_name
```
