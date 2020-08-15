# Oracle DBA Register 
## Alejandro Jimenez   
# 
![logo oracle](https://cdn.ttgtmedia.com/visuals/German/article/Oracle-Open-World-Hero.jpg
)



# Instalacion de Oracle

## Requisitos
## Requisitos instalacion Oracle

### requisitos para LINUX
    * OpenSSH
    * Redhat 7
    * Oracle Linux 7
    * Centos 7
    * SUSE Linux Enterprise Server 12 * SP3
    * SUSE Linux Enterprise Server 15
    * Desactivar Transpoarent HugePages
    * 2 Gigas de RAM
    * Resolucion de 1024 x 768
    * 1 GB en /tmp
    * Area de SWAP al menos del mismo * tamano que la memoria.
    * 8GB minimo de espacio en disco

#  

### Requisitos instalacion Oracle Windows.

    * Windows 8.1 x64 - Pro and * Enterprise editions
    * Windows 10 x64 - Pro, Enterprise, * and Education editions.
    * Windows Server 2012 R2 x64 - * Standard , Datacenter, * Essentials, and Foundations * editions.
    * 2 Gigas de RAM
    * Resolucion de 1024 x 768
    * 2 GB en /tmp
    * Area de SWAP al menos del mismo * tanamo de la memoria.
    * 8 GB minimo de espacio en disco

 # 


# Usuarios para lainstalación

## Requisitos instalación Oracle
### GRUPOS

|GRUPO       |  DESCRIPCIÓN |
|------------|------------------------|
|oinstall | Oracle Inventory group| 
|dba        | OSDBA. Privilegios de administración (SYSDBA)|
|oper       | OSOPER. Privilegios limitados de administración (SYSOPER)|
| backupdba | OSBACKUPDBA. Privilegios para gestión de Backup|
| dgdba     | OSDGDBA. Privilegios para Oracle Data Guard |
| mkdba     | OSKMDBA. Encription key management |

#

| USUARIO   | DESCRIPCION       |
|-----------|---------------------------|
| oracle    | Usuario propietario de Oracle |


# 

# OFA (Optimal Flexible Architecture)

## OFA- Optimal Flexible Architecture

+ Es un estándar que determina como e deben instalar las aplicaciones de Oracle en una áquina:
+ Organizar grandes cantidades de datos y software en el disco para mantener el orden y para evitar cuellos de botella.
+ Facilitar tareas administrativas, por ejemplo para backups
+ Facilitar el cambio entre distintas bases de datos Oracle.
+ Manejar de manera adecuada el crecimiento de las bases de datos Oracle.
+ Ayudar a evitar la defragmentación y evitar la contención de datos.
+ Etc.


