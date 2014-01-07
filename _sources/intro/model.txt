Modelo Cliente/Servidor de LliureX
==================================

Apoyándonos en los conceptos que acabamos de ver, el esquema del modelo más simple sería el siguiente:

.. nwdiag::

   nwdiag {
    Internet [shape = cloud]
    Internet -- Router;

    network centro {
      label = 'Red del Centro'
      Router;
      Servidor [label = 'Servidor Aula'];
    } 

    network aula {
      label = 'Red del Aula'
      Servidor;
      'Cliente 1';
      'Cliente 2';
      'Cliente n';
    }
   }

En este esquema sólo disponemos de un aula de informática. El servidor actúa de intermediario entre la red del centro y los clientes de aula (cada uno de los equipos que utilizan los alumnos del aula). Así pues, sólo nos tenemos que preocupar de mantener actualizada la réplica para proceder a la actualización periódica del aula (tanto de todos los clientes como del propio servidor).
