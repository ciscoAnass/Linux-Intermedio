# CONFIGURACIÓN Y GESTIÓN DE RAID EN LINUX

## Instalación del Paquete Esencial

Para empezar a trabajar con RAID en sistemas Linux, se debe instalar el paquete **mdadm**. Este paquete ofrece herramientas avanzadas para crear y gestionar configuraciones RAID.

```bash
sudo apt-get update && sudo apt-get install mdadm
```

## Archivo de Configuración de RAID

El archivo de configuración de **mdadm** se encuentra en **/etc/mdadm/mdadm.conf**. En este archivo se definen las configuraciones de los arrays RAID, lo que asegura su correcto funcionamiento, incluso después de reinicios del sistema.

---

## Verificación del Estado de los Dispositivos RAID

Para consultar el estado actual de los dispositivos RAID en tu sistema, utiliza el siguiente comando:

```bash
cat /proc/mdstat
```

# CONFIGURACIÓN DE RAID 1 CON DISCO DE RESERVA

## Creación de un RAID 1

Vamos a configurar un RAID 1, conocido como **md1**, utilizando dos discos. El RAID 1 proporciona alta redundancia, ya que duplica los datos en ambos discos, lo que incrementa la seguridad y disponibilidad de la información.

Para crear el array RAID 1, ejecuta el siguiente comando:

```bash
sudo mdadm --create /dev/md1 --level=1 --raid-devices=2 /dev/sdb /dev/sdc
```
## Incorporación de un Disco de Reserva (Hot Spare)

Para aumentar la tolerancia a fallos, añadiremos un tercer disco como disco de reserva. Este disco actuará como **hot spare**, reemplazando automáticamente cualquier disco activo que falle, asegurando que el array RAID continúe operando sin interrupciones.

Para añadir el disco de reserva, ejecuta:

```bash
sudo mdadm --add /dev/md1 /dev/sdd
```

## Formateo y Montaje del RAID

Una vez creado el RAID, es necesario formatearlo con el sistema de archivos **ext4** para poder almacenar datos de manera eficiente. Luego, montaremos el array RAID en el sistema, creando un punto de montaje adecuado.

1. Formatea el RAID con el sistema de archivos **ext4**:

```bash
sudo mkfs.ext4 /dev/md1
```
2. Crea un directorio para montar el RAID y procede al montaje:

```bash
sudo mkdir /mnt/raid1
sudo mount /dev/md1 /mnt/raid1
```
3. Para asegurar que el RAID se monte automáticamente tras reiniciar el sistema, añade la siguiente línea al archivo /etc/fstab:
   
```bash
echo '/dev/md1 /mnt/raid1 ext4 defaults 0 0' | sudo tee -a /etc/fstab
```

## Simulación de un Fallo en el Disco

Para evaluar la resiliencia del RAID, simular un fallo en uno de los discos es un paso crucial. Esta acción nos permitirá observar cómo el sistema RAID gestiona la pérdida de un disco activo y cómo el disco de reserva toma su lugar para mantener la funcionalidad del array.

Para simular el fallo del disco **/dev/sdb**, utiliza el siguiente comando:

```bash
sudo mdadm --fail /dev/md1 /dev/sdb
```
