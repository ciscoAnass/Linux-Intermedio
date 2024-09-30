# MONITORIZACIÓN DE PROCESOS
- **apt install htop**

| Syntax         | Description                                              |
| ---------------| ------------------------------------------------------- |
| ps             | Nos muestra los procesos del sistema                   |
| pstree -p     | Nos muestra los procesos de sistema de forma árbol     |
| top            | Nos muestra los procesos de forma gráfica y con menú    |
| htop           |                                                       |

# GESTIÓN DE PROCESOS A LARGO PLAZO

| Syntax                    | Description                                               |
| ------------------------- | ------------------------------------------------------- |
| ping 8.8.8.8 + CTL+Z     | Ejecutamos el comando ping y después, con CTL+Z, el proceso se acaba pero se queda en segundo plano. Podemos volver a ejecutarlo. |
| nano hola.txt &          | Cuando se añade el "&" se pone la ejecución del proceso en segundo plano. |
| jobs                      | Para ver los procesos en lista de espera               |
| bg [num]                 | Reinicia el trabajo a segundo plano                     |
| fg                       | Similar a bg                                           |

# MATAR PROCESOS

- Para matar un proceso del usuario heidi, primero entramos como heidi y hacemos:
  > nano prueba.txt

- Luego entramos como su y ponemos este comando:
  > ps u -u heidi | grep nano

- Así nos sale la tarea nano con su PID. A través del PID ejecutamos este comando:
  > kill -9 29385 [número de PID]

## MATAR VARIOS PROCESOS A LA VEZ

- Para matar varios procesos al mismo tiempo, necesitamos saber qué proceso es. Por ejemplo, si hay muchas pestañas de Google abiertas y queremos cerrarlas todas, solo tenemos que hacer este comando:
  > killall -9 chrome

## MATAR USUARIO

- Para matar un usuario conectado, se hace falta el comando:
  > pkill -9 -u heidi
