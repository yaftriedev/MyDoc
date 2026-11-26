# Manipulación de datos con Pandas

> https://aprendeconalf.es/docencia/python/manual/pandas/

| Tipo de datos | Función |
| --- | --- |
| CSV | `pd.read_csv(url/path)` |
| Excel | `pd.read_excel(url/path, sheet_name?="")` |
| JSON | `pd.read_json(url/path)` |
| SQL | `pd.read_sql(sql_query, conn)` |
| Objeto de Python | `pd.DataFrame(obj)` |

| Atributos | Función |
| --- | --- |
| `df.info()` | Devuelve información (número de filas, número de columnas, índices, tipo de las columnas y memoria usado) sobre el DataFrame `df`. |
| `df.shape` | Devuelve una tupla con el número de filas y columnas del DataFrame `df` . |
| `df.size` | Devuelve el número de elementos del DataFrame. |
| `df.columns` | Devuelve una lista con los nombres de las columnas del DataFrame `df`. |
| `df.index` | Devuelve una lista con los nombres de las filas del DataFrame `df`. |
| `df.dtypes` | Devuelve una serie con los tipos de datos de las columnas del DataFrame `df`. |
| `df.head(n)` | Devuelve las `n` primeras filas del DataFrame `df`. |
| `df.tail(n)` | Devuelve las `n` últimas filas del DataFrame `df`. |
| `df.index` | Devuelve el índice de las filas. |

- **Mostrar varios campos:** `df[ [campo1, campo2] ]`
- **Filtrar:** `df[condiciones]`. Ej: `df[df['PassengerId']==148]`
- **Filtrar y montrar por columnas:** `df[condicion][columna]`
- **Ordenar por Columna:** `df.sort_values(columna, ascending=bool)`
- **Ordenar por Index:** `df.sort_index(ascending=bool)`

| Análisis Descriptivo | Función | Matemática |
| --- | --- | --- |
| `df[campo].count()` | Devuelve una serie con el **número de elementos que no son nulos** ni `NaN` en cada columna del DataFrame `df`. | n = Total elementos en X |
| `df[campo].sum()` | Devuelve una serie con la **suma de los datos de las columnas** del DataFrame `df` cuando los datos son de un tipo numérico, o la concatenación de ellos cuando son del tipo cadena `str`. | $\sum x_i$ |
| `df[campo].min()` | Devuelve una serie con los **menores de los datos** de las columnas del DataFrame `df`. | $min \ x_i$ |
| `df[campo].max()` | Devuelve una serie con los **mayores de los datos** de las columnas del DataFrame `df`. | $max \ x_i$ |
| `df[campo].mean()` | Devuelve una serie con las **medias de los datos** de las columnas numéricas del DataFrame `df`. | $\bar{x} = \frac{\sum x_i}{n}$ |
| `df[campo].var()` | Devuelve una serie con las **varianzas de los datos** de las columnas numéricas del DataFrame `df`. | $s^2 = \frac{1}{n-1} \sum_{i=1}^{n} (x_i - \bar{x})^2$ |
| `df[campo].std()` | Devuelve una serie con las **desviaciones típicas de los datos** de las columnas numéricas del DataFrame `df`. | $s = \sqrt{\frac{1}{n-1} \sum_{i=1}^{n} (x_i - \bar{x})^2}$ |
| `df[campo].cov()` | Devuelve un DataFrame con las **covarianzas de los datos** de las columnas numéricas del DataFrame `df`. | $\operatorname{Cov}(X,Y) = \frac{1}{n-1} \sum_{i=1}^{n} (x_i - \bar{x})(y_i - \bar{y})$ |
| `df[campo].corr(df[campo])` | Devuelve un DataFrame con los **coeficientes de correlación de Pearson de los datos** de las columnas numéricas del DataFrame `df`. | $\rho_{X,Y} = \frac{\operatorname{Cov}(X,Y)}{s_X \cdot s_Y}$ |