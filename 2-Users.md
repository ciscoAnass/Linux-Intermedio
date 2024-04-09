# CONOCIMIENTO


| Syntax | Description |
| --- | ----------- |
| id [-u ,-g]| See all info | 
| w , who | los usuario activos al momento  |
| lastlog| la ultima vez cuando los usuarios han conectado |
| lastb | usuarios q han fallado a loguearse  |
| getent passwd heidi | Ver informaciones del usuario heidi por el fichero /etc/passwd  |

- Si quitamos el "x" del segundo campo de algun usuario , eso nos deja a entrar a usuarios sin pedir contrasena 

***

# /etc/shadow

| Syntax | Description |
| --- | ----------- |
| heidi| See all info |
| dasbioasdhoisdaoiasd |  |
| 19758 | cuanto de dias por la ultima vez q se ha cambiado la contrasena desde 1975  |
| 0 | cuanto dias han pasado para cambiar la contrasena |
| 99999 | cuanto dias te esperan pa q no puedes hacer log mas con la contrasena actual |
| 7 | cuanto de dias te avisan antes de la caducacion de la contrasena |
| normalmente vacia | n de dias q vas a esperar desde q la cuenta se ha caducado hasta que se eimina definitivamente |
| normalmente vacia | fecha en la q la cuenta expira  |


***
# MATAR USUARIO
| Syntax | Description |
| --- | ----------- |
| pkill -9 -u heidi| desconectar y matar un usuario |


***
# CREAR USUSARIO
| Syntax | Description |
| --- | ----------- |
| adduser| es una forma rápida, fácil e interactiva de crear usuarios |
| useradd| es otra manera de crear usuarios y no es la mejor manera ( no crea el directorio /home/usuario) | 

***

# PASSWORD SET/CHANGE
| Syntax | Description |
| --- | ----------- |
| passwd | poner o cambiar la contrasena de un usuario  |

***

# SET INFO BY DEFECT

| Syntax | Description |
| --- | ----------- |
| /etc/login.defs |   |


***
# AUTOAMTIZAZATION OF DATA INTEGRATION IN EVERY USER

| Syntax | Description |
| --- | ----------- |
| /etc/skell  |   |

- Es para poner archivos a cualquier usuario de manera automatica 




***
# USERMOD : CAMBIAR NOMBRE / BLOQUEAR USUARIO

| Syntax | Description |
| --- | ----------- |
| usermode -L heidi  | se bloquea la uenta de entrar y se anade un "!" por la contrasen criptada en /etc/shadow   |
| usermode -l javier heidi  | Hemos cambiado el nombre de usuario heidi a javier (nuevo_nombre = javier)  |
| usermode -aG heidi  | anadir heidi a sudo  |


- Para hacer un desbloqueo a la cuenta se hace falta ir a /etc/shadow y quitar "!" desde el lado de la contrasena encriptada del usuarioq  hemos bloqueado

***
# chage


| Syntax | Description |
| --- | ----------- |
| chage -d 0 heidi   | Te obliga a cmabiar la contrasena al tiempo   |
| chage -E 2024-05-30 heidi  | desactiva el usuario por rl 30-05 y asi n se puede acceder con este usuario el dia siguiente 01-06   |
| chage -E 1 heidi   | Activar un usuario bloqueado   |


***

# USERDEL : BORRAR USUARIO


| Syntax | Description |
| --- | ----------- |
| userdel -r heidi | borrar el usuario heidi y despues hacer 'userdel' hacemo 'rm -r /home/heidi'    |


***
# GROUPS
| Syntax | Description |
| --- | ----------- |
| addgroup 1asir  | crear grupo se llama 1asir  |
| groupmod |  |
| groupdel 1asir | borrar grupo 1asir |
| adduser heidi sudo | anadir usuario heidi a grupo sudo |
| deluser heidi sudo | quitar el usuario 1asir del grupo sudo  |
| newgrp |  |
| chwon heidi:1asir diskM.sh | cambiar el dueno grupo del fichero diskM.sh desde heidi a 1asir   |


# PASSWD -S heidi
- Para ver si el usuario esta bloqueado o no , si Sale P pues esta libre si esta L pues bloqueado 

 


# FOLDERS IMPORTANTES

| Syntax | Description |
| --- | ----------- |
| cat /etc/group | grep sudo | para ver quien esta por el grupo sudo y podemos a haceerla  cualquier grupo   |






***

- saber la configuracion de EXPIRE, INACTIVE en fichero /etc/default/useradd
- cat /etc/login.defs |grep -v "^#\|^$"
- que es /etc/skel
- chage
- nwegrp
- groupmod grupo


