# AT

- **NECESARIO:**

> sudo apt install at  
> mesg yes  
> ctrl+d  

- **Archivos Importantes:**
  - **/etc/at.deny**

| Comando        | Descripción                      |
|----------------|----------------------------------|
| at 17:57       | Programar tarea a esta hora      |
| atq            | Ver las tareas programadas        |
| at -c          | Ver información de las tareas     |
| atrm [número]  | Eliminar tarea                    |

- Para quitar algún usuario de los servicios at, añadimos el nombre del usuario en el archivo **/etc/at.deny** de la siguiente manera:
> echo "heidi" > /etc/at.deny  

***

# Correo

> sudo apt install mailutils  

| Comando           | Descripción                       |
|-------------------|-----------------------------------|
| mail              | Escribir y leer correos           |
| mail -f           | Ver y leer correos ya leídos      |
| mail -s "Invitación a boda" < boda.txt | Enviar un correo desde un script |

# CRONTAB

| Comando         | Descripción                         |
|------------------|-------------------------------------|
| ps aux           | Ver todas las tareas                |
| crontab -e       | Editar el archivo crontab y crear nuevas tareas |
| crontab -l       | Ver tareas                          |
| crontab -r       | Borrar tareas                       |

- En crontab tenemos 5 campos, cada uno con su utilización:
  - **Campo 1**: minutos [0-59]
  - **Campo 2**: horas [0-23]
  - **Campo 3**: días [1-31]
  - **Campo 4**: meses [1-12]
  - **Campo 5**: día de la semana [0 domingo - 6 sábado]

- Si queremos ejecutar algo cada 10 minutos, usamos **"*/10"**.

***

# ANACRON

> sudo apt install anacron  

- **Archivos Importantes:**
  - **/etc/anacrontab**
