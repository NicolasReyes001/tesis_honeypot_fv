#  Harrou et al. (2023) - Cybersecurity of PV Systems
**DOI:** 10.3389/fenrg.2023.1274451  
**Fecha de lectura:** 08/06/2026 (Lunes)  
**Enfoque para mi tesis:** Extraer vectores de ataque y protocolos a emular en el honeypot

## 3 conceptos clave para mi honeypot
1. **Vulnerabilidad estructural del inversor:** El inversor actúa como punto de convergencia IT/OT. Su exposición a redes externas lo convierte en vector de entrada para comprometer la estabilidad y seguridad de la red eléctrica.
2. **Protocolos legacy sin seguridad nativa:** Modbus TCP y MQTT, ampliamente usados para monitoreo y control, carecen de autenticación y cifrado por defecto, facilitando ataques DoS/DDoS y suplantación de identidad.
3. **Prioridad de integridad sobre confidencialidad:** Los ataques buscan alterar decisiones de control (FDIA, Replay) más que robar datos. Un honeypot debe detectar anomalías en comandos y lecturas de sensores antes de que impacten la operación real.

## Amenazas específicas a sistemas FV mencionadas
- **DoS / DDoS:** Saturación de servidores, canales de comunicación o interfaces de monitoreo. DDoS utiliza múltiples fuentes, dificultando el rastreo y provocando interrupción de telemetría y control.
- **Ataques a la integridad de datos (DIA):** Alteración de datos en tránsito para inducir decisiones erróneas. Se subclasifica en:
  - *FDIA (False Data Injection):* Inyección de mediciones falsas para engañar algoritmos de estimación/control.
  - *Covert Attacks (CA):* Alteraciones coordinadas que evaden detectores de anomalías, manteniéndose ocultos por largos periodos.
  - *Replay Attacks (RA):* Captura y retransmisión diferida de tramas legítimas para ejecutar comandos fuera de contexto o activar actuadores indebidamente.
- **MITM (Man-in-the-Middle):** Intercepción y manipulación de canales de comunicación para robo de información, alteración de setpoints o pérdida de confidencialidad.
- **Exfiltración de datos:** Extracción silenciosa de datos operativos, propiedad intelectual o configuraciones sensibles. El honeypot actúa como trampa para capturar TTPs (Tactics, Techniques, Procedures) del atacante.

## Protocolos/comunicaciones citados como vulnerables
- **Falta de cifrado y segmentación:** Redes OT expuestas sin firewalls o VLANs aisladas.
- **Modbus TCP (Puerto 502):** Sin autenticación ni cifrado nativo. Vulnerable a escaneo, spoofing y escrituras no autorizadas.
- **MQTT (Puerto 1883/8883):** Telemetría IoT moderna. Vulnerable si no implementa TLS, autenticación por certificados o listas de control de acceso (ACL).
- **SunSpec Alliance Models:** Estándar abierto para inversores. Expone estructura de registros críticos (estado, potencia, configuración).
- **HTTP/REST APIs:** Portales de gestión web. Susceptibles a inyección, XSS o credenciales débiles si no están hardenizados.

## Ideas aplicables a mi honeypot solar
- **Servicios a emular (Scope Semestre 1):**
  - *Inversor SunSpec/Modbus:* Registros de potencia activa, tensión DC, temperatura e irradiación. Respuestas coherentes con perfil solar diario.
  - *Broker MQTT:* Tópicos `pv/planta1/inversor/data` y `pv/planta1/control`. Acepta suscripciones anónimas para capturar reconocimiento.
  - *(Futuro/Extensión):* Interfaz HTTP básica y nodo IEC 61850 (ZINV/MMXU) para alta interacción.
- **Tráfico a monitorear:**
  - *Rate limiting:* Peticiones/segundo por IP. Umbrales >X req/s indican DoS/DDoS.
  - *Escrituras en registros críticos:* Funciones Modbus `06` (Write Single) o `10` (Write Multiple) en registros de solo lectura.
  - *Secuencia y timing:* Detección de tramas idénticas retransmitidas (Replay) o intervalos anormalmente regulares (bots).
  - *Clientes MQTT no autorizados:* Conexiones sin credenciales o suscripción a tópicos de control (`/cmd`, `/setpoint`).
  - *Reconocimiento:* Conexiones TCP que cierran sin handshake válido o solicitan banners/fingerprinting.
- **Indicadores de ataque (Alertas):**
  - Valores fuera de rango físico (ej: potencia > capacidad nominal, temperatura < -40°C o > 150°C).
  - Deriva acumulada de setpoints > 5% en ventana de 10 min (indicador de FDIA progresivo).
  - Tramas duplicadas (mismo payload + timestamp anterior al último registrado).
  - Suscripción a tópicos de control desde IPs no whitelisted.
  - Saturación >3 IPs simultáneas en <5s → clasificación automática DDoS.