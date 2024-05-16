# Capas Raster  

![scheme](./scheme.png)

## ImageryProvider

### OpenStreetMapImageryProvider  | OSM  | [📘 Doc](https://cesium.com/learn/ion-sdk/ref-doc/OpenStreetMapImageryProvider.html)
Proporciona imágenes en mosaico alojadas en OpenStreetMap, por defecto "https://tile.openstreetmap.org/".
```javascript
const osmProvider = new Cesium.OpenStreetMapImageryProvider({
  url : 'https://tile.openstreetmap.org/'
});

viewer.imageryLayers.addImageryProvider(osmProvider);
```   

**Ejemplos:**  
▶️ [openstreetmap](https://github.com/AlvaroCodes/cesiumJS_notebook/blob/main/05_Capas_raster/examples/03_OpenStreetMapImageryProvider.html)  

### TileMapServiceImageryProvider | TMS - XYZ | [📘 Doc](https://cesium.com/learn/ion-sdk/ref-doc/TileMapServiceImageryProvider.html)
  
### WebMapServiceImageryProvider | WMS
[📘 Doc](https://cesium.com/learn/ion-sdk/ref-doc/WebMapServiceImageryProvider.html)

### UrlTemplateImageryProvider | TMS - XYZ - WMS - WMTS | [📘 Doc](https://cesium.com/learn/ion-sdk/ref-doc/UrlTemplateImageryProvider.html)  
Realiza una consulta a una tesela por medio de una URL y te devuelve la imagen del provedor.

```javascript
const osmProvider = new Cesium.UrlTemplateImageryProvider({
   url: 'http://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png'
});

viewer.imageryLayers.addImageryProvider(osmProvider);
```

<details>
  <summary>tileWidth y tileHeight -> "TileSize"</summary>
  Tamaño de la tesela. por defecto los valores son 256.
  
  * **tileWidth** | [📘 Doc](https://cesium.com/learn/cesiumjs/ref-doc/UrlTemplateImageryProvider.html?classFilter=UrlTemplateImageryProvider#tileWidth)
  * **tileHeight** | [📘 Doc](https://cesium.com/learn/cesiumjs/ref-doc/UrlTemplateImageryProvider.html?classFilter=UrlTemplateImageryProvider#tileHeight)
</details>  

**Ejemplos:**  
▶️ [openstreetmap](https://github.com/AlvaroCodes/cesiumJS_notebook/blob/main/05_Capas_raster/examples/01_UrlTemplateImageryProvider.html)  
▶️ [mierune + credit](https://github.com/AlvaroCodes/cesiumJS_notebook/blob/main/05_Capas_raster/examples/02_UrlTemplateImageryProvider.html)

### SingleTileImageryProvider | WMS - WMTS  
Proporciona un único mosaico de imágenes (WGS84 / EPSG:4326).  

[📘 Doc](https://cesium.com/learn/ion-sdk/ref-doc/SingleTileImageryProvider.html)  

**Ejemplos:**  
▶️ [Dog Img](https://github.com/AlvaroCodes/cesiumJS_notebook/blob/main/05_Capas_raster/examples/04_SingleTileImageryProvider.html)  

### WebMapTileServiceImageryProvider | WMTS
[📘 Doc](https://cesium.com/learn/ion-sdk/ref-doc/WebMapTileServiceImageryProvider.html)

### Providers Visuales
* TileCoordinatesImageryProvider  
  [📘 Doc](https://cesium.com/learn/ion-sdk/ref-doc/TileCoordinatesImageryProvider.html)
* GridImageryProvider  
  [📘 Doc](https://cesium.com/learn/ion-sdk/ref-doc/GridImageryProvider.html)

### Otros Providers
* **Mapbox**
  * **MapboxStyleImageryProvider**  
    [📘 Doc](https://cesium.com/learn/ion-sdk/ref-doc/MapboxStyleImageryProvider.html)
  * **MapboxImageryProvider**  
    [📘 Doc](https://cesium.com/learn/ion-sdk/ref-doc/MapboxImageryProvider.html?classFilter=mapbox)
* **Bingmapsportal**
   * BingMapsImageryProvider  
    [📘 Doc](https://cesium.com/learn/ion-sdk/ref-doc/BingMapsImageryProvider.html?classFilter=Bingmaps)
* **Cesium**
   * IonImageryProvider  
    [📘 Doc](https://cesium.com/learn/ion-sdk/ref-doc/IonImageryProvider.html?classFilter=ionima)
* **ArcGis**
  * ArcGisMapServerImageryProvider  
    [📘 Doc](https://cesium.com/learn/ion-sdk/ref-doc/ArcGisMapServerImageryProvider.html?classFilter=arc)
* **GoogleEarth**
  * GoogleEarthEnterpriseImageryProvider  
    [📘 Doc](https://cesium.com/learn/ion-sdk/ref-doc/GoogleEarthEnterpriseImageryProvider.html)
  * GoogleEarthEnterpriseMapsProvider  
    [📘 Doc](https://cesium.com/learn/ion-sdk/ref-doc/GoogleEarthEnterpriseMapsProvider.html)
