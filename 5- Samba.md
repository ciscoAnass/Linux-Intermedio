# BASIC


- **sudo apt install samba**
- **/etc/samba/smb.conf** : FIchero de configuracion


| Syntax | Description |
| --- | ----------- |
| smbpasswd -a heidi | anadir el usuario heidi a grupo samba | 
| pdbedit -w -L | Ver los usuarios que estan por samba | 
| testparm | Check changes | 
| sysytemctl restar smbd  | depsues cada cambio es necesario hacer este comando  | 
| smb://172.26.10.11/ | para conectar a samba desde el entorno grafico | 


- **Configuracion Samba publica :**
-Primero :
> mkdir /mnt/apuntes
- Segundo :
> nano /etc/samba/smb.conf
> [apuntes]
> comment = Compartida de apuntes
> path = /mnt/apuntes
> guest ok = yes
> read only = yes
> browseable = yes


-  **Configuracion Samba a un usuario :**
- Primero : creamos usuario anass0 :
> adduser anass0
- Segundo : anadimos el usuario a samba :
> smbpasswd -a anass0
- Tercero : Configuramos el samba
> nano /etc/samba/smb.conf
> [apuntes]
> comment = Compartida de apuntes
> path = /mnt/apuntes
> guest ok = no
> read only = no
> browseable = yes
> valis users = anass0
- Cuarto : Lo ultimo
> systemctl restart smbd
- y luego Nos vamos a el entorno grafico y poner :
> smb://192.168.1.142/




***
compartir con grupo nada mas
compartir con un usuario nada mas
