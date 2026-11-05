# Creador de mapas

App web para dibujar zonas a mano sobre un mapa base, superponer puntos GPS y exportar:

- Zonas como shapefile (.zip con .shp, .shx, .dbf, .prj y .cpg) en UTM 18S, UTM 19S o WGS84, o como GeoJSON.
- Figura PNG con título, leyenda, barra de escala y flecha de norte.

Funciona en cualquier navegador, sin instalar nada. Las zonas se guardan en el navegador entre sesiones.

## Publicar en GitHub Pages

1. Crea un repositorio público (por ejemplo `creador-mapas`) y sube `index.html` a la raíz.
2. En el repositorio: Settings > Pages > Source: "Deploy from a branch", rama `main`, carpeta `/ (root)`.
3. Tras uno o dos minutos queda disponible en `https://<usuario>.github.io/creador-mapas/`.

## Formatos de entrada

| Formato | Uso |
|---|---|
| `.gpx` | Puntos de tracks, rutas y waypoints (con elevación y hora si existen) |
| `.csv` / `.txt` | Columnas `lat` y `lon` en grados decimales; acepta `;` como separador y coma decimal |
| `.geojson` | Puntos, líneas (se usan sus vértices) y polígonos |
| `.zip` | Shapefile comprimido; los polígonos se importan como zonas |

## Uso del shapefile en R

```r
library(sf)
zonas <- st_read("zonas.shp")   # CRS EPSG:32718 si elegiste UTM 18S
```
