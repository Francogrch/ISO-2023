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
Los Runlevels el el encargado de iniciar o parar una serie de servicios. Sirve para categorizar el estado del SO. Se dividen en 7 niveles.
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
La finalidad del archivo /etc/inittab es la de contener los procesos que se van a ejecutar de a cuerdo a al entrada en inittab .La estructura es: 
id:NivelDeEjecucion:Accion:Proceso
### Punto g

### Punto b
### Punto b
