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