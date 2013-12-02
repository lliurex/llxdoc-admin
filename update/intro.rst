Gestión de actualizaciones en LliureX
=====================================

LliureX es una distribución que está en constante evolución y mejora. Para poder disfrutar de las novedades, y de la corrección de los fallos que van surgiendo, es importante mantener los equipos actualizados. Para mantener los equipos actualizados se emplean dos aplicaciones desarrolladas por LliureX: *LliureX Mirror* y *LliureX Up*.

¿Qué es LliureX Mirror?
-----------------------

LliureX Mirror es una aplicación para crear y mantener una copia actualizada (*mirror*) del repositorio de paquetes de LliureX. La función principal de esta copia es la **distribución óptima de la actualización de los equipos de un aula y de todo el centro**. Además, a partir de LliureX Pandora 13.06, **si emplea clientes ligeros** en el centro, mantener una copia del repositorio de LliureX pasa a ser una **parte fundamental y crítica, sin la cual no es posible funcionar**.  

Racionalizar el acceso a Internet
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

En los centros docentes hay un parque informático numeroso (desde unas pocas decenas de equipos hasta algún que otro centenar, según el centro). En lugar de descargar las actualizaciones desde cada uno de los ordenadores (lo cual colapsaría la conexión a Internet del centro), **es más eficiente descargarse los paquetes nuevos en un solo equipo (que actuará como copia o réplica local)**.

De esta manera, si configuramos adecuadamente los equipos del centro, podremos hacer una actualización a la velocidad de la red local (100 Mbps ó 1 Gbps, dependiendo de la infraestructura existente). Así pues, sólo se utilizaría el ancho de banda de la conexión a Internet para los nuevos paquetes *en un solo equipo*. Tenga en cuenta que, la primera vez que se copia el repositorio, tendrá que descargarlo en su totalidad (actualmente unos 9 GB). Por lo tanto, la duración del proceso inicial de copia será mucho más largo que las actualizaciones posteriores (si se hacen con frecuencia).

Novedades
^^^^^^^^^

A partir de LliureX Pandora 13.06 se dispone de **dos arquitecturas: 32 y 64 bits**. Se emplean 32 bits en el equipamiento más antiguo y en la mayoría de clientes ligeros. Por lo tanto, puede ser necesario mantener ambos repositorios con lo cual duplicamos el tamaño necesario para descargar y alojar en el equipo que hará de *mirror* local.

Además, LliureX Mirror le permite guardar en un dispositivo de almacenamiento externo (p.e. disco USB o *pendrive*) una copia del repositorio. Gracias a esta utilidad es posible descargarse el *mirror* en un sitio con buena conectividad y copiarlo en otro con mala o nula conectividad. El ejemplo más claro es el de un aulario o equipo que está aislado o funciona con un enlace *wifi*. Con este **mecanismo de importación y exportación de repositorios** podemos mantener actualizados equipos en dicha situación.

.. _lliurex_up_intro:

¿Qué es LliureX Up?
-------------------

LliureX Up es un programa que aplica los cambios y novedades disponibles desde el repositorio configurado. Realiza la descarga de las **versiones nuevas de los paquetes que ya están instalados en nuestro sistema** y aplica la instalación ordenada de los mismos. Adicionalmente, LliureX Up realiza varias comprobaciones y corrige lo que sea necesario para el correcto funcionamiento de las actualizaciones.

LliureX Up es accesible desde:

* *Centro de Control de LliureX*, apartado *Sistema* (aparece como *Actualizador de LliureX*)
* Menú del sistema, opción *Actualizar software*
* Desde la línea de comandos, ejecutando la orden *sudo lliurex-upgrade*

Conceptos básicos
-----------------

Para poder sacar el máximo partido a la herramienta de LliureX Mirror es necesario tener claro unos conceptos fundamentales. Los vemos a continuación:

**Repositorio de paquetes** (*pool*)
  Directorio con un conjunto indexado de paquetes dispuestos para su descarga y posterior instalación. Como ejemplo, puede *navegar* por el repositorio de LliureX Pandora en: http://lliurex.net/pandora/

**Paquete**
  Archivo comprimido que contiene los ficheros y la información necesaria para instalar un programa o *parte* de un programa (p.e. una librería). Tienen la extensión *.deb* (Ubuntu está basado en *Debian* GNU/Linux, de ahí las letras de la extensión). Si ha navegado por el *pool* habrá encontrado estos archivos. Podemos ver por ejemplo los paquetes de LliureX Mirror en: http://lliurex.net/pandora/pool/main/l/lliurex-mirror/

**Dependencia**
  Relación que se establece entre paquetes y que indica la necesidad de instalar previamente otros paquetes para el correcto funcionamiento de un paquete concreto. Para saber los paquetes de los que depende, por ejemplo, *stellarium* puede abrir el terminal y teclear: *apt-cache depends stellarium*

**Réplica** (*mirror*)
  Copia exacta de un repositorio con la finalidad de agilizar el proceso de instalación de paquetes y evitar la descarga repetitiva de equipos iguales (caso de un aula de informática). A lo largo de este documento se emplea indistintamente tanto *Réplica de LliureX* como *LliureX Mirror*.

Requisitos de funcionamiento
----------------------------

LliureX Mirror viene instalado en cualquier servidor LliureX (Aula, Centro o Independiente). Para poder utilizarlo en cualquier otro sabor de LliureX deberá de instalar el paquete *python-lliurex-mirror*.

Disponga el espacio suficiente en el disco duro para almacenar la copia del repositorio o repositorios (en el caso de que vaya a copiar ambas arquitecturas, 32 y 64 bits). Igualmente es necesaria una conexión a Internet de Banda Ancha (sobre todo para la copia inicial).

.. note::
  Tenga en cuenta que, dependiendo de la frecuencia de las actualizaciones, la cantidad de archivos a descargar será mayor o menor. Si tardamos uno o varios meses en actualizar la copia local, el tamaño de la descarga puede ser de varias decenas de MB (e incluso algun centenar de MB, dependiendo de lo que se actualice en esas fechas). Así pues, la recomendación es realizarlas al menos semanalmente.
