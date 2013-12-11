Actualización de equipos
========================

Una vez tenga actualizado el repositorio del que depende su equipo, podrá utilizar LliureX-Up para mantenerlo al día. Un equipo independiente depende por defecto del repositorio central de LliureX. Un equipo dependiente de un servidor (bien sea de aula o de centro) tiene configurado como repositorio por defecto la réplica de dicho servidor. Por tanto, deberemos velar por la previa actualización de dicha réplica si queremos incorporar las últimas correcciones y novedades en el equipo cliente.

Es recomendable incorporar las correcciones y novedades de LliureX con una frecuencia mínima de una vez a la semana. De esta manera evitará la acumulación excesiva de actualizaciones, haciendo que el proceso sea más corto. Para ello puede utilizar el *Planificador de tareas de LliureX* y así programar una vez a la semana el mantenimiento, por ejemplo. Puede acceder al *Planificador* desde el menú de *Administración LliureX*.

.. warning::
   El hecho de tener una réplica del repositorio actualizada no significa que el equipo esté actualizado. Para aplicar las novedades recibidas en dicha sincronización es necesario lanzar LliureX-Up.

Equipo independiente con conectividad
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

En el caso de un equipo independiente (como pueda ser un portátil o el propio ordenador de casa), *no es necesario instalar LliureX Mirror para su actualización*. Únicamente deberá lanzar el *Actualizador de LliureX* o *LliureX Up* por las tres vías posibles comentadas en la :ref:`introducción <lliurex_up_intro>`. Sólo en el caso de que vaya a utilizar dicho equipo para mantener una copia del repositorio de LliureX (y así poder sincronizar otro aislado o con baja conectividad) será necesaria la instalación de LliureX Mirror.

Equipo aislado o con baja conectividad
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Para poder mantener un equipo aislado (o con baja conectividad) actualizado necesitará otro que sí disponga de conectividad (de banda ancha) y que tenga instalado LliureX Mirror (no es necesario que sea un servidor). Los pasos a seguir son:

#. Actualice el repositorio en el equipo con conectividad.
#. Exporte el repositorio actualizado a un dispositivo de almacenamiento externo.
#. Importe el repositorio en el equipo aislado.
#. Proceda con la actualización con LliureX Up.

.. warning::
   Para poder realizar la importación será necesario que el equipo aislado tenga previamente instalado LliureX Mirror. Así pues es conveniente instalarlo en un lugar con conectividad o instalar a mano los paquetes necesarios.

Servidor LliureX
^^^^^^^^^^^^^^^^

Actualizar un servidor conlleva previamente mantener una réplica del repositorio de LliureX. Esta es una tarea crítica por los siguientes motivos:

* Es imprescindible para la generación de las imágenes de los clientes ligeros (caso de que vaya a utilizarlos).
* Es necesario para la actualización a velocidad óptima de los equipos cliente normales.

Por lo tanto, el procedimiento de cada servidor debe ser:

#. Actualizar la réplica.
#. Aplicar las actualizaciones en el servidor (localmente).
#. Aplicar las actualizaciones a todos los clientes (normales) y a las imágenes de los clientes ligeros/semi-ligeros (en su caso).

Si hay más de un servidor en el centro, se puede escoger uno de ellos para usarlo de copia maestra y que el resto (esclavos) se sincronicen con él. De esta manera sólo actualizaríamos una vez desde el repositorio central de LliureX y el resto de servidores lo harían dentro de la red local a mucha mayor velocidad. En este caso, los esclavos deberían configurar como origen la IP externa del que actúe como maestro. Tiene un ejemplo de esta configuración en la sección de :ref:`replicas_internas`.

Equipo cliente
^^^^^^^^^^^^^^

Puede actualizar un conjunto de equipos simultáneamente mediante la herramienta de *Gestión remota de clientes* en el *Centro de Control de LliureX*. Esta herramienta establece (desde un servidor) una conexión con todos los equipos cliente que dependen de él. Aparecerá una línea de comandos desde la que podrá ejecutar una orden simultánea: *sudo lliurex-upgrade*. De esta manera, todos los clientes accedidos empezarán el proceso de actualización usando el repositorio (que debe estar recién sincronizado) del servidor local al que están conectados (si llevan la configuración por defecto).

