<img src="../imagenes/MI-LICENCIA88x31.png" style="float: left; margin-right: 10px;" />

# Casos Prácticos ⌨️🖱️

## Versión de vsftpd instalado.

```bash
vsftpd -v
```

![version vsftpd](../imagenes/vsftpdVersion.jpg)

## Usuarios creados en la instalación.

![version vsftpd](../imagenes/usuariosYGrupos.jpg)

## Servicio asociado.

```bash
systemctl status vsftpd.service
```
ó

```bash
/etc/init.d/vsftpd status
```

![servicio vsftp](../imagenes/estadoServicioInstalacion.jpg)

## Ficheros de configuración.

Principalmente casi toda la configuración de vsftpd está en: `/etc/vsftpd.conf`

```bash
find / -iname *vsftpd*
ls -l /etc/vsftpd.conf
```

![servicio vsftp](../imagenes/busquedaDeFicheros.jpg)

### Explicación de las directivas más importantes.


|Directivas  | Descripción  |
|:---------:|---------|
|anonymous_enable=NO|Deshabilitar el inicio de sesión anónimo|
|local_enable=YES|Permite inicios de sesión locales|		 
|write_enable=YES|Habilita los comandos FTP que cambian el sistema de archivos|		 
|local_umask=022|Valor de umask para la creación de archivos para usuarios locales|		     
|dirmessage_enable=YES| Habilita la visualización de mensajes cuando los usuarios ingresan por primera vez a un nuevo directorio |	 
|xferlog_enable=YES|Se mantendrá un archivo de registro que detalla las cargas y descargas|		 
|connect_from_port_20=YES|Usar el puerto 20 (ftp-data) en la máquina del servidor para conexiones de estilo PORT| 
|xferlog_std_format=YES|Mantener el formato de archivo de registro estándar|   
|listen=NO|Evitar que vsftpd se ejecute en modo independiente|   			 
|listen_ipv6=YES|Vsftpd escuchará en un socket IPv6 en lugar de IPv4|		     
|pam_service_name=vsftpd|Nombre del servicio PAM que vsftpd usará|
|userlist_enable=YES|Habilita vsftpd para cargar una lista de nombres de usuario|
|tcp_wrappers=YES|Activa los contenedores tcp |

## Configuraciones Avanzadas ⚙️

### Fichero de configuración ⚠️

Para las prácticas eliminaré todos los comentarios y explicaciones que nos brinda el fichero e iré redirecionando las configuraciones en el fichero principalmente, confiaré en la lectura secuencial del fichero vsftpd.conf dejando algunas configuraciónes por defecto duplicadas con las mias.

## [E) Acceso al servidor FTP: usuarios del sistema 🖥️.](CasosPracticosApartados/AccesoUsuariosDelSistema.md)
## [F) Acceso al servidor FTP: anónimo Lectura 📃](CasosPracticosApartados/anonimoLecutura.md)
## [G) Acceso al servidor FTP: anónimo Escritura/Lectura 📃 📝](CasosPracticosApartados/anonimoEscrituraLectura.md)
## [H) Acceso al servidor FTP: Creación de usuarios virtuales.👥](CasosPracticosApartados/usuariosVirtuales.md)
## [I) Acceso seguro al servidor FTP.🔐](CasosPracticosApartados/cifrado.md)

________________________________________
*[Volver al índice...](../README.md)*