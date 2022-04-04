## Volumes

Remover todos os volumes não utilizados:
```
docker volume prune
```

Criar volumes (Mapeia um diretório local para ser sincronizado com o diretório de um container):
```
docker run -v $(caminhoDoDiretorioLocal):caminhoDoDiretorioNoContainer
```
