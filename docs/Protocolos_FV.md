# 📊 Tabla Comparativa: Protocolos en Sistemas Fotovoltaicos

| Protocolo | Puerto Default | Cifrado Nativo | Uso en Campo (FV) | Vulnerabilidad Principal | Prioridad Honeypot |
|-----------|----------------|----------------|-------------------|--------------------------|--------------------|
| **Modbus TCP** | 502 | ❌ No | Inversores legacy, RTUs, Medidores | Sin autenticación, spoofing fácil, lectura/escritura sin validación |  Alta |
| **MQTT** | 1883 / 8883 | ️ Opcional (TLS) | IoT, Telemetría Cloud | Credenciales en texto plano, suscripciones anónimas, topics sin ACL |  Alta |
| **SunSpec** | (Sobre Modbus) | ❌ No | Estándar de datos inversores | Expone estructura interna de registros | 🟡 Media |
| **IEC 61850** | 102 / 104 | ⚠️ Opcional | Subestaciones, Parques Grandes | Complejidad de implementación | 🟢 Futuro |
| **HTTP/REST** | 80 / 443 | ⚠️ HTTPS | Portales Web, APIs | Inyección SQL, XSS, credenciales débiles |  Media |

## 🔍 Análisis Breve y Justificación

### 1. Modbus TCP (Prioridad 🔴)
*   **Justificación:** Es el "lenguaje" universal de la automatización industrial. Casi todos los inversores solares (SMA, Fronius, Huawei) lo soportan para configuración local.
*   **Debilidad crítica:** Cualquier dispositivo en la red puede enviar un comando `Write` para apagar el inversor o cambiar sus límites de potencia sin pedir contraseña.
*   **Estrategia del Honeypot:** Emular un inversor que responda a lecturas pero que registre cualquier intento de escritura en una "base de datos de atacantes".

### 2. MQTT (Prioridad 🔴)
*   **Justificación:** Es el estándar para la **IoT Solar moderna**. Los inversores envían datos a la nube (monitoreo remoto) usando este protocolo ligero.
*   **Debilidad crítica:** Muchos instaladores dejan el broker abierto sin contraseña o usan credenciales por defecto (`admin/admin`).
*   **Estrategia del Honeypot:** Crear un broker falso que permita conectarse a cualquiera y ver qué tópicos (temas) intenta controlar el atacante.

### 3. SunSpec (Prioridad 🟡)
*   **Nota:** No es un protocolo de red en sí, sino un **modelo de datos** que se transporta usualmente sobre Modbus.
*   **Estrategia:** Nuestro honeypot de Modbus debe responder con valores que sigan el estándar SunSpec (ej: Register 40000 para Manufacturer, 40001 para Model) para parecer un dispositivo real.

### 4. IEC 61850 (Prioridad 🟢 - Futuro)
*   **Contexto:** Se usa en parques solares grandes conectados a subestaciones de alta tensión.
*   **Decisión:** Por complejidad técnica, se deja como recomendación para una fase 2 o tesis de maestría.

---

## 🎯 Conclusión para el Diseño del Honeypot
Basado en esta tabla, el proyecto se centrará en emular dos servicios principales:
1.  **Servidor Modbus TCP** (para atacar la capa de control industrial).
2.  **Broker MQTT** (para atacar la capa de telemetría IoT/Cloud).