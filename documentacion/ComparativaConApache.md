<img src="../imagenes/MI-LICENCIA88x31.png" style="float: left; margin-right: 10px;" />

# Comparativa entre Apache y Nginx 🆚

Mientras que Apache abre un nuevo proceso o hilo para cada solicitud del cliente, nginx trabaja enfocado a eventos. Esto hace que puede procesar solicitudes de forma asíncrona, ahorrando memoria y espacio. Este software de servidor es puede ser usado en GNU/Linux, Mac OS o Windows.


>**¡Importante!**
> Con una arquitectura que soporta eventos, nginx ofrece una alternativa a la gestión de conexiones del servidor HTTP Apache basada en procesos, pero esta característica no es suficiente por sí misma para explicar por qué nginx saca tan buena nota en los tests Benchmark, pues desde la versión 2.4, Apache también soporta un mecanismo de procesamiento de las solicitudes de los clientes basado en eventos. En comparativas de servidores web del tipo *Apache* vs *Nginx* se debe prestar siempre atención, por ello, a los módulos utilizados por los servidores web para realizar los tests, a la configuración de los servidores y a las tareas que deben afrontarse.  — [ionos.es](https://www.ionos.es/)


|Características  |Apache  |Nginx  |
|---------|---------|---------|
|**Contenido estático/dinámico**|Apache es flexible y puede manejar contenido estático y dinámico sin problemas mediante el uso de [MPMs](https://httpd.apache.org/docs/2.4/es/mpm.html), en ocasiones, con un alto costo en recursos.|Nginx maneja el contenido estático muy rápidamente debido a su arquitectura. Para manejar contenido dinámico debe usar un componente externo.|
|**Configuración**|Además de los archivos fuente para su configuración, Apache puede usar archivos ocultos. Por defecto, utiliza las directivas en el archivo .htaccess, lo que permite descentralizar la configuración de Apache, facilitando su implementación incluso cuando no tiene acceso a los archivos .conf dentro del servidor.|Nginx debe ser configurado desde los archivos fuente, en otras palabras, el acceso a su configuración es absolutamente centralizado|
|**Arquitectura**|Flexible a través de módulos, puede estar basado en hilos, procesos o eventos|Arquitectura basada en eventos. Procesamiento asíncrono.|
|**Rendimiento**|El uso de memoria y CPU generalmente es bueno, pero depende de la configuración y selección de módulos.Puede fallar cuando existe alto tráfico (muchas solicitudes concurrentes).|Mejora el rendimiento considerablemente. Debido a la eficiencia de su algoritmo y arquitectura suele consumir menos recursos incluso en picos de sesiones concurrentes.|
|**Características y prestaciones**|Soporte para lenguajes de programación del lado del servidor; soporte de interfaces de lenguajes comunes como Perl, Python y PHP; módulos útiles de autenticación; soporte para SSL/TLS; módulos para proxy; archivos log personalizables; soporte de filtros; reescritura de URL; hosting virtual que permite que el mismo servidor sirva distintos sitios web; métodos de compresión como gzip; entre otras.|Sirve archivos estáticos; soporte SSL/TLS; proxy inverso; balanceo de carga; compresión; control de acceso; reescritura de URL; registro de logs personalizado; hosting virtual que permite que el mismo servidor sirva distintos sitios web; entre otros.|
|**Documentación y soporte**|Ampliamente documentado(guías, manuales, tutoriales e incluso libros).*Al mantenerse como una plataforma gratuita, no provee servicios de soporte*.|Cada vez existe más documentación, pero no es tan abundante como en el caso de Apache. El servicio pago de Nginx plus provee soporte.|

________________________________________
*[Volver al índice...](../README.md)*
