# docker-nginxproxymanager

## Login

```bash
http://127.0.0.1:81

Email:    admin@example.com
Password: changeme
```

## Host en puerto no-estándar

Para habilitar un host en un puerto no-estándar, se debe editar la configuracion avanzada y exponer el puerto.
Para habilitar host.dominio.com:8080 :
En docker-compose:

```bash
npm-srv:
    container_name: npm-srv
    image: 'jc21/nginx-proxy-manager:latest'
    ports:
      - '80:80'
      - '443:443'
      - '8080:8080'
```

Luego entrar al panel de NPM y generar un host con el nombre de dominio host.dominio.com:8080.
Luego ir a Advanced y agregar las lineas

```bash
#Usar solo una de las opciones
#Escuchar en puerto 8080 HTTP
listen 8080;
listen [::]:8080;
​
#Escuchar en puerto 8080 HTTPS
listen 8080 ssl http2;
listen [::]:8080 ssl http2;
```

## Cargar SSL .key *(Esto ya no es necesario en versiones mas nuevas)*

Para subir certificados, es necesario editar el archivo KEY para que no de error al intentar cargarla:

```bash
-----BEGIN RSA PRIVATE KEY-----
CONTENIDO DE LA LLAVE
-----END RSA PRIVATE KEY-----
```

**FUENTE:** <https://nginxproxymanager.com/setup/#initial-run>
