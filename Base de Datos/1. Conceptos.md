# ¿Qué es una base de datos?

Una **base de datos** es una colección organizada de información que se puede guardar, consultar, modificar y eliminar. Por ejemplo, una tienda puede almacenar clientes, productos, pedidos y pagos.

Un **sistema gestor de bases de datos (SGBD)** es el software que administra esos datos. MySQL, PostgreSQL, MongoDB y Redis son ejemplos de SGBD. La aplicación se comunica con el gestor para leer o guardar información.

**SQL** es un lenguaje usado para consultar y administrar datos en muchos SGBD relacionales. **MySQL** es un SGBD que utiliza SQL; SQL y MySQL no son lo mismo.

# Conceptos esenciales

- **Tabla:** conjunto de datos organizado en filas y columnas. Por ejemplo, una tabla `clientes`.
- **Fila o registro:** una instancia de una entidad; por ejemplo, los datos de una persona cliente.
- **Columna o campo:** un atributo de los registros, como `nombre`, `correo` o `fecha_alta`.
- **Esquema:** definición de la estructura de la base de datos: tablas, columnas, tipos y relaciones.
- **Clave primaria (PRIMARY KEY):** columna o conjunto de columnas que identifica de forma única cada fila.
- **Clave foránea (FOREIGN KEY):** columna que enlaza una tabla con otra y ayuda a mantener la integridad de la relación.
- **Índice:** estructura que acelera ciertas búsquedas, a cambio de ocupar espacio y añadir trabajo en escrituras.
- **Consulta:** instrucción para recuperar o modificar datos.
- **Restricción:** regla aplicada a los datos, como `NOT NULL`, `UNIQUE` o `CHECK`.
- **Transacción:** grupo de operaciones que se ejecuta como una unidad lógica. En un sistema transaccional, por ejemplo, registrar un pedido y descontar inventario puede tratarse como una operación coordinada.
- **Copia de seguridad (backup):** copia que permite recuperar datos ante errores, daños o pérdida.
- **Replicación:** mantenimiento de copias de datos en otros servidores o ubicaciones, por disponibilidad o distribución de carga.

# ¿Dónde se usan las bases de datos?

Se usan en casi cualquier sistema que necesite conservar y recuperar información, por ejemplo:

- **Tiendas en línea**: productos, clientes, pagos y pedidos;
- **Bancos y sistemas de pago**: cuentas, movimientos y transacciones;
- **Aplicaciones móviles**: perfiles, mensajes y preferencias;
- **Hospitales y clínicas**: citas, pacientes y registros;
- **Escuelas**: alumnos, cursos, notas y asistencia;
- **Redes sociales**: publicaciones, comentarios y conexiones;
- **Empresas**: inventarios, ventas, nóminas y reportes;
- **Videojuegos**: cuentas, progreso y partidas;
- **Sistemas de transporte**: reservas, rutas y horarios;
- **Sensores e IoT**: lecturas, eventos y mediciones.

La base de datos suele trabajar detrás de una aplicación o servicio. Una página web, por ejemplo, puede solicitar los productos al servidor, y este consulta la base de datos para responder.

# Tipos de datos en SQL y MySQL

Un **tipo de dato** indica qué clase de valor puede guardar una columna y cómo debe interpretarse. Los tipos exactos varían entre gestores y versiones; esta lista describe familias comunes de MySQL 8.4.

| Familia | Tipos de MySQL | Para qué sirven | Ejemplos |
|---|---|---|---|
| **Enteros** | `TINYINT`, `SMALLINT`, `MEDIUMINT`, `INT`, `BIGINT` | Números enteros | cantidad, identificador, edad |
| **Decimales exactos** | `DECIMAL`, `NUMERIC` | Valores donde importa conservar la precisión decimal | precios, saldos |
| **Decimales aproximados** | `FLOAT`, `DOUBLE` | Cálculos científicos o valores aproximados | mediciones, cálculos numéricos |
| **Texto** | `CHAR`, `VARCHAR`, `TEXT` | Texto fijo, variable o largo | código postal, nombre, descripción |
| **Binarios** | `BINARY`, `VARBINARY`, `BLOB` | Bytes o archivos binarios | hashes, contenido binario |
| **Fecha y hora** | `DATE`, `TIME`, `DATETIME`, `TIMESTAMP`, `YEAR` | Fechas, horas y marcas temporales | nacimiento, duración, momento de creación |
| **Booleanos** | normalmente `BOOLEAN` o `BOOL` | Valores verdadero/falso | activo, confirmado |
| **JSON** | `JSON` | Documentos JSON validados y consultables | preferencias o atributos variables |

