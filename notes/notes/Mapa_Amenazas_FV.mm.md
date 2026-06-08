 Ex# 🗺️ Mapa de Amenazas - Sistemas Fotovoltaicos Inteligentes
*(Basado en Harrou et al., 2023)*

## 🎯 Central: Ciberseguridad en Plantas FV
### 🔌 Capa de Comunicación
- Modbus TCP / IEC 61850.
- MQTT / RS485
- HTTP REST

### 🦠 Tipos de Ataques Identificados
- DoS / DDoS
- DIA -> FDIA / CA / Replay.
- MITM / Exfiltracción

### ⚡ Impacto Operativo
- Pérdida de generación — fluctuaciones y cortes en red
- Decisiones erróneas — control basado en datos falsos
- Daño a equipos — inversores y actuadores

### 🛡️ Oportunidades para Honeypot
- Servicios señuelo — inversor, EMS, broker MQTT
- Detección por rango físico — irradiancia, temperatura, potencia
- Fingerprinting de atacante — IP, protocolo, secuencia, timing