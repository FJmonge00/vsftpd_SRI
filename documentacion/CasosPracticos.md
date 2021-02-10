<img src="../imagenes/MI-LICENCIA88x31.png" style="float: left; margin-right: 10px;" />

# Casos Prácticos ⌨️🖱️
<!-- NGINX -T -->

## Primeros pasos

### Pre-Intalación

*Aconsejo no usar una máquina en la ya exista un servicio web apache2*
*Si tenemos instalado apache2 aconsejo borrarlo por completo...*

```bash
systemctl stop apache2.service 
systemctl disable apache2.service
# SI EXISTEN PROYECTOS Y SERVICIOS WEBs EN PRODUCCIÓN EN EL SERVIDOR WEB QUIZÁS
# PREFIERAS HACER UNA COPIA DE SEGURIDAD DE ESTO YA QUE LOS VAMOS A ELIMINAR
rm -R /etc/apache2/*
rm -R /var/www/*
rm -R /var/log/apache2/
apt purge apache2
apt autoremove
```
*Aconsejo no usar máquina en la que ya tuvisemos un servicio web apache*

### Instalación

```bash
apt update
apt-get install nginx -y
systemctl enabled nginx.service
systemctl status nginx.service
```

### Versión de Nginx instalado.

```bash
nginx -v
```

![version nginx](../imagenes/versionNginx.jpg)

### Servicio asociado.

```bash
systemctl status nginx.service
```
ó

```bash
/etc/init.d/nginx status
```
![servicio nginx](../imagenes/servicioNginx.jpg)

 ### Ficheros de configuración.

```bash
ls -la --color /etc/nginx/
ls -la --color /usr/share/nginx/
ls -la --color /var/www/
```

![ficheros nginx](../imagenes/ficherosConfNginx.png)

### Página web por defecto.

```bash
echo "<h1>Bienvenidos a mi servidor web</h1>" > /var/www/html/index.nginx-debian.html
echo "<h2>Mi nombre es: Fran Monge</h2>" >> /var/www/html/index.nginx-debian.html
firefox localhost #Para abrir la página con firefox
```
*En principio no es necesario reiniciar el servicio web cada vez que hay un cambio dentro de los dicheros del DocumentRoot, pero si no se actualizará:*

- Navegador:
    1. Borrar caché del navegador
    2. Pestaña de incógnito navegador (*evitamos tener que volver a borrar caché*)
    3. Ingresamos nuestra dirección ``http://localhost`` 
- Nginx:
    - Recargamos el servicio(no habrá cortes en el servicio): ``systemctl reload nginx``
*ó*
    - Reiniciamos el servicio (el servicio no estará disponible mientras se reinicia): ``systemctl restart nginx``

![Acceso nginx](../imagenes/accesoDefecto.png)

## Configuraciones Avanzadas

### [Virtual Hosting](CasosPracticosApartados/VirtualHosting.md)
### [Autentificación, Autorización y Control de acceso](CasosPracticosApartados/autenAutoContAcc.md)
### [Seguridad](CasosPracticosApartados/seguridad.md)
________________________________________
*[Volver al índice...](../README.md)*