Instalación
===========

Requisitos hardware del servidor
--------------------------------

Para un adecuado funcionamiento, la configuración mínima recomendada es la siguiente:

* Procesador:  Pentium IV 3 GHz
* Memoria RAM: 4 GB
* Disco duro: 1 disco duro de 80 GB
* 2 tarjetas de red: cada una a 1 Gbps

.. note::
  Para dar servicio a clientes ligeros los requisitos son mayores (ver apartado :doc:`../manage/intro`)

Requisitos de la instalación de red
-----------------------------------

* Acceso a Internet de banda ancha
* Cableado estructurado (categoría 5e)
* Conmutador (*switch*) con al menos 1 puerto a 1 Gbps (para el servidor) y tantos puertos como equipos a 100 Mbps haya en el aula (se recomienda tener todos los puertos a 1Gbps).

Consideraciones previas antes de comenzar la instalación
--------------------------------------------------------

Antes de proceder la instalación hay que tener en cuenta que un servidor LliureX necesita dos interfaces (tarjetas) de red. Una interfaz que sirve para unir el servidor a la red del centro (interfaz externa) y la otra que sirve para dar servicios a los equipos del aula (interfaz interna).

Convenciones que se han decidido en LliureX:

* La interfaz externa es **eth1**
* La interfaz interna es **eth0**

.. important::
  Es fundamental que las interfaces internas del aula (servidor y cliente) no pertenezcan a la misma red física que la externa.

En particular se debe tener en cuenta:

* Separar las interfaces internas y externas del servidor de aula.
* Conectar la interfaz interna del servidor al conmutador (*switch*) del aula.
* Las rosetas de conexión de los clientes del aula conectadas al mismo *switch* que la conexión interna del servidor.
* En caso de que el *switch* tenga puertos a diferente velocidad, conectar el servidor al puerto más rápido.
* Si el servidor dispone de dos discos duros (como suele ser en la dotación de centros) se recomienda emplear todo el segundo disco para el directorio **/net**
* Cuando se le solicite un nombre de usuario (administrador local del servidor), se recomienda usar *adminN* siendo *N* el número de aula de la instalación (reservando *admin0* para el servidor de centro).
* Como nombre del equipo parece sensato incluir igualmente el número del aula. Ejemplos válidos serían: *srv1, aula1, srv_aula1*, etc.

.. tip::
  Para asignar el segundo disco duro al directorio **/net** hay que seleccionar como tipo de instalación la opción "Algo más" (*Puede crear particiones, redimensionarlas o elegir varias particiones para LLiureX*). En el primer disco, necesitará como mínimo una partición de *swap* o intercambio (se recomienda un tamaño ligeramente superior al de la memoria RAM, p.e. si la RAM son 4GB, escoger 5GB de *swap*). El resto del primer disco se puede asignar al directorio raíz (/). Se recomienda el sistema de ficheros *ext4* tanto para la partición del directorio raíz como para la de */net*. Finalmente se asigna todo el segundo disco al montaje de */net*. Puede ver este proceso con más detalle en el apartado :doc:`../advanced/add_disc`.

.. note::
  En el primer arranque, después de finalizar la instalación del servidor, es muy recomendable realizar una actualización del mismo.
