## Container

List all containers:
```
docker container ls -a
```

List only running containers:
```
docker container ls
```

List the ids of all containers (The -q flag only returns the ids):
```
docker container ls -a -q
```

Create container without running it:
```
docker container create nomeDoContainer
```

Stop container:
```
docker stop idDoConteiner
```

Stop containers based on a docker command return:
```
docker stop $(docker ps -a -q)
```

Start stopped container:
```
docker start idDoConteiner
```

View container usage statistics:
```
docker stats idDoConteiner
```

Remove a container (Use the -f at the end if the container is running):
```
docker rm idDoConteiner
```

Run a container in the background, using the -d flag of detached:
```
docker -d image-name
```

Return to a closed (but not stopped) container:
```
docker attach container-id
```

Remove all containers:
```
docker rm $(docker ps -a -q); 
```

Configure the container home directory:
```
docker run -w caminhoDoDiretorioNoContainer
```

Map port (In this example local port 80 is mapped to port 80 of the apache2 container):
```
docker run -p 80:80 apache2
```

Open container terminal:
```
docker exec nomeDaImagem bash
```

Use the container's interactive terminal (The interactive terminal is for us to be able to answer questions that arise during the execution of a command, such as typing yes to allow something):
```
docker exec -it image-name comandoAserExecutadoNoContainer
```
