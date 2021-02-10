<img src="../../imagenes/MI-LICENCIA88x31.png" style="float: left; margin-right: 10px;" />

# Virtual Hosting

## Crear DocumentRoot y pagina Web

```bash
mkdir /var/www/web1
mkdir /var/www/web2
echo "<h1>Bienvenido a la web1</h1>" > /var/www/web1/index.html
echo "<h1>Bienvenido a la web 2</h1>" > /var/www/web2/index.html
chown -R www-data:www-data /var/www/web1/
chown -R www-data:www-data /var/www/web2/
```

*Comprobamos los ficheros*

```bash
tree /var/www/
ls -l
```
![webs](../../imagenes/documentRoot.jpg)

## Crear Virtual Hosts

```bash
cd /etc/nginx/sites-available/
cp default web1.org
cp default web2.org
vi web1.org 
vi web2.org
cd /etc/nginx/sites-enabled/
ln -s /etc/nginx/sites-available/web1.org .
ln -s /etc/nginx/sites-available/web2.org .
systemctl reload nginx.service # Tambien puede se puede usar nginx -s reload
```
**Definir Virtual Host**

![AccesoALaswebs](../../imagenes/web1.png)

**IMPORTANTE**
> Nginx  cuenta con sitio virtual por defecto. en el caso de que acceda a este y no sea por ningún dominio registrado, este es sitio es el ``default`` que hemos copiado, Nginx solo permite 1 sitio virtual por defecto.

![AccesoALaswebs](../../imagenes/conDefaultServer.png)

*Tendremos que eliminar este parámetro:*

![AccesoALaswebs](../../imagenes/sinDefaultServer.png)

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
}
```

*Al copiar NO copian las tabulaciones*

[Clic para descargar configuración](../../ficherosConfiguracion/web1.org.EjercicioE.conf)

🤔 **¿Tienes Servidor DNS?** 🤔
> Ya que en este momento no cuento con un servidor DNS donde añadir a la zona directa e inversa de estos 2 nuevos dominios, haré uso del fichero ``/etc/hosts`` :

*Cliente Red externa*
![AccesoALaswebs](../../imagenes/ficheroHosts.jpg)

*Cliente Red Interna*
![AccesoALaswebs](../../imagenes/ficheroHostsClienteInterno.jpg)

## Accedemos a la Web 1 y 2:

*En este momento es accesible por todas las interfaces de red del Servidor Web*

```bash
firefox www.web1.org
firefox www.web2.org
```

![AccesoALaswebs](../../imagenes/accesoALaWeb.jpg)

________________________________________
*[Volver atrás...](../CasosPracticos.md)*

*[Ir a Siguiente punto...](./autenAutoContAcc.md)*