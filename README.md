# Gestion-de-Datos

Repo pa guardar trash del ramo Gestion de datos 2026-2

## Métodos y Funciones de Pandas Utilizados

### Configuración y Lectura

**`set_option()`**

- Configura opciones globales de visualización de pandas
- Ejemplo: `pd.set_option("display.max_columns", None)`

**`read_csv()`**

- Lee un archivo CSV y lo convierte en un DataFrame
- Ejemplo: `pd.read_csv(f)`

### Indexación y Selección

**`.loc[]`**

- Selecciona filas y columnas por etiqueta de índice
- Ejemplo: `alumnos_df.loc[(alumnos_df.carrera == "Ing. Informática") & (alumnos_df.sede == "Concepción")]`

**`.iloc[]`**

- Selecciona filas y columnas por posición numérica
- Ejemplo: `promedios_s.iloc[1]`

**`.set_index()`**

- Establece una columna como índice del DataFrame
- Ejemplo: `dfs_cache["alumnos"].set_index("id")["promedio"]`

### Exploración de Datos

**`.info()`**

- Muestra información general del DataFrame (tipos de datos, valores no nulos, memoria)
- Ejemplo: `alumnos_df.info()`

**`.describe()`**

- Calcula estadísticas descriptivas (count, mean, std, min, max, percentiles, etc.)
- Ejemplo: `alumnos_df.describe()`

**`.head()`**

- Retorna las primeras n filas (por defecto 5)
- Ejemplo: `alumnos_df.head()`

### Operaciones Básicas

**`.value_counts()`**

- Cuenta la frecuencia de valores únicos en una columna
- Ejemplo: `alumnos_df.carrera.value_counts()`

**`.sum()`**

- Suma los valores de una columna
- Ejemplo: `alumnos_df.isna().sum()[lambda id: id > 0]`

**`.mean()`**

- Calcula el promedio de valores en una columna
- Ejemplo: `alumnos_df.promedio.mean()`

**`.median()`**

- Calcula la mediana de valores en una columna
- Ejemplo: `alumnos_df.groupby("sede")["asistencia_pct"].transform("median")`

### Limpieza de Datos

**`.isna()`**

- Retorna un DataFrame booleano indicando valores nulos (NaN)
- Ejemplo: `alumnos_df.promedio.isna()`

**`.notna()`**

- Retorna un DataFrame booleano indicando valores no nulos
- Ejemplo: `alumnos_df.promedio.notna().all()`

**`.fillna()`**

- Rellena valores faltantes (NaN) con un valor especificado
- Ejemplo: `alumnos_df["promedio"] = alumnos_df.promedio.fillna(alumnos_df.promedio.mean())`

### Transformación de Datos

**`.transform()`**

- Aplica una función a cada elemento de una columna o grupo
- Ejemplo: `alumnos_df["promedio"].transform(categoria_rendimiento_handler)`

**`.sort_values()`**

- Ordena el DataFrame por valores de una o más columnas
- Ejemplo: `alumnos_df.sort_values("promedio", ascending=False).head()`

**`.merge()`**

- Combina dos DataFrames basándose en una columna común (similar a JOIN en SQL)
- Ejemplo: `alumnos_df.merge(sedes_df, on="sede")`

**`.pivot_table()`**

- Crea una tabla pivote con filas, columnas y valores agregados
- Ejemplo: `alumnos_region_inscripciones.pivot_table(values="promedio_final", index="sede", columns="carrera", aggfunc="mean")`

### Agrupación y Cálculos

**`.groupby()`**

- Agrupa datos por una o más columnas para realizar cálculos agregados
- Ejemplo: `alumnos_region_inscripciones.groupby("sede").promedio_final.mean()`

### Conversión de Tipos

**`to_datetime()`**

- Convierte strings a tipo datetime para trabajar con fechas
- Ejemplo: `pd.to_datetime(fecha, format="%Y-%m-%d")`

### Exportación

**`.to_csv()`**

- Exporta un DataFrame a un archivo CSV
- Ejemplo: `alumnos_fecha[["id", "nombre", "carrera", "sede", "promedio", "fecha_inscripcion"]].to_csv(output_data_dir / "reporte_filtrado.csv")`
