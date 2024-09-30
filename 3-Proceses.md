## MONITORIZACIÓN DE PROCESOS

- **Instalación de htop:**
  ```bash
  apt install htop
  ```

***
### Comandos para monitorear procesos en Linux

| Comando        | Descripción                                                |
| ---------------| ---------------------------------------------------------- |
| `ps`           | Muestra una lista de los procesos en ejecución en el sistema. |
| `pstree -p`    | Muestra los procesos en forma de árbol, con sus PID asociados. |
| `top`          | Muestra los procesos en tiempo real con un menú interactivo. |
| `htop`         | Similar a `top`, pero con una interfaz más amigable y opciones avanzadas. |

***
### Gestión de Procesos en Segundo Plano

| Comando                    | Descripción                                                                            |
| -------------------------- | -------------------------------------------------------------------------------------- |
| `ping 8.8.8.8 &`           | Ejecuta el comando `ping` en segundo plano.                                             |
| `nano hola.txt &`          | Ejecuta el editor `nano` en segundo plano al añadir `&` al final del comando.           |
| `jobs`                     | Muestra una lista de los trabajos o procesos en segundo plano.                         |
| `bg [num]`                 | Envía un trabajo en pausa (detenido) al segundo plano y lo reanuda.                     |
| `fg [num]`                 | Trae un trabajo en segundo plano al primer plano para continuar su ejecución.           |

***

### Finalizar Procesos

- Para finalizar un proceso iniciado por el usuario `heidi`, primero iniciamos sesión como `heidi` y ejecutamos el siguiente comando para abrir un archivo en `nano`:

```bash
  nano prueba.txt
```
- Luego, cambiamos al usuario `root` con `su` y ejecutamos este comando para obtener el PID del proceso `nano` de `heidi`:

```bash
  ps -u heidi | grep nano
```
- Esto mostrará el proceso de `nano` con su PID. Para finalizar el proceso usando ese PID, ejecutamos:

  kill -9 [número_de_PID]

  Ejemplo:

```bash
  kill -9 29385
```

***

### Matar Varios Procesos a la Vez

- Para matar múltiples procesos de una aplicación, como Google Chrome, usamos:

```bash
killall -9 chrome
```

### Matar Usuario Conectado

- Para desconectar a un usuario, usamos el siguiente comando:
```bash
 pkill -9 -u heidi
```
