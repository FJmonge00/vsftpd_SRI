<img src="../imagenes/MI-LICENCIA88x31.png" style="float: left; margin-right: 10px;" />

# Comparativa entre Proftpd y Vsftpd 🆚

| Proftpd | Vsdtpd |
|-|-|
| Tiene un archivo de configuración principal, que contiene directivas y grupos de directivas que son muy intuitivas si has utilizado el servidor web Apache, ya que se basaron en él para crear Proftpd. | Dispone de configuraciones de IP virtual |
| Dispone de un directorio llamado «.Ftpaccess» que es similar a «.htaccess» de Apache. | Puedes crear usuarios virtuales |
| Es muy fácil configurar múltiples servidores FTP virtuales y servicios FTP anónimos. | Puede funcionar en modo operación independiente o inetd. |
| Dispone de directorios raíz anónimos que no requieren ninguna estructura de directorio, archivos binarios del sistema u otros archivos del sistema. | Las opciones de configuración por parte del usuario son muy avanzadas. |
| No hay comando SITE EXEC,evitando así, los problemas que puede acarrear en seguridad. | Las opciones de configuración por parte del usuario son muy avanzadas. |
| Los directorios y archivos ocultos están basados en permisos de estilo Unix. | Dispone de un acelerador de ancho de banda para que funcionen las cargas y descargas aún mejor. |
| Dispone de modo autónomo que se ejecuta como un usuario sin privilegios para disminuir las posibilidades de ataques. | Puedes establecer límites por IP. |
| Dispone de un servicio para administrar contraseñas ocultas y soporte para cuentas caducadas. | Es compatible con IPv6. |
| Está diseñado de forma modular, eso quiere decir que permite ampliar fácilmente el servidor con módulos como por ejemplo módulos para bases de datos SQL, servidores LDAP, encriptación SSL / TLS, soporte RADIUS, etc. | Tiene soporte de cifrado a través de la integración con SSL. |
| Es compatible y tiene soporte de IPv6. |  |                   |
________________________________________
*[Volver al índice...](../README.md)*
