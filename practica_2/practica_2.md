# Practica 2
## Punto 1 - Editor de textos
- a) vim, nvim, nano
- b) Se diferencian en que un editor de texto, permite modificar el texto mientras que cat, more o less, solo muestra el texto en pantalla. Vim tiene tres modos de operacion, el Normal, el Visual, y el de Inserción. 
- c) Los comandos mas comunes pueden ser: w, q, dd, y, p, u ,/x

## Punto 2 - Proceso de Arranque de SystemV
### Punto a)
- 1 Se empieza a ejecutar el codigo del BIOS
- 2 El BIOS ejecuta el POST
- 3 El BIOS lee el sector de arranque (MBR)
- 4 Se carga el gestor de arranque (MBC)
- 5 El bootloader carga el kernel y el initrd
- 6 Se monta el initrd como sistema de archivos raiz y se inicializan componentes esenciales (ej.: scheduler)
- 7 El Kernel ejecuta el proceso init y se desmonta el initrd
- 8 Se lee el /etc/inittab
- 9 Se ejecutan los scripts apuntados por el runlevel 1
- 10 El final del runlevel 1 le indica que vaya al runlevel por defecto
- 11 Se ejecutan los scripts apuntados por el runlevel por defecto
- 12 El sistema esta listo para usarse


### Punto b
El proceso INIT lo ejecuta el kernel y es el encargado de cargar todos los subprocesos necesarios para el correcto funcionamiento del SO. 
### Punto c
El comando pstree muestra en pantalla los directorios en formato de arbol.

### Punto d
Los Runlevels son los encargado de iniciar o parar una serie de servicios. Sirve para categorizar el estado del SO. Se dividen en 7 niveles.
### Punto e
Existen 7, y permiten iniciar un conjunto de procesos al arranque o apagado del sistema
Segun el estandar:
- 0: halt (parada)
- 1: single user mode (monousuario)
- 2: multiuser, without NFS (modo multiusuario sin soperte de red)
- 3: full multiuser mode console (modo multiusuario completo por consola)
- 4: no se utiliza
- 5: X11 (modo multiusuario completo con login grafico basado en X)
- 6: reboot
En /etc/inittab se encuentra donde se define que Runlevel ejecutar al inciar el SO.
No todas las distribuciones respetan estos estandares.
### Punto f
La finalidad del archivo /etc/inittab es definir que Runlevel se va a ejecutar.La estructura es: 
id:NivelDeEjecucion:Accion:Proceso
### Punto g
sudo init <\Y>
El cambio no es permantente ya que cuando se reinice la pc, a volver a cargar el inittab, volveria al RunLevel X.
### Punto h
La finalidad es la de saber que procesos se tienen que lanzar al momento de apagar, y de prender la pc, de acuerdo al runlevel. Estos se almacenan en /etc/rcX.d , siendo x el nivel de runLevel.
Debido a que el formato es de esta manera:
        
        [S|K]<orden><nombreScript>

El orden, y en que momento ejecutar cada script esta definido en el formato.
S de start. K de kill(apagado).

### Punto i
El insserv se utiliza para administrar el orden de los enlaces simboliscos de los Scripts RC.
El beneficio principal es la capacidad de modificar facilmente la cantidad de scripts que se ejecutan al prender o apagar la pc.

### Punto j
El Upstarts maneja el arranque mediante jobs, que se ejecutan de manera asincronica. 

### Punto k
SystemV funciona de manera secuencial y sincronica, mientras que Upstart de manera asicronica, oriendado a eventos.
El primero las depencias hay que especificarlas, mientras que en Upstart esto lo hace automaticamete.
Ademas Upstart tiene mas registros sobre los eventos, por ende es mas facil el mantenimiento.

### Punto l
En Upstart se le llaman Jobs, que es un conjunto o un script en particular y se encuntra en /etc/init.d

### Punto m
Las primeras tres lineas es sobre informacion del Job. Tanto del nombre, en comentario, descripcion y el autor del mismo
Luego especifica que job tiene ejecutar de a cuerdo a los runlevels que nombra.
Y por ultimo el ejecutable.

### Punto n
El systemd es un proceso de arranque que centraliza la administracion de demonios y de librerias del sistema.
El control de dependencias de manera logica, y en ves de solo cargar las dependencias necesaria carga un grupo de dependencias anteriormente definido. Mejora el paralelismo del booteao.

### Punto enie
Hace referencia a la posibilidad de no tener cargado los scripts en memoria y solamente cargarlos al momento de activar un socket, o conectar algun dispisitivo.

### Punto o
El cgroup organiza el conjunto de procesos, de manera jerarquica tal que al momento de necesitar algun otro proceso, se cargue un grupo de procesos que psoiblemente se vayan a utilizar.


## Punto 3

### Punto a
Claro, aquí tienes la respuesta más concisa:

En un sistema GNU/Linux, los archivos clave utilizados para guardar información de los usuarios son:

1. `/etc/passwd`: Contiene información básica de los usuarios.
2. `/etc/shadow`: Almacena contraseñas cifradas.
3. `/etc/group`: Guarda información sobre grupos de usuarios.
4. `/home`: Directorio donde se encuentran los directorios de inicio de los usuarios.
5. `/var/spool/mail` y `/var/mail`: Almacenan buzones de correo si el sistema utiliza correo local.
6. `/var/log`: Registros del sistema, incluyendo registros de inicio de sesión de usuarios y eventos del sistema.
   
Estos archivos y directorios son fundamentales en la gestión de usuarios y grupos en el sistema.

### Punto b
Hacen referiencia a los ID de los usuarios y a los ID de los grupos. Y estos son unicos no pueden repetirse, hay casos donde esto puede ocurrir, pero va a depender del sistema, si es que maneja de mala manera los permisos.

### Punto c
El usuario root es el usario con mas privilegios y permisos del sistema, y solamente existe un solo root, la UID es la 0.

### Pundo d
groupadd catedras
usueradd -u iso2017 -d /home/iso_2017 -g catedra
su
cd /home/iso_2017
touch hello.py
userdel -r iso2017

### Punto e


