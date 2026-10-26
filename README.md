# mapasimbb

Polígonos de México listos para mapas (Leaflet, Apps Script, etc.): las 32 entidades y todos sus municipios.

## Archivos

| Archivo | Qué tiene |
|---|---|
| `entidades.json` | 32 entidades (GeoJSON). Campos: `CVE_ENT`, `NOM_ENT` |
| `municipios/{CVE_ENT}.json` | Municipios de una entidad, p. ej. `municipios/12.json` = Guerrero. Campos: `CVEGEO`, `CVE_ENT`, `CVE_MUN`, `NOMGEO`, `NOM_ENT` |
| `contorno_mexico.json` | Contorno del país, para tapar lo que queda fuera de México |
| `catalogo_entidades.json` | Clave, nombre y número de municipios de cada entidad |

Coordenadas WGS84 (lat/long), simplificadas para que carguen rápido (5.7 MB en total; el archivo más grande, Oaxaca, pesa 520 KB).

## Claves de entidad

01 Aguascalientes · 02 Baja California · 03 Baja California Sur · 04 Campeche · 05 Coahuila · 06 Colima · 07 Chiapas · 08 Chihuahua · 09 Ciudad de México · 10 Durango · 11 Guanajuato · 12 Guerrero · 13 Hidalgo · 14 Jalisco · 15 México · 16 Michoacán · 17 Morelos · 18 Nayarit · 19 Nuevo León · 20 Oaxaca · 21 Puebla · 22 Querétaro · 23 Quintana Roo · 24 San Luis Potosí · 25 Sinaloa · 26 Sonora · 27 Tabasco · 28 Tamaulipas · 29 Tlaxcala · 30 Veracruz · 31 Yucatán · 32 Zacatecas

## Cómo usarlo en cualquier mapa (CDN)

Los archivos se sirven gratis por jsDelivr, no hay que descargar nada:

```js
const BASE = 'https://cdn.jsdelivr.net/gh/alanma23cp/mapasimbb@main';

// Las 32 entidades
fetch(BASE + '/entidades.json').then(r => r.json()).then(geo => L.geoJSON(geo).addTo(mapa));

// Municipios de una entidad (12 = Guerrero)
fetch(BASE + '/municipios/12.json').then(r => r.json()).then(geo => L.geoJSON(geo).addTo(mapa));
```

jsDelivr guarda copia hasta 12 h. Si cambias un archivo y lo necesitas al momento, usa una versión fija
(`@v1`, `@v2`... creando un *release* o *tag*) o purga la caché en `https://purge.jsdelivr.net/gh/alanma23cp/mapasimbb@main/<archivo>`.

## Fuente y licencia

Marco Geoestadístico INEGI 2023, tomado de [PhantomInsights/mexico-geojson](https://github.com/PhantomInsights/mexico-geojson) (MIT) y simplificado con mapshaper.
