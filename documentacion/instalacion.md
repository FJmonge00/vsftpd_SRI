<img src="../imagenes/MI-LICENCIA88x31.png" style="float: left; margin-right: 10px;" />

# Instalacion ⌨️🖱️

## Pre-Intalación

*Aconsejo no usar una máquina en la ya exista un servicio web proftpd*

*Si tenemos instalado proftpd aconsejo borrarlo por completo...(o algún otro servicio FTP)*

```bash
systemctl stop proftpd.service 
systemctl disable proftpd.service
# SI EXISTEN PROYECTOS Y SERVICIOS EN PRODUCCIÓN CON EL SERVIDOR PROFTPD QUIZÁS
# PREFIERAS HACER UNA COPIA DE SEGURIDAD, VAMOS A ELIMINAR TODO
rm -R -i /etc/proftpd/*
rm -R -i /srv/proftpd/*
apt purge proftpd-basic -y
apt autoremove
```

*Aconsejo no usar máquina en la que ya tuvisemos un servicio web proftpd*

## Instalación

```bash
apt update
apt-get install vsftpd -y
```
<!-- *Descomentamos o añadimos las siguientes estas lineas*

```conf
chroot_list_enable=YES
chroot_list_file=/etc/vsftpd.chroot_list
write_enable=YES
allow_writeable_chroot=YES
``` -->

Activamos el servicio y comprobamos su estado

```bash
systemctl enable vsftpd.service
systemctl restart vsftpd.service
systemctl status vsftpd.service
```

*En Centos...*

```bash
firewall-cmd --zone=public --permanent --add-port=21/tcp
firewall-cmd --zone=public --permanent --add-service=ftp
firewall-cmd --reload
```

![servicio vsftp](../imagenes/estadoServicioInstalacion.jpg)
________________________________________
*[Volver al índice...](../README.md)*
