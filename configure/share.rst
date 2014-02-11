Compartición de directorios en LliureX
======================================

A partir de la versión 13.06 de LliureX (Pandora) se establecen una serie de directorios compartidos en el servidor para distintas finalidades:

Compartir ficheros con todo el aula
-----------------------------------

Todos los usuarios tienen en su carpeta de Inicio (*home*) un directorio llamado *Compartido* (que corresponde a */net/server-sync/share* en el servidor). Únicamente los profesores y el usuario *netadmin* tienen acceso de escritura. Los alumnos solo pueden leer.
Así pues, cuando queramos compartir ficheros o directorios para un aula (o para todo el centro si hemos implantado el *Modelo de Centro*), será la opción más conveniente.

Compartir ficheros con un grupo
-------------------------------

Todos los usuarios de un grupo, a traves del directorio *Compartit_de_grups* de la carpeta de Inicio (que corresponde a */net/server-sync/groups_share* en el servidor). Dentro de esta carpeta se encuentra organizado por los grupos que se hayan creado desde Llum. Los alumnos sólo podrán entrar en el grupo al que pertenezcan (con permisos de lectura). Los profesores y netadmin tienen acceso de escritura.

Compartir ficheros entre profesores
-----------------------------------

Sólo los profesores tienen acceso (en su carpeta de Inicio) al directorio "Professorat" (localizado en */net/server-sync/teachers_share/* en el servidor).

Acceso a las carpetas de los alumnos
------------------------------------

Los profesores también tienen en su carpeta de Inicio un directorio llamado "alum". Este directorio contiene la relación de carpetas correspondiente a cada uno de los alumnos. Desde cada una de estas carpetas se puede acceder al directorio Escritorio y Documentos.

Entrega puntual de trabajos mediante el *Recolector de trabajos*
----------------------------------------------------------------

Esta opción está pensada para que los alumnos puedan entregar ficheros al profesor. 

Tabla resumen
-------------

=============================== ========================== ==========================================
Directorio (dentro de Inicio)   Finalidad                  Perfiles
=============================== ========================== ==========================================
Compartido                      Compartir con el aula      Escritura: netadmin, profesores / Lectura: alumnos
Compartit_de_grups              Compartir con un grupo     Escritura: netadmin, profesores / Lectura: alumnos del grupo
Professorat                     Compartir entre profesores Escritura: netadmin, profesores
alum                            Acceder carpetas alumnos   Escritura: netadmin, profesores
=============================== ========================== ==========================================
