<img src="../../imagenes/MI-LICENCIA88x31.png" style="float: left; margin-right: 10px;" />

# Autentificación, Autorización y Control de acceso

## Ejercicio F

- www.web1.org se puede acceder desde la red externa y la red interna.
- www.web2.org sólo se puede acceder desde la red interna.

### Configuración del Virtual Host

*Web1 no configuramos nada respecto al punto anterior* [Clic para ver web1](https://github.com/FJmonge00/nginx_SRI/blob/master/imagenes/web1.png)

![ficheroconfiguracion](../../imagenes/web2Restricciones.png)

**Quitando los comentarios y lineas en blanco así quedaría nuestro sitio virtual:**

```nginx
server {
        listen 80;
        listen [::]:80;
        root /var/www/web1;
        index index.html index.htm index.nginx-debian.html;
        server_name www.web1.org;
        location / {
                # First attempt to serve request as file, then
                # as directory, then fall back to displaying a 404.
                try_files $uri $uri/ =404;
                allow 192.168.3.0/24;
                deny all;
        }
}
```

[Clic para descargar configuración](../../ficherosConfiguracion/web2.org.EjercicioF.conf)

### Recargarmos el servicio de Nginx

```bash
systemctl reload nginx
```

### Comprobación

#### Cliente-red interna

Acceso www.web1.org:

![ficheroconfiguracion](../../imagenes/web1RectricionesInterna.jpg)

Acceso www.web2.org:

![ficheroconfiguracion](../../imagenes/web2RectricionesInterna.jpg)

#### Cliente-red externa

Acceso www.web1.org:

![ficheroconfiguracion](../../imagenes/web1Restricciones.jpg)

Acceso www.web2.org:

![ficheroconfiguracion](../../imagenes/accesoWeb2EjercicioF.jpg)

## Ejercicio G

- www.web1.org contiene un directorio llamado privado.
- Configura una autentificación básica. Sólo puede acceder usuarios válidos.

### Paso previo...

Comprobamos que ``apache2-utils`` se encuentra instalado para poder usar ``htpasswd`` .

*Para RHEL y Centos 8 : ``httpd-tools``*

```bash
apt policy apache2-utils
```
*Si no esta instalado...*

```bash
apt install apache2-utils
```

### Creamos el directorio privado

```bash
mkdir /var/www/web1/privado
chown -R www-data:www-data /var/www/web1/ 
```

![ficheroconfiguracion](../../imagenes/directorioPrivado.jpg)

### Crear archivo de usuario de autenticación HTTP

Comenzamos creando un archivo que almacene pares de usuario y contraseña. Usaremos la utilidad de apache ``htpasswd`` para crear este archivo.

### Creamos usuarios

```bash
htpasswd -c /etc/nginx/conf.d/.htpasswd usuario01
```

*Para crear un segundo usuario NO usar la opción -c.*(Unicamente usar la primera vez para crear el fichero)**

```bash
htpasswd /etc/nginx/conf.d/.htpasswd usuario02
```

### Comprobamos los usuarios creados

```bash
cat /etc/nginx/conf.d/.htpasswd
```

![anadirUsuarios](../../imagenes/anadirUsuarios.jpg)

### Configuración del Virtual Host de www.web1.org

![ficheroconfiguracion](../../imagenes/configuracionEjercicioG.png)

**Quitando los comentarios y lineas en blanco así quedaría nuestro sitio virtual:**

```nginx
server {
        listen 80;
        listen [::]:80;
        root /var/www/web1;
        index index.html index.htm index.nginx-debian.html;
        server_name www.web1.org;
        location / {
                try_files $uri $uri/ =404;
                }
location /privado {
		auth_basic           	"Restricted Access!";
    		auth_basic_user_file 	/etc/nginx/conf.d/.htpasswd; 
	}
}
```
[Clic para descargar configuración](../../ficherosConfiguracion/web1.org.EjercicioG.conf)

### Recargarmos el servicio de Nginx

```bash
systemctl reload nginx.service
systemctl status nginx.service
```
![ficheroconfiguracion](../../imagenes/servicioEjerG.png)

### Comprobación

#### Cliente-red externa

Acceso www.web1.org/privado:

![ficheroconfiguracion](../../imagenes/pruebaEjercicio.gif)

<!-- ![ficheroconfiguracion](../../imagenes/accedoWeb1EjercicioG.png)

![ficheroconfiguracion](../../imagenes/accedoWeb1EjercicioG2.png) -->

#### Posibles errores

>**Importante** En Nginx por defecto esta desactivada la opción de indexar directorios, si no añadimos ningún fichero index en /privado nos dará error `403 forbidden` no confundir con la alerta de usuario no autorizado. 

![ficheroconfiguracion](../../imagenes/posibleError.jpg)

## Ejercicio H

- www.web1.org contiene un directorio llamado privado.
- Desde la red externa pide autorización y desde la red interna NO.

> **IMPORTANTE**
> Para poder realizar esta actividad haremos uso de la directiva ``satisfy``, esta por defecto se encuentra con valor ``All``, esto significa que se deben cumplir todas las condiciones que se definen en la configuración del sitio virtual, (Semejante a definir las reglas con un `AND`). Para poder hacer lo que nos pide este ejercicio cambiaremos el valor de esta directiva por ``any``, es decir, que se cumpla al menos una de las condiciones, (semejante a enumerar las reglas con un `OR`).

>Esta directiva es importante que la cambiemos __**unicamente en la localización de /privado**__ dentro de este sitio virtual. Los clientes que accedan a los recursos que estén ``www.web1.org`` y en concreto ``/privado`` tendrán que cumplir al menos una de las reglas definidas. En este casó serán: Que pertenezca a la red 192.168.3.0/24 ó que se identifiquen con usuario y contraseña.(Si aplica estas normas al sitio virtual por completo pueda dar pié a grandes fallos de seguridad.)

>Dejo la URL para más información sobre la directiva ``satisfy`` por parte de [Nginx.org](http://nginx.org/en/docs/http/ngx_http_core_module.html#satisfy) .

![ficheroconfiguracion](../../imagenes/EjercicioHConfiguracion.png)

**Quitando los comentarios y lineas en blanco así quedaría nuestro sitio virtual:**

```nginx
server {
        listen 80;
        listen [::]:80;
        root /var/www/web1;
        index index.html index.htm index.nginx-debian.html;
        server_name www.web1.org;
        location / {
                try_files $uri $uri/ =404;
                }
location /privado {
                satisfy any; #Al poner esta directiva en any accederá si se cumple alguna de las reglas establecidas
                allow 192.168.3.0/24;
                deny all;
                auth_basic              "Restricted Access!";
                auth_basic_user_file    /etc/nginx/conf.d/.htpasswd;
        }
}
```
[Clic para descargar configuración](../../ficherosConfiguracion/web1.org.EjercicioH.conf)

### Recargarmos el servicio de Nginx

```bash
systemctl reload nginx.service
systemctl status nginx.service
```
![ficheroconfiguracion](../../imagenes/servicioEjerG.png)

### Comprobación

#### Cliente-red externa

Acceso www.web1.org/privado:

![PruebaRedExterna](../../imagenes/pruebaEjercicioHRedExterna.gif)


#### Cliente-red Interna

Acceso www.web1.org/privado:

![PruebaRedInterna](../../imagenes/pruebaEjercicioH.gif)
________________________________________
*[Volver atrás...](../CasosPracticos.md)*

*[Ir a Siguiente punto...](./seguridad.md)*
