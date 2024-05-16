# docker-nginxproxymanager

## Install

* Preparar .env

```bash
cp env_example .env
```

* Iniciar npm

```bash
docker-compose --compatibility up -d; docker-compose logs -ft --tail=35
```

* Agregamos nuestro cidr arg *(lo usamos para filtrar el acceso a sitios especificos)*

```bash
mkdir data/access/ips
cp cidr-arg.conf data/access/ips/cidr-arg.conf
cp RFC1918.conf data/access/ips/RFC1918.conf
cp cloudflare.conf data/access/ips/cloudflare.conf
```

* Y en la pestaña "Advanced" de nuestro sitio quedaria algo asi

```bash
# Allow access from specific IPs
include /data/access/ips/RFC1918.conf;
include /data/access/ips/cidr-arg.conf;
include /data/access/ips/cloudflare.conf;
allow 152.170.176.17/24;

# Deny access to all other IPs
deny all;
```

## Login

```bash
http://127.0.0.1:81

Email:    admin@example.com
Password: changeme
```
