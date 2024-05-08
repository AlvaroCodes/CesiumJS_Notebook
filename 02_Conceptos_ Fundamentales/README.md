# Coordenadas, sistemas de referencia y proyecciones.

## Coordenadas
Par de valores numéricos que representan la ubicación de un punto en la superficie de la Tierra. Estos valores, comúnmente expresados en grados decimales de latitud y longitud (cartográficas). En el caso de **CesiumJS** podemos entrar:
  * **Cartesianas**  
    Normalmente se expresan en latitud y longitud, que son medidas angulares con respecto al ecuador y el meridiano de Greenwich, respectivamente. 
    * [Cartesian2](https://cesium.com/learn/cesiumjs/ref-doc/Cartesian2.html): Un punto en coordenadas cartesianas en 2D (x,y).
    * [Cartesian3](https://cesium.com/learn/cesiumjs/ref-doc/Cartesian3.html): Un punto en coordenadas cartesianas en 3D (x, y, z).
    * [Cartesian4](https://cesium.com/learn/cesiumjs/ref-doc/Cartesian4.html): Un punto en coordenadas cartesianas en 4D (x, y, z, w).    
      La **"W"** representa el tiempo, un momento específico en el tiempo.
  * **Cartográficas**   
    Las coordenadas cartesianas se utilizan para representar puntos en un espacio bidimensional o tridimensional.
    Se representan como (x, y) para coordenadas 2D o (x, y, z) para coordenadas 3D.
    * [Cartographic](https://cesium.com/learn/cesiumjs/ref-doc/Cartographic.html): Las coordenadas son definidas por la longitud, latitud y la altura (longitude, latitude, height).
    * [CartographicGeocoderService](https://cesium.com/learn/cesiumjs/ref-doc/CartographicGeocoderService.html): Geocodifica consultas que contienen coordenadas cartográficas (longitude,      latitude, height).
      
        <br/>
   ```JavaScript
   import { Cartesian2, Cartesian3, Cartesian4, Cartographic } from 'cesium';
   const cat2 = new Certesian2(x, y)
   ```
## Proyecciones y Sistema de referencia
  * [WebMercatorProjection | EPSG:4326](https://cesium.com/learn/ion-sdk/ref-doc/WebMercatorProjection.html). Esta proyección es el estándar para representar coordenadas geográficas (latitud y longitud), es una proyección cilíndrica, tiene la capacidad para representar áreas extensas de la Tierra con distorsión mínima.   
    EPSG:4326 representa las coordenadas geográficas en grados decimales de latitud y longitud, donde la latitud varía entre -90 y 90 grados y la longitud entre -180 y 180 grados.
    
  * [GeographicProjection | EPSG:3857](https://cesium.com/learn/ion-sdk/ref-doc/GeographicProjection.html).  Convierte las coordenadas geográficas en pares de coordenadas planas X e Y en metros, capacidad para representar grandes áreas con precisión pero puede introducir distorsiones en áreas cercanas a los polos.

    
    <br/>
   ```JavaScript
   import { Viewer, WebMercatorProjection } from 'cesium';
   const viewer = new Viewer("cesiumContainer", mapProjection: new WebMercatorProjection());
   ```
