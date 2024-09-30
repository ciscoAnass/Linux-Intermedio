# Conocimiento sobre Comandos del Sistema

| Sintaxis                     | Descripción                                                        |
|------------------------------|--------------------------------------------------------------------|
| `id [-u, -g]`                | Muestra toda la información del usuario actual.                   |
| `w`, `who`                   | Muestra los usuarios activos en el sistema.                       |
| `lastlog`                    | Muestra la última vez que cada usuario se conectó.                |
| `lastb`                      | Muestra los usuarios que fallaron al intentar iniciar sesión.      |
| `getent passwd heidi`       | Muestra la información del usuario "heidi" desde el archivo `/etc/passwd`. |

- Si se elimina la "x" del segundo campo de un usuario, esto permite el acceso sin solicitar contraseña.


***

# Archivo /etc/shadow

| Sintaxis                             | Descripción                                                                                     |
|--------------------------------------|-------------------------------------------------------------------------------------------------|
| `heidi`                              | Muestra toda la información del usuario.                                                       |
| `dasbioasdhoisdaoiasd`              | Contraseña encriptada del usuario.                                                              |
| `19758`                              | Días desde el último cambio de contraseña, contando desde 1975.                               |
| `0`                                  | Días transcurridos para el próximo cambio de contraseña.                                       |
| `99999`                              | Días restantes antes de que no se pueda acceder con la contraseña actual.                      |
| `7`                                  | Días de aviso antes de la caducación de la contraseña.                                         |
| Normalmente vacío                     | Días que se esperan desde que la cuenta ha caducado hasta su eliminación definitiva.           |
| Normalmente vacío                     | Fecha en la que la cuenta expira.                                                              |


***
# Matar Usuario

| Sintaxis                   | Descripción                          |
|----------------------------|--------------------------------------|
| `pkill -9 -u heidi`       | Desconecta y finaliza el proceso del usuario "heidi". |



***
# Crear Usuario

| Sintaxis        | Descripción                                                                         |
|-----------------|-------------------------------------------------------------------------------------|
| `adduser`       | Método rápido, fácil e interactivo para crear usuarios.                            |
| `useradd`      | Otra forma de crear usuarios que no es la más recomendada (no crea el directorio `/home/usuario`). |


***

# Establecer/Cambiar Contraseña

| Sintaxis  | Descripción                                         |
|-----------|-----------------------------------------------------|
| `passwd`  | Establece o cambia la contraseña de un usuario.    |


***
# Configuración de Información por Defecto

| Sintaxis            | Descripción                                                   |
|---------------------|---------------------------------------------------------------|
| `/etc/login.defs`   | Archivo de configuración que define los parámetros predeterminados para la creación de usuarios. |


***
# Automatización de la Integración de Datos en Cada Usuario

| Sintaxis         | Descripción                                                   |
|------------------|---------------------------------------------------------------|
| `/etc/skel`      | Directorio utilizado para proporcionar archivos de configuración a nuevos usuarios de manera automática. |

- Permite agregar archivos a cualquier usuario de forma automática.




***

# USRMOD: Cambiar Nombre / Bloquear Usuario

| Sintaxis                     | Descripción                                                                                     |
|------------------------------|-------------------------------------------------------------------------------------------------|
| `usermod -L heidi`           | Bloquea la cuenta de usuario y añade un "!" a la contraseña encriptada en `/etc/shadow`.      |
| `usermod -l javier heidi`    | Cambia el nombre de usuario de "heidi" a "javier" (nuevo_nombre = javier).                   |
| `usermod -aG heidi`          | Añade el usuario "heidi" al grupo "sudo".                                                     |

- Para desbloquear la cuenta, es necesario ir a `/etc/shadow` y eliminar el "!" de la contraseña encriptada del usuario bloqueado.

***

# Gestión de Contraseñas y Estado de Usuario con chage

| Sintaxis                        | Descripción                                                                                      |
|---------------------------------|--------------------------------------------------------------------------------------------------|
| `chage -d 0 heidi`             | Obliga al usuario a cambiar la contraseña en el próximo inicio de sesión.                      |
| `chage -E 2024-05-30 heidi`     | Desactiva el usuario el 30 de mayo de 2024, impidiendo el acceso a partir del 1 de junio.      |
| `chage -E 1 heidi`             | Activa un usuario que ha sido bloqueado.                                                       |



***
# USERDEL: Borrar Usuario

| Sintaxis                | Descripción                                                                                          |
|-------------------------|------------------------------------------------------------------------------------------------------|
| `userdel -r heidi`     | Elimina el usuario "heidi" y su directorio home. Tras ejecutar `userdel`, se debe ejecutar `rm -r /home/heidi` para eliminar el directorio. |



