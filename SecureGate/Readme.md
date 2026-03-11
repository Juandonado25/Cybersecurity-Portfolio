Para la infraestructura de **Secure Gate** se eligió una infraestructura segmentada porque me permite controlar mejor el trafico de la red y tener mejor control de la seguridad.

Este laboratorio se desplegó en un entorno virtual usando Virtualbox.

Se usa Port Forwarding para poder usar la IP de WAN y redirigir el trafico web a DMZ y así poder acceder desde el exterior de la red a la API.
## Componentes de la red

![[Pasted image 20260127003918.png]]

---

 **Firewall:** Un firewall Pfsense que maneja 3 interfaces:
- **WAN:** Interfaz Puenteada que permite el acceso a internet.
- **DMZ:** Interfaz con red interna que contiene solo al servidor web.
- **LAN:** Esta interfaz también es una red interna y su principal uso es para administrar el firewall desde una computadora administrador.

**Usuario de pfsense:** admin
**Contraseña:** securegate.fw.123

---

**Web Server:** En este server se va a usar un contenedor Docker desplegar la API. En principio este endpoint no tiene acceso a internet porque la red WAN esta bloqueada por defecto por el firewall.

**S.O:** Debian 13
**hostname:** debian
**Root Password:** securegate.server.321
**user:** gatekeeper
**User Password:** gatekeeper.pass.321

---

**Debian Client (Admin):** El proposito de este endpoint es administrar el Pfsense por medio de el navegador web.

**S.O:** Debian 13
**hostname:** debian-client
**Root Password:** securegate.client.321
**user:** gateadmin
**User Password:** gateadmin.pass.321
