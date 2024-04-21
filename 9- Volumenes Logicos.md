# IMportante 
- Instalamos el paquete lvm2 :
>apt install lvm2
- Nos vamos a utilizar la herramienta de virtualizacion VirtualBox , pues primero insertamos Discos Virtuales ( para prueba )

# Crear Volumen Fisico

- Para Crear Volumen Fisico :
> pvcreate /dev/sdb
- Para mosntrar infromaciones de los volumenes Fisicos :
> pvs


# Crear Grupo de Volumenes

- Creamos Un grupo que v a llevar 2 disco ( sdb , sdc ) y nos vamos a llamar este grupo vg1
> vgcreate vg1 /dev/sdb /dev/sdc 
- Para Consultar informaciones sobre los Grupos :
> vgs


# Crear Volumen Logico
- Creamos un volumen Logico se llama **lv1** de 150 Mb a partir del grupo vg1 :
> lvcreate -L 150 -n lv1 vg1
- Para Consultar informaciones sobre los Volumenes Logicos :
> lvs


# Formateamos y MOntamos los VOlumenes

- Formatear :
> mkfs.ext4 /dev/vg1/lv1

- Montar :
> mkdir /mnt/lv1
> mount /dev/vg1/lv1 /mnt/lv1

- Comprobacion :
> df -hT


# Extender El volumen Logico

- En caso que necesitamos mas espacio al volumen Logico lv1 , nos tenemos que anadir un tercer disco al volumen :
>pvcreate /dev/sdd
>vgextend vg1 /dev/sdd

- Solo hemos anadido un disco al volumen pero si queremos anadir mas espacio del disco al volumen se hace falta : 
>  lvextend -L +50 /dev/vg1/lv1
Basicamente hemos anadido 50 MB al volumen


# Snapshot

- Nos vamos a tneer una copia de seguridad de nuestro volumenes
- Primero Creamos un snapshor de 50Mb se llama lv1-fecha y es una copia de seguridad del volumen /dev/vg1/lv1
>  lvcreate -L 50 -s -n lv1-$(date +%d-%m-%Y) /dev/vg1/lv1

- ahora creamos una carpeta en /mnt
> mkdir /mnt/snapchot

- ahora montamos en snapshot en la carpeta 
> mount /dev/vg1/lv1-fecha /mnt/snapshot


