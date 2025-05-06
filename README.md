# PROYECTO INTEGRADOR: Accidentalidad Vial en Medellín

Este proyecto busca analizar información de accidentalidad vial en Medellín, combinando datos de accidentes y condiciones meteorológicas.

## 📁 Archivos del repositorio

- `accidentalidad.ipynb`: Notebook con el código de análisis y unificación de datos.
- `accidentes_muestra.csv`: Muestra representativa de los accidentes.
- *(si subes datos del clima en `.csv`, también inclúyelos aquí)*

## 🔗 Fuentes de datos

- **Accidentes**: Base de datos original en `.csv` con datos de accidentes en Medellín.
- **Datos meteorológicos**: Obtenidos desde una API externa (`https://...`) mediante peticiones `GET`.

## ⚙️ Tecnologías y librerías usadas

- `pandas`
- `numpy`
- `requests`
- `matplotlib` / `seaborn`

## 🔄 Proceso realizado

1. Carga de datos CSV y desde API.
2. Limpieza y estandarización de columnas (fechas, nombres, etc.).
3. Unificación de datos con `merge`.
4. Exportación de muestra `.csv` para uso en GitHub.
5. Análisis descriptivo y visualización de patrones.

## ✍️ Autor

GitHub: [sarasandoval](https://github.com/sarasandoval)
