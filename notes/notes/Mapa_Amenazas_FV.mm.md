# 🗺️ Mapa de Amenazas - Sistemas Fotovoltaicos Inteligentes
*(Basado en Harrou et al., 2023)*

## 🎯 Central: Ciberseguridad en Plantas FV
### 🔌 Capa de Comunicación
- Modbus TCP (puerto 502)
- MQTT (puerto 1883)
- IEC 61850 / SunSpec
- HTTP/REST (portales de monitoreo)

### 🦠 Tipos de Ataques Identificados
- False Data Injection (FDI)
- Denegación de Servicio (DoS)
- Man-in-the-Middle (MITM)
- Replay / Spoofing de setpoints
- Acceso no autorizado a inversores IoT

### ⚡ Impacto Operativo
- Pérdida de sincronización con la red
- Sobrecarga/desconexión forzada de inversores
- Manipulación de mediciones de potencia/irradiancia
- Exposición de datos de generación a terceros

### 🛡️ Oportunidades para Honeypot
- Emular endpoint Modbus con registros solares falsos
- Capturar escaneos de puertos y consultas MQTT
- Registrar intentos de escritura en registros read-only
- Generar alertas tempranas antes de tocar activos reales