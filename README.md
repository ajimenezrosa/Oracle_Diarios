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


# Que es un diccionario de datos.
    un conjuto de tablas que contiene toda la informacion de metadatos de la base de datos.

|Diccionario de Datos|
|----------------------|
|Un conjunto de tablas de solo lectura que proporcionan informacion sobre la base de datos.|
|Un diccionario de datos Contiene|
|       -La definicion de cada objetivode la tabla de datos|
|       -la Cantidad de espacio asignado y utilizado actualmente por los objetos|
|       -Datos de seguridad, como los hombres de los usuarios, privilegios y roles concedidos a los usuarios|

# 
# 


## Tablas Basicas
#### Estas almacenan informacion sobre la base de datos.  Solo Oracle puede escribir y leer estas tablas.  Los usuarios rara vez acceden a las tablas base directamente porque estan nomalizadas y la mayoria de los datos se almacenan en un formato criptico.

Mi conseje es que se vea estas tablas solo bajo soporte del personal de ORACLE Diretamente.


### Vistas
Permiten ver la informacion de las tablas Base de una forma legible para los Administradores o Desarrolladores. Algunas vistas son accesibles para todos los usuarios de la base de datos, miemtras que otras estan destinadas a los administradores.


la mayoria de las vistas de administracion inician de la siguiente manera.

|Prefijo | Usuarios  | Contenido | Descripcion   |
|------------|-----------|----------|------------------|
|DBA_   | Administradores de base de datos | Todos los Objetos | Algunas vistas DBA_ columnas adicionales que contienen informacion util para el administrador|
|ALL_   | Todos los Usuarios | Objetos a los que el usuario tiene privilegios| Son Tanto los suyos como los de otros usuarios que le han dada permisos|
|USER_  | Todos los usuarios | Objetos propiedad del usuario | La Lista con el prefijo USER_  normalmente excluyen la columna PROPIETARIO. Esta columna esta implicita para que sea el usuario que emite la columna. |



### Vistas dinamicas (Performance Views)

|Vistas dinamicas (Performance Views)|
|------------------------------------|
|Son vistas que nos permiten comprobar la informacion y comportamiento de la  base de datos en tiempo real y dinamico|
|Estas vistas son dinamicas porque se actualizan continuamente con la informacion de la base de datos|
|Estas Vistas a veces reciben el nombre de vistas V$ por que sus nombres comienzan con V$ |


# 

## V$FIXED_TABLE. Encontrar informacion de Vistas y Tablas dinámicas

#### Hacer un listado de las vistas que nos traen informacion del sistema en ORACLE.

~~~SQL
SQL>SELECT * FROM v$FIXED_TABLE;
~~~
#### con esto me aparecen todas las tablas del diccionario de datos. del sistema.
el numero de  tablas o vistas de administracion vaira de version en viersion de ORACLE.  por esto es importante que entre cambio de versions revisemos nuestros scripts de administracion pues muchas tablas pueden varirar.

#### al ejecutar el select de las vistas en SQLPLUS veremos que la muchos nombres de las vistas son muy largos.  es posible que sea un poco dificil leerlos.

 utilizaremos una instruccion para esto que nos permite formatear una columna 
~~~sql
SQL>COL NAME FORMAT A40
~~~
 Para los que no estan familiazados con **sqlplus** esto nos formatea la columna **NAME** a solo 40 caracteres.

si ejectuas el comando ***run*** veras que las columnas salen en un formato mas legibles.

Tambien es posible que quiera paginar mi **select** pues al realizar la instruccion solo veo las ultimas lineas del query resultante. Para paginar el resutltado colocare la siguiente instruccion.
~~~sql
SQL> SET PAUSE ON
~~~

## resultados del query.

