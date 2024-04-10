# AT

 - **NECESSARY :**

> sudo apt install at
> mesg yes
> ctrl+d
- **Ficheros de Importancia :**
- **/etc/at.deny**


| Command  | Description |
| ------------- | ------------- |
| at 17:57   | hacer tarea a esta hora   |
|  atq  |  ver las tareas  |
|  at -c  | ver informaciones de tareas   |
|  atrm [num de tarea]  | borrar tarea   |

- Para quitar algun usuario desde los servicios at , nos vamos a poner el nombre del usuario por el fichero **/etc/at.deny** , y se hace asi :
> echo "heidi" > /etc/at.deny




***
# Mail
> sudo apt install mailutils

| Command  | Description |
| ------------- | ------------- |
|  mail  |  escribir y leer los correos  | 
|mail -f | ver y leer los correos q ya se ha leido |
|mail -s "Invitacion a boda" < boda.txt | (se utilziza en script) |

# CRONTAB


| Command  | Description |
| ------------- | ------------- |
|  ps aux  |  Ver todas las tareas  |
| crontab -e   | editar el fichero crontab y crear nuevas tareas   |
| crontab -l   | Ver tareas   |
|  crontab -r  | Borrar Tareas   |
|    |    |
 - En el contrab tenemos 5 estrellas se explica cada uno y su utilizacion :
 - **Estrella 1** : minutos [0-59]
 - **Estrella 2** : horas [0-23]
 - **Estrella 3** : dias [1-31]
 - **Estrella 4** : meses [1-12]
 - **Estrella 5** : dia de semana [0 domingo -6 sabado ]

- Si queremos ejectuar algo cada 10 minutos hacemos **"*/10"**


***
# ANACRON

> sudo apt install anacron

- **Ficheros de Importancia :**
- **/etc/anacrontab**


