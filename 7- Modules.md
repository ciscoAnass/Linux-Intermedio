# BASIC

| Syntax | Description |
| --- | ----------- |
| uname -r | Ver la version del kernel | 
| /lib/modules/$(uname -r)/modules.dep | Los Modulos disponibles | 
|/lib/modules/version/modules.builtin | Los modulos Incluidos en el nucleo | 
| wc -l |To see how many modules we have we just need to put wc -l after cat modules.dep or bullitin | 
|lsmod | Para ver los modulos que estan cargados actualmente por la sistema  | 
***
# Obtener Informaciones sobre los modulos
| Syntax | Description |
| --- | ----------- |
| modinfo [nombre_modulo] | nos da infos sobre el modulo  | 
| modinfo -d [nombre_modulo] | nos da descripcion sobre el modulo  | 

***
# ELiminar modulos De la memoria

| Syntax | Description |
| --- | ----------- |
| modprobe [Nombre_Modulo]| Carga un modulo en memoria  | 
| modprobe -r [Nombre_Modulo] | ELimina el modulo de la memoria  | 
| modprobe -v [Nombre_Modulo] | Devolver el modulo a la memoria | 

***
# Blacklist  a Module

- Para ponr un modulo en la lista negra se hace falta hacer eso
>  echo "blacklist [numero de modulo]"  >> /etc/modprobe.d/blacklist.conf
***

# Errores De modulos

| Syntax | Description |
| --- | ----------- |
| sudo dmesg  | nos ensena si hay algun error por algun nucleo  | 
|  |  | 
|  |  | 
|  |  | 


# HARDWARE

| Syntax | Description |
| --- | ----------- |
| lsusb | Informaciones sobre el pendrive que hemos instalado | 
| lspci | Muestra los dispotivos conectados a los buses PCI | 









| Syntax | Description |
| --- | ----------- |
|  |  | 
|  |  | 
|  |  | 
|  |  | 
