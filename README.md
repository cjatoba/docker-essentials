# docker-essentials
Comandos e dicas para utilização do docker

Imagem = Funciona como se fosse uma classe, a partir da imagem são criados os containers, que seriam semelhantes a instância de uma imagem

Container = Funciona como se fosse um instância de uma imagem Docker 

Listar todos os containers:
```
docker ps -a
```

Listar apenas os containers em execução:
```
docker ps
```

Listar os ids de todos os containers (A flag -q fas retornar apenas os ids):
```
docker ps -a -q
```

Listar todas as imagens na máquina:
```
docker images
```

Criar container sem executá-lo:
```
docker create nomeDoContainer
```

Parar um container
```
docker stop idDoConteiner
```

Parar os containers com base no retorno de um comanfdo docker
```
docker stop $(docker ps -a -q)
```

Inicia um container parado:
```
docker start idDoConteiner
```

Exibe as estatísticas de uso do container
```
docker stats idDoConteiner
```

Remove um container (Utilizar o -f no final caso o container esteja em execução)
```
docker rm idDoConteiner
```

Abrir o terminal do container:
```
docker exec nomeDaImagem bash
```

Utilizar o terminal interativo do container (O terminal interativo serve para conserguirmos responder as questões que surgirem durante a execução de um comando, como digitar yes para permitir algo):
```
docker exec -it image-name comandoAserExecutadoNoContainer
```

Comandos no terminal interativo:

```CTRL + D```
Vai fechar o container, matando o bash, e se o bash for o job principal do container, irá matar o container também.

```CTRL + P CTRL + Q```
Irá sair do container sem matar ele, apenas fechado. Você pode voltar para este container utilizando o comandoattach.

Rodar um container em background, utilizando a flag -d de detached:
```
docker -d image-name
```

Retorna para um container fechado (mas não parado):
```
docker attach container-id
```

Remover todos os container:
```
docker rm $(docker ps -a -q); 
```

Remover todas as imagens
```
docker rmi $(docker images -a -q) -f
```

Remover todos os volumes
```
docker system prune --volumes
```

Procurar imagens no Docker Hub:
```
docker search nomeDaImagem
```

Baixar imagem Docker:
```
docker pull nomeDaImagem
```

Executar imagens baixadas (Caso a imagem não existe será feito o download primeiro):
```
docker run ubuntu
```

Criar volumes (Mapeia um diretório local para ser sincronizado com o diretório de um container)
```
docker run -v $(caminhoDoDiretorioLocal):caminhoDoDiretorioNoContainer
```

Configurar o diretório inicial do container:
```
docker run -w caminhoDoDiretorioNoContainer
```

Mapear porta (Neste exemplo a porta 80 local é mapeada para a porta 80 do container apache2)
```
docker run -p 80:80 apache2
```

Arquivo docker-compose.ylm

## Fontes para estudo: 
https://dev.to/soutoigor/docker-imagens-containers-e-seus-principais-comandos-23p6

https://www.youtube.com/watch?v=REcUhZSSU4U&t=2130s