## Las tablas X$
![](https://img2018.cnblogs.com/blog/1435518/201902/1435518-20190227145527683-1776936647.png)

para empesar , todo lo que inicia con X$ son tablas del sistema.  No se tocan
No se puedenn moficiar , son de tipo READONLY y casi nunca se utilizan.

***Nota*** estas tablas solo debe actualizarlas y/o modificarlas el propio ***ORACLE***

## Las Tablas V$
![](https://selimkaratas.com.tr/wp/wp-content/uploads/2014/03/CropperCapture473.png)]

Aqui ya podemos ver que los nombres de las tablas tienen un sentido con relacion al mundo de **ORACLE**
Como puedes notar por cada tabla V$ existe una tabla GV$  con el mismo nombre.  esto es porque para las V$ nos muestra las informaciones de la base de datos **ORACLE** que tenemos montada en este momento diremos la Normal o ***Stand Alone***. Pero como sabes podemos tener un **CLUSTER** de bases de datos montado.  La informacion de este ***CLUSTER*** la podriamos sacar de las tablas GV$. Si tenemos N bases de datos montadas en ese ***CLUSTER*** tendremos la informacion todas ellas en la GV$.


Un ejemplo de uso que le podriamos dar a V$fixed_table
es el siguiente.

me es necesario hacer un query de las vistas de las que en su nombre tienen la palabra ***MEMORY*** 
~~~sql
SQL> Select * from V$FIXED_TABLE where name like 'V$%MEMORY%'
~~~
### Haremos un ejemplo de como podemos encontrar informacion de **SGA** utilizando las V$

Podriamos usar un comando de sustitucion ya utilizado anteriormente por nosotros.
~~~sql
SQL> l
    1* SELECT * FROM V$FIXED_TABLE WHERE NAME LIKE 'V$%MEMORY%'    
SQL> C .MEMORY.SGA.
    1* SELECT * FROM V$FIXED_TABLE WHERE NAME LIKE 'V$%SGA%'
SQL>
~~~ 


Tenemos una vista muy basica que nos da la informacion de como esta dividad ahoramismo nuestra SGA.
~~~SQL
SQL> SELECT * FROM V$SGA;
~~~
![](https://image.slidesharecdn.com/adb-inmemory-presentation-170129174432/95/oracle-database-inmemory-13-638.jpg?cb=1485712157)

### Recordemos que tenemos un comando show sga
![](https://3.bp.blogspot.com/-tWTILFqzWlY/UimApeGdBwI/AAAAAAAABNE/iJ061t5-6wU/s1600/1.png)

Esto no es mas que una especie de Atajo que nos muestra la informacion del comando anterior **SELECT * FROM V$SGA**

### Si quiere ser mas concreto sobre lo que tengo en la ***SGA*** debo usar la tabla ***V$sgainfo

![](https://slideplayer.com/slide/4363854/14/images/26/select+%2A+from+v%24sgainfo.jpg)

### Tenemos tambien la tabla ***V$SGASTAT

![](https://slideplayer.com/slide/4363854/14/images/27/select+%2A+from+v%24sgastat+order+by+bytes+desc.jpg)

# 
#  Parámetros de la Base de datos
correspondientes a estos identifican el modo de almacenamiento del objeto dentro de la base de datos. Los parámetros y las cadenas de configuración se agrupan a través de palabras clave de configuración.

Esto nos muestra todos los parametros que tenemos activos dentro de la base de datos.
~~~SQL
SQL> show parameter
~~~
Esta es una Vista que nos muestra mas informacion sobre los parametros pero con muchos mas detalles.
~~~SQL
SQL># Formateamos las columnas para que sea mas legible
SQL> COL NAME FORMAT A30
SQL> COL VALUE FORMAT A30
SQL> SELECT * FROM V$PARAMETER
~~~

Si queremos por ejemplo ver los parametros de la BASE DE DATOS que tienen el nombre ***CACHE***, ***SGA***
~~~sql
SQL> # EXTRAER LOS PARAMETROS QUE CONTENGAN CACHE
SQL> SELECT NAME, VALUE FROM V$PARAMETER WHERE UPPER(NAME) LIKE '%CACHE%'
~~~
~~~sql
SQL> # EXTRAER LOS PARAMETROS QUE CONTENGAN SGA
SQL> SELECT NAME, VALUE FROM V$PARAMETER WHERE UPPER(NAME) LIKE '%SGA%'
~~~


En geodatabases almacenadas en una base de datos de Oracle, los pares de cadenas nombre del parámetro-configuración son utilizados por ArcGIS para los fines siguientes:

+ Establecer las características de almacenamiento de las tablas y los índices.
+ Definir el tipo de almacenamiento para columnas de atributos, ráster y espaciales.
+ Definir la manera de almacenar los documentos XML.
+ Habilitar las palabras clave para los usuarios en la interfaz de ArcGIS.
+ Proporcionar comentarios que describan la palabra clave de configuración.

#### Las combinaciones Palabra clave/Parameter_name son únicas. Por ejemplo, no podría tener el mismo parámetro definido bajo la misma palabra clave, tal y como se muestra aquí:

|KEYWORD    |   PARAMETER_NAME     |     CONFIG_STRING|
|-----------|----------------------|------------------|
|DEFAULTS  |   RASTER_STORAGE      |    BLOB   |
|DEFAULTS  |     RASTER_STORAGE    |   SDO_GEOMETRY|

Sin embargo, la mayoría de parámetros pueden utilizarse bajo varias palabras clave de configuración distintas. Por ejemplo, el parámetro RASTER_STORAGE aparece también agrupado con varias otras palabras clave. En este ejemplo, verá que se incluye en la palabra clave SDELOB.

~~~sql
SQL>  SELECT * FROM SDE.DBTUNE
  2  WHERE KEYWORD = 'SDELOB';
~~~  
|KEYWORD | PARAMETER_NAME   |   CONFIG_STRING|
|--------|------------------|----------------|
|SDELOB  | ATTRIBUTE_BINARY |  BLOB         |
|SDELOB  | GEOMETRY_STORAGE |  SDELOB       |
|SDELOB  | RASTER_STORAGE   |  BLOB         |


# 
# 
# 


#  QUERYS DE ADMINISTRACION _ COLOCADOS AL FINAL---

#
# 



# Definición SQL
#### SQL (Lenguaje de consulta estructurado) es un lenguaje declarativo de acceso a bases de datos relacionales que permite especificar diversos tipos de operaciones en éstas. Una de sus características es el manejo del álgebra y el cálculo relacional permitiendo efectuar consultas con el fin de recuperar, de una forma relativamente sencilla, información de interés de una base de datos, así como también hacer cambios sobre ella. Es un lenguaje de cuarta generación (4GL).

## Consultas SQL útiles para obtener información sobre Oracle Database
#### Vista que muestra el estado de la base de datos:
~~~sql
select * from v$instance
~~~
#### Consulta que muestra si la base de datos está abierta:
~~~sql
select status from v$instance
~~~

#### Vista que muestra los parámetros generales de Oracle:
~~~sql
select * from v$system_parameter
~~~

#### Versión de Oracle:
~~~sql
select value 
from v$system_parameter 
where name = 'compatible'
~~~

#### Ubicación y nombre del fichero spfile:
~~~sql
select value 
from v$system_parameter 
where name = 'spfile'
~~~

#### Ubicación y número de ficheros de control:
~~~sql
select value 
from v$system_parameter 
where name = 'control_files'
~~~

#### Nombre de la base de datos
~~~sql
select value 
from v$system_parameter 
where name = 'db_name'
~~~
#### Vista que muestra las conexiones actuales a Oracle:
~~~sql
select osuser, username, machine, program 
  from v$session 
  order by osuser
~~~  
#### Vista que muestra el número de conexiones actuales a Oracle agrupado por aplicación que realiza la conexión
~~~sql
select program Aplicacion, count(program) Numero_Sesiones
from v$session
group by program 
order by Numero_Sesiones desc
~~~
#### Vista que muestra los usuarios de Oracle conectados y el número de sesiones por usuario
~~~sql
select username Usuario_Oracle, count(username) Numero_Sesiones
from v$session
group by username
order by Numero_Sesiones desc
~~~
#### Propietarios de objetos y número de objetos por propietario
~~~sql
select owner, count(owner) Numero 
  from dba_objects 
  group by owner 
  order by Numero desc
 ~~~

#### Diccionario de datos (incluye todas las vistas y tablas de la Base de Datos):
~~~sql
select * from dictionary
~~~


#### select table_name from dictionary
  
#### Muestra los datos de una tabla especificada (en este caso todas las tablas que lleven la cadena "EMPLO"):
~~~sql
select * 
from ALL_ALL_TABLES 
where upper(table_name) like '%EMPLO%'
~~~
#### Muestra los disparadores (triggers) de la base de datos Oracle Database:
~~~sql
select *
from ALL_TRIGGERS 
~~~
#### Tablas propiedad del usuario actual:
~~~sql
select * from user_tables
~~~
### Todos los objetos propiedad del usuario conectado a Oracle:
~~~sql
select * from user_catalog
~~~
#### Consulta SQL para el DBA de Oracle que muestra los tablespaces, el espacio utilizado, el espacio libre y los ficheros de datos de los mismos:
~~~sql
Select t.tablespace_name  "Tablespace",  t.status "Estado",  
    ROUND(MAX(d.bytes)/1024/1024,2) "MB Tamaño",
    ROUND((MAX(d.bytes)/1024/1024) - 
    (SUM(decode(f.bytes, NULL,0, f.bytes))/1024/1024),2) "MB Usados",   
    ROUND(SUM(decode(f.bytes, NULL,0, f.bytes))/1024/1024,2) "MB Libres", 
    t.pct_increase "% incremento", 
    SUBSTR(d.file_name,1,80) "Fichero de datos"  
FROM DBA_FREE_SPACE f, DBA_DATA_FILES d,  DBA_TABLESPACES t  
WHERE t.tablespace_name = d.tablespace_name  AND 
    f.tablespace_name(+) = d.tablespace_name    
    AND f.file_id(+) = d.file_id GROUP BY t.tablespace_name,   
    d.file_name,   t.pct_increase, t.status ORDER BY 1,3 DESC
 ~~~

#### Productos Oracle instalados y la versión:
~~~sql
select * from product_component_version 
~~~
#### Roles y privilegios por roles:
~~~sql
select * from role_sys_privs
~~~

#### Reglas de integridad y columna a la que afectan:

~~~sql
select constraint_name, column_name 
from sys.all_cons_columns
~~~
#### Tablas de las que es propietario un usuario, en este caso "HR":
~~~sql
SELECT table_owner, table_name 
from sys.all_synonyms 
where table_owner like 'HR'
~~~
#### Otra forma más efectiva (tablas de las que es propietario un usuario):
~~~sql
SELECT DISTINCT TABLE_NAME 
FROM ALL_ALL_TABLES 
WHERE OWNER LIKE 'HR' 
~~~
#### Parámetros de Oracle, valor actual y su descripción:
~~~sql
SELECT v.name, v.value value, decode(ISSYS_MODIFIABLE, 'DEFERRED', 
     'TRUE', 'FALSE') ISSYS_MODIFIABLE,  decode(v.isDefault, 'TRUE', 'YES',
     'FALSE', 'NO') "DEFAULT",  DECODE(ISSES_MODIFIABLE,  'IMMEDIATE',  
     'YES','FALSE',  'NO',  'DEFERRED', 'NO', 'YES') SES_MODIFIABLE,   
     DECODE(ISSYS_MODIFIABLE, 'IMMEDIATE', 'YES',  'FALSE', 'NO',  
     'DEFERRED', 'YES','YES') SYS_MODIFIABLE ,  v.description  
FROM V$PARAMETER v 
WHERE name not like 'nls%'   ORDER BY 1
~~~  
#### Usuarios de Oracle y todos sus datos (fecha de creación, estado, id, nombre, tablespace temporal,...):
~~~sql
Select  * FROM dba_users
~~~
#### Tablespaces y propietarios de los mismos:
~~~sql
select owner, decode(partition_name, null, segment_name, 
   segment_name || ':' || partition_name) name, 
   segment_type, tablespace_name,bytes,initial_extent, 
   next_extent, PCT_INCREASE, extents, max_extents 
from dba_segments 
Where 1=1 And extents > 1 order by 9 desc, 3 
Últimas consultas SQL ejecutadas en Oracle y usuario que las ejecutó:
select distinct vs.sql_text, vs.sharable_mem, 
  vs.persistent_mem, vs.runtime_mem,  vs.sorts,
  vs.executions, vs.parse_calls, vs.module,  
  vs.buffer_gets, vs.disk_reads, vs.version_count, 
  vs.users_opening, vs.loads,  
  to_char(to_date(vs.first_load_time,
  'YYYY-MM-DD/HH24:MI:SS'),'MM/DD  HH24:MI:SS') first_load_time,  
  rawtohex(vs.address) address, vs.hash_value hash_value , 
  rows_processed  , vs.command_type, vs.parsing_user_id  , 
  OPTIMIZER_MODE  , au.USERNAME parseuser  
from v$sqlarea vs , all_users au   
where (parsing_user_id != 0)  AND 
(au.user_id(+)=vs.parsing_user_id)  
and (executions >= 1) order by   buffer_gets/executions desc 
~~~

#### Todos los ficheros de datos y su ubicación:
~~~sql
select * from V$DATAFILE
~~~
#### Ficheros temporales:
~~~sql
select * from V$TEMPFILE
~~~
#### Tablespaces:
~~~sql
select * from V$TABLESPACE
~~~
#### Otras vistas muy interesantes:
~~~sql
select * from V$BACKUP

select * from V$ARCHIVE   

select * from V$LOG   

select * from V$LOGFILE    

select * from V$LOGHIST          

select * from V$ARCHIVED_LOG    

select * from V$DATABASE
~~~

#### Memoria Share_Pool libre y usada:
~~~sql
select name,to_number(value) bytes 
from v$parameter where name ='shared_pool_size'
union all
select name,bytes 
from v$sgastat where pool = 'shared pool' and name = 'free memory'
 ~~~ 
#### Cursores abiertos por usuario:
~~~sql
select b.sid, a.username, b.value Cursores_Abiertos
      from v$session a,
           v$sesstat b,
           v$statname c
      where c.name in ('opened cursors current')
      and   b.statistic# = c.statistic#
      and   a.sid = b.sid 
      and   a.username is not null
      and   b.value >0
      order by 3
~~~      
#### Aciertos de la caché (no debe superar el 1 por ciento):
~~~sql
select sum(pins) Ejecuciones, sum(reloads) Fallos_cache,
  trunc(sum(reloads)/sum(pins)*100,2) Porcentaje_aciertos 
from v$librarycache
where namespace in ('TABLE/PROCEDURE','SQL AREA','BODY','TRIGGER');
Sentencias SQL completas ejecutadas con un texto determinado en el SQL:
SELECT c.sid, d.piece, c.serial#, c.username, d.sql_text 
FROM v$session c, v$sqltext d 
WHERE  c.sql_hash_value = d.hash_value 
  and upper(d.sql_text) like '%WHERE CAMPO LIKE%'
ORDER BY c.sid, d.piece
Una sentencia SQL concreta (filtrado por sid):
SELECT c.sid, d.piece, c.serial#, c.username, d.sql_text 
FROM v$session c, v$sqltext d 
WHERE  c.sql_hash_value = d.hash_value and sid = 105
ORDER BY c.sid, d.piece
Tamaño ocupado por la base de datos
select sum(BYTES)/1024/1024 MB 
from DBA_EXTENTS  
Tamaño de los ficheros de datos de la base de datos:
select sum(bytes)/1024/1024 MB 
from dba_data_files
Tamaño ocupado por una tabla concreta sin incluir los índices de la misma
select sum(bytes)/1024/1024 MB 
from user_segments
where segment_type='TABLE' and segment_name='NOMBRETABLA'
Tamaño ocupado por una tabla concreta incluyendo los índices de la misma
select sum(bytes)/1024/1024 Table_Allocation_MB 
from user_segments
where segment_type in ('TABLE','INDEX') and
  (segment_name='NOMBRETABLA' or segment_name in
    (select index_name 
     from user_indexes 
     where table_name='NOMBRETABLA'))
~~~

#### Tamaño ocupado por una columna de una tabla:
~~~sql
select sum(vsize('NOMBRECOLUMNA'))/1024/1024 MB 
from NOMBRETABLA
Espacio ocupado por usuario:
SELECT owner, SUM(BYTES)/1024/1024 
FROM DBA_EXTENTS MB
GROUP BY owner
~~~

#### Espacio ocupado por los diferentes segmentos (tablas, índices, undo, rollback, cluster, ...):
~~~sql
SELECT SEGMENT_TYPE, SUM(BYTES)/1024/1024 
FROM DBA_EXTENTS MB
GROUP BY SEGMENT_TYPE
~~~
#### Espacio ocupado por todos los objetos de la base de datos, muestra los objetos que más ocupan primero:
~~~sql
SELECT SEGMENT_NAME, SUM(BYTES)/1024/1024 
FROM DBA_EXTENTS MB
GROUP BY SEGMENT_NAME
ORDER BY 2 DESC
~~~
#### Obtener todas las funciones de Oracle: NVL, ABS, LTRIM, ...:
~~~sql
SELECT distinct object_name 
FROM all_arguments 
WHERE package_name = 'STANDARD'
order by object_name
~~~

#### Obtener los roles existentes en Oracle Database:
~~~sql
select * from DBA_ROLES
~~~
#### Obtener los privilegios otorgados a un rol de Oracle:
~~~sql
select privilege 
from dba_sys_privs 
where grantee = 'NOMBRE_ROL'
~~~
#### Obtener la IP del servidor de la base de datos Oracle Database:
~~~sql
select utl_inaddr.get_host_address IP
from dual
~~~ 
#### Mostrar datos de auditoría de la base de datos Oracle (inicio y desconexión de sesiones):
~~~sql
select username, action_name, priv_used, returncode
from dba_audit_trail
~~~
#### Comprobar si la auditoría de la base de datos Oracle está activada:
~~~sql
select name, value
from v$parameter
where name like 'audit_trail'
~~~

 [Parámetros de configuración de Oracle](https://desktop.arcgis.com/es/arcmap/10.3/manage-data/gdbs-in-oracle/configuration-parameters-oracle.htm#:~:text=Los%20par%C3%A1metros%20de%20configuraci%C3%B3n%20identifican,de%20la%20base%20de%20datos./ "Title") inline link.


# Fichero de parámetros SPFILE
![](https://donhk.files.wordpress.com/2019/02/image-7.png)

#### En esta direccion debe haber un archivo con el nombre de la base de datos .ora , lo pasa en realidad es que al Iniciar la base de datos el ***ORACLE*** busca en esta direccion un archivo con eso nombre y lo carga.

#### Hasta la version numero 8 de **ORACLE** todo esto estaba en init.ora.   Este es un archivo de texto , se puede modificar utilizando un editor.  Que pasa con este!!
#### Bueno si haciendo la modificacion yo cometo un error esto podria probocar que la base de datos no arranque.  Por esto ***ORACLE***  incorporo los archivos ***spfile*** , estos deben ser modificados por linea de comando, minimizando asi el margen de error en los mismos.

# 

#### es bueno senalas que todos los parametros que inician con:
 
+ __ ***NO SE TOCAN*** Estos son parametros internos de la base de datos  y salvo que el personal de **ORACLE**  me pida que los toque no deben ser tocados.
+ El * me indica que si hay mas de una Instancia en la base de datos , esto vale para todas las instancias.
+ Aunque vez una **300 o 400** parametros existen unos ***30 o 40 paramatros llamados parametros basicos*** que son los que se suelen tocar.

![](https://hetmanrecovery.com/es/pic/blog/a27/notepad.png)

# 
#  Niveles de los parámetros

#### Anteriormente vimos la vista v$parameter, pero existe otra vista llamada v$spparameter

esta vista muestra los valores que tienen estos parametros dentro del fichero de parametros.

### la V$PARAMETER me muestra el valor actual del parametro
![](https://image.slidesharecdn.com/less04databaseinstance-130111040459-phpapp02/95/less04-database-instance-16-638.jpg?cb=1357877155)
### la V$SPPARAMETER me muestra el valor original del parametro.
![](https://lh3.googleusercontent.com/proxy/_3aZsR6UyPjRQMLgx8-Z9FAU54jj5LYAx5JdBwnGhi5pF1D6YwlOqfgekJ2wx7cf6hcCI3kuchbln-pH)

### Tenemos tambien la vista V$SYSTEM_PARAMETER
    Esta vista me muestra los valores que estan cargados en toda la instancia.



