# Mapa de pozos con cambios piezométricos significativos

Este script genera un mapa con los pozos que presentan cambios piezométricos mayores a 5 metros entre años consecutivos. Los pozos se representan sobre un mapa base de Esri y se clasifican por tipo de cambio (positivo o negativo), usando diferentes colores.

## 🔍 Objetivo

Visualizar espacialmente los pozos con variaciones significativas en el nivel piezométrico, como parte del análisis exploratorio del acuífero Conejos-Médanos. Este análisis permite identificar zonas clave para su posterior comparación con otras variables (almacenamiento de agua subterránea, precipitación, temperatura y evaporación).

## 📁 Estructura del script

1. **Carga de datos**
   - Archivo CSV con datos piezométricos (`pozos.csv`)
   - Límite del acuífero en formato Shapefile (`aol_conejos.shp`)

2. **Conversión de coordenadas**
   - Se crea una `GeoDataFrame` con coordenadas en EPSG:26713 (NAD27 / UTM zona 13N).
   - Se proyecta a EPSG:4326 para visualización en mapa base web.

3. **Selección de pozos clave**
   - Se seleccionan pozos específicos con base en su nomenclatura (`CM-009`, `CM-022A`, etc.)
   - Se clasifican en dos grupos:
     - Cambios negativos (descensos): color **rojo**
     - Cambios positivos (ascensos): color **negro**

4. **Visualización**
   - Se crea el mapa con `matplotlib` y `contextily`.
   - Se superpone el límite del acuífero.
   - Se agregan etiquetas desplazadas para evitar empalmes entre pozos con coordenadas similares.

## 📌 Requisitos

- Python 3.x
- Paquetes:
  - `pandas`
  - `geopandas`
  - `matplotlib`
  - `contextily`
  - `pyproj`

Instalar dependencias:

```bash
pip install pandas geopandas matplotlib contextily pyproj
