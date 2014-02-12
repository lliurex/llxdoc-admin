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
      Servidor [address = 172.21.240.254, label = 'Servidor Aula']
    }

    network aula {
      label = 'Red del Aula'
      Servidor [address = 10.2.1.254];
      'Cliente 1' [address = 10.2.1.1];
      'Cliente 2' [address = 10.2.1.2];
      'Cliente 15' [address = 10.2.1.15];
    }
   }

En el ejemplo de la figura se plantea un esquema de un aula de informática con 15 ordenadores cliente. Se puede observar que las direcciones IP de dentro del aula corresponden todas al rango 10.2.1.X (reservándose -como convenio- la 254 para el servidor). En la tarjeta externa del servidor aparece una IP interna a la Red Corporativa de Aulas de la Conselleria. Se puede obtener dinámicamente (mediante DHCP) o bien asignar manualmente. En este caso, que sólo existe un servidor en el centro, se recomienda usar la acabada en 254.

.. nota::
   Para los ejemplos de direcciones IP de la Red Corporativa de Aulas se está empleando el rango 172.21.240/24 (sin asignar) para un centro docente hipotético.

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
      ServidorC [address = 172.21.240.254, label = 'Servidor Centro']
      ServidorA1 [address = 172.21.240.253, label = 'Servidor Aula 1']
      ServidorA2 [address = 172.21.240.252, label = 'Servidor Aula 2']
    }

    network centro {
      label = 'Red del Centro'
      ServidorC [address = 10.2.0.254];
      Cliente1AC [address = 10.2.0.1, label = 'Cliente 1']
      ClientenAC [address = 10.2.0.35, label = 'Cliente 35']
    }

    network aula1 {
      label = 'Red del Aula 1'
      ServidorA1 [address = 10.2.1.254];
      Cliente1A1 [address = 10.2.1.1, label = 'Cliente 1']
      ClientenA1 [address = 10.2.1.15, label = 'Cliente 15']
    }

    network aula2 {
      label = 'Red del Aula 2'
      ServidorA2 [address = 10.2.2.254];
      Cliente1A2 [address = 10.2.2.1, label = 'Cliente 1']
      ClientenA2 [address = 10.2.2.20, label = 'Cliente 20']
    }
   }

Siguiendo el esquema, podemos observar una serie de patrones en las direcciones IP que corresponden a las recomendaciones de arquitectura de red de LliureX:

* Las direcciones IP de la red troncal del centro se corresponden al rango asignado al centro. Se comienza numerando al Servidor de Centro con la IP terminada en 254 y se continua -hacia atrás- con las aulas.
* En cada red interna (proporcionada por cada servidor) se repite el patrón siguiente:

  * 10.2.X.254 para el servidor (siendo X = 0 para el caso del servidor de centro, 1 para el Aula 1 y así sucesivamente).
  * las direcciones IP de los clientes comienzan desde el principio del rango en el que están inscritas (en este ejemplo el servidor de centro tendría 35, el "Aula 1" 15 y el "Aula 2" 20 equipos cliente respectivamente.

.. hint:: Como curiosidad técnica, en el funcionamiento interno del modelo de centro se crea una red alias en la red troncal. De esta manera se simplifica el direccionamiento entre los servidores del centro: 10.3.0.254 (centro), 10.3.0.1 (aula 1), 10.3.0.2 (aula 2), etc.

Asistente de configuración del servidor LliureX
-----------------------------------------------

El servidor Lliurex 13.06 incluye un asistente llamado *Zero Server Wizard* que permite realizar todo el proceso de configuración de manera automática y en cómodos pasos. Para acceder a esta herramienta de configuración automática vaya al menú *Aplicaciones* -> *Administración de LliureX* -> *Centro de Control LliureX*. Una vez dentro del *Centro de Control de LliureX* acceda a la pestaña *Sistema* y ejecute *Zero Server Wizard*. Se abrirá una ventana con el siguiente aspecto:

.. image:: ../_static/Zero-Server-Wizard-indep1.png
   :alt: Formulario inicial de Zero Server Wizard para un servidor independiente

En la nueva versión de LliureX se ha añadido el usuario **netadmin** para la administración global. Este usuario se genera al inicializar el servidor con el asistente (*zero-server-wizard*) y lo podremos utilizar para entrar en cualquier equipo de la red (ya que se da de alta en LDAP y tiene permisos de administración).

.. note::
  Hay que diferenciar el usuario **netadmin** del usuario que creamos al instalar el servidor (que será administrador local y no podrá entrar en el resto de equipos de la red).

