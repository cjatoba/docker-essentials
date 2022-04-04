## Docker Compose

### Definição do Docker Compose adaptada do endereço https://docs.microsoft.com/pt-br/visualstudio/docker/tutorials/use-docker-compose:

Docker Compose é uma ferramenta desenvolvida para ajudar a definir e compartilhar aplicativos com vários contêineres. Com o Compose, você pode criar um arquivo YAML para definir os serviços e com um único comando, pode girar tudo ou desmontar tudo isso.

A grande vantagem de usar o Compose é que você pode definir a pilha de aplicativos em um arquivo (docker-compose.yml), mantê-lo na raiz do seu repositório de projetos (agora é controlado por versão) e permitir que outra pessoa contribua com facilidade para o seu projeto. Alguém precisaria apenas clonar seu repositório e iniciar o aplicativo de composição. na verdade, você pode ver alguns projetos em GitHub/GitLab fazendo exatamente isso agora.

### Definição (Conforme documentação do Docker em https://docs.docker.com/compose/)

Compose é uma ferramenta para definir e executar aplicativos Docker de vários contêineres. Com o Compose, você usa um arquivo YAML para configurar os serviços do seu aplicativo. Então, com um único comando, você cria e inicia todos os serviços de sua configuração.

### Comandos

Executar todos os services em background (A flag -d permite a execução dos conteiners sem bloquear o terminal):
```
docker-compose up -d
```

Reiniciar um service:
```
docker-compose restart <service name>
```

Executar services específicos em background:
```
docker-compose up -d <service name 1> <service name 2>
```

Examinar os logs de todos os services (A flag -f permite a exibição dos logs em tempo real):
```
docker-compose logs -f
```

Examinar os logs de services específicos (A flag -f permite a exibição dos logs em tempo real):
```
docker-compose logs -f <service name 1> <service name 2>
```

Desmontar todos os containers em execução:
```
docker-compose down
```

Desmontar todos os containers em execução e remover os volumes:
```
docker-compose down --volumes
```

Remover container em execução:
```
docker-compose rm -v <service name>
```
