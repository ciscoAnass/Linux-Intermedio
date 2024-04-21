# BASIC

- Paquete Pa Instalar :
> apt install mdadm
- Fichero de Configuracion : **/etc/mdadm/mdadm.conf**
-Ver El estado de los RAID : **/etc/proc/mdsatat**

# CREAR RAID 1 + Hot Spare

- Vamod a crear un RAID se llama md1 contiene 2 discos :
> mdadm -C /dev/md1 -l1 -n2 /dev/sdb /dev/sdc

- Andimo el tercer disco como hot spare :
> mdadm /dev/md1 -a /dev/sdd

- Vamos  A Formatearlo y montarlo :
> mkfs.ext4 /dev/md1
> mkdir /mnt/raid1
> mount /dev/md1 /mnt/raid1

- Vamos  provocar un Fallo :
- mdadm /dev/md1 -f /dev/sdb
