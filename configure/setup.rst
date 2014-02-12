Configuración inicial
=====================

Al arrancar la máquina con el nuevo sistema, en primer lugar se muestra una ventana para el inicio de sesión de usuario. Introduzca el nombre de usuario y contraseña del usuario (los que haya especificado durante la instalación).

.. note::
  Le recordamos que es muy recomendable realizar una actualización del servidor antes de comenzar la configuración inicial del mismo.

En este punto debe decidir (en función del modelo que desea poner en marcha) el tipo de servidor que ha de instalar. Existen dos opciones según la funcionalidad que desee obtener y los recursos de los que disponga en el centro:

* Modelo de Aula
* Modelo de Centro

Modelo de Aula LliureX
----------------------

Este modelo está pensado para soportar la configuración de aulas independientes. Es la elección lógica cuando los únicos ordenadores del centro están localizados en una o varias aulas. Las ventajas de este modelo son las siguientes:

* Gestión simplificada de los equipos cliente (instalación por red, actualizaciones centralizadas, control del aula, etc.)
* Ahorro en ancho de banda al actuar de servidor proxy-caché (agilizando la consulta repetida a una misma página)
* Perfil de usuario (el alumno puede cambiar de puesto en el aula, teniendo acceso a su carpeta personal)
* Compartición sencilla de ficheros y recogida de trabajos de los alumnos

.. nwdiag::

   nwdiag {
    Internet [shape = cloud]
    Internet -- Router;

    network centro {
      label = 'Red del Centro'
      Router;
      Servidor [label = 'Servidor Aula']
    }

    network aula {
      label = 'Red del Aula'
      Servidor;
      'Cliente 1';
      'Cliente 2';
      'Cliente n';
    }
   }

Modelo de Centro LliureX
------------------------

Cuando un centro docente dispone de más ordenadores fuera de las aulas de informática (sala de profesores, biblioteca, un equipo por cada aula normal, departamentos didácticos, etc.) se puede extender el modelo de aula a todo el centro. Podemos, por ejemplo, utilizar un servidor para la biblioteca, otro para los departamentos y sala de profesores y otro para las aulas tradicionales. O bien un sólo servidor para todos los equipos del centro que no estén en las aulas de informática.

Las ventajas que se pueden obtener de este modelo son:

* Replicación de usuarios y grupos por todo el centro
* Replicación de archivos entre servidores

Es decir, con nuestro usuario y contraseña, podemos acceder a nuestro perfil (carpeta personal, departamental, grupos, etc) desde cualquier equipo cliente del centro.

Para ello hay que cumplir con una serie de recomendaciones:

* Infraestructura de la red del centro en óptimas condiciones (recomendable categoría 6)
* Planificar la distribución de servidores por el centro

  * Decidir cual actuará como maestro (aunque no haya una red jerárquica sino de tipo *bus*)
  * Adecuar el *hardware* a la carga (cantidad de clientes y tipo) que vaya a tener cada servidor
  * Disponer las conexiones de mayor ancho de banda para la comunicación (sincronización) entre servidores

.. nwdiag::

   nwdiag {
    Internet [shape = cloud]
    Internet -- Router;

    network redcentro {
      label = 'Troncal del Centro'
      Router;
      ServidorC [label = 'Servidor Centro']
      ServidorA1 [label = 'Servidor Aula 1']
      ServidorA2 [label = 'Servidor Aula 2']
    }

    network centro {
      label = 'Red del Centro'
      ServidorC;
      Cliente1AC [label = 'Cliente 1']
      ClientenAC [label = 'Cliente n']
    }

    network aula1 {
      label = 'Red del Aula 1'
      ServidorA1;
      Cliente1A1 [label = 'Cliente 1']
      ClientenA1 [label = 'Cliente n']
    }

    network aula2 {
      label = 'Red del Aula 2'
      ServidorA2;
      Cliente1A2 [label = 'Cliente 1']
      ClientenA2 [label = 'Cliente n']
    }
   }

Asistente de configuración del servidor LliureX
-----------------------------------------------

El servidor Lliurex 13.06 incluye un asistente llamado *Zero Server Wizard* que permite realizar todo el proceso de configuración de manera automática y en cómodos pasos. Para acceder a esta herramienta de configuración automática vaya al menú *Aplicaciones* -> *Administración de LliureX* -> *Centro de Control LliureX*. Una vez dentro del *Centro de Control de LliureX* acceda a la pestaña *Sistema* y ejecute *Zero Server Wizard*. Se abrirá una ventana con el siguiente aspecto:

.. image:: ../_static/Zero-Server-Wizard-indep1.png
   :alt: Formulario inicial de Zero Server Wizard para un servidor independiente

En la nueva versión de LliureX se ha añadido el usuario **netadmin** para la administración global. Este usuario se genera al inicializar el servidor con el asistente (*zero-server-wizard*) y lo podremos utilizar para entrar en cualquier equipo de la red (ya que se da de alta en LDAP y tiene permisos de administración).

.. note::
  Hay que diferenciar el usuario **netadmin** del usuario que creamos al instalar el servidor (que será administrado local y no podrá entrar en el resto de equipos de la red).

