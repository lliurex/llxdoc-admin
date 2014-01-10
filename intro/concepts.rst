Conceptos básicos
=================

Servidor
--------

Un servidor es un ordenador que tiene unas características *hardware* superiores a las de un equipo normal. Su finalidad es proporcionar servicios (de ahí su nombre) a un conjunto de ordenadores (denominados *clientes* por ser los receptores de dichos servicios). Si la función del servidor es muy específica, se matiza en el nombre. Por ejemplo, llamaremos *servidor de ficheros* a un servidor cuya principal función es la de ofrecer espacio en disco (por red). Este espacio se mostrará en cada equipo cliente como un directorio normal pero en realidad corresponde a un directorio del servidor.

LliureX ofrece un servidor *multifunción*, es decir, que incorpora varias funcionalidades en la misma máquina. Actualmente LliureX Servidor puede actuar como:

* Servidor de ficheros (SAMBA)
* Servidor de usuarios y grupos en red (Llum y OpenLDAP)
* Servidor de nombres de dominio (DNS)
* Servidor de direcciones IP dinámicas para los equipos (DHCP)
* Servidor de sincronización temporal (NTP)
* Servidor de bases de datos (MySQL)
* Servidor web (Apache)
* Servidor Proxy-caché (Squid)
* Servidor de clientes ligeros (LTSP)
* Servidor de aprendizaje en línea (Moodle)
* Servidor de actualizaciones (LliureX Mirror)
* Servidor de instalación de equipos por red (llx-netinstall)
* Servidor de gestión de equipos (epoptes y clusterssh)

La colección de servicios es muy amplia. Ningún producto comercial ofrece un *software* equivalente tras una instalación. Desde LliureX intentamos que la configuración y el mantenimiento del aula sea lo más sencillo posible, sin necesidad de amplios conocimientos de informática, para que cualquier docente con muy pocas horas de formación pueda encargarse de ella.

En definitiva, LliureX ofrece una importante colección de servicios mediante una infraestructura compleja pero de gestión simplificada.

Cliente
-------

Un cliente es un equipo normal que hace uso de los servicios ofertados por un servidor o servidores. Pero un cliente puede actuar de varias maneras en función de sus capacidades. Las posibilidades son:

Cliente normal
  Equipo tradicional en el que se instala la versión de LliureX Cliente en su disco duro. La instalación se puede realizar por red o mediante llave USB. Esta versión está diseñada para coordinarse con el Servidor y aprovechar los servicios que éste ofrece. Por ejemplo, el nombre de usuario que se introduzca para comenzar la sesión será validado en el Servidor LliureX y, en función del grupo al que pertenezca, le serán aplicados unos permisos concretos así como unas carpetas determinadas.

Cliente ligero
  Como se verá más adelante (ver apartado :doc:`../manage/intro`), los clientes ligeros tienen una serie de ventajas (reducido tamaño, consumo y facilidad de gestión) que los hacen muy interesantes para un aula. Un cliente ligero sólo necesita el *hardware* que le permita mostrar una sesión gráfica en el servidor. Por ello, la ejecución de las aplicaciones y las necesidades de almacenamiento que tengan estas (RAM y disco duro) tienen lugar en el servidor.

Cliente semi-ligero
  Para los casos en los que el servidor no tiene suficientes recursos (poca RAM o procesador antiguo) y el equipo no es un cliente ligero, se puede configurar LliureX LTSP para repartir los recursos entre el servidor y el cliente. Como se ha podido apreciar, el adjetivo de *ligero* se aplica al *esfuerzo* que tendrá que realizar el equipo del usuario final para poder llevar en marcha las aplicaciones que vaya a usar.

.. note::
  Existe la posibilidad de configurar otras versiones de LliureX (como Infantil o Lleuger) para que arranquen como cliente de LliureX Servidor. Para ello es necesario configurarlo apropiadamente en LliureX LTSP (en el caso de clientes semi-ligeros o ligeros). Más información en :doc:`../manage/intro`

Servicios
---------

Ficheros
^^^^^^^^

La función de servidor de ficheros permite compartir (de manera transparente) uno o varios directorios del servidor con uno o varios equipos de la red. En el equipo cliente aparecerá formando parte de su sistema de ficheros. Por ejemplo, algunos directorios de la carpeta de usuario (por ejemplo *Documentos*, *Descargas*, *Escritorio* y *Compartido*) están físicamente localizados en el servidor. De esta manera, es posible tener las *mismas* carpetas (con su contenido) con independencia del equipo cliente al que nos conectemos o también hacer copias de seguridad centralizadas en el servidor.

Usuarios y grupos en red
^^^^^^^^^^^^^^^^^^^^^^^^

Para poder definir perfiles de usuarios (administrador, profesor, alumno) y aplicar los permisos adecuados es necesario disponer de una base de datos de usuarios y grupos. Esta base de datos se configura inicialmente con la información de GESCEN o ITACA (puede ver el proceso en el apartado :doc:`../configure/import_users`). Se crearán grupos genéricos (como el de profesores) y específicos (correspondientes a los grupos definidos en el curso). Para poder gestionar grupos o usuarios nuevos puede consultar el apartado :doc:`../configure/manage_users`. Así, al introducir nuestro *nombre de usuario* y *contraseña* en la pantalla de entrada estaremos autorizados por el servicio de autenticación de usuarios y nos apareceran los directorios correspondientes a nuestro perfil de usuario.

Nombres de dominio
^^^^^^^^^^^^^^^^^^

Para poder acceder a otra máquina es necesario saber su dirección IP (p.e. 10.2.1.254). Para no tener que recordar los números IP de todas las máquinas a las que nos podamos conectar, se creó el servicio de nombres de dominio. Este servicio traduce un nombre de dominio (p.e. *mirror*) a un número IP (de la misma manera que una guía telefónica o la agenda de contactos de un teléfono móvil). 
