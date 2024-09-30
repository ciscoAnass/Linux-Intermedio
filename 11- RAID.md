# INTRODUCCIÓN A RAID

- **Instalación del Paquete Necesario:**
  
> Para comenzar a trabajar con RAID, es esencial instalar el paquete **mdadm**, que proporciona herramientas robustas para la creación y gestión de dispositivos RAID en sistemas Linux.
  
> ```bash
> sudo apt install mdadm
> ```

- **Archivo de Configuración Importante:**
  
> La configuración de **mdadm** se encuentra en el archivo **/etc/mdadm/mdadm.conf**. Aquí es donde se definen las configuraciones de los dispositivos RAID, lo cual es crucial para su correcto funcionamiento.

- **Consulta del Estado de los Dispositivos RAID:**
  
> Para verificar el estado actual de los dispositivos RAID en el sistema, utiliza el siguiente comando:
  
> ```bash
> cat /proc/mdstat
> ```

# CREACIÓN DE UN RAID 1 CON DISCO DE RESERVA

- **Establecimiento del RAID 1:**
  
> Vamos a crear un RAID 1 denominado **md1**, que contendrá dos discos. La configuración RAID 1 ofrece redundancia al duplicar los datos en dos discos, mejorando la seguridad de la información.
  
> Ejecutamos el siguiente comando para crear el RAID:
  
> ```bash
> sudo mdadm -C /dev/md1 -l1 -n2 /dev/sdb /dev/sdc
> ```

- **Incorporación de un Disco de Reserva:**
  
> A continuación, añadimos un tercer disco como disco de reserva (hot spare). Este disco estará disponible para reemplazar a un disco activo en caso de falla, garantizando que el RAID siga operativo sin interrupciones.
  
> ```bash
> sudo mdadm /dev/md1 -a /dev/sdd
> ```

- **Formateo y Montaje del RAID:**
  
> Ahora procederemos a formatear el RAID y montarlo en el sistema. Formatear el RAID con el sistema de archivos **ext4** es esencial para permitir el almacenamiento de datos. Luego, crearemos un directorio para el montaje.
  
> ```bash
> sudo mkfs.ext4 /dev/md1  
> sudo mkdir /mnt/raid1  
> sudo mount /dev/md1 /mnt/raid1  
> ```

- **Simulación de un Fallo en el Disco:**
  
> Para poner a prueba la resiliencia del RAID, provocaremos un fallo en uno de los discos. Esto nos permitirá observar cómo el RAID maneja la pérdida de un disco activo y cómo el disco de reserva asume su lugar.
  
> ```bash
> sudo mdadm /dev/md1 -f /dev/sdb  
> ```
