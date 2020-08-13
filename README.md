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
#### Es un estándar de cómo se deben instalar las aplicaciones de Oracle en una computadora o servidor. De esta forma, se puede:

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

# 

