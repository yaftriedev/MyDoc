# DDL: Definición de datos

DDL sirve para crear, cambiar o eliminar la estructura de una base de datos, como tablas y columnas.

## Palabras clave

- `CREATE`: crea una base de datos, tabla u otro objeto.
- `ALTER`: modifica la estructura de un objeto existente; por ejemplo, agrega una columna.
- `DROP`: elimina una tabla u otro objeto completo, incluida su estructura.
- `TRUNCATE`: elimina todos los registros de una tabla, pero conserva la tabla y sus columnas.

## Estructura y ejemplos

```sql
CREATE TABLE estudiantes (
    id INT PRIMARY KEY,
    nombre VARCHAR(100),
    edad INT
);
```

- `CREATE TABLE`: crea una tabla.
- `estudiantes`: nombre de la tabla.
- `id`, `nombre`, `edad`: nombres de las columnas.
- `INT`: tipo de dato para números enteros.
- `VARCHAR(100)`: texto de hasta 100 caracteres.
- `PRIMARY KEY`: identifica de forma única cada registro.

Para agregar una columna:

```sql
ALTER TABLE estudiantes
ADD correo VARCHAR(150);
```

- `ALTER TABLE`: indica qué tabla se va a modificar.
- `ADD`: agrega una columna.
- `correo`: nombre de la nueva columna.

Para eliminar todos los registros, pero conservar la tabla:

```sql
TRUNCATE TABLE estudiantes;
```

Para eliminar la tabla completa:

```sql
DROP TABLE estudiantes;
```

# DML: Manipulación de datos

DML sirve para agregar, cambiar o borrar registros dentro de las tablas.

## Palabras clave

- `INSERT`: agrega registros.
- `UPDATE`: modifica registros existentes.
- `DELETE`: elimina registros.
- `INTO`: indica en qué tabla se insertarán los datos.
- `VALUES`: indica los valores que se agregarán.
- `SET`: indica qué columna y valor se modificarán.
- `WHERE`: establece una condición para seleccionar los registros afectados.

## Estructura y ejemplos

Agregar un registro:

```sql
INSERT INTO estudiantes (id, nombre, edad)
VALUES (1, 'Ana López', 20);
```

- `INSERT INTO estudiantes`: agrega datos en la tabla `estudiantes`.
- `(id, nombre, edad)`: columnas que recibirán datos.
- `VALUES`: anuncia los valores.
- `(1, 'Ana López', 20)`: valores en el mismo orden que las columnas.

Modificar un registro:

```sql
UPDATE estudiantes
SET edad = 21
WHERE id = 1;
```

- `UPDATE estudiantes`: indica la tabla que se modificará.
- `SET edad = 21`: cambia la edad a 21.
- `WHERE id = 1`: limita el cambio al registro cuyo identificador es 1.

Eliminar un registro:

```sql
DELETE FROM estudiantes
WHERE id = 1;
```

- `DELETE FROM estudiantes`: elimina registros de esa tabla.
- `WHERE id = 1`: elimina únicamente el registro con ese identificador.

**Importante:** antes de ejecutar `UPDATE` o `DELETE`, revisa la condición `WHERE`. Si la omites, podrías modificar o eliminar todos los registros de la tabla.

# DQL: Consulta de datos

DQL sirve para consultar y mostrar los datos almacenados. Su comando principal es `SELECT`.

## Palabras clave más usadas

- `SELECT`: elige qué columnas quieres ver.
- `FROM`: indica de qué tabla se obtendrán los datos.
- `WHERE`: filtra los registros según una condición.
- `AND`: exige que se cumplan dos o más condiciones.
- `OR`: permite que se cumpla una condición u otra.
- `NOT`: niega una condición.
- `ORDER BY`: ordena los resultados.
- `ASC`: orden ascendente; por ejemplo, A–Z o de menor a mayor. Es el orden predeterminado.
- `DESC`: orden descendente; por ejemplo, Z–A o de mayor a menor.
- `DISTINCT`: evita mostrar valores duplicados.
- `AS`: asigna un nombre temporal a una columna o tabla.
- `LIKE`: busca texto que coincida con un patrón.
- `IN`: comprueba si un valor está dentro de una lista.
- `BETWEEN`: busca valores dentro de un rango.
- `IS NULL`: busca datos que no tienen valor registrado.
- `LIMIT`: limita la cantidad de resultados que se muestran. Su uso exacto puede variar según el sistema de base de datos.
- `COUNT`: cuenta registros.
- `AVG`: calcula el promedio.
- `SUM`: suma valores.
- `MIN`: encuentra el valor menor.
- `MAX`: encuentra el valor mayor.
- `GROUP BY`: agrupa registros que tienen valores iguales en una columna.
- `HAVING`: filtra los grupos creados con `GROUP BY`.

## Estructura básica

```sql
SELECT columnas
FROM tabla
WHERE condición
ORDER BY columna ASC;
```

## Ejemplos de consultas

Mostrar todas las columnas y registros:

```sql
SELECT *
FROM estudiantes;
```

El asterisco `*` significa “todas las columnas”.

Mostrar solo algunas columnas:

```sql
SELECT nombre, edad
FROM estudiantes;
```

Filtrar por una condición:

```sql
SELECT nombre, edad
FROM estudiantes
WHERE edad >= 18;
```

Mostrar estudiantes mayores de edad cuyo nombre sea Ana:

```sql
SELECT nombre, edad
FROM estudiantes
WHERE edad >= 18 AND nombre = 'Ana';
```

Mostrar estudiantes que se llamen Ana o Luis:

```sql
SELECT nombre
FROM estudiantes
WHERE nombre = 'Ana' OR nombre = 'Luis';
```

Ordenar edades de mayor a menor:

```sql
SELECT nombre, edad
FROM estudiantes
ORDER BY edad DESC;
```

Mostrar nombres sin repetirlos:

```sql
SELECT DISTINCT nombre
FROM estudiantes;
```

Buscar nombres que comiencen con “A”:

```sql
SELECT nombre
FROM estudiantes
WHERE nombre LIKE 'A%';
```

El símbolo `%` representa cualquier cantidad de caracteres. Por ejemplo, `'A%'` encuentra nombres que empiezan con A.

Buscar estudiantes con edades entre 18 y 25 años:

```sql
SELECT nombre, edad
FROM estudiantes
WHERE edad BETWEEN 18 AND 25;
```

Contar cuántos estudiantes hay:

```sql
SELECT COUNT(*) AS total_estudiantes
FROM estudiantes;
```

- `COUNT(*)`: cuenta los registros.
- `AS total_estudiantes`: muestra el resultado con ese nombre temporal.

Calcular la edad promedio:

```sql
SELECT AVG(edad) AS edad_promedio
FROM estudiantes;
```

Agrupar estudiantes por edad:

```sql
SELECT edad, COUNT(*) AS cantidad
FROM estudiantes
GROUP BY edad;
```

Mostrar solo los grupos que tienen más de un estudiante:

```sql
SELECT edad, COUNT(*) AS cantidad
FROM estudiantes
GROUP BY edad
HAVING COUNT(*) > 1;
```

`WHERE` filtra registros individuales antes de agruparlos; `HAVING` filtra los grupos después de agruparlos.