
#Diplomado Software Libre GNU/LINUX - EGPP
## Modulo II
##Docente David Mendoza Paco
##Recuperación de PRÁCTICAS EN CLASES

```
Documentar todo el proceso en github, con capturas de pantalla
1. Crear un disco duro virual de 8 G
2. Crear el grupo LVM 'sistemas-kvm01'
3. Crear el grupo LVM 'sistemas-kvm02'
4. Crear 3 volumenes logicos dentro de 'sistemas-kvm'
```
* Primero ingresamos a MAQUINA VIRTUAL y marcamos la máquina virtual

![Imgur](http://imgur.com/UQqWmIx.png)


* Nos vamos a LOCALHOST (click derecho) - DETALLES - ALMACENAMIENTO - ELEGIMOS MAQUINA VIRTUAL - (click) NUEVO VOLUMEN
![Imgur](http://imgur.com/8622Gd9.png)

* Damos el tamaño, indicandole el formato "qcow2" y FINALIZAR
 ![Imgur](http://imgur.com/JLjzad9.png)
 
* Ingresamos a DEBIAN en modo consola el siguiente comando: fdisk -l para ver lo creado e inmediatamente después el comando cfdisk /dev/vdc para crear la nueva partición
![Imgur](http://imgur.com/cPgrzB5.png)

* Para el ejemplo creamos  dos particiones una PRIMARIA y otras dos LOGICAS, siendo la primera BOOTEABLE, escogemos la opción WRITE 
![Imgur](http://imgur.com/MPDvav6.png)

```
REINICIAR LA MAQUINA VIRTUAL
```
* A continuación escribimos el comando: fdisk -l /dev/vdc5
* y creamos la partición física: pvcreate /dev/vdc5
* Ahora creamos los grupos con la siguiente instrucción: vgcreate sistemas-kvm01 /dev/vdc5
* Mostrándonos la siguiente confirmación:
![Imgur](http://imgur.com/MEytrWy.png)

* Ahora creamos el volumen lógico con la siguiente instrucción: 
* lvcreate -L 1000 M -n vol_log1 sistemas-kvm01
* Finalmente vemos los volumenes lógicos creados con la instrucción lvdisplay
![Imgur](http://imgur.com/gaEaIEj.png)

 