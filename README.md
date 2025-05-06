# 📊 Análisis de Accidentalidad Vial en Medellín — Proceso de Datos

Este repositorio contiene el notebook y las bases de datos utilizadas para el análisis de accidentes de tránsito en Medellín. Aquí documentamos detalladamente **el tratamiento de los datos**, desde su origen hasta la unificación, limpieza y análisis, como parte de la Entrega 2 del Proyecto Integrador.

---

##  Estructura del repositorio

| Archivo                        | Descripción                                                                 |
|-------------------------------|-----------------------------------------------------------------------------|
| `ENTREGA2_PROYECTO.ipynb`     | Notebook de Google Colab con el proceso completo de tratamiento de datos.  |
| `incidentes_viales_.zip`      | Archivo comprimido con la base original de incidentes viales.              |
| `README.md`                   | Documento actual, explicando el proceso técnico de manejo de datos.        |

---

## Fuentes de los datos utilizados

###  Incidentes viales
- **Fuente**: Datos Abiertos de la Alcaldía de Medellín (MEDATA)
- **Formato original**: `.csv` (separado por punto y coma `;`)
- **Contenido principal**:
  - Fecha y hora del accidente
  - Tipo y gravedad del siniestro
  - Barrio, comuna, dirección
  - Coordenadas geográficas
  - Tipo de actor vial involucrado

- **Fuente**: [Open-Meteo – Historical Weather API](https://open-meteo.com/en/docs/historical-weather-api)
- **Formato**: `.xlsx` (descargado por fechas)
- **Variables extraídas**:
  - Temperatura máxima y mínima
  - Humedad relativa
  - Precipitaciones
  - Radiación solar
  - Visibilidad
  - Humedad del suelo
  - Velocidad del viento

---

##  Proceso de tratamiento de los datos

### 1. Carga de datos
- El archivo de accidentes fue leído desde Google Drive usando su `file_id`.
- Se usó `pandas.read_csv` con `sep=';'` y `low_memory=False` para evitar advertencias.
- Se limpiaron nombres de columnas eliminando caracteres especiales (`\ufeff`).

### 2. Limpieza y estandarización
- Conversión de texto a mayúsculas en columnas como `DIRECCION`.
- Conversión de `FECHA` a tipo `datetime`, extrayendo componentes como año, mes, día y hora.
- Eliminación de registros vacíos o con datos inconsistentes.
- df['FECHA'] = pd.to_datetime(df['FECHA'])
- df['DIRECCION'] = df['DIRECCION'].str.upper()
- df['HORA'] = df['FECHA'].dt.hour

### 3. Integración de la API climática
- Se utilizó la API de Open-Meteo para descargar datos meteorológicos históricos.
- Se configuraron parámetros como latitud, longitud, fecha de inicio y fin.
- Se seleccionaron variables diarias relevantes.
- Los datos fueron descargados en `.xlsx`, luego convertidos a `DataFrame`.

### 4. Unión de bases
- Se realizó un `merge()` en pandas usando la columna `FECHA` como clave.
- Esto permitió asociar a cada accidente las condiciones climáticas del día correspondiente.
- Se verificó la integridad de la unión (registros con y sin cruce).

---

##  Análisis realizado

- Visualización de la frecuencia de accidentes por hora, día, comuna y tipo.
- Cruce de variables meteorológicas con tipo y gravedad de accidentes.
- Exploración de patrones estacionales o relacionados con lluvia, visibilidad o temperaturas extremas.

---

##  Notas importantes

- El archivo `.csv` completo excede los 100MB permitidos por GitHub, por lo cual fue comprimido.
- Los datos climáticos se obtienen con un desfase de 5 días, lo que limita la consulta más reciente.
- El análisis es reproducible usando el notebook disponible en este repositorio.

---

##  Ejecutar en Google Colab

[![Abrir en Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/sarasandoval/PROYECTO-INTEGRADOR-Accidentalidad-Vial-en-Medell-n/blob/main/ENTREGA2_PROYECTO.ipynb)

---

## Este análisis fue desarrollado por:

- Sara Sandoval Álvarez
- Catalina Betancur Higuita
- Ximena Castañeda Ruiz
- Juan Manuel Arredondo

Curso: Proyecto Integrador – Universidad de Antioquia (2025)


