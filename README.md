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


![Descripcion]: https://orlandoolguin.wordpress.com/2010/08/23/que-es-la-ofa/#:~:text=Como%20ya%20lo%20coment%C3%A9%20en,para%20evitar%20cuellos%20de%20botella. datos del OFA.

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


# STANDALONE

![](https://www.oracle.com/technetwork/es/images/clientfailover-standbydatabases-05-2660845.png)


# RAC REAL APPLICATION CLUSTER
![](https://nageshbattula.files.wordpress.com/2018/08/racsharding.png?w=485)




# SGA (SYSTEM GLOBAL AREA)

![](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRMsJ35LO2ODZFI8kM2uAPU_k0A-818RPMwVJ-FRdCSoHM7cak&s)

![](https://upload.wikimedia.org/wikipedia/commons/f/f4/Sga_proceso.png)

# SHARED POOL
![](https://1.bp.blogspot.com/-5wkKVDPyHPs/TZQbR2BLusI/AAAAAAAAADA/MGpeeCGpllw/s1600/Instance.jpg)





# DATABASE BUFFER CACHE

|               |               |
|---------------|---------------|
| KEEP POOL     |  RECLICLE POOL|
| BUFFER CACHE 1|  BUFFER CACHE2|

#

# PGA (PROGRAM GLOBAL AREA)
|SORT AREA      | HASH AREA     | 
|---------------|---------------|
|BITMAP AREAS   | DATOS SESION Y CURSORES|




# procesos de ORACLE

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


# FICHEROS

|TIPO FICHERO|DESCRIPCIÓN|
|--------------------|--------------------|
|CONTROL|Información sobre la base de atos y su estructura|
|DATOS| Ficheros que almacenan los datos de las aplicaciones|
|Redo Log Online|Permiten el recovery de la Base de datos en caso de caída. Contiene las transacciones que se van generando|
|Redo Log archivados|Histórico de las transacciones de la Base de datos. Usados para Recovery|
|Parameter file|Fichero de parámetro de la Base de datos|
|Backup|Ficheros de copia de seguridad|
|Traza y alert|Ficheros de traza y log de la Base de datos|
