# Configuración Básica de Samba

### Instalación de Samba

```bash
sudo apt install samba
```
### Fichero de Configuración


```bash
/etc/samba/smb.conf
```

| Comando | Descripción |
| --- | ----------- |
| smbpasswd -a heidi | Añadir el usuario heidi al grupo Samba | 
| pdbedit -w -L | Ver los usuarios que están configurados en Samba | 
| testparm | Verificar los cambios en la configuración de Samba | 
| sysytemctl restar smbd  | Reiniciar el servicio Samba después de cada modificación | 
| smb://172.26.10.11/ | Conectar a Samba desde el entorno gráfico | 

```bash
```
### Configuración de Carpeta Pública en Samba
1. Crear la carpeta compartida:
```bash
mkdir /mnt/apuntes
```
2. Editar la configuración de Samba:

```bash
nano /etc/samba/smb.conf
```
Añadir la siguiente configuración al final del archivo:
```bash
[apuntes]
   comment = Carpeta Pública de Apuntes
   path = /mnt/apuntes
   guest ok = yes
   read only = yes
   browseable = yes
```


***

### Configuracion Samba a un usuario 

1. Crear el usuario

```bash
adduser anass0
```
2. Añadir el usuario a Samba
   
```bash
smbpasswd -a anass0
```
3. Editar la configuración de Samba:
```bash
nano /etc/samba/smb.conf
```
Añadir la siguiente configuración al final del archivo:
```bash
[apuntes]
   comment = Carpeta Privada de Apuntes
   path = /mnt/apuntes
   guest ok = no
   read only = no
   browseable = yes
   valid users = anass0
```

4. Reiniciar Samba:
   
```bash
systemctl restart smbd
```

5. Conectar a Samba desde el entorno gráfico:
   
```bash
smb://192.168.1.142/
```


***
compartir con grupo nada mas
compartir con un usuario nada mas
