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
* La interfaz interna es **eth0** y se mantendrá la siguiente configuración: IP = 10.2.1.254/24 (esto no se aplica a la configuración del modelo de centro).

.. important::
  Es fundamental que las interfaces internas del aula (servidor y cliente) no pertenezcan a la misma red física que la externa.

En particular se debe tener en cuenta:

* Separar las interfaces internas y externas del servidor de aula.
* Conectar la interfaz interna del servidor al conmutador (*switch*) del aula.
* Las rosetas de conexión de los clientes del aula conectadas al mismo *switch* que la conexión interna del servidor.
* En caso de que el *switch* tenga puertos a diferente velocidad, conectar el servidor al puerto más rápido.