***
# Gestión de Grupos

| Sintaxis                   | Descripción                                                                                              |
|----------------------------|----------------------------------------------------------------------------------------------------------|
| `addgroup 1asir`          | Crea un nuevo grupo llamado "1asir".                                                                    |
| `groupmod`                 | Permite modificar las propiedades de un grupo existente.                                                |
| `groupdel 1asir`          | Elimina el grupo "1asir".                                                                                |
| `adduser heidi sudo`      | Añade el usuario "heidi" al grupo "sudo".                                                               |
| `deluser heidi sudo`      | Quita el usuario "heidi" del grupo "sudo".                                                              |
| `newgrp`                   | Cambia el grupo efectivo del usuario actual a uno nuevo.                                                |
| `chown heidi:1asir diskM.sh` | Cambia el propietario y el grupo del archivo `diskM.sh` a "heidi" y "1asir", respectivamente.            |


***

# Comprobar Estado de Contraseña con passwd -S

- `passwd -S heidi`: Permite verificar si el usuario "heidi" está bloqueado o no. 
  - Si el resultado es **P**, el usuario está activo. 
  - Si el resultado es **L**, el usuario está bloqueado.

***

# SUDOERS

- **Archivo de configuración**: **/etc/sudoers**
- Para editar el archivo `/etc/sudoers`, utiliza **`visudo -f`**.
- Para comprobar si todo está correcto, utiliza **`visudo -c`**.

| Sintaxis                   | Descripción                                                   |
|----------------------------|---------------------------------------------------------------|
| `getent group sudo`       | Muestra los usuarios que tienen privilegios de root.        |


### Otorgar Privilegios de Root a un Usuario

Para dar privilegios de root a un usuario, se realiza de la siguiente manera:

```bash
visudo -f /etc/sudoers
heidi ALL=(ALL:ALL) ALL
```

### Asignar Privilegios de Comandos Específicos a un Usuario

Para otorgar privilegios de algunos comandos específicos a un usuario, se realiza de la siguiente manera:

```bash
visudo -f /etc/sudoers
Cmnd_Alias CTL=/bin/systemctl, /bin/ip
%heidi ALL=CTL  # (HEIDI es el nombre del grupo)
```

### Modificación de Archivos de Configuración de Red en Ubuntu

Para poder modificar el archivo `/etc/network/interfaces` o `/etc/netplan/00-...` en Ubuntu, se hace de la siguiente manera, con una modificación:

```bash
Cmnd_Alias CTL=/bin/systemctl, /bin/nano /etc/netplan/00-yaml
%heidi ALL=CTL
```

### Deshabilitar Solicitud de Contraseña para un Usuario

Para que no se pida la contraseña, es necesario copiar la línea anterior y añadir lo siguiente:

```bash
%heidi ALL=NOPASSWD:CTL
```
### Limitar Intentos de Contraseña

Para limitar el acceso mediante contraseña, es decir, solicitar la contraseña dos veces y, si no se inserta correctamente, permitir que el usuario repita el intento, se utiliza la siguiente línea:

```bash
Defaults:ALL passwd_tries=2
```

***
# CREACIÓN DE USUARIOS

| Sintaxis | Descripción |
| --- | ----------- |
| useradd -m -s /bin/bash empleado | Crea un usuario llamado "empleado" (es necesario ejecutar el comando `passwd empleado` para asignarle una contraseña y poder iniciar sesión) |

***

# CREACIÓN DE CUENTAS CON CONTRASEÑA ENCRIPTADA

- Es necesario instalar el siguiente paquete:
```bash
sudo apt install whois
```
| Sintaxis                                                   | Descripción                                        |
| --------------------------------------------------------- | -------------------------------------------------- |
| useradd -m -s /bin/bash -p $(mkpasswd -m sha-512 gato) gato | Crea una cuenta llamada "gato" con una contraseña encriptada. |



# CREACIÓN MASIVA DE USUARIOS

![Crear Usuario de Forma Masiva](/img/Crear-UsuarioDeFormaMassiva.png)

# ELIMINACIÓN MASIVA DE USUARIOS

![Borrar Usuarios de Forma Masiva](/img/BorrarUsuariosDeFormaMassiva.png)


***

# ARCHIVOS DE CONFIGURACIÓN DEL SISTEMA

| Sintaxis                       | Descripción                                                             |
| ------------------------------ | ----------------------------------------------------------------------- |
| cat /etc/group | grep sudo    | Muestra quién pertenece al grupo sudo y permite modificar grupos.       |
| cat /etc/passwd                | Muestra información sobre las cuentas de usuario en el sistema.        |
| cat /etc/shadow               | Muestra información sobre las contraseñas de usuario y su estado.      |



