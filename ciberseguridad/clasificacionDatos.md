# Clasificación de los Datos

# NIST CSF

| Objetivo de seguridad y Definición | Impacto bajo | Impacto moderado | Impacto alto |
| --- | --- | --- | --- |
| **Confidencialidad:** Preservar las restricciones autorizadas sobre el acceso y la divulgación de la información, incluyendo los medios para proteger la privacidad personal y la información propietaria. *[44 U.S.C., Sec. 3542]* | La divulgación no autorizada de información podría esperarse que tuviera un efecto adverso **limitado** sobre las operaciones de la organización, los activos de la organización o los individuos. | La divulgación no autorizada de información podría esperarse que tuviera un efecto adverso **grave** sobre las operaciones de la organización, los activos de la organización o los individuos. | La divulgación no autorizada de información podría esperarse que tuviera un efecto adverso **severo o catastrófico** sobre las operaciones de la organización, los activos de la organización o los individuos. |
| **Integridad:** Proteger contra la modificación o destrucción indebida de la información, e incluye garantizar la no repudio y la autenticidad de la información. *[44 U.S.C., Sec. 3542]* | La modificación o destrucción no autorizada de información podría esperarse que tuviera un efecto adverso **limitado** sobre las operaciones de la organización, los activos de la organización o los individuos. | La modificación o destrucción no autorizada de información podría esperarse que tuviera un efecto adverso **grave** sobre las operaciones de la organización, los activos de la organización o los individuos. | La modificación o destrucción no autorizada de información podría esperarse que tuviera un efecto adverso **severo o catastrófico** sobre las operaciones de la organización, los activos de la organización o los individuos. |
| **Disponibilidad:** Garantizar el acceso y uso oportuno y fiable de la información. *[44 U.S.C., Sec. 3542]* | La interrupción del acceso o uso de la información o de un sistema de información podría esperarse que tuviera un efecto adverso **limitado** sobre las operaciones de la organización, los activos de la organización o los individuos. | La interrupción del acceso o uso de la información o de un sistema de información podría esperarse que tuviera un efecto adverso **grave** sobre las operaciones de la organización, los activos de la organización o los individuos. | La interrupción del acceso o uso de la información o de un sistema de información podría esperarse que tuviera un efecto adverso **severo o catastrófico** sobre las operaciones de la organización, los activos de la organización o los individuos. |

# GDPR (General Data Protection Regulation)

> https://gdpr.eu/

El **Reglamento General de Protección de Datos (RGPD)** es la **ley de privacidad y seguridad más estricta del mundo**. Aunque fue redactada y aprobada por la Unión Europea (UE), impone obligaciones a las **organizaciones de cualquier lugar, siempre que se dirijan a personas de la UE** o recopilen datos relacionados con ellas. La GDPR está principalmente orientada a la protección de datos personales.

GDPR define los **datos personales** como cualquier **información que pueda identificar a una persona** física, directa o indirectamente, por ejemplo:

- Nombre, un número de identificación, datos de localización, un identificador en línea, uno o más factores específicos de la identidad física, fisiológica, genética, mental, económica, cultural o social de la persona

Para cumplir con GDPR, las organizaciones necesitan incorporar controles como la clasificación de los datos, donde deben tenerse en cuenta factores como:

- Tipo de datos (información financiera, datos sanitarios, etc.), base para la protección de datos (información personal o sensible), las categorías de las personas implicadas (clientes, pacientes, etc.), las categorías de destinatarios (especialmente terceros proveedores internacionales).

# PCI DSS (Payment Card Industry Data Security Standard)

> https://listings.pcisecuritystandards.org/documents/PCI_DSS_v3-2es-LA.pdf

PCI DSS **incluye medidas técnicas y operativas diseñadas para proteger información financiera personal de los consumidores**, como los datos de las tarjetas de crédito y débito utilizados en las transacciones con tarjetas de pago. 

La información financiera personal se define como un número de tarjeta de crédito en combinación con uno o varios de los siguientes elementos de datos:

- Nombre del titular de la tarjeta, Código de servicio, Fecha de caducidad, Valor CVC2, CVV2 o CID, PIN o bloque de PIN, Contenido de la banda magnética de una tarjeta de crédito.

Para cumplir con PCI DSS una organización debe incorporar diferentes controles de seguridad en el entorno donde se trata la información financiera. Entre estos requisitos de seguridad se encuentran: Seguridad de las comunicaciones, seguridad de los datos, control de acceso, gestión de vulnerabilidades…

# HIPAA (Health Insurance Portability and Accountability Act)

HIPAA aplica a EEUU y establece controles administrativos, físicos y técnicos para garantizar la confidencialidad, integridad y disponibilidad de información sanitaria (PHI y ePHI).

Se considera PHI cualquier información sanitaria que identifica a un individuo, incluyendo:

- Historial de salud mental, servicios sanitarios, pagos por asistencia sanitaria, otra información identificable, como el nombre, la dirección o el número de la Seguridad Social del paciente.

La ePHI se define como cualquier información sanitaria protegida almacenada o transmitida por medios electrónicos (discos duros de ordenador, así como los medios de memoria digital extraíbles
o transportables). Los medios de transmisión incluyen Internet o redes privadas. Ejemplos:

- Nombre, dirección postal, cualquier fecha directamente relacionada con un individuo, incluyendo cumpleaños, fecha de admisión o alta, o fecha de defunción, número de teléfono o fax, dirección de correo electrónico, número de la Seguridad Social, número de historia clínica, número de beneficiario de un plan de salud o seguro médico, identificador del vehículo, número de serie o matrícula, identificador biométrico, como huella dactilar, huella vocal o fotografía de cara completa, cualquier otro número, característica o código identificativo único.