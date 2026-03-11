# Configuración de pfSense - Secure Gateway

**Archivo:** `config-fw01-pfsense.secure.gateway-20260127023754.xml`
**Fecha de Reporte:** 27 de enero de 2026

---

## 🖥️ Identificación del Sistema
* **Hostname:** `fw01-pfsense`
* **Dominio:** `secure.gateway`
* **Versión de Firmware:** 24.0
* **Zona Horaria:** `America/Argentina/Buenos_Aires`
* **Servidores DNS:** * 8.8.8.8
  * 8.8.4.4

---

## 🌐 Interfaces y Direccionamiento
| Interfaz | Dispositivo | Descripción | Tipo IPv4 | Dirección IP |
| :--- | :--- | :--- | :--- | :--- |
| **WAN** | `em0` | Conexión externa | DHCP | Dinámica |
| **LAN** | `em2` | Red Interna | Estática | 172.16.0.1/24 |
| **DMZ** (OPT1) | `em1` | Zona Desmilitarizada | Estática | 10.0.0.1/24 |

---

## 📶 Servicios DHCP y Reservas

### Segmento LAN (172.16.0.0/24)
* **Rango:** 172.16.0.100 - 172.16.0.199
* **Mapeo Estático:**
  * **Dispositivo:** Debian-Client
  * **IP:** 172.16.0.10
  * **MAC:** `08:00:27:07:95:db`
  * **Descripción:** Debian cliente (Administrador)

### Segmento DMZ (10.0.0.0/24)
* **Rango:** 10.0.0.100 - 10.0.0.199
* **Mapeo Estático:**
  * **Dispositivo:** Webserver-Debian
  * **Hostname:** `server`
  * **IP:** 10.0.0.50
  * **MAC:** `08:00:27:74:25:bd`
  * **Descripción:** Servidor Web en DMZ

---

## 🔥 Reglas de Firewall (Políticas de Filtrado)

### 📥 WAN (Entrante)
* **Permitir HTTP (80):** Desde el host `192.168.1.33` hacia la IP de WAN.
* **Permitir HTTPS (443):** Desde cualquier origen hacia el servidor web `10.0.0.50`.
* **Permitir HTTP (80):** Desde cualquier origen hacia el servidor web `10.0.0.50`.
* **Bloqueo Total:** Denegación explícita de todo el tráfico restante desde WAN.

### 🏠 LAN (Interna)
* **Administración SSH:** Permitido desde `172.16.0.10` hacia el servidor `10.0.0.50` (Puerto 22).
* **Acceso Web Local:** Permitido desde la red LAN hacia el servidor `10.0.0.50` (Puertos 80, 443).
* **Diagnóstico:** Tráfico ICMP permitido desde LAN hacia el servidor `10.0.0.50`.
* **Aislamiento:** Bloqueo de cualquier otro tráfico desde LAN hacia la red DMZ.
* **Salida Internet:** Regla `Default allow LAN to any` activa.

### 🛡️ DMZ (Zona de Servidores)
* **Aislamiento LAN:** Bloqueo estricto de tráfico desde DMZ hacia la red LAN.
* **Salida WAN:** Permitido el tráfico desde DMZ hacia cualquier destino externo.

---

## 🔑 Seguridad y Administración
* **Usuario Administrador:** `admin`
* **Acceso Shell:** Habilitado para el usuario admin.
* **WebGUI:** Configurada sobre protocolo HTTP (Puerto 80).
* **SNMP:** Comunidad de lectura `public` configurada.