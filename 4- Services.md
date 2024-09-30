## Activar/Desactivar Servicios

| Comando                      | Descripción                                          |
| -----------------------------| ---------------------------------------------------- |
| systemctl enable [servicio]   | Activar el servicio para el próximo inicio del sistema |
| systemctl disable [servicio]  | Desactivar el servicio para el próximo inicio del sistema |
| systemctl is-enabled [servicio] | Verificar si el servicio está activo                 |

***

## Creación de Servicios

- Para crear un servicio en Linux, sigue estos pasos:

1. **Primero:** Crear al menos dos scripts, uno para iniciar el servicio y otro para detenerlo.
   
2. **Segundo:** Crear un archivo llamado `algo.service` en la carpeta `/etc/systemd/system`.

3. **Tercero:** Coloca la siguiente configuración en el archivo que acabas de crear:

```bash
[Unit]
Description=Mi servicio de prueba


[Service]
Type=simple
ExecStart=/root/conexiones
ExecStop=/root/borraConexiones
RemainAfterExit=yes

[Install]
WantedBy=multi-user.target
```

 4- Da permisos de ejecución a los scripts con el siguiente comando:
  
```bash
chmod +x *.sh
```

5- Reinicia el sistema de servicios con este comando:

```bash
systemctl daemon-reload
```
