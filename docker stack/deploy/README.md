## Deploy with environment variables
Directory structure:
```
📂application
 ┣ ...
 ┣ 📜stack.yml
 ┣ 📜.env
```
This command reads the stack.yml file with the docker-compose command using the .env file variables and sends the output to the docker stack deploy -c command
```
docker stack deploy -c <(docker-compose -f stack.yml config) stack_name
```
