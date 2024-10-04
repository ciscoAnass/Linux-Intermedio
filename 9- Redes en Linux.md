# Redes en Linux

## Introducción
Las redes son una parte fundamental de los sistemas Linux modernos. Este módulo cubrirá conceptos intermedios de redes en Linux, herramientas comunes y configuraciones típicas.


## Configuración de red
### Archivos de configuración importantes
- `/etc/network/interfaces` (Debian/Ubuntu)
- `/etc/sysconfig/network-scripts/` (CentOS/RHEL)

### Ejemplo de configuración estática
```
auto eth0
iface eth0 inet static
    address 192.168.1.100
    netmask 255.255.255.0
    gateway 192.168.1.1
    dns-nameservers 8.8.8.8 8.8.4.4
```

## Herramientas de red
- `ip`: Herramienta moderna para configurar interfaces y rutas
- `ss`: Reemplazo moderno de `netstat`
- `ping`: Verificar conectividad
- `traceroute`: Trazar ruta de paquetes
- `nmap`: Escaneo de puertos y descubrimiento de red

### Ejemplo: Uso de `ip`
```bash
# Mostrar interfaces de red
ip link show

# Configurar una dirección IP
sudo ip addr add 192.168.1.100/24 dev eth0

# Agregar una ruta
sudo ip route add default via 192.168.1.1
```

## Firewall con iptables
iptables es una herramienta poderosa para configurar el firewall en Linux.

### Ejemplo básico de reglas de iptables
```bash
# Permitir tráfico SSH entrante
sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT

# Bloquear todo el tráfico entrante no especificado
sudo iptables -A INPUT -j DROP
```

## VPN con OpenVPN
OpenVPN es una solución popular para crear redes privadas virtuales en Linux.

### Pasos básicos para configurar un servidor OpenVPN
1. Instalar OpenVPN
2. Generar certificados y claves
3. Configurar el servidor OpenVPN
4. Iniciar el servicio OpenVPN

## Servidor DNS con BIND
BIND (Berkeley Internet Name Domain) es el servidor DNS más utilizado en sistemas Unix/Linux.

### Configuración básica de BIND
1. Instalar BIND
2. Configurar zonas en `/etc/named.conf`
3. Crear archivos de zona
4. Reiniciar el servicio BIND
