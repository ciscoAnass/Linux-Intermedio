# Monitorizacion de Procesos
- **apt install htop**

| Syntax | Description |
| --- | ----------- |
| ps  | Nos muestra los procesos del sistema|
| pstree -p | Nos muestra los procesos de sistema de froma arbol|
| top | nos muestra los procesos de forma grafica y con menu   |
| htop |    |




# Gestion de procesos  a largo plazo

| Syntax | Description |
| --- | ----------- |
| ping 8.8.8.8 + CTL+Z  | ejectuamos el comando ping y despues ejectuarlo hacmeos CTLZ y asi el proceso se acaba pero se queda en segundo plano osea que podemos a vovler a ejecutarlo  |
| nano hola.txt & | cuando se anade el "&" se pone la ejecutacion del proceso a segundo plano  |
| jobs | Para ver los procesos en lista de espera |
| bg [num] | reinincia el trabajo a 2 plano|
| fg | mas o menos lo mismo que bg|



# Matar Procesos

sigkill
sigterm


- Para matar un proceso del ususario heidi , primero entramos como heidi y hacemos :
> nano prueba.txt
- Luego nos vamos a entrar como su y ponemos este comando :
> ps u -u heidi | grep nano
- y asi nos sale la tarea nano con su PID Y atraves del PID ejecutamos este comando 
> kill -9 29385 [num de PID]

## Matar Varios procesos a la vez

- Para matar varios procesos al mismo tiempo , nos vamos a tener q saber q proceso es , por ejemplo si son muchas pestanas de google abiertas y quermos quitarlas todas solo se hace falta hacer este comando
> killall -9 chrome

## Matar usuario
- Para matar un usaurio conectado se hace falta el comando :
> pkill -9 -u heidi
