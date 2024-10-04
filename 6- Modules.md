# Comandos Básicos del Sistema

| Comando | Descripción |
| --- | ----------- |
| `uname -r` | Ver la versión del kernel actual. | 
| `/lib/modules/$(uname -r)/modules.dep` | Ver los módulos disponibles en el sistema. | 
| `/lib/modules/$(uname -r)/modules.builtin` | Ver los módulos incluidos en el núcleo del sistema. | 
| `cat /lib/modules/$(uname -r)/modules.dep | wc -l` | Ver la cantidad de módulos disponibles (se utiliza `wc -l` para contar las líneas de salida). | 
| `lsmod` | Ver los módulos que están cargados actualmente en el sistema. |

***

# Obtener Información sobre los Módulos

| Comando | Descripción |
| --- | ----------- |
| `modinfo [nombre_modulo]` | Proporciona información detallada sobre el módulo especificado. | 
| `modinfo -d [nombre_modulo]` | Proporciona una descripción del módulo especificado. |

***
# Eliminar Módulos de la Memoria

| Comando | Descripción |
| --- | ----------- |
| `modprobe [Nombre_Modulo]` | Carga un módulo en memoria. | 
| `modprobe -r [Nombre_Modulo]` | Elimina el módulo de la memoria. | 
| `modprobe -v [Nombre_Modulo]` | Devuelve información detallada sobre el módulo cargado. |

***
# Añadir un Módulo a la Lista Negra

- Para poner un módulo en la lista negra, se debe ejecutar el siguiente comando:
> `echo "blacklist [nombre_modulo]" >> /etc/modprobe.d/blacklist.conf`

***

# Diagnosticar Errores de Módulos

| Comando | Descripción |
| --- | ----------- |
| `sudo dmesg` | Muestra si hay algún error relacionado con el núcleo del sistema. |

***
# Información sobre Hardware

| Comando | Descripción |
| --- | ----------- |
| `lsusb` | Muestra información sobre dispositivos USB conectados, como pendrives. | 
| `lspci` | Muestra los dispositivos conectados a los buses PCI del sistema. |






