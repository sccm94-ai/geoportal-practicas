# Geoportal HTML para GitHub Pages

Este proyecto contiene un **geoportal en HTML** listo para publicar en **GitHub Pages**.

## Qué incluye

- Pestaña de **Curriculum Vitae del estudiante**
- Pestaña para **visualizar la imagen WMS** de:
  - capa de puntos
  - capa de líneas
  - capa de polígonos
  - composición de las 3 capas
- Pestaña de **descarga** de las capas en:
  - Shapefile
  - KML
  - GML
- **Visor en OpenLayers** con:
  - fondo OpenStreetMap
  - composición WMS
  - barra de escala
  - coordenadas lat/long
- Pestaña de **contacto** mediante correo

## Antes de subir a GitHub

Abre el archivo `index.html` y reemplaza el bloque `APP_CONFIG` por los datos reales de tu GeoServer/IDESINDE:

- `geoserverBaseUrl`
- `workspace`
- `compositeLayerName` (opcional)
- `bbox4326`
- `layers.puntos.name`
- `layers.lineas.name`
- `layers.poligonos.name`
- `contactEmail`

## Ejemplo de configuración

```javascript
const APP_CONFIG = {
  siteTitle: 'Geoportal del Estudiante',
  contactEmail: 'mi_correo@ejemplo.com',
  geoserverBaseUrl: 'https://servidor.xyz/geoserver',
  workspace: 'practicas',
  compositeLayerName: 'practicas:composicion_capas',
  bbox4326: [-78.60, -0.45, -78.30, -0.05],
  layers: {
    puntos: {
      title: 'Capa de puntos',
      name: 'practicas:hidrantes',
      description: 'Capa de puntos simbolizada.'
    },
    lineas: {
      title: 'Capa de líneas',
      name: 'practicas:tuberia_agua',
      description: 'Capa de líneas simbolizada.'
    },
    poligonos: {
      title: 'Capa de polígonos',
      name: 'practicas:sectores_hidraulicos',
      description: 'Capa de polígonos simbolizada.'
    }
  }
};
```

## Publicación en GitHub Pages

1. Crea un repositorio nuevo en GitHub.
2. Sube el archivo `index.html`.
3. Ve a **Settings > Pages**.
4. En **Build and deployment**, selecciona:
   - **Source:** Deploy from a branch
   - **Branch:** `main` / root
5. Guarda los cambios.
6. GitHub te dará un enlace como:
   `https://tuusuario.github.io/tu-repositorio/`

## Importante

- Si tu GeoServer usa `http` y GitHub Pages usa `https`, el navegador puede bloquear la carga por seguridad.
- Lo ideal es que el GeoServer esté disponible por **HTTPS**.
- El formulario de contacto usa `mailto:`. En un sitio estático eso abre el cliente de correo del visitante.

