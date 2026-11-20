# Resumen

| Motor | Licencia o modelo general | Usos frecuentes | Punto fuerte | Principal consideración |
|---|---|---|---|---|
| **PostgreSQL** | Licencia PostgreSQL, permisiva y de código abierto | Aplicaciones de negocio, sistemas geoespaciales, analítica y servicios web | Funcionalidad amplia y extensible | Puede exigir más experiencia de configuración y ajuste |
| **MySQL** | Community bajo GPLv2; también ofrece licencias y ediciones comerciales | Sitios web, comercio electrónico y aplicaciones transaccionales | Ecosistema y adopción muy amplios | Revisar las condiciones GPL si se distribuye junto con software propio |
| **MariaDB** | Servidor Community bajo GPLv2; existen productos y servicios comerciales | Aplicaciones web y sistemas que buscan compatibilidad con MySQL | Código abierto y familiaridad con MySQL | La compatibilidad con MySQL no es total en todos los escenarios |
| **SQL Server** | Ediciones comerciales; Developer y Express gratuitas con restricciones distintas | Aplicaciones empresariales, especialmente con .NET y herramientas Microsoft | Integración y herramientas de administración | La edición y el modelo de licencia influyen mucho en el costo |
| **Oracle Database** | Principalmente propietario; hay una edición gratuita con límites | Sistemas empresariales críticos, transacciones y grandes despliegues | Amplias capacidades y ecosistema empresarial | Licenciamiento y opciones pueden ser complejos |
| **IBM Db2** | Ediciones comerciales y una Community Edition gratuita con límites | Sistemas empresariales, cargas transaccionales y analíticas | Experiencia en entornos empresariales y disponibilidad | Ecosistema y conocimientos pueden ser menos comunes que los de alternativas abiertas |

## Conceptos básicos

Un **sistema de gestión de bases de datos relacionales (SGBDR)** organiza información en tablas relacionadas mediante claves. Se consulta y modifica principalmente con SQL. En aplicaciones transaccionales suelen importar propiedades como ACID: atomicidad, consistencia, aislamiento y durabilidad.

Aunque los motores comparten conceptos y parte de la sintaxis, **no son intercambiables sin trabajo**. Pueden diferir en dialecto SQL, tipos de datos, procedimientos, herramientas, replicación, extensiones y comportamiento. Una migración puede requerir cambios en el esquema y en el código de la aplicación.

# Análisis por motor

## PostgreSQL

PostgreSQL es un sistema relacional de código abierto conocido por su extensibilidad, sus tipos de datos y sus funciones avanzadas. El proyecto oficial lo describe como un sistema objeto-relacional con una larga trayectoria de desarrollo y énfasis en fiabilidad y robustez. La licencia PostgreSQL es permisiva, lo que permite usar el motor en aplicaciones comerciales sujetándose a sus términos.

**Ventajas**
- Amplio conjunto de funciones SQL y opciones para extender el motor.
- Adecuado para esquemas complejos, consultas elaboradas y transacciones.
- Puede ampliarse mediante extensiones para necesidades especializadas.
- Su licencia permisiva suele simplificar la inclusión en productos propietarios, aunque hay que revisar también las licencias de extensiones y dependencias.

**Desventajas**
- Requiere administración y ajuste cuidadosos cuando crecen la carga y la complejidad.
- Algunas extensiones o servicios gestionados pueden tener condiciones y ciclos de soporte propios.
- La migración desde otros motores puede implicar adaptar SQL, tipos y procedimientos.

**Usos comunes:** aplicaciones de negocio, plataformas web, sistemas geoespaciales con extensiones, análisis operacional y proyectos que necesitan un motor configurable sin una licencia propietaria del servidor.

## MySQL

MySQL es un motor cliente-servidor ampliamente utilizado en aplicaciones web y transaccionales. Oracle ofrece **MySQL Community Edition** bajo GPL, además de ediciones comerciales con funciones, herramientas y soporte adicionales.

**Ventajas**
- Gran disponibilidad de herramientas, conectores, documentación y experiencia profesional.
- Opción Community sin costo de licencia, con transacciones ACID cuando se emplea InnoDB.
- Puede servir desde proyectos pequeños hasta aplicaciones de alta demanda, con diseño y operación adecuados.
- Replicación y opciones de escalado para distintas arquitecturas.

**Desventajas**
- Las capacidades varían entre Community y las ofertas comerciales.
- La licencia GPL requiere atención si se distribuye MySQL junto con una aplicación propia; Oracle también ofrece una licencia comercial para determinados casos de distribución.
- Aunque es compatible con SQL, no se debe asumir que las consultas o herramientas se trasladarán sin cambios desde otro motor.

