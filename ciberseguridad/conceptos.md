# Conceptos Basicos
> Conjunto de prácticas, políticas, herramientas y marcos técnicos destinados a proteger sistemas informáticos, redes, datos y servicios frente a accesos no autorizados, daños, interrupciones o uso indebido. Incluye prevención, detección, respuesta y recuperación ante amenazas.

## Red Team vs Blue Team
- **Blue Team:** defiende. Supervisa, endurece sistemas, detecta intrusiones, mitiga ataques y mejora controles. Su enfoque es defensivo.
    - **SOC Analyst (Niveles 1–3):** Monitoriza alertas, investiga eventos, clasifica amenazas y escala incidentes.
    - **Threat Intelligence Analyst:** Recoge, analiza y correlaciona inteligencia de amenazas para anticipar ataques.
    - **Incident Responder:** Gestiona el ciclo de respuesta: identificación, contención, erradicación y recuperación.
    - **Digital Forensics Analyst:** Preserva evidencias, reconstruye actividades del atacante y apoya investigaciones.
- **Red Team:** simula atacantes reales. Busca vulnerar sistemas, encontrar fallos, explotar debilidades y demostrar el impacto. Su enfoque es ofensivo.

## Amenaza, Ataque y Vulnerabilidad
- **Amenaza (Threat):** Es cualquier *circunstancia o evento con el potencial de causar daño a un sistema, red o información*. Las amenazas pueden ser intencionales (como un hacker) o accidentales (como un fallo eléctrico).
    *Ejemplo: Un virus informático que puede corromper datos sensibles.*
    
- **Ataque (Attack):** Es la *acción concreta que explota una vulnerabilidad* para *comprometer la seguridad de un sistema o información*. Un ataque transforma la amenaza potencial en un daño real.
    *Ejemplo: Un atacante envía un malware que se instala en un servidor y roba información.*
    
- **Vulnerabilidad (Vulnerability):** Es una *debilidad o fallo en un sistema, aplicación o proceso que puede ser explotado* por una amenaza para ejecutar un ataque.
    *Ejemplo: Una contraseña débil o software sin actualizar que permite acceso no autorizado.*   

## Triada CIA (CID en español)

- **Confidencialidad**: garantizar que la información *no sea accesible ni revelada a individuos no autorizados*, tanto en su almacenamiento como en su transmisión.
- **Integridad**: garantizar la *exactitud y completitud de la información* a lo largo de todo su ciclo de vida, evitando modificaciones no autorizadas, ya sean accidentales o intencionadas.
    - **Protección contra errores accidentales:** Error-correcting codes y Checksums (ej: CRCs).
    - **Protección contra alteraciones intencionadas:** Funciones hash y MACs.
    - **No repudio:** propiedad de seguridad que **impide que alguien niegue haber realizado una acción**, normalmente haber enviado un mensaje o haber firmado un documento.
- **Disponibilidad**: garantizar que la información y los sistemas que la gestionan *estén accesibles siempre que los usuarios autorizados* necesiten acceder a ellos.