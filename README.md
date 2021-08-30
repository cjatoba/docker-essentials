# docker-essentials
Comandos e dicas para utilização do docker

## Definições

Imagem = Funciona como se fosse uma classe, a partir da imagem são criados os containers, que seriam semelhantes a instância de uma imagem.

Container = Funciona como se fosse uma instância de uma imagem Docker.

## Container

Listar todos os containers:
```
docker ps -a
```

Listar apenas os containers em execução:
```
docker ps
```

Listar os ids de todos os containers (A flag -q faz retornar apenas os ids):
```
docker ps -a -q
```

Criar container sem executá-lo:
```
docker create nomeDoContainer
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

### Atalhos no terminal interativo do container:

Fechar o container, matando o bash, e se o bash for o job principal do container, irá matar o container também:
```CTRL + D```

Irá sair do container sem matar ele, apenas fechado. Você pode voltar para este container utilizando o comandoattach:
```CTRL + P CTRL + Q```

# Imagens

Procurar imagens no Docker Hub:
```
docker search nomeDaImagem
```

Baixar imagem do Docker Hub:
```
docker pull nomeDaImagem
```

Executar imagens baixadas (Caso a imagem não existe será feito o download primeiro):
```
docker run ubuntu
```

Listar todas as imagens na máquina:
```
docker images
```

Remover todas as imagens:
```
docker rmi $(docker images -a -q) -f
```

## Volumes

Remover todos os volumes não utilizados:
```
docker volume prune
```

Criar volumes (Mapeia um diretório local para ser sincronizado com o diretório de um container):
```
docker run -v $(caminhoDoDiretorioLocal):caminhoDoDiretorioNoContainer
```

## Arquivo docker-compose.yml

### Definição (Conforme documentação do Docker em https://docs.docker.com/compose/)

Compose é uma ferramenta para definir e executar aplicativos Docker de vários contêineres. Com o Compose, você usa um arquivo YAML para configurar os serviços do seu aplicativo. Então, com um único comando, você cria e inicia todos os serviços de sua configuração.

## Fontes para estudo: 
https://docs.docker.com

https://dev.to/soutoigor/docker-imagens-containers-e-seus-principais-comandos-23p6

https://www.youtube.com/watch?v=REcUhZSSU4U&t=2130s
