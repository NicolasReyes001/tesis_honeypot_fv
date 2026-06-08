# 📄 Harrou et al. (2023) - Cybersecurity of PV Systems
**DOI:** 10.3389/fenrg2023.1274451  
**Fecha de lectura:** 08/06/2026  - lunes 
**Enfoque para mi tesis:** Extraer vectores de ataque y protocolos a emular en el honeypot

## 🔑 3 conceptos clave para mi honeypot
1. El inversor solar, el cerebro de los sistemas fotovoltaicos presenta vulnerabilidades que pueden ser aprovechadas por los piratas informáticos puede acarrear problemas de funcionamiento del sistema como la estabilidad y la seguridad de la red eléctrica.
2. Los protocolos de comunicación en los sistemas fotovoltaicos son de los campos mas vulnerableles, estos protocolos son los encargados de  la monitorización y control de las plantas fotovoltaicas permitiendo la comunicación interna entre los dispositivos con el exterior y asegurando que la información se produzca de forma automática y instantánea, aun asi son vulnerables a ataques DoS y DDoS interrumpiendolos y inundandolos con paquetes de datos o solicitudes y suplantación de identidad.
3. Los sistemas de control son una de las fuentes de ataques cibernéticos con el objetivo de provocar acciones no deseadas y toma de decisiones no deseadas e inexactas.
4. Los sensores sufren ataques cibernéticos que alteran los comandos y las lecturas de dichos sensores afectando a los mecanismos de control y que estos reciban datos inexistentes y falsos y asi actuen de una manera inadecuada.
5. La exfiltración de datos es encargada de robar dichos datos confidenciales de forma silenciosa, estos datos pueden ser financieros, propiedad intelectuar, datos del sistema real, o cualquier información sensible del sistema que puede afectar directamente a la empresa o el usuario dueño del sistema y causar inestabilidad en la red eléctrica.


## ⚠️ Amenazas específicas a sistemas FV mencionadas
- Ataques de denegación de servicio (DoS): Ataques de una sola fuente dirigidos a distintos componentes de los sistemas fotovoltaicos como lo pueden ser: Servidores, canales de comunicación, sensores e interfaces de monitorización.
- Ataques distribuidos de denegación de servicio (DDoS): Ataques que usan múltiples dispositivos para realizar ataques simultaneos, son muy dificiles de detectar y rastrear su fuente e interrumpen a la comunicación, los inversores, la transmición de datos y el control.
- Ataques a la integridad de los datos (DIA): Ataques que tienen como objetivo modificar, falsificar o alterar datos transmitidos reales para el el sistema tome decisiones incorrectas e imprecisas, este consta de los siguientes tipos de ataques:
    - Ataques de inyección de datos falsos (FDIA): Consiste en introducir al sistema datos falsos para engañar a los algoritmos de monitoreo, control o estimación para que tome desiciones erróneas del sistema, alarmas falsas, manipulación de procesos industriales y daños operativos.
    - Ataques encubiertos (CA): Ataques ocultos que alteran el comportamiento del sistema de manera estrategica y precisa para evitar la detección por sistemas de monitoreo y detectores de anomalías, son muy dificiles de detectar y suelen permanecer activos durante largos periodos de tiempo generando degradación progresiva del sistema.
    - Ataques de repetición (RA): Consiste en capturar los mensajes legítimos del sistema y retransmitirlos posteriormente con el objetivo de captar una información correcta en el sistema y transmitirla despues de un largo tiempo para realizar ejecución de comandos fuera de contexto, activación indebida de actuadores y altecación de procesos industriales.
- Ataques MITM: Ataque en el cual el pirata cibernético se sitúa entre dos entidades que se comunican con el objetivo de espiar, interceptar o manipular la información que se transmite en ese canal y se usa para robo de información, alteración de comandos, manipulación de procesos críticos y pérdidad de integridad y confidencialidad.


##  Protocolos/comunicaciones citados como vulnerables
- Falta de cifrado y cortafuegos en las redes: Muchos de estos sitemas fotovoltaicos no cuentan con mecanismos y metodos de seguridad como el cifrado y los cortafuegos dejando al expuesto el acceso no autorizado y la filtracion de datos no deseados.
- Redes de comuniación: Estas redes carecen de protección adecuada y ofrecen oportunidades de ataques cibernéticos  para manipulación de datos sensibles.
- Modbus TCP (Puerto 502): Usado ampliamente en inversores antiguos; carece de cifrado y autenticación nativa.
- MQTT (Puerto 1883/8883): Común en inversores IoT modernos para telemetría; vulnerable si no usa TLS/certificados.
- SunSpec Alliance Models: Estándar de datos para inversores; expone registros críticos de estado y control.
- HTTP/REST APIs: Usadas en portales web de gestión de plantas; susceptibles a inyección SQL o XSS si no están parcheadas.

## 💡 Ideas aplicables a mi honeypot solar
- Servicios a emular: 
    - Inversor Solar (SunSpec): Registros de potencia activa, tensión DC y temperatura con simuladores con valores coherentes al horario.
    - SmartLogger / EMS: Interfaz wb y API con credenciales débiles deliberadas.
    - Broker MQTT sin TLS: Publica telemetría falsa en tiempo real para atraer suscriptores maliciosos.
    - SCADA IEC 61850: Nodo logico de inversores (ZINV) y  medidores inteligentes (MMXU) accesibles vía MMS.
- Tráfico a monitorear: 
    - Tasa de peticiones por IP: peticiones por segundo hacia cada servicio. Captura floods ModBus, HTTP y MQTT que delatan DoS/DDoS de fuente única o distribuida.
    - Escrituras a registros de control: Cualquier función Modbus sobre registros de setpoint o comandos de actuador.
    - Secuencia y timing de tramas: Hash + timestamp de cada trama recibida que detecta tramas idénticas retrasnmitidas o intervalos anormalmente regulares (bots).
    - Clientes MQTT no autorizados: Conexipnes al broker sin credenciales.
    - Escaneos de puertos / banner grab: Conexiones TCP que leen el anner y cierran sin enviar datos válidos. Indica reconocimento previo al ataque.
- Indicadores de ataque: 
    - Cambios abruptos e irreales en datos de potencia solicitados por el atacante.
    - Umbral de saturación para DoS, si proviene de mas de 3 IPs simultaneas en menos de 5s clasificar como DDoS.
    - Valor del sensor fuera de rango fisico.
    - Deriva acumulada del setpoint, vaciación total de 5% del valor nominal en una ventana de 10 min.
    - Tramas duplicadas (mismo hash) payload idéntico al de una trama anterior o timestamp anterior al último visto en esa sesión.
    - Suscripción a topic de contro o interceptación topics de actuador sin pertenencia a la lista blanda del EMS
