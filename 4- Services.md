# Activar/Desactivar servicios

| Syntax | Description |
| --- | ----------- |
| systemctl enable service | activar el servicio por el proximo inicio de sistema |
| systemctl disable service |Desactivar el servicio por el proximo inicio de sistema|
| systemctl is-enabled service | Verificar si el servicio esta activo |

***

#  Creacion de Servicion
- Para Crear un Servicio en Linux , nos vamos a tener que seguir estos pasos :
- **Primero :** Crear al menos 2 scripts , uno para start service y otro para stop
- **Segundo :** nos vamos a crear un fichero se llama "algo.service" en esta carpeta "/etc/systemd/system"
- **Tercero :** Ponemos esta Configuracion en el fichero que hemos creado
>[Unit]

>Description=Mi servicio de prueba

>[Service]

>Type=simple

>ExecStart=/root/conexiones

>ExecStop=/root/borraConexiones

>RemainAfterExit=yes

>[Install]

>WantedBy=multi-user.target

- **Cuarto :** hacemos este comando a los scripts :
> chmod +x *sh

- **Ultimo :** reninciamos la sistema de servicios
> systemctl daemon-reload


