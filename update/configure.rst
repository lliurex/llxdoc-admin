Configuración de LliureX Mirror
===============================

Configuración del repositorio de LliureX Mirror
-----------------------------------------------

La configuración por defecto tiene como repositorio central el de LliureX en la Conselleria d'Educació, Esport i Cultura (accesible por la Red Corporativa de aulas).

Réplicas del repositorio central de LliureX
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Hay dos réplicas adicionales disponibles en:

* Universidad Politécnica de Valencia: http://lliurex.upv.es/pandora/
* RedIRIS (Red Académica Española): http://ftp.rediris.es/mirror/Lliurex/pool/pandora/

Puede configurar cualquiera de estos dos repositorios **si comprueba que van más rápidos desde su localización**. Tenga en cuenta que estas réplicas se refrescan con una periodicidad menor a la del respositorio central de LliureX.

Para ello será necesario introducir el repositorio escogido en el campo marcado de la imagen y pulsar sobre el botón de actualización indicado:

.. figure:: ../_static/lliurex-mirror-other-repo.png
   :height: 400px
   
   *Especifique otro repositorio para LliureX Mirror*

.. _replicas_internas:

Réplicas internas
^^^^^^^^^^^^^^^^^

En caso de tener configurado el Modelo de Centro de LliureX (en el que hay un servidor de centro y otro por cada aula) puede configurar este campo **para que los servidores de aula se actualicen a partir del mirror del servidor de centro**. Para ello deberá introducir http://10.3.0.254/mirror/ en la configuración de LliureX Mirror de cada servidor de aula. De esta manera sólo el servidor de centro se sincronizará con el repositorio central de LliureX.

Si decide configurarlo de esta manera, es recomendable programar las actualizaciones para que se hagan de manera automática (por ejemplo con la Herramienta de Planificador de Tareas). Puede escoger realizarlas por la noche (bien todas las noches, o varias noches a la semana). Debe evitar actualizar los servidores de aula a una hora en la que pueda estar actualizándose el servidor de centro dado que podrián surgir inconsistencias en los repositorios. Por ello *no se deben solapar los tiempos de actualización entre servidores*. De todas maneras recuerde que (de tener esta configuración) **la actualización de los servidores de aula se hará a la velocidad de la red local** del centro (100 Mbps o 1 Gbps, dependiendo de la infraestructura instalada).

Importación y exportación de repositorios
-----------------------------------------

Otra de las funcionalidades que incorpora LliureX Mirror, para mayor comodidad, es la posibilidad de importar y exportar repositorios. Esta característica es **muy interesante para reducir drásticamente el tiempo de la copia inicial de un repositorio**. Si, por ejemplo, tenemos dos servidores aislados y en el primero disponemos de una copia actualizada del *mirror*, podemos exportar (copiar en un medio de almacenamiento externo) dicha réplica para poder importarla en el segundo servidor. Téngase en cuenta que no es necesario que ambos sean servidores para realizar esta operación, es decir, podemos instalar LliureX Mirror y obtener una réplica del repositorio en un LliureX Escriptori con buena conectividad. A continuación, exportarlo a un *pendrive* y, por último, importarlo en un LliureX Infantil o un servidor de LliureX que no tiene conectividad con el resto del centro.

Puede ver en la imagen las opciones que permiten realizar estas operaciones.

.. figure:: ../_static/lliurex-mirror-import-export.png
   :height: 400px

   *Puede importar réplicas de repositorios y exportar el repositorio local para otro equipo*
