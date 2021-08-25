# Implementação do Bind9 no docker.
> Nos diretórios seguem configurações do bind9

```bash
$ docker run -d --name=bind9 --restart=always --publish 53:53/udp --publish 53:53/tcp --publish 127.0.0.1:953:953/tcp --volume C:\bind9\bind\etc:/etc/bind --volume C:\bind9\var\cache\bind:/var/cache/bind --volume C:\bind9\var\lib\bind:/var/lib/bind --volume C:\bind9\var\log:/var/log internetsystemsconsortium/bind9:9.16
```
```yml
# Environment file .env
COMPOSE_PROJECT_NAME=bind-dns
```

```yml
# Docker compose file docker-compose.yml
version: '3.9'

services:
  bind:
    container_name: bind-robson
    image: internetsystemsconsortium/bind9:9.16
    restart: always
    ports:
      - 53:53/udp
      - 53:53/tcp
      - 953:953/tcp
    volumes:
      - C:\App\bind\etc:/etc/bind
      - C:\App\bind\var\cache\bind:/var/cache/bind 
      - C:\App\bind\var\lib\bind:/var/lib/bind
      - C:\App\bind\var\log:/var/log

networks:
  default:
    name: minharede
    external: true
```

```bash
$ docker-compose up -d # Cria a composição
$ docker-compose -p bind-dns up -d # Cria a composição com nome de grupo
$ docker-compose down # Destre a composição
```

```bash
$ dig @127.0.0.1 sgt.localhost. axfr
$ dig @127.0.0.1 api.sgt.localhost. ns
$ dig @127.0.0.1 api.sgt.localhost. a
$ dig @127.0.0.1 api.sgt.localhost. soa
```

1- [DockerHub](https://hub.docker.com/_/bind9/plans/3af94cc6-b9c6-43c2-8658-e617ef977949?tab=instructions)
2- [Docker Exemplo Git](https://github.com/labbsr0x/docker-dns-bind9)
3- [Site de exemplo](https://fabiotavarespr.dev/posts/configurar-dns-bind9-com-docker/)