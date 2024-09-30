# BÁSICO

- **Paquete a Instalar:**
  
> Para comenzar a trabajar con RAID, es necesario instalar el paquete **mdadm**. Este paquete proporciona herramientas para crear y gestionar dispositivos RAID en Linux.
  
> ```bash
> sudo apt install mdadm
> ```

- **Fichero de Configuración:**
  
> La configuración de **mdadm** se almacena en el archivo **/etc/mdadm/mdadm.conf**, donde se puede definir cómo se configuran los dispositivos RAID.

- **Ver el estado de los RAID:**
  
> Para comprobar el estado actual de los dispositivos RAID en el sistema, se utiliza el siguiente comando:
  
> ```bash
> cat /proc/mdstat
> ```

# CREAR RAID 1 + Hot Spare

- **Creación del RAID 1:**
  
> Vamos a crear un RAID 1 llamado **md1**, que contendrá dos discos. El RAID 1 es una configuración que proporciona redundancia al duplicar los datos en dos discos. 
> 
> Ejecutamos el siguiente comando para crear el RAID:
  
> ```bash
> sudo mdadm -C /dev/md1 -l1 -n2 /dev/sdb /dev/sdc
> ```

- **Añadir un Hot Spare:**
  
> A continuación, añadimos un tercer disco como hot spare. Un hot spare es un disco que se encuentra disponible para ser utilizado en caso de que uno de los discos activos falle. Esto asegura que el RAID continúe funcionando sin interrupciones.
  
> ```bash
> sudo mdadm /dev/md1 -a /dev/sdd
> ```

- **Formateo y Montaje:**
  
> Ahora procederemos a formatear el RAID y montarlo en el sistema. Formatear el RAID con **ext4** es esencial para que pueda almacenar datos. Luego, creamos un directorio para montarlo y realizamos el montaje.
  
> ```bash
> sudo mkfs.ext4 /dev/md1  
> sudo mkdir /mnt/raid1  
> sudo mount /dev/md1 /mnt/raid1  
> ```

- **Provocar un Fallo:**
  
> Finalmente, para probar la resiliencia del RAID, provocaremos un fallo en uno de los discos. Esto nos permitirá observar cómo el RAID responde a la pérdida de un disco activo y cómo el hot spare toma su lugar.
  
> ```bash
> sudo mdadm /dev/md1 -f /dev/sdb  
> ```
