# Volumes

## Remove unused volumes:
```
docker volume prune
```

## Create volumes (Maps a local directory to be synchronized with a container directory):
```
docker run -v $(caminhoDoDiretorioLocal):caminhoDoDiretorioNoContainer
```

## Create volume in custom folder for mysql with percona:5.7

- Display user uuid and groups of image

```bash
docker run --rm -t percona:5.7 sh -c 'id'
```

- In this example return is `uid=999(mysql) gid=999(mysql) groups=999(mysql)`

- Change owner and group in path of volume:

```bash
sudo chown -R 999:999 /my_volume_local_path
```

- Add volume em docker-compose file:
```docker-compose
...
  volumes:
    /my_volume_local_path:/var/lib/mysql/
...
```
