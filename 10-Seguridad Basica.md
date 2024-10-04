# Seguridad Básica en Linux

## Introducción
La seguridad es crucial en cualquier sistema operativo. Este módulo cubrirá conceptos y prácticas de seguridad básica e intermedia para sistemas Linux.

## Gestión de usuarios y permisos
### Principio de mínimo privilegio
Asigna a los usuarios solo los permisos necesarios para realizar sus tareas.

### Ejemplo: Configuración de permisos restrictivos
```bash
# Crear un nuevo usuario
sudo adduser nuevouser

# Agregar usuario a un grupo específico
sudo usermod -aG grupo nuevouser

# Cambiar permisos de un directorio
sudo chmod 750 /directorio/importante
```

## Actualización del sistema
Mantener el sistema actualizado es crucial para la seguridad.

### Comandos importantes
- Debian/Ubuntu: `sudo apt update && sudo apt upgrade`
- CentOS/RHEL: `sudo yum update`

## Configuración de SSH
Secure Shell (SSH) es el método principal para acceso remoto seguro.

### Ejemplo: Configuración segura de SSH
Edita `/etc/ssh/sshd_config`:
```
PermitRootLogin no
PasswordAuthentication no
UsePAM yes
```

Reinicia el servicio SSH: `sudo systemctl restart sshd`

## Firewall básico
Utiliza `ufw` (Uncomplicated Firewall) en Ubuntu o `firewalld` en CentOS para configuración básica de firewall.

### Ejemplo con ufw
```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow ssh
sudo ufw enable
```

## Detección de intrusiones con AIDE
AIDE (Advanced Intrusion Detection Environment) ayuda a detectar cambios no autorizados en el sistema.

### Configuración básica de AIDE
1. Instalar AIDE: `sudo apt install aide`
2. Inicializar la base de datos: `sudo aideinit`
3. Ejecutar comprobaciones: `sudo aide --check`

## Logs y auditoría
Los logs son cruciales para la seguridad y el diagnóstico de problemas.

### Herramientas importantes
- `journalctl`: Para sistemas que usan systemd
- `auditd`: Sistema de auditoría más avanzado

### Ejemplo: Configuración básica de auditd
1. Instalar auditd: `sudo apt install auditd`
2. Iniciar el servicio: `sudo systemctl start auditd`
3. Habilitar en el arranque: `sudo systemctl enable auditd`
