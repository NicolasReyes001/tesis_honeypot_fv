# 🗓️ PLAN DE ACCIÓN INTENSIVO: 2 MESES (8 SEMANAS)

## 🎯 Honeypot para Sistemas Fotovoltaicos Inteligentes

### ⚡ Alta Intensidad · 4-6 horas diarias · Enfoque práctico-académico


**Universidad:** Santo Tomás - Bogotá  
**Carrera:** Ingeniería Electrónica  
**Estudiante:** [Nicolás Daniel Reyes Meneses]  
**Fecha de inicio:** 07/06/2026  
**Asesor:** [Nombre del Docente]

---

# 📑 Índice

1. [Estado actual del proyecto](#-estado-actual-del-proyecto)
2. [Semana 1 - Fundamentos de Ciberseguridad en Energía Solar](#-semana-1-fundamentos-de-ciberseguridad-en-energía-solar)
3. [Semana 2 - Arquitectura de Sistemas Fotovoltaicos Inteligentes](#-semana-2-arquitectura-de-sistemas-fotovoltaicos-inteligentes)
4. [Semana 3 - Fundamentos Técnicos de Honeypots ICSOT](#-semana-3-fundamentos-técnicos-de-honeypots-icsot)
5. [Semana 4 - Diseño de la Propuesta de Tesis](#-semana-4-diseño-de-la-propuesta-de-tesis-documento-preliminar)
6. [Semana 5 - Desarrollo del Emulador de Servicios Solares](#-semana-5-desarrollo-del-emulador-de-servicios-solares)
7. [Semana 6 - Validación y Pruebas de Seguridad](#-semana-6-validación-y-pruebas-de-seguridad)
8. [Semana 7 - Redacción Avanzada](#-semana-7-redacción-avanzada-y-preparación-de-sustentación-preliminar)
9. [Semana 8 - Consolidación](#-semana-8-consolidación-revisión-final-y-plan-de-ejecución-semestral)
10. [Métricas de Éxito](#-métricas-de-éxito-del-plan)
11. [Contactos y Recursos](#-contactos-y-recursos)
12. [Bitácora](#-bitácora-de-avance-semanal)

## 📊 Estructura diaria sugerida
## 🌅 BLOQUE MAÑANA (2h) - *Teoría y lectura*
* **30 min:** Repaso del día anterior.
* **90 min:** Lectura técnica/artículos **+** toma de notas estructuradas.

## 🌞 BLOQUE TARDE (2-3h) - *Práctica y desarrollo*
* **30 min:** Configuración de entorno/herramientas.
* **90-120 min:** *Coding*, pruebas y experimentación.
* **30 min:** Documentación de hallazgos y errores.

## 🌙 BLOQUE NOCHE (30-60 min) - *Síntesis y planificación*
* **20 min:** Actualizar bitácora de investigación.
* **20 min:** Planificar tareas del día siguiente.
* **20 min:** Repaso ligero de conceptos clave.

## ✅ ESTADO ACTUAL DEL PROYECTO

## ✅ COMPLETADO (Configuración inicial)

* **📁 Estructura de carpetas:**

```text
tesis_honeypot_fv/
├── docs/
├── code/
│   ├── deploy/
│   ├── handlers/
│   ├── simulacion/
│   ├── tests/
│   └── config/
├── logs/
├── results/
├── refs/
└── notes/
```
* **🐍 Python:** Versión 3.14 + pip 26.1.2 funcional.
* **💻 Editor:** VS Code con extensiones (Python, Docker, Pylance).
* **📦 Entorno:** Entorno virtual (`.venv`) activo con librerías clave.
* **🐳 Docker:** Docker Desktop + WSL2 integrado y verificado.
* **📚 Bibliografía:** 3 papers clave en `refs/` con `referencias.bib` en formato IEEE.
* **📝 Notas:** Plantillas de lectura guiada listas.

---

### 📍 UBICACIÓN DEL PROYECTO
`C:\Proyecto De Grado\tesis_honeypot_fv`


---

# 📅 SEMANA 1: Fundamentos de Ciberseguridad en Energía Solar

### 🎯 Objetivo: Comprender el ecosistema de amenazas en sistemas FV

| Día | Actividad Principal | Entregable | Tiempo |
|-----|-------------------|------------|--------|
| **Lun** | Lectura: Harrou et al. (2023) - Cybersecurity of PV systems | Mapa mental de amenazas FV | 4h |
| **Mar** | Investigación: Protocolos en plantas solares (Modbus TCP, MQTT, IEC 61850) | Tabla comparativa de protocolos | 4h |
| **Mié** | Estudio: Tipos de honeypots (baja/alta interacción) | Diagrama de clasificación honeypots | 4h |
| **Jue** | Análisis de casos: Ataques reales a infraestructura energética | Línea de tiempo de incidentes | 4h |
| **Vie** | Configuración de herramientas: Wireshark, análisis de tráfico | Capturas de ejemplo en logs/ | 5h |
| **Sáb** | Lectura: Diamantoulakis et al. (2020) - Game Theoretic Honeypot | Resumen de estrategias de despliegue | 3h |
| **Dom** | **Checkpoint semanal**: Redactar problema preliminar + 3 preguntas | `notes/Semana1_Problema.md` | 2h |

### 📚 Lecturas obligatorias Semana 1:
1. ✅ Harrou, F. et al. (2023). "Cybersecurity of photovoltaic systems..." - Frontiers in Energy Research
2. ✅ Diamantoulakis, P. et al. (2020). "Game Theoretic Honeypot Deployment..." - Sensors, MDPI
3. ✅ Walker, A. et al. (2021). "Cybersecurity in Photovoltaic Plant Operations" - NREL

### 📝 Tareas clave:
- [ ] Crear `notes/01_lectura_harrou_2023.md` con plantilla de extracción
- [ ] Crear `notes/02_lectura_diamantoulakis_2020.md`
- [ ] Crear `notes/03_lectura_walker_nrel_2021.md`
- [ ] Tabla comparativa de protocolos en `docs/protocolos_FV.md`
- [ ] Diagrama de tipos de honeypots en `docs/tipos_honeypots.md`

---

# 📅 SEMANA 2: Arquitectura de Sistemas Fotovoltaicos Inteligentes

### 🎯 Objetivo: Modelar los componentes a emular en el honeypot

| Día | Actividad Principal | Entregable | Tiempo |
|-----|-------------------|------------|--------|
| **Lun** | Estudio: Arquitectura típica de planta FV inteligente | Diagrama de arquitectura FV | 4h |
| **Mar** | Investigación: Comportamiento normal vs. anómalo en telemetría solar | Lista de 10 métricas clave a emular | 4h |
| **Mié** | Práctica: Usar `pvlib-python` para simular generación solar | Script `code/simulacion/simular_generacion.py` | 5h |
| **Jue** | Estudio: Puertos y servicios en inversores comerciales (SMA, Fronius) | Tabla de puertos/servicios objetivo | 4h |
| **Vie** | Práctica: Capturar tráfico MQTT/Modbus con Wireshark | Archivo `.pcap` en `logs/` + análisis | 5h |
| **Sáb** | Lectura complementaria + síntesis de vulnerabilidades | Lista de 5 vulnerabilidades críticas | 3h |
| **Dom** | **Checkpoint**: Documento de arquitectura del honeypot | `docs/Arquitectura_Honeypot.md` | 2h |

### 💻 Código a desarrollar

```python
# code/simulacion/simular_generacion.py

import pandas as pd
import matplotlib.pyplot as plt
from pvlib import location, irradiance, temperature, pvsystem

# Definir ubicación Bogotá
loc = location.Location(4.6, -74.1, 'America/Bogota', -5)

times = pd.date_range(
    '2026-06-01',
    periods=24,
    freq='H',
    tz=loc.tz
)

# Calcular irradiación y temperatura
solpos = loc.get_solarposition(times)

dni = irradiance.clearsky(
    loc.latitude,
    loc.longitude,
    times
)['dni']

temp_amb = temperature.sapm_temp(
    'open_rack_glass_glass',
    times.hour,
    dni
)

# Modelo de panel básico
system = pvsystem.PVSystem(
    surface_tilt=20,
    surface_azimuth=180,
    module_parameters={
        'pdc0': 300,
        'gamma_pdc': -0.004
    }
)

ac_power = system.get_ac(
    'pvwatts',
    system.get_dc(dni, temp_amb)
)

# Graficar
ac_power.plot(
    title='Generación AC simulada - Bogotá'
)

plt.ylabel('Potencia [W]')
plt.grid(True)
plt.tight_layout()

plt.savefig(
    '../results/generacion_bogota.png',
    dpi=300
)
```

## 📝 Tareas Clave

- [ ] Crear `docs/arquitectura_FV.drawio`
- [ ] Implementar simulación en `code/simulacion/simular_generacion.py`
- [ ] Generar gráficas en `results/`
- [ ] Documentar puertos en `docs/puertos_servicios_FV.md`
- [ ] Capturar tráfico en `logs/trafico_modbus.pcap`

## 📅 SEMANA 3

## 📅 SEMANA 3: Fundamentos Técnicos de Honeypots ICS/OT
**🎯 Objetivo:** Dominar herramientas y frameworks de honeypots industriales.

| Día | Actividad Principal | Entregable | Tiempo |
| :--- | :--- | :--- | :--- |
| **Lun** | Estudio: Conpot, GridPot, Virtuepot: comparación | Matriz comparativa de frameworks | 4h |
| **Mar** | Práctica: Desplegar Conpot en Docker y explorar config base | Dockerfile funcional + logs | 5h |
| **Mié** | Práctica: Modificar plantilla Conpot para emular Modbus en puerto 502 | `code/config/modbus_template.xml` | 5h |
| **Jue** | Estudio: Logging y análisis de ataques (formato JSON, SIEM básico) | Esquema de logging estructurado | 4h |
| **Vie** | Práctica: Integrar Conpot con Elastic Stack o Wazuh | Dashboard básico de ataques | 6h |
| **Sáb** | Lectura: Survey sobre SCADA Security and Honeypot | Lista de 7 buenas prácticas | 3h |
| **Dom** | Checkpoint: Documento de implementación | `docs/Implementacion_Conpot_FV.md` | 2h |

---

## 🐳 Docker Compose para Honeypot

```yaml
# code/deploy/docker-compose.yml

version: "3.8"

services:
  honeypot-fv:
    image: mushorg/conpot:latest
    container_name: honeypot_fv

    ports:
      - "502:502"
      - "1883:1883"
      - "80:80"

    volumes:
      - ./config:/etc/conpot
      - ./logs:/var/log/conpot

    restart: unless-stopped

    networks:
      - honeynet

networks:
  honeynet:
    driver: bridge
```

### 📝 Tareas clave

- [ ] Conpot corriendo en Docker y accesible
- [ ] Configuración personalizada en `code/config/`
- [ ] Logs de prueba en `logs/conpot_test.log`
- [ ] Matriz comparativa en `docs/comparativa_honeypots.md`

## 📅 SEMANA 4

# 📅 SEMANA 4: Diseño de la Propuesta de Tesis (Documento Preliminar)

## 🎯 Objetivo
Redactar los primeros 3 capítulos en formato IEEE.

| Día | Actividad Principal | Entregable | Tiempo |
|------|--------------------|------------|---------|
| Lun | Redacción: Introducción (contexto, justificación, relevancia) | Sección 1.0 completa (~800 palabras) | 4h |
| Mar | Redacción: Planteamiento del problema + pregunta de investigación | Sección 1.1-1.2 validada | 4h |
| Mié | Redacción: Objetivos (general + 3-4 específicos) + alcance | Sección 1.3-1.4 con verbos en infinitivo | 4h |
| Jue | Marco teórico I: Ciberseguridad en ICS/SCADA + protocolos | Sección 2.1 con 8-10 referencias IEEE | 5h |
| Vie | Marco teórico II: Honeypots en Smart Grid + estado del arte FV | Sección 2.2-2.3 con tabla comparativa | 5h |
| Sáb | Formato IEEE: Aplicar estilo, generar referencias con Zotero | `docs/Propuesta_Preliminar_IEEE.docx` | 4h |
| Dom | Checkpoint: Revisión con checklist de calidad | Documento listo para asesor | 2h |

## 📝 Tareas clave

- Documento completo en `docs/Propuesta_Preliminar_IEEE.docx`
- `Referencias.bib` actualizado con 10+ fuentes
- Checklist de calidad completado
- Enviado a asesor para revisión

## Estructura del documento IEEE

```text
1. Introducción
   1.1 Planteamiento del problema
   1.2 Pregunta de investigación
   1.3 Objetivos
   1.4 Alcance

2. Marco Teórico
   2.1 Ciberseguridad en ICS/SCADA
   2.2 Honeypots para Smart Grids
   2.3 Estado del arte en sistemas fotovoltaicos

3. Metodología Preliminar

Referencias
```

---

## 📅 SEMANA 5

# 📅 SEMANA 5: Desarrollo del Emulador de Servicios Solares

## 🎯 Objetivo
Crear el núcleo funcional del honeypot especializado.

| Día | Actividad Principal | Entregable | Tiempo |
|------|--------------------|------------|---------|
| Lun | Diseño: Especificar respuestas realistas para consultas Modbus | `docs/especificacion_respuestas.md` | 4h |
| Mar | Coding: Extender Conpot para emular registros solares | `code/handlers/solar_modbus_handler.py` | 5h |
| Mié | Coding: Implementar servicio MQTT simulado para telemetría | `code/handlers/mqtt_emulator.py` | 5h |
| Jue | Pruebas: Validar respuestas a consultas legítimas con datos coherentes | Video/demo de interacción básica | 4h |
| Vie | Seguridad: Aislar honeypot en red, configurar logging seguro | Diagrama de aislamiento de red | 5h |
| Sáb | Optimización: Reducir overhead de recursos (CPU/RAM) | Benchmark: consumo vs funcionalidad | 3h |
| Dom | Checkpoint: Demo funcional + documentación técnica | Repo con código comentado | 2h |

## 🔧 Ejemplo de handler Modbus

```python
from pymodbus.datastore import ModbusSequentialDataBlock

class SolarModbusHandler:
    def __init__(self):
        self.power_kw = 125.4
        self.voltage_v = 480
        self.current_a = 261

    def read_register(self, address):
        registers = {
            1000: int(self.power_kw * 10),
            1001: self.voltage_v,
            1002: self.current_a
        }

        return registers.get(address, 0)

handler = SolarModbusHandler()
print(handler.read_register(1000))
```

## 📝 Tareas clave

- Handler Modbus funcional en `code/handlers/`
- Emulador MQTT funcional
- Demo grabada en `results/demo_honeypot.mp4`
- `README.md` actualizado con instrucciones de despliegue

---

## 📅 SEMANA 6

# 📅 SEMANA 6: Validación y Pruebas de Seguridad

## 🎯 Objetivo
Evaluar la efectividad del honeypot con ataques simulados.

| Día | Actividad Principal | Entregable | Tiempo |
|------|--------------------|------------|---------|
| Lun | Preparación: Configurar máquina atacante (Kali Linux VM) | Entorno de pruebas aislado funcional | 4h |
| Mar | Pruebas I: Escaneo de puertos con Nmap y análisis | `pruebas_nmap.pdf` con capturas | 5h |
| Mié | Pruebas II: Conexiones Modbus malformadas con Pymodbus | Logs de ataques capturados + análisis | 5h |
| Jue | Pruebas III: Simular ataque FDIA alterando valores de potencia | `code/tests/test_fdia.py` | 4h |
| Vie | Análisis: Comparar detección vs sistema sin protección (baseline) | Tabla comparativa de métricas | 4h |
| Sáb | Métricas: Calcular tasa de detección, falsos positivos, overhead | Gráficas de resultados + interpretación | 3h |
| Dom | Checkpoint: Documento de validación | Presentación de 5 diapositivas | 2h |

## 🔧 Script de prueba

```python
from pymodbus.client import ModbusTcpClient

client = ModbusTcpClient("192.168.1.100", port=502)

if client.connect():
    result = client.read_holding_registers(
        address=1000,
        count=5,
        slave=1
    )

    print(result.registers)
    client.close()
else:
    print("No se pudo conectar")
```

## 📝 Tareas clave

- Entorno de pruebas con Kali Linux o herramientas de pentesting
- Al menos 10 ataques simulados y capturados en `logs/`
- Métricas calculadas en `results/metricas_validacion.xlsx`
- Documento `docs/Resultados_Validacion.md`

---

## 📅 SEMANA 7

# 📅 SEMANA 7: Redacción Avanzada y Preparación de Sustentación Preliminar

## 🎯 Objetivo
Tener documento casi completo y presentación de avance.

| Día | Actividad Principal | Entregable | Tiempo |
|------|--------------------|------------|---------|
| Lun | Redacción: Capítulo 3 - Metodología (diseño, herramientas) | Sección 3.0 completa (~1200 palabras) | 4h |
| Mar | Redacción: Capítulo 4 - Resultados (implementación, pruebas) | Sección 4.0 con 3-4 gráficas profesionales | 5h |
| Mié | Redacción: Conclusiones preliminares + trabajo futuro | Sección 5.0 con 3 conclusiones clave | 4h |
| Jue | Formato final: Revisar citas IEEE, numeración, márgenes | `docs/Tesis_Avance_Completo_IEEE.pdf` | 4h |
| Vie | Presentación: Diseñar slides de 10-12 diapositivas | `docs/Presentacion_Avance.pptx` | 5h |
| Sáb | Ensayo: Practicar exposición oral (15 min) + Q&A | Grabación de ensayo + lista de Q&A | 3h |
| Dom | Checkpoint: Revisión final con checklist | Paquete completo para asesor | 2h |

## Estructura de presentación (12 slides)

```text
1. Título
2. Contexto
3. Problema
4. Justificación
5. Objetivos
6. Marco Teórico
7. Arquitectura Propuesta
8. Implementación Honeypot
9. Metodología de Validación
10. Resultados
11. Conclusiones
12. Trabajo Futuro
```

## 📝 Tareas clave

- Documento completo en formato IEEE
- Presentación en PowerPoint o Beamer
- Ensayo grabado y autoevaluado
- Lista de 10 preguntas frecuentes con respuestas

---

## 📅 SEMANA 8

# 📅 SEMANA 8: Consolidación, Revisión Final y Plan de Ejecución Semestral

## 🎯 Objetivo
Entregar propuesta sólida y planificar el semestre de tesis.

| Día | Actividad Principal | Entregable | Tiempo |
|------|--------------------|------------|---------|
| Lun | Revisión externa: Compartir documento con asesor/compañeros | Lista de mejoras priorizadas | 3h |
| Mar | Ajustes: Incorporar retroalimentación, corregir errores | Versión 2.0 del documento | 4h |
| Mié | Planificación: Diseñar cronograma detallado para el semestre | `docs/Cronograma_Semestral_Gantt.png` | 4h |
| Jue | Documentación técnica: Mejorar README, añadir diagramas | Repo GitHub listo para compartir | 4h |
| Vie | Preparación administrativa: Revisar requisitos USTA | `docs/Checklist_Tramites_UST.md` | 3h |
| Sáb | Simulación de defensa: Presentar ante espejo o grabar video | Autoevaluación con rúbrica | 2h |
| Dom | GRAN CHECKPOINT FINAL: Paquete completo de entrega | Carpeta `ENTREGA_FINAL/` | 3h |

## Estructura final de entrega

```text
ENTREGA_FINAL/
│
├── docs/
│   ├── Propuesta_Preliminar_IEEE.docx
│   ├── Tesis_Avance_Completo_IEEE.pdf
│   ├── Presentacion_Avance.pptx
│   ├── Resultados_Validacion.md
│   ├── comparativa_honeypots.md
│   ├── especificacion_respuestas.md
│   ├── Cronograma_Semestral_Gantt.png
│   └── Checklist_Tramites_UST.md
│
├── code/
│   ├── handlers/
│   │   ├── solar_modbus_handler.py
│   │   └── mqtt_emulator.py
│   │
│   └── tests/
│       └── test_fdia.py
│
├── logs/
│   └── conpot_test.log
│
├── results/
│   ├── demo_honeypot.mp4
│   └── metricas_validacion.xlsx
│
├── Referencias.bib
├── README.md
└── LICENSE
```

## 📝 Tareas clave

- Carpeta `ENTREGA_FINAL/` completa
- Cronograma del semestre en formato Gantt
- Checklist de trámites USTA completado
- Repositorio GitHub actualizado

---

# 🎯 MÉTRICAS DE ÉXITO DEL PLAN

## ✅ Al finalizar las 8 semanas tendrás:

- Documento de propuesta en formato IEEE listo para revisión formal.
- Prototipo funcional de honeypot emulando servicios solares (Modbus/MQTT).
- Repositorio documentado y versionado en GitHub.
- Presentación de avance preparada para defensa preliminar.
- Cronograma detallado para el semestre de tesis.
- Dominio de Docker, Python, pvlib y Wireshark.
- 15-20 referencias IEEE organizadas y citadas correctamente.

---

# 💡 CONSEJOS PARA MANTENER ALTA INTENSIDAD

- Bloquea distracciones con Cold Turkey o Focus To-Do.
- Establece recompensas semanales.
- Participa en comunidades de ciberseguridad industrial.
- Dormir 7-8 horas por noche.
- Realizar pausas activas cada 90 minutos.
- Realizar commits diarios en Git.
- Mantener respaldos en la nube.

---

# 📞 CONTACTOS Y RECURSOS

## Asesor

- Nombre: `[Completar]`
- Email: `[Completar]`
- Horario de atención: `[Completar]`

## Recursos clave

- Repositorio GitHub: `https://github.com/TU-USUARIO/tesis_honeypot_fv`
- Biblioteca USTA: `https://biblioteca.usta.edu.co/`
- IEEE Xplore: Acceso mediante proxy institucional USTA
- NREL Publications: `https://www.nrel.gov/publications`

## Herramientas

- Python 3.14 + pip
- Docker Desktop + WSL2
- VS Code + extensiones Python, Docker y GitLens
- Wireshark
- Draw.io
- Zotero

---

# 📓 BITÁCORA DE AVANCE SEMANAL

## Semana 1 (07-13 Jun 2026)

- [ ] Lecturas completadas
- [ ] Mapa mental de amenazas
- [ ] Tabla de protocolos
- [ ] Problema de investigación definido

**Notas:**

---

## Semana 2 (14-20 Jun 2026)

- [ ] Arquitectura definida
- [ ] Simulación pvlib funcional
- [ ] Capturas de tráfico

**Notas:**

---

## Semana 3 (21-27 Jun 2026)

- [ ] Conpot desplegado
- [ ] Configuración personalizada
- [ ] Logs integrados

**Notas:**

---

## Semana 4 (28 Jun - 04 Jul 2026)

- [ ] Documento preliminar redactado
- [ ] Formato IEEE aplicado
- [ ] Enviado a asesor

**Notas:**

---

## Semana 5 (05-11 Jul 2026)

- [ ] Handlers Modbus/MQTT funcionales
- [ ] Demo grabada
- [ ] Código documentado

**Notas:**

---

## Semana 6 (12-18 Jul 2026)

- [ ] Pruebas de penetración completadas
- [ ] Métricas calculadas
- [ ] Resultados validados

**Notas:**

---

## Semana 7 (19-25 Jul 2026)

- [ ] Documento completo
- [ ] Presentación lista
- [ ] Ensayo realizado

**Notas:**

---

## Semana 8 (26 Jul - 01 Ago 2026)

- [ ] Revisión final completada
- [ ] Paquete de entrega listo
- [ ] Cronograma del semestre definido

**Notas:**