# Resumen ejecutivo

| Motor | Modelo | Licencia o modalidad general | Usos comunes | Consideración clave |
|---|---|---|---|---|
| **MongoDB** | Documentos | Community Server bajo SSPL; hay opciones comerciales y servicio Atlas | Aplicaciones con datos JSON y esquemas cambiantes | La SSPL no es una licencia de código abierto aprobada por OSI; revisa sus términos si ofreces MongoDB como servicio |
| **Apache Cassandra** | Columnas anchas | Apache License 2.0 | Grandes volúmenes distribuidos, alta disponibilidad y escrituras intensivas | Conviene diseñar las tablas a partir de las consultas previstas |
| **Redis** | Clave-valor en memoria y estructuras de datos | Redis 8 ofrece opciones AGPLv3, SSPLv1 y RSALv2; productos comerciales con otros términos | Caché, sesiones, colas, datos en tiempo real | Las condiciones dependen de la versión y de la licencia elegida |
| **Amazon DynamoDB** | Clave-valor y documentos | Servicio propietario gestionado en AWS | Aplicaciones cloud que necesitan operación administrada y escala variable | Dependencia de AWS y costos que dependen del uso y las opciones habilitadas |
| **Neo4j** | Grafos | Community Edition bajo GPLv3; Enterprise y servicios gestionados con condiciones comerciales | Redes de relaciones, recomendaciones y detección de fraude | Brilla cuando las relaciones son centrales, pero puede ser excesivo para datos simples |
| **Apache CouchDB** | Documentos JSON | Apache License 2.0 | Aplicaciones móviles, sincronización y trabajo sin conexión | Conflictos de sincronización pueden requerir lógica de resolución en la aplicación |

# Análisis por motor

## 1. MongoDB

MongoDB almacena información como documentos BSON organizados en colecciones. Los documentos pueden contener campos anidados y no necesitan compartir exactamente la misma estructura, lo que facilita adaptar el modelo de datos conforme evoluciona una aplicación.

**Ventajas**
- Es flexible cuando los registros tienen estructuras distintas o cambian con frecuencia.
- El modelo de documento puede representar juntos datos que la aplicación suele leer o modificar en conjunto.
- Tiene opciones de réplicas para disponibilidad y de fragmentación para distribuir datos.
- Ofrece transacciones ACID de varios documentos, aunque su conveniencia debe evaluarse frente al diseño de los datos y la carga.

**Desventajas**
- La flexibilidad del esquema no elimina la necesidad de controlar calidad y consistencia de los datos.
- Consultas complejas, relaciones y agregaciones requieren un diseño deliberado; no hay que asumir que reemplaza directamente los joins relacionales.
- La fragmentación, los índices y la memoria requieren planificación para mantener un buen rendimiento a escala.

**Usos comunes:** catálogos, perfiles, aplicaciones web y móviles, gestión de contenido, eventos y datos semiestructurados.

**Licencia:** MongoDB Community Server, para versiones publicadas después del 16 de octubre de 2018, se distribuye bajo la Server Side Public License (SSPL); también hay licencias comerciales. La SSPL no está aprobada por la Open Source Initiative como licencia de código abierto. Antes de ofrecer el propio motor como servicio o redistribuirlo, revisa las condiciones aplicables.

## 2. Apache Cassandra

Cassandra es una base distribuida de **columnas anchas**, diseñada para repartir datos entre nodos y centros de datos. Su modelo se adapta mejor cuando se conocen de antemano las consultas principales y se diseña el esquema para ellas.

**Ventajas**
- Puede distribuir datos y carga en clústeres, con tolerancia a fallos.
- Resulta apropiada para escrituras intensivas y grandes conjuntos de datos.
- Su arquitectura distribuida y sin un único nodo maestro facilita despliegues con alta disponibilidad.

**Desventajas**
- No es una base de propósito general para consultas arbitrarias: las claves de partición y el patrón de acceso importan mucho.
- No ofrece las mismas facilidades que un motor relacional para joins y consultas ad hoc.
- Operar y ajustar un clúster requiere conocimientos específicos de replicación, consistencia y distribución.

**Usos comunes:** telemetría, actividad de usuarios, mensajería, registros de eventos, IoT y aplicaciones distribuidas con gran volumen de escrituras.

**Licencia:** Apache Cassandra es software de Apache Software Foundation bajo Apache License 2.0.

## 3. Redis

Redis almacena datos principalmente en memoria y ofrece estructuras como cadenas, hashes, listas, conjuntos, colas y estructuras ordenadas. Es común usarlo junto con una base persistente, aunque también puede guardar datos de forma persistente según la configuración.

**Ventajas**
- Acceso muy rápido cuando los datos se sirven desde memoria.
- Estructuras y operaciones útiles para cachés, contadores, colas, sesiones y datos en tiempo real.
- Puede reducir la carga sobre una base principal y responder con baja latencia en patrones compatibles.

**Desventajas**
- La memoria suele ser más costosa que el almacenamiento en disco; hay que controlar el tamaño de los datos y la política de expiración.
- No es un reemplazo automático para almacenamiento persistente de largo plazo ni para consultas relacionales complejas.
- La replicación, persistencia, recuperación y alta disponibilidad deben configurarse conforme a los requisitos del sistema.

**Usos comunes:** caché, gestión de sesiones, límites de solicitudes, colas, rankings, notificaciones y procesamiento de datos en tiempo real.

**Licencia:** cambió con el tiempo. La página oficial indica que, desde Redis 8, Redis Open Source ofrece las opciones AGPLv3, SSPLv1 y RSALv2. AGPLv3 está aprobada por OSI; SSPLv1 y RSALv2 son licencias de código disponible, pero no son licencias de código abierto aprobadas por OSI. Los productos propietarios tienen condiciones comerciales propias. Comprueba la licencia de la versión y los componentes exactos que piensas usar.

## 4. Amazon DynamoDB

DynamoDB es un servicio NoSQL administrado de AWS, con modelos de clave-valor y documentos. AWS opera la infraestructura del servicio; el cliente define tablas, claves, índices y opciones de capacidad.

**Ventajas**
- Evita administrar directamente servidores de base de datos y permite integrarse con otros servicios de AWS.
- Puede resultar práctico para aplicaciones nativas de AWS con patrones de acceso conocidos.
- Admite modos de capacidad bajo demanda o provisionada, según la oferta y la región; las funciones opcionales, como replicación y copias de seguridad, pueden modificar el costo.

**Desventajas**
- El diseño depende de las claves y consultas previstas; consultas no planeadas pueden ser costosas o difíciles de expresar.
- El costo depende de factores como solicitudes, almacenamiento, índices y funciones adicionales; hay que estimarlo con el patrón de uso real.
- Crea dependencia operativa del ecosistema AWS y no se administra como un servidor de base de datos portable entre proveedores.

**Usos comunes:** servicios web en AWS, sistemas sin servidor, carritos y sesiones, catálogos de acceso por clave, estados de aplicaciones y cargas con tráfico variable.

**Licencia y costos:** no se instala como un motor comunitario gratuito: es un servicio comercial de AWS, con facturación por uso y configuración. Revisa la página de precios de AWS para la región y las funciones concretas que planeas utilizar.

## 5. Neo4j

Neo4j representa la información como **nodos, relaciones y propiedades**. En vez de modelar las conexiones mediante tablas y joins, permite recorrer relaciones como parte central del modelo.

**Ventajas**
- Adecuado para consultas que exploran muchas relaciones o caminos entre entidades.
- Su lenguaje Cypher está orientado a consultas de grafos.
- Puede simplificar modelos en los que las conexiones cambian o tienen tanta importancia como los datos de las entidades.

**Desventajas**
- No suele ser la opción más sencilla para tablas independientes y relaciones simples.
- Introduce un modelo y herramientas que el equipo debe aprender.
- Las capacidades avanzadas y las opciones administradas pueden depender de ediciones o servicios comerciales.

**Usos comunes:** redes sociales, motores de recomendación, detección de fraude, dependencias de infraestructura, grafos de conocimiento y análisis de rutas.

**Licencia:** Neo4j Community Edition se ofrece bajo GPLv3; Enterprise Edition incluye componentes cerrados y requiere una licencia comercial. Consulta los términos de la edición y el modo de despliegue que elijas.

## 6. Apache CouchDB

CouchDB almacena documentos JSON y ofrece una API basada en HTTP. Una de sus características distintivas es la replicación, que permite sincronizar datos entre servidores y dispositivos, incluso cuando hubo períodos sin conexión.

**Ventajas**
- Adecuado para aplicaciones que necesitan trabajar sin conexión y sincronizarse después.
- Usa documentos JSON y una API basada en HTTP.
- Puede empezar con una instancia individual y pasar a un clúster en proyectos más exigentes.

**Desventajas**
- La replicación puede crear conflictos que la aplicación debe detectar y resolver.
- No es la opción ideal si se necesitan muchas consultas relacionales complejas.
- El modelo de consultas y vistas puede requerir un enfoque diferente al de bases SQL o de documentos con lenguajes de consulta más amplios.

**Usos comunes:** aplicaciones móviles y distribuidas, formularios de campo, catálogos replicados y sistemas que deben seguir funcionando durante interrupciones de conectividad.

**Licencia:** Apache CouchDB se distribuye bajo Apache License 2.0.