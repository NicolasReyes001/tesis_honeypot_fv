# 🗺️ Mapa de Amenazas - Sistemas Fotovoltaicos Inteligentes
*(Basado en Harrou et al., 2023)*

## 🎯 Central: Ciberseguridad en Plantas FV
### 🔌 Capa de Comunicación
- Modbus TCP / SunSpec
- MQTT (IoT/Telemetría)
- HTTP REST / IEC 61850 (Extensión)

### 🦠 Tipos de Ataques Identificados
- DoS / DDoS
- DIA → FDIA / Covert / Replay
- MITM / Exfiltración de datos

### ⚡ Impacto Operativo
- Pérdida de generación / fluctuaciones en red
- Decisiones de control basadas en datos falsos
- Desgaste acelerado o daño a inversores/actuadores

### 🛡️ Oportunidades para Honeypot
- Servicios señuelo (Inversor Modbus + Broker MQTT)
- Detección por validación de rango físico y coherencia temporal
- Fingerprinting de atacante (IP, protocolo, secuencia de tramas, TTPs)