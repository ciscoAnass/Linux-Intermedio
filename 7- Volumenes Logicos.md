# Volumenes Logicos


### Instalación de Herramientas Importantes

- Instalamos el paquete `lvm2`:
```bash
apt install lvm2
```

***

### Crear Volumen Físico

- Para crear un volumen físico, utiliza el siguiente comando:
  
```bash
pvcreate /dev/sdb
```
- Para mostrar información sobre los volúmenes físicos, utiliza:

```bash
pvs
```

***

### Crear Grupo de Volúmenes

- Creamos un grupo que llevará dos discos (`sdb` y `sdc`) y lo llamamos `vg1`:

```bash
vgcreate vg1 /dev/sdb /dev/sdc
```

- Para consultar información sobre los grupos de volúmenes, utiliza:
  
```bash
vgs
```
***
### Crear Volumen Lógico

- Creamos un volumen lógico llamado **lv1** de 150 MB a partir del grupo `vg1`:
  
```bash
lvcreate -L 150 -n lv1 vg1
```

- Para consultar información sobre los volúmenes lógicos, utiliza:

```bash
lvs
```

***

### Formatear y Montar los Volúmenes

- Para formatear el volumen lógico:

```bash
mkfs.ext4 /dev/vg1/lv1
```

- Para montar el volumen lógico:

```bash
mkdir /mnt/lv1 && mount /dev/vg1/lv1 /mnt/lv1
```


- Para comprobar el estado de los sistemas de archivos montados:

```bash
df -hT
```
***
### Extender el Volumen Lógico

- Si necesitamos más espacio en el volumen lógico **lv1**, debemos añadir un tercer disco al volumen:
- 
```bash
pvcreate /dev/sdd && vgextend vg1 /dev/sdd
```

- Para añadir más espacio del disco al volumen, utilizamos el siguiente comando:
```bash
lvextend -L +50 /dev/vg1/lv1
 ```
 Básicamente, hemos añadido 50 MB al volumen.


***

### Crear un Snapshot

- Vamos a crear una copia de seguridad de nuestros volúmenes.
- Primero, creamos un snapshot de 50 MB llamado **lv1-fecha**, que es una copia de seguridad del volumen `/dev/vg1/lv1`:
```bash
lvcreate -L 50 -s -n lv1-$(date +%d-%m-%Y) /dev/vg1/lv1
```

- Ahora, creamos una carpeta en `/mnt`:
```bash
mkdir /mnt/snapshot
```

- Finalmente, montamos el snapshot en la carpeta:
```bash
mount /dev/vg1/lv1-fecha /mnt/snapshot
```



