<img src="../imagenes/MI-LICENCIA88x31.png" style="float: left; margin-right: 10px;" />

# Casos Prácticos ⌨️🖱️

## Versión de Nginx instalado.

```bash
vsftpd -v
```

![version vsftpd](../imagenes/vsftpdVersion.jpg)

## Usuarios creados en la instalación.ç

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

LOREM IPSUM LOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMVLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUMLOREM IPSUM

## Configuraciones Acceso Servidor FTP.

<!-- - vsftpd:
    - Recargamos el servicio(no habrá cortes en el servicio): ``systemctl reload vsftpd``
*ó*
    - Reiniciamos el servicio (el servicio no estará disponible mientras se reinicia): ``systemctl restart vsftpd`` -->

## Configuraciones Avanzadas

## [Acceso al servidor FTP: usuarios del sistema.](CasosPracticosApartados/AccesoUsuariosDelSistema.md)
## [Acceso al servidor FTP: anónimo Lectura](CasosPracticosApartados/anonimoLecutura.md)
## [Acceso al servidor FTP: anónimo Escritura/Lectura](CasosPracticosApartados/anonimoEscrituraLectura.md)
________________________________________
*[Volver al índice...](../README.md)*