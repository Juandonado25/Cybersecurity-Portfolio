# Cybersecurity Portfolio - Juan Donado

Bienvenido a mi repositorio de proyectos y laboratorios de ciberseguridad. Aquí documento mi progreso técnico en administración de redes seguras, implementación de SIEM y defensa activa.

---

## Proyecto Principal: Secure Gate

**Secure Gate** es una infraestructura de red segmentada diseñada para el despliegue seguro de servicios y el monitoreo centralizado de eventos.

### Arquitectura de Red
El entorno utiliza un firewall **pfSense 24.0** para gestionar tres zonas aisladas:
* **WAN:** Interfaz externa con reglas estrictas de filtrado y Port Forwarding.
* **DMZ (10.0.0.0/24):** Aloja un servidor Debian 13 con la API de Secure Gate y el stack de monitoreo.
* **LAN (172.16.0.0/24):** Segmento dedicado exclusivamente a la administración del firewall y servidores.

### Stack de Seguridad (SIEM)
Implementación de **Wazuh (v4.14.3)** sobre Docker para la recolección y análisis de logs:
* **Ingesta de Datos:** Centralización de logs de pfSense (Sistema, Firewall y DNS) vía Syslog UDP/514.
* **Hardening:** Configuración de Filebeat con archivado de logs habilitado y segmentación de puertos de gestión (Dashboard en puerto 8443).
* **Detección:** Uso de decoders y reglas personalizadas para la normalización de eventos de red.

---

## Habilidades Técnicas

### Networking & Firewalls
* **pfSense:** Configuración de interfaces (WAN/LAN/DMZ), NAT/Port Forwarding y reglas de filtrado perimetral.
* **Protocolos:** Gestión de servicios DHCP, ICMP para diagnóstico y SSH seguro para administración remota.

### Operaciones de Seguridad (SOC)
* **SIEM/EDR:** Despliegue y mantenimiento de infraestructuras Wazuh basadas en contenedores.
* **Análisis de Logs:** Experiencia en la unificación de bloques de configuración y gestión de APIs de seguridad.

### Infraestructura
* **Sistemas Operativos:** Linux (Debian 13 "Trixie") enfocado en servidores de producción y contenedores.
* **Contenerización:** Despliegue modular de servicios mediante Docker y Docker Compose.

---

## Estructura del Repositorio

* **[/SecureGate](./SecureGate):** Documentación detallada, diagramas de red y archivos de configuración del laboratorio.
* **[/Labs](./Labs):** Ejercicios prácticos y entornos de entrenamiento.
* **[/Notes](./Notes):** Documentación sobre procesos de instalación, decoders y reglas de monitoreo.
* **[/Report Templates](./Report%20Templates):** Plantillas para documentación de hallazgos y reportes de seguridad.

---
**Contacto:** [LinkedIn](https://www.linkedin.com/in/juandonado25/) | [Email](juandonado25@gmail.com)