**Usos comunes:** sitios y aplicaciones web, sistemas de gestión de contenidos, comercio electrónico y servicios que priorizan un ecosistema conocido y conectores disponibles.

## MariaDB

MariaDB nació como una bifurcación de MySQL y mantiene una comunidad y una oferta comercial propias. La documentación del proyecto indica que MariaDB Server se distribuye bajo GPLv2; sus bibliotecas cliente pueden usar licencias distintas, como LGPL.

**Ventajas**
- Alternativa abierta con una historia y herramientas cercanas a MySQL.
- Puede facilitar la adopción en aplicaciones que ya usan tecnologías del ecosistema MySQL.
- Incluye motores de almacenamiento y funciones adicionales, según versión y configuración.

**Desventajas**
- MariaDB y MySQL han evolucionado por separado: la compatibilidad no debe darse por garantizada, especialmente en funciones avanzadas y versiones recientes.
- Una migración requiere pruebas de compatibilidad, rendimiento, replicación y conectores.
- Al igual que con otras bases GPL, es importante revisar la licencia al redistribuir el servidor o componentes cliente.

**Usos comunes:** aplicaciones web, proyectos que buscan un servidor de código abierto y equipos que desean una ruta de transición desde MySQL, siempre que validen compatibilidad.

## Microsoft SQL Server

SQL Server es un producto de Microsoft con ediciones de pago y gratuitas. En SQL Server 2025, **Developer** es gratuita para desarrollo y pruebas, no para producción; **Express** es gratuita y está orientada a aplicaciones pequeñas, incluidas algunas de producción. Enterprise y Standard son ediciones comerciales.

**Ventajas**
- Integración estrecha con tecnologías y herramientas de Microsoft, como .NET y SQL Server Management Studio.
- Opciones de seguridad, administración, disponibilidad y análisis para entornos empresariales.
- Developer facilita probar funciones de las ediciones correspondientes sin usar una licencia de producción.
- Express permite empezar sin costo de licencia, aunque tiene límites de capacidad.

**Desventajas**
- El costo y las condiciones dependen de la edición, el despliegue y el modelo de licenciamiento.
- Express puede quedarse corto si el sistema crece más allá de sus límites.
- SQL Server emplea T-SQL y tiene particularidades que pueden exigir cambios al migrar desde otro motor.

**Usos comunes:** aplicaciones empresariales en entornos Microsoft, sistemas desarrollados con .NET, bases corporativas y soluciones que aprovechan herramientas de análisis e informes de Microsoft.

## Oracle Database

Oracle Database es una plataforma propietaria orientada a entornos empresariales. Oracle publica documentación de licenciamiento que detalla qué funciones están incluidas o requieren opciones adicionales; por eso, el costo y los derechos de uso dependen de la edición y de las capacidades habilitadas. Oracle también ofrece una edición gratuita con límites de recursos y almacenamiento.

**Ventajas**
- Muy utilizado en organizaciones con sistemas empresariales de misión crítica.
- Amplio conjunto de capacidades para administrar grandes entornos y cargas complejas.
- Puede encajar bien si la organización ya cuenta con conocimientos, contratos y herramientas Oracle.

**Desventajas**
- La estructura de licencias y opciones puede resultar compleja; conviene revisar los derechos concretos de cada función y edición.
- La edición gratuita tiene límites y no equivale a una edición empresarial sin restricciones.
- Migrar desde Oracle puede implicar costos de adaptación, pruebas y capacitación, además de los costos de plataforma.

**Usos comunes:** sistemas empresariales críticos, aplicaciones corporativas consolidadas y entornos donde ya existe una inversión importante en tecnología Oracle.

## IBM Db2

IBM Db2 cuenta con ofertas comerciales y una Community Edition. IBM describe esta edición gratuita como utilizable en producción y no producción, con límites de recursos —la oferta consultada indica 4 núcleos y 16 GB de memoria— y sin soporte empresarial estándar. Los límites y condiciones dependen de la oferta concreta y deben verificarse antes del despliegue.

**Ventajas**
- Plataforma consolidada en organizaciones con sistemas IBM y cargas empresariales.
- IBM destaca funciones para transacciones, compresión, cifrado y alta disponibilidad, según producto y edición.
- La edición Community permite evaluar Db2 y desarrollar aplicaciones con una barrera inicial menor.

**Desventajas**
- Las ediciones comerciales y el soporte pueden ser necesarios para despliegues empresariales sin límites de Community.
- Puede ser más difícil encontrar experiencia disponible que con motores muy extendidos en desarrollo web.
- Es importante comprobar con precisión las condiciones de la edición y la licencia del entorno elegido.

**Usos comunes:** organizaciones que ya operan infraestructura IBM, sistemas empresariales y proyectos que requieren evaluar Db2 antes de contratar una edición comercial.