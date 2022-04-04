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