# OFA- Optimal Flexible Architecture.
![](https://1.bp.blogspot.com/-HnYOX-k8sss/TZccdpcyw9I/AAAAAAAAGOE/g6y7P8Cw8F0/s1600/soa_dir.png)


# ¿Qué es la OFA?
#### Es un estándar de cómo se deben instalar las aplicaciones de Oracle en una computadora o servidor.

####  De esta forma, se puede:

+ Organizar grandes cantidades de datos y software en el disco para mantener un orden y para evitar cuellos de botella.
+ Facilitar tareas administrativas sobre la misma información, como respaldos.
+ Facilitar el cambio entre distintas bases de datos Oracle.
+ Manejar de manera adecuada el crecimiento de las bases de datos Oracle.
+ Ayudar a evitar la defragmentación y evitar la contención de datos.

##  Características de la OFA
#### Una instalación correcta de la OFA, ayuda en los siguientes rubros:

+ Organización de File Systems (o directorios). Se mantienen organizados facilitando la administración de la información como agregar datos, usuarios, crear bases de datos o incluso, agregar hardware.
+ Cargas distribuidas de I/O. Al estar distribuidos los distintos archivos de datos y aplicación, en distintos discos (file systems), se facilita la paralelización de tal forma que se mejora el performance.
+ Soporte de Hardware. En muchos casos, se puede prevenir la compra de hardware al organizar de manera correcta la información.
+ Prevención contra fallas de drives. Cuando se distribuyen las aplicaciones en más de un disco, se evita que cuando uno falle, afecte a otras aplicaciones.
+ Distribución de directorios home de Oracle. Distintos directorios home, pueden ser distribuidos en distintos discos o file systems así como su contenido.
+ Integridad de directorios home de login. Se pueden agregar, mover o borrar directorios home de login sin tener que revisar programas que hacen referencia a ellos.
+ Independencia de subdirectorios Unix. Al usar distintos subdirectorios de Unix y categorizándolos para una mínima afectación entre archivos de distintas categorías.
+ Soporta ejecución concurrente de aplicaciones. Al estar todo debidamente separado, se pueden tener por ejemplo, escenarios en los cuales por ejemplo, se puede tener una versión de pruebas para una nueva base de datos sin tener que prescindir de la anterior. Una vez probada y verificada, el hacer el upgrade de la original resulta muy fácil.
+ Separa información administrativa para cada base de datos. De ésta forma, se gana mucha ventaja al administrar las bases de datos.
+ Usa nombres de archivos de base de datos consistentes. Los archivos de la base de datos deben tener nombres adecuados que los distingan de otro tipo de archivos y al mismo tiempo, saber a qué base de datos y tablespace pertenecen. Los control files, redo log files y data files, se identifican de manera fácil.
+ Separación de contenido de tablespaces. El contenido de los tablespaces, es separado para minimizar la fragmentación y la contención de I/O, así como maximizar la administración de los mismos.

 [Descripcion de OFA](https://orlandoolguin.wordpress.com/2010/08/23/que-es-la-ofa/#:~:text=Como%20ya%20lo%20coment%C3%A9%20en,para%20evitar%20cuellos%20de%20botella./ "Title") inline link.

# 
# 


# Instalación en Linux. Configurar parametros de Kernel


+ fs.file-max = 6815744
+ kernel.sem = 250 32000 100 128
+ kernel.shmmni = 4096
+ kernel.shmall = 1073741824
+ kernel.shmmax = 4398046511104
+ kernel.panic_on_oops = 1
+ net.core.rmem_default = 262144
+ net.core.rmem_max = 4194304
+ net.core.wmem_default = 262144
+ net.core.wmem_max = 1048576
+ net.ipv4.conf.all.rp_filter = 2
+ net.ipv4.conf.default.rp_filter = 2
+ fs.aio-max-nr = 1048576
+ net.ipv4.ip_local_port_range = 9000 65500



# Instalacion de paquetes linux

+ oracle   hard   nproc    16384
+ oracle   soft   stack    10240
+ oracle   hard   stack    32768
+ oracle   hard   memlock    134217728
+ oracle   soft   memlock    134217728

# Creacion de Grupos y Usuarios necesarios

+ yum install -y bc    
+ yum install -y binutils
+ yum install -y compat-libcap1
+ yum install -y compat-libstdc++-33
+ #yum install -y dtrace-modules
+ #yum install -y dtrace-modules-headers
+ #yum install -y dtrace-modules-provider-headers
+ yum install -y dtrace-utils
+ yum install -y elfutils-libelf
+ yum install -y elfutils-libelf-devel
+ yum install -y fontconfig-devel
+ yum install -y glibc
+ yum install -y glibc-devel
+ yum install -y ksh
+ yum install -y libaio
+ yum install -y libaio-devel
+ yum install -y libdtrace-ctf-devel
+ yum install -y libXrender
+ yum install -y libXrender-devel
+ yum install -y libX11
+ yum install -y libXau
+ yum install -y libXi
+ yum install -y libXtst
+ yum install -y libgcc
+ yum install -y librdmacm-devel
+ yum install -y libstdc++
+ yum install -y libstdc++-devel
+ yum install -y libxcb
+ yum install -y make
+ yum install -y net-tools # Clusterware
+ yum install -y nfs-utils # ACFS
+ yum install -y python # ACFS
+ yum install -y python-configshell # ACFS
+ yum install -y python-rtslib # ACFS
+ yum install -y python-six # ACFS
+ yum install -y targetcli # ACFS
+ yum install -y smartmontools
+ yum install -y sysstat
+ 
# Added by me.
+ yum install -y unixODBC

# Instalación de Oracle con RPM

# Arquitectura general de ORacle

![structura oracle 1](https://adminbasedatosudla.files.wordpress.com/2014/10/arqoracle.png)


### STANDALONE

![](https://www.oracle.com/technetwork/es/images/clientfailover-standbydatabases-05-2660845.png)


### RAC REAL APPLICATION CLUSTER
![](https://nageshbattula.files.wordpress.com/2018/08/racsharding.png?w=485)




### SGA (SYSTEM GLOBAL AREA)

![](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRMsJ35LO2ODZFI8kM2uAPU_k0A-818RPMwVJ-FRdCSoHM7cak&s)

![](https://upload.wikimedia.org/wikipedia/commons/f/f4/Sga_proceso.png)

### SHARED POOL
![](https://1.bp.blogspot.com/-5wkKVDPyHPs/TZQbR2BLusI/AAAAAAAAADA/MGpeeCGpllw/s1600/Instance.jpg)





### DATABASE BUFFER CACHE

|               |               |
|---------------|---------------|
| KEEP POOL     |  RECLICLE POOL|
| BUFFER CACHE 1|  BUFFER CACHE2|

# 

### PGA (PROGRAM GLOBAL AREA)
|SORT AREA      | HASH AREA     | 
|---------------|---------------|
|BITMAP AREAS   | DATOS SESION Y CURSORES|




### procesos de ORACLE

| PROCESO BACKGROUND | DESCRIPCIÓN |
|--------------------|--------------|
|DBWn- Database Writer Process| Encargado de escribir el contenido de los buffers en los datafiles. Los procesos DBWn son los esponsables de escribir los buffers modificados (dirty) en la cache de buffer a disco. |
|LGWR- Log Writer Process | Este proceso es que se encarga de escribir el contenido del búfer de Redo Log en los ficheros de Redo Log Online.|
| CKPT- Checkpoint Process | Almacena información de los checkpoint en el fichero de control y en la cabecera de los archivos de datos |
| SMON (System Monitor) | Se encarga del recovery de la instancia en el arranque y de limipar segmentos temporales y no utilizados |
| PMON (Process Monitor) | Se encarga del recovery de un proceso al fallar. Motnitoriza sesiones, limpia la buffer cache y libera recursos |
| RECO. Recover Process |Solo para entornos distribuidos. Recupera transacciones distribuidas incorrectas |
| LREG (Listener Registration) | Registra información de la instancia y los prcesos dispatcher con el Listener |
| ARCn (Archiver) | Copua los redo log online a redo log archivados |


### FICHEROS

|TIPO FICHERO|DESCRIPCIÓN|
|--------------------|--------------------|
|CONTROL|Información sobre la base de atos y su estructura|
|DATOS| Ficheros que almacenan los datos de las aplicaciones|
|Redo Log Online|Permiten el recovery de la Base de datos en caso de caída. Contiene las transacciones que se van generando|
|Redo Log archivados|Histórico de las transacciones de la Base de datos. Usados para Recovery|
|Parameter file|Fichero de parámetro de la Base de datos|
|Backup|Ficheros de copia de seguridad|
|Traza y alert|Ficheros de traza y log de la Base de datos|

# 

### MULTITENANT

##### Oracle Multitenant es la arquitectura de la nube de base de datos de la nueva generación. Ofrece aislamiento, agilidad y economías de escala. Una base de datos de contenedor multiempresa puede contener muchas bases de datos de tipo "pluggable". Una base de datos existente puede simplemente adoptarse sin que se requieran cambios en la aplicación. Oracle Multitenant complementa totalmente otras opciones, incluidos Oracle Real Application Clusters y Oracle Active Data Guard.

![](https://1.bp.blogspot.com/-RioWC28x8_M/U3gHLHwigmI/AAAAAAAADhw/sto69JfXkiQ/s1600/3.jpg)

### Links de consultas 




 [Oracle Multitenant](https://www.oracle.com/es/database/technologies/multitenant.html#:~:text=Oracle%20Multitenant%20es%20la%20arquitectura,datos%20de%20tipo%20%22pluggable%22./ "Title") inline link.

 [Database Concepts / 17 Introduction to the Multitenant Architecture](https://docs.oracle.com/database/121/CNCPT/cdbovrvw.htm#CNCPT89234/ "Title") inline link.



# Creación de Bases de Datos

### Creacion de Bases de datos Simples DBCA
### Creación de una base de datos Oracle
##### Después de verificar la instalación y la configuración de Oracle Database, cree las bases de datos Oracle que necesite.

+ Si utiliza Oracle Database sin bases de datos en spera, siga el procedimiento Cómo crear una base de datos primaria de Oracle. Este procedimiento no es necesario para las bases de datos adicionales que puede crear y configurar.

+ Si utiliza Oracle Data Guard, cree las siguientes instancias de base de datos:

    + Instancia de base de datos primaria. Para obtener instrucciones sobre cómo crear una base de datos primaria, consulte Cómo crear una base de datos primaria de Oracle.

    + Instancia de base de datos en espera. Una instancia de base de datos en espera puede ser una instancia de base de datos física en espera o una instancia de base de datos lógica en espera. Para obtener instrucciones sobre cómo crear instancias de base de datos en espera, consulte la documentación de Oracle Database.

##### Cómo crear una base de datos primaria de Oracle
1-  **Prepare los archivos de configuración de base de datos.**
###### Coloque todos los archivos de la base de datos (archivos de datos, archivos de registro de rehacer y archivos de control) en los dispositivos globales sin formato compartidos o en el sistema de archivos del cluster. Consulte Preparación de los nodos y los discos para obtener información sobre las ubicaciones de instalación.

**Nota** - Si la base de datos se encuentra en la zona no global, no coloque los archivos relacionados con la base de datos en los dispositivos sin formato compartidos.
#
En los archivos  ***init$ORACLE_SID.ora o config$ORACLE_SID.ora***, es posible que necesite modificar las asignaciones para control_files y background_dump_dest con el fin de especificar las ubicaciones de los archivos de control y los archivos de alerta.
# 

**Nota** - Si utiliza la autenticación de Solaris para inicios de sesión de base de datos, defina la variable remote_os_authent del archivo ***init$ORACLE_SID.ora*** en True.

2- **Inicie la creación de la base de datos mediante una utilidad de la siguiente lista:**

 + El instalador de Oracle
 + El comando sqlplus(1M) de Oracle
 + El asistente de configuración de bases de datos de Oracle

Durante el proceso de creación, compruebe que todos los archivos de la base de datos estén en la ubicación adecuada, ya sea en los dispositivos globales compartidos, en el sistema de archivos del cluster o en un sistema de archivos local de alta disponibilidad.

3. **Compruebe que los nombres de los archivos de control coincidan con los de los archivos de configuración.**
4. **Cree la vista** ***v$sysstat.***

Ejecute las secuencias de comandos de catálogos que crean la vista ***v$sysstat.*** El supervisor de fallos de HA para Oracle utiliza esta vista. Para obtener más información, consulte la documentación de Oracle Database.

Pasos siguientes

Cuando haya completado los pasos indicados en esta sección, vaya a Configuración de permisos de base de datos de Oracle.

#### Configuración de permisos de base de datos de Oracle
Precaución - No realice los pasos de esta sección para una base de datos física en espera de Oracle Database.

Siga el procedimiento de esta sección para definir los permisos de base de datos para una base de datos Oracle primaria o una base de datos Oracle lógica en espera.


#### Cómo definir permisos de bases de datos Oracle
###### Permita el acceso para el usuario y la contraseña que se utilizarán para la supervisión de fallos.
###### Para utilizar el método de autenticación de Oracle Database, otorgue a este usuario autoridad en la vista v_$sysstat y en la vista v_$archive_dest.
~~~sql
# sqlplus  "/ as sysdba"
sql>    create user user identified by passwd;
sql>    alter user user default tablespace system quota 1m on system;
sql>    grant select on v_$sysstat to user;
sql>    grant select on v_$archive_dest to user;
sql>    grant select on v_$database to user;
sql>    grant create session to user;
sql>    grant create table to user;
sql>    create profile profile limit PASSWORD_LIFE_TIME UNLIMITED;
sql>    alter user user identified by passwd profile profile;

sql>    exit;
#
~~~
Puede usar este método para todas las versiones de Oracle Database admitidas.

+ Para utilizar el método de autenticación de Solaris, aplique los pasos que se describen a continuación:
    + Confirme que el parámetro remote_os_authent esté definido en TRUE

~~~sql
# sqlplus  "/ as sysdba"
sql> show parameter remote_os_authent

NAME                       TYPE        VALUE
---------------------- ----------- ---------------
remote_os_authent         boolean     TRUE
~~~

 + Determine el valor del parámetro os_authent_prefix.
 ~~~sql
sql>  show parameter os_authent_prefix

NAME                       TYPE        VALUE
---------------------- ----------- ---------------
os_authent_prefix         string      ops$
 ~~~
# 
+ Otorgue a la base de datos el permiso para utilizar la autenticación de Oracle Solaris

~~~sql
sql> create user prefix user identified by externally default 
tablespace system quota 1m on system;
sql> grant connect, resource to prefix user;
sql> grant select on v_$sysstat to prefix user;
sql> grant select on v_$archive_dest to prefix user;
sql> grant select on v_$database to prefix user;
sql> grant create session to prefix user;
sql> grant create table to prefix user;
sql> exit;
#
~~~

##### Los elementos reemplazables de estos comandos son los siguientes:


+ prefix es el valor del parámetro os_authent_prefix. El valor predeterminado de este parámetro es ops$.
user es el usuario para el que está activando la autenticación de Oracle Solaris. Asegúrese de que el usuario tenga los archivos en el directorio ***$ORACLE_HOME.***
# 
**Nota** - No agregue ningún espacio entre ***prefix y user.***

2. **Configure NET8 para el software Oracle Solaris Cluster.**

El archivo listener.ora debe ser accesible desde todos los nodos o zonas del cluster. Coloque los archivos en el sistema de archivos de cluster o en el sistema de archivos local de cada uno de los nodos o cada una de las zonas donde podrían ejecutarse los recursos de Oracle Database.

# 
***Nota*** - Si coloca el archivo listener.ora en una ubicación que no sea el directorio /var/opt/oracle o el directorio $ORACLE_HOME/network/admin, debe especificar la variable TNS_ADMIN o una variable de Oracle Database equivalente en un archivo de entorno de usuario. Para obtener información sobre las variables de Oracle Database, consulte la documentación de Oracle Database.

También debe ejecutar el comando clresource(1CL) para definir el parámetro de extensión de recurso User_env, que proporciona el archivo de entorno de usuario. Consulte Propiedades de extensión de SUNW.oracle_listener o Propiedades de extensión SUNW.oracle_server para obtener detalles sobre formato.

# 

HA para Oracle no impone ninguna restricción en el nombre del listener; puede ser cualquier nombre de listener de Oracle Database que sea válido.

El siguiente ejemplo de código identifica las líneas de listener.ora que se actualizan.



### Ficheros y directorios creados

### Procesos y memoria

### Uso de DBCA en modo avanzado. Crear Bases de Datos

### Configuracion de Variables de Entorno

# 
# 

# SQL*Plus. Herramienta de administración
### SqlPlus

**SQLPlus** es un programa de línea de comandos de Oracle que puede ejecutar comandos ***SQL y PL/SQL*** de forma interactiva o mediante un script. ... Los programadores y los administradores de bases de datos (DBA's) lo usan de forma muy común como interfaz fundamental en la mayoría de las instalaciones de software de Oracle.


### Manuales de SqlPlus..

 [Manual de Iniciación a Oracle](https://www.mundoracle.com/entorno-sql-plus.html?Pg=sql_plsql_10.htm/ "Title") inline link.
#


### Algunos Comandos Utiles de SqlPlus.

~~~sql
~~~

~~~sql
SELECT SYSDATE FROM DUAL;
~~~

+ L muestra comando almacenado en memria
+ R ejecuta lo que esta en memoria

+ si coloco un numero por ejemplo 2 , me muestra la linea 2.
+ pudeo hacer cambios con esto por ejemplo si coloco 2 * , me cambia la linea 2 por un *
+ otra forma es C .SYSDATE.*. Lo que hacemos aqui es sustituir SYSDATE por *
+ Del 2 , nos borra la linea 2 del comando almacenado en memoria.

Otra forma es lanzar un comando para trabajar con un editor **ed** carga un editor en el cual podemos trabjar la linea de comandos.

Si quiero cambiar el editor por defecto del **ed** puedo usar el siguiente comando
~~~linux
SQL> def_editor=gedit
~~~
en este caso me coloca el **gedit** como editor por defecto.  





# Administracion Basica de la Base de Datos.

## Arranque y Parada 
![](https://ittutorial.org/wp-content/uploads/2019/02/img_5c751e8c40812.png)
### Faces del aranque de una base de datos ORACLE.

|Faces de Startup [Arranque]|
|---------------------------|
|PARADA |
|NOMOUNT|
|MOUNT  |
|ABIERTA|

~~~plsql
~~~

### Arranque y parada de una base de datos Oracle

## 1. Objetivos

Explicar brevemente los diferentes métodos para parar y arrancar una base de datos ORACLE.

## 2. Arrancar base de datos

El arranque de una base de datos ORACLE requiere tres etapas
1. Arrancar la instancia
2. Montar la base de datos
3. Abrir la base de datos

+ **Arrancar la base de datos**

En esta parte del arranque se generan los procesos background.

Se crea la SGA. Sus dimensiones se basan en el fichero de inicialización «init.ora».

SQLPLUS> connect sys as sysdba connected SQLPLUS> startup nomount Oracle Instance started

+ Montar la base de datos

En esta parte del proceso de arranque se produce la conexión al/los archivo/s de control.


En este estado se puede:

+  Cambiar el modo de archivado de la B.D.
+ Renombrado de archivos de Redo Log o del asociado al tablespace SYSTEM
+ Crear, modificar o suprimir nuevos Redo Log o grupos de Redo Log

Partiendo del anterior estado ( nomount ), montamos la base de datos de la siguiente forma:
~~~sql
SQLPLUS> alter database mount database mounted
~~~
En caso de que queramos iniciar la base de datos en este estado bastaría con hacer lo siguiente:
~~~sql
SQLPLUS> connect sys as sysdba connected 
SQLPLUS> startup mount Oracle Instance started Database mounted
~~~    
+ ***Abrir base de datos***

En esta parte de proceso abren todos los ficheros asociados a los tablespaces y los ficheros de Redo Log.

La B.D. está accesible para todos los usuarios

Si es necesaria una recuperación (por un fallo de luz o CPU), se produce en este momento.

Partiendo del anterio estando ( mount ), abrimos la base de datos de la siguiente forma:
~~~sql
SQLPLUS> alter database open database opened
~~~

En caso de que queramos iniciar la base de datos en este estado bastaría con hacer lo siguiente:

~~~sql
SQLPLUS> connect sys as sysdba connected 
SQLPLUS> startup Oracle Instance started Database opened
~~~ 
## 3. Más alternativas para el arranque de base de datos
Arranque solo para usuarios con el privilegio RESTRICTED SESSION
~~~sql
SQLPLUS> startup restrict
~~~

Arranque forzado
~~~sql
SQLPLUS> startup force
~~~

Arranque con un fichero de parámetros distinto al habitual o localizado en una situación diferente a donde se encuentra por defecto
~~~sql
SQLPLUS> startup pfile=/oracle/database/init2.ora
~~~ 

## 4. Parada base de datos
La parada de una B.D. Oracle se realiza mediante el comando SHUTDOWN desde SQL*DBA después de haber establecido una conexión como SYS AS SYSDBA

Existen tres tipos de shutdown:
1. shutdown normal
2. shutdown immediate
3. shutdown abort
    + ***Shutdown normal***

Espera a que los usuarios conectados actualmente finalicen TODAS las operaciones.
Evita nuevas conexiones. Los usuarios que intentan conectarse reciben el mensaje «Shutdown in progress».
Cierra y desmonta la B.D. Cierra la SGA para los procesos background.
No necesita recuperacion al arrancar la base de datos.
~~~sql
SQLPLUS> connect sys as sysdba connected SQLPLUS> shutdown normal
~~~
 

+ ***Shutdown immediate***

Espera a que las transacciones actuales se completen.
Evita nuevas transacciones y nuevas conexiones. Los usuarios que intentan conectarse o los que ya están conectados al intentar realizar una nueva transacción reciben el mensaje «Shutdown in progress».
El proceso PMON finaliza las sesiones no activas y realiza ROLLBACK de aquellas transacciones que no estén validadas.
Cierra y desmonta la B.D. Cierra la SGA para los procesos background.
No necesita recuperacion al arrancar la base de datos.
~~~sql
SQLPLUS> connect sys as sysdba connected SQLPLUS> shutdown immediate
~~~ 

+ ***Shutdown abort***

Parada drástica, no espera a que los usuarios conectados actualmente finalicen sus transacciones. El usuario conectado recibe el mensaje «No logged on».
No se realiza ROLLBACK de las transacciones pendientes.
El proceso PMON finaliza las sesiones no activas y realiza ROLLBACK de aquellas transacciones que no estén validadas.
SI necesita recuperacion al arrancar la base de datos.
~~~sql
SQLPLUS> connect sys as sysdba connected SQLPLUS> shutdown abort
~~~ 


# 
# Pruebas con los modos de la DB

### Arrancar la Base de datos. Comando STARTUP

parar la base de datos de forma immediata
~~~sql
SQL> shutdown immediate
~~~


#### la forma mas estandar para arrancar una base de datos es el comando.
~~~sql
SQL> startup
~~~


#### para arrancar la base de datos en un modo concreto.  Por ejemplo en modo nomoun

#### Ejecutaremos el siguiente comando
~~~sql
SQL> startup nomount
~~~

en este modo podemos mostrar el proceso pmon.
~~~linux
px -ef | grop pmon
~~~

#### Generalmente cargamos el modo ***nomount*** para solucionar algun problema. por ejemplo se estropeo un archivo o fichero y queremos recuperarlo.

#### para pasar del modo ***nomount*** al modo ***mount*** podemos hacerlo de la siguiente manera.
~~~sql
SQL> ALTER DATABASE MOUNT;
~~~


#### Para pasar a la fecha de ***Abierto*** ejecutaremos el comando:
~~~sql
ALTER DATABASE OPEN;
~~~

## Parar la Base de Datos. Introducción

| Modo de Parar La DB |   Descripcion e implicaciones|
|-----------------|-----------------------|
|NORMAL        | Finalizacion normal de la Base de Datos. Espera a que los usuarios terminen la session antes de cerrar del todo|
|IMMEDIATE  | Termina todas las transacciones pendientes y cierra la Base de Datos.|
|TRASACTIONAL | Espera a que terminen las transacciones en marcha , pero no permite que comience ninguna nueva |
| ABORT  | no espera a nada. Solo deberia usarse en casos excepcionales |


### Ejercicios con paradas de Bases de Datos oracle
![](https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcQjm6dWDW8F3U5VLZFnziBfOpEmrvxnk_xUEw&usqp=CAU)
~~~sql
shutdown transactional
~~~
##### de existir transacciones abiertas la base de datos termina dichas transacciones y luego hace el SHUTDOWN
~~~sql
shutdown IMMEDIATE;
~~~
##### de existir transacciones abiertas la base de datos cierra todas las transacciones sin hacer commit.

~~~SQL
SHUTDOWN ABORT
~~~
#### esto es como apagar el servidor o desconectarle la energia. para tales fines la la base de datos se detendra sin importar si tiene transacciones o no pendientes.  
#### ***Nota*** esto solo debe utilizarce en casos de EMERGENCIA.

# 

## Poner la Base de datos en modo Administrador (QUIESCE)

Este modo se utiliza para colocar la base de Datos en modo ***QUIESCE***  esto para poder realizar algunas tareas de administracion.


#### Crear un usuario en oracle usando sqlplus.

~~~sql
SQL>CREATE USER USER1 IDENTIFIED BY usu1;
SQL>GRANT CONNECT, RESOURCE TO USU1;
~~~

Colocar base de datos en modo QUIESCE
Este seria un modo administrativo en el cual solo puede entrar el administrador de la base de datos.

Esto se utiliza generalmente para realizar tareas de mantenimiento de las bases de datos.

~~~sql
SQL>ALTER SYSTEM QUIESCE RESTRICTED;
~~~

para regresar la base de datos a modo normal utilizaremos los siguientes comandos.

~~~sql
SQL>ALTER SYSTEM UNQUIESCE;
~~~

***Nota***
Es necesario decir que todas las conecciones a la base de datos que no sean de usuarios administradores estaran inhabilitadas. 

##  Diccionario de Datos: Tablas y Vistas
![Diccionario de Datos: Tablas y Vistas](https://slideplayer.es/slide/3613109/12/images/4/Oracle+Database%3A+Conceptos+Fundamentales+de+SQL+II+3-4.jpg)


### Que es un diccionario de datos.
    un conjuto de tablas que contiene toda la informacion de metadatos de la base de datos.

|Diccionario de Datos|
|----------------------|
|Un conjunto de tablas de solo lectura que proporcionan informacion sobre la base de datos.|
|Un diccionario de datos Contiene|
|       -La definicion de cada objetivode la tabla de datos|
|       -la Cantidad de espacio asignado y utilizado actualmente por los objetos|
|       -Datos de seguridad, como los hombres de los usuarios, privilegios y roles concedidos a los usuarios|
