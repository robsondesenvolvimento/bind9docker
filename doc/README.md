docker run -d --name=bind9 --restart=always --publish 53:53/udp --publish 53:53/tcp --publish 127.0.0.1:953:953/tcp --volume C:\bind9\bind\etc:/etc/bind --volume C:\bind9\var\cache\bind:/var/cache/bind --volume C:\bind9\var\lib\bind:/var/lib/bind --volume C:\bind9\var\log:/var/log internetsystemsconsortium/bind9:9.16

https://hub.docker.com/_/bind9/plans/3af94cc6-b9c6-43c2-8658-e617ef977949?tab=instructions

https://github.com/labbsr0x/docker-dns-bind9

https://fabiotavarespr.dev/posts/configurar-dns-bind9-com-docker/