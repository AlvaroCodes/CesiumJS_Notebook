# Conteptos Fundamentales

# 1. Coordenadas, sistemas de referencia y proyecciones.
wiew.scene (proyecciones)
* **Coordenadas:**
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
* **Proyecciones y Sistema de referencia:**
  * [GeographicProjection](https://cesium.com/learn/ion-sdk/ref-doc/GeographicProjection.html) - EPSG:3857.
  * [WebMercatorProjection](https://cesium.com/learn/ion-sdk/ref-doc/WebMercatorProjection.html) - EPSG:4326.
    
    <br/>
   ```JavaScript
   import { Viewer, WebMercatorProjection } from 'cesium';
   const viewer = new Viewer("cesiumContainer", mapProjection: new WebMercatorProjection());
   ```

# 2. Cámara y vista