MySQL dispone de tipos temporales `DATE`, `TIME`, `DATETIME`, `TIMESTAMP` y `YEAR`; también admite fracciones de segundo en `TIME`, `DATETIME` y `TIMESTAMP`.
El tipo `JSON` valida los documentos al almacenarlos y permite funciones para consultar y modificar sus valores.

**Consejos para elegir tipos:**

- Usa `DECIMAL` para dinero; los tipos de coma flotante pueden representar ciertos decimales de forma aproximada.
- Elige un entero que admita el rango esperado, sin usar `BIGINT` por costumbre si basta otro tipo.
- Usa tipos de fecha y hora para fechas y tiempos; evita guardar fechas como texto si luego necesitas ordenarlas o compararlas.
- Selecciona límites razonables para `VARCHAR`, pero no confundas su límite declarado con el espacio que ocupa cada valor.
- Para valores que deben estar presentes, añade `NOT NULL`; para valores que no deben repetirse, considera `UNIQUE`.
- No almacenes en una columna información de varios tipos distintos sin una razón clara: dificulta validar, buscar y mantener los datos.

## ¿Qué significa SQL vs. NoSQL?

**SQL** suele referirse a bases relacionales consultadas con el lenguaje SQL. **NoSQL** agrupa distintos modelos no relacionales: documentos, clave-valor, columnas anchas y grafos, entre otros.

| Aspecto | Relacional / SQL | NoSQL |
|---|---|---|
| **Estructura habitual** | Tablas, filas y columnas | Documentos, pares clave-valor, columnas anchas o grafos |
| **Esquema** | Normalmente definido de forma explícita | Puede ser flexible, según el motor |
| **Relaciones entre datos** | Claves y consultas como `JOIN` | Pueden representarse dentro de documentos, mediante claves o como relaciones de grafo |
| **Consultas** | SQL ampliamente compartido, con diferencias entre motores | APIs y lenguajes de consulta propios de cada producto o familia |
| **Escalado** | Puede escalar verticalmente y también distribuirse, según el motor y el diseño | Algunos motores están diseñados especialmente para distribuir datos entre muchos nodos |
| **Adecuado cuando** | Importan las relaciones, las reglas de integridad y las consultas variadas | El modelo de datos o la carga encaja mejor con documentos, clave-valor, grafos u otro patrón |
| **Ejemplos** | MySQL, PostgreSQL, SQL Server | MongoDB, Redis, Cassandra, DynamoDB, Neo4j |

La diferencia no es simplemente “SQL es rígido y NoSQL es flexible”, ni “NoSQL siempre escala mejor”. Los motores tienen capacidades distintas: algunos NoSQL ofrecen transacciones y algunos relacionales pueden distribuirse. La decisión debe basarse en el modelo de datos, las consultas, la consistencia necesaria, el volumen y las capacidades del equipo.

### Ejemplo práctico de elección

- Para **facturas y pagos**, donde importan las relaciones y la consistencia entre operaciones, una base relacional suele ser una buena opción.
- Para **perfiles con campos muy variables**, una base documental puede encajar bien.
- Para una **caché de sesiones** de acceso rápido, una base clave-valor como Redis puede complementar a la base principal.
- Para explorar **conexiones entre personas, dispositivos o entidades**, puede ser útil una base de grafos.

## Normalización y duplicación de datos

La **normalización** consiste en organizar los datos para reducir duplicaciones y evitar inconsistencias. Por ejemplo, guardar el nombre de cada cliente una sola vez en `clientes` y referenciarlo desde `pedidos` evita repetirlo en todos los pedidos.

A veces se **desnormaliza** de forma deliberada para acelerar lecturas o simplificar consultas. Es una decisión de diseño que puede aumentar la duplicación y exige mantener coherentes los valores repetidos.

# Seguridad y mantenimiento básico

- Asigna a cada aplicación solo los permisos que necesita;
- Usa contraseñas robustas y conexiones protegidas cuando corresponda;
- Crea copias de seguridad y prueba que se puedan restaurar;
- Actualiza el motor y revisa la compatibilidad antes de cambios grandes;
- Controla el acceso a datos personales y limita su recopilación;
- Monitorea espacio, rendimiento, errores y crecimiento;
- Evita formar consultas concatenando directamente datos ingresados por usuarios; utiliza consultas parametrizadas para reducir riesgos de inyección SQL.