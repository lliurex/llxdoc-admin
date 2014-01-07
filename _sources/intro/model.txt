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
