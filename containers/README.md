## Container

Listar todos os containers:
```
docker container ls -a
```

Listar apenas os containers em execução:
```
docker container ls
```

Listar os ids de todos os containers (A flag -q faz retornar apenas os ids):
```
docker container ls -a -q
```

Criar container sem executá-lo:
```
docker container create nomeDoContainer
```

Parar um container:
```
docker stop idDoConteiner
```

Parar os containers com base no retorno de um comando docker:
```
docker stop $(docker ps -a -q)
```

Iniciar um container parado:
```
docker start idDoConteiner
```

Exibir as estatísticas de uso do container:
```
docker stats idDoConteiner
```

Remover um container (Utilizar o -f no final caso o container esteja em execução):
```
docker rm idDoConteiner
```

Rodar um container em background, utilizando a flag -d de detached:
```
docker -d image-name
```

Retornar para um container fechado (mas não parado):
```
docker attach container-id
```

Remover todos os container:
```
docker rm $(docker ps -a -q); 
```

Configurar o diretório inicial do container:
```
docker run -w caminhoDoDiretorioNoContainer
```

Mapear porta (Neste exemplo a porta 80 local é mapeada para a porta 80 do container apache2):
```
docker run -p 80:80 apache2
```

Abrir o terminal do container:
```
docker exec nomeDaImagem bash
```

Utilizar o terminal interativo do container (O terminal interativo serve para conserguirmos responder as questões que surgirem durante a execução de um comando, como digitar yes para permitir algo):
```
docker exec -it image-name comandoAserExecutadoNoContainer
```
