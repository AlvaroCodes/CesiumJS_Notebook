# 5. Capas Raster  

![scheme](./scheme.png)

## 5.1. ImageryProvider
Capa Rástes que recibe un provedor ```(new Cesium.ImageryLayer(imageryProvider, options))```.  
[📘 Doc](https://cesium.com/learn/cesiumjs/ref-doc/ImageryLayer.html?classFilter=ImageryLaye)  

**Opciones:**
<details>
  <summary>Alpha ➡️ "Opacity"</summary>
 Valor Alpha, se puede utilizar para dar opacidad a la capa. Valor por defecto 1.0.  
  
 [📘 Doc](https://cesium.com/learn/cesiumjs/ref-doc/ImageryLayer.html?classFilter=ImageryLayer#alpha)
  
```javascript
const osmProvider = new Cesium.UrlTemplateImageryProvider({
   url: 'http://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
});

viewer.imageryLayers.addImageryProvider(osmProvider, {alpha: 0.5});
```
</details>  

<details>
  <summary>Show ➡️ "Visibility"</summary>
Determina si se muestra o no la capa.
  
 [📘 Doc](https://cesium.com/learn/cesiumjs/ref-doc/ImageryLayer.html?classFilter=ImageryLayer#show)
  
```javascript
const osmProvider = new Cesium.UrlTemplateImageryProvider({
   url: 'http://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
});

viewer.imageryLayers.addImageryProvider(osmProvider, {show: false});
```
</details>  

<details>
  <summary>minimumTerrainLevel y maximumTerrainLevel ➡️ "minZoom y maxZoom"</summary>
Limita el zoom.  
[📘 Doc](https://cesium.com/learn/cesiumjs/ref-doc/ImageryLayer.html?classFilter=ImageryLayer)  

```javascript
const osmProvider = new Cesium.UrlTemplateImageryProvider({
   url: 'http://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
});

viewer.imageryLayers.addImageryProvider(osmProvider, {minimumTerrainLevel: minZoom, maximumTerrainLevel:maxZoom});
```
</details>  

## 5.2 Proveedores
### 5.2.1. OpenStreetMapImageryProvider  | OSM  | [📘 Doc](https://cesium.com/learn/ion-sdk/ref-doc/OpenStreetMapImageryProvider.html)
Proporciona imágenes en mosaico alojadas en OpenStreetMap, por defecto "https://tile.openstreetmap.org/".
```javascript
const osmProvider = new Cesium.OpenStreetMapImageryProvider({
  url : 'https://tile.openstreetmap.org/'
});

viewer.imageryLayers.addImageryProvider(osmProvider);
```   

**Ejemplos:**  
▶️ [openstreetmap](https://github.com/AlvaroCodes/cesiumJS_notebook/blob/main/05_Capas_raster/examples/03_OpenStreetMapImageryProvider.html)  

### 5.2.2. TileMapServiceImageryProvider | TMS - XYZ | [📘 Doc](https://cesium.com/learn/ion-sdk/ref-doc/TileMapServiceImageryProvider.html)
  
### 5.2.3. WebMapServiceImageryProvider | WMS | [📘 Doc](https://cesium.com/learn/ion-sdk/ref-doc/WebMapServiceImageryProvider.html)

### 5.2.4. UrlTemplateImageryProvider | TMS - XYZ - WMS - WMTS | [📘 Doc](https://cesium.com/learn/ion-sdk/ref-doc/UrlTemplateImageryProvider.html)  
Realiza una consulta a una tesela por medio de una URL y te devuelve la imagen del provedor.

```javascript
const osmProvider = new Cesium.UrlTemplateImageryProvider({
   url: 'http://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png'
});

viewer.imageryLayers.addImageryProvider(osmProvider);
```

<details>
  <summary>tileWidth y tileHeight ➡️ "TileSize"</summary>
  Tamaño de la tesela, por defecto los valores son 256.
  
  * **tileWidth** | [📘 Doc](https://cesium.com/learn/cesiumjs/ref-doc/UrlTemplateImageryProvider.html?classFilter=UrlTemplateImageryProvider#tileWidth)
  * **tileHeight** | [📘 Doc](https://cesium.com/learn/cesiumjs/ref-doc/UrlTemplateImageryProvider.html?classFilter=UrlTemplateImageryProvider#tileHeight)

```javascript
const osmProvider = new Cesium.UrlTemplateImageryProvider({
   url: 'http://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
   tileWidth: 256,
   tileHeight: 256
});

viewer.imageryLayers.addImageryProvider(osmProvider);
```
</details>  

<details>
  <summary>maximumLevel y minimumLevel ➡️ "TileGridMaxZoom y TileGridMinZoom"</summary>
  Zoom máximo y mínimo de la tesela en forma de rejilla.
  
  * **maximumLevel** | [📘 Doc](https://cesium.com/learn/cesiumjs/ref-doc/UrlTemplateImageryProvider.html?classFilter=UrlTemplateImageryProvider#maximumLevel)
  * **minimumLevel** | [📘 Doc](https://cesium.com/learn/cesiumjs/ref-doc/UrlTemplateImageryProvider.html?classFilter=UrlTemplateImageryProvider#minimumLevel)

```javascript
const osmProvider = new Cesium.UrlTemplateImageryProvider({
   url: 'http://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
   maximumLevel:  17, // especifica el nivel máximo creado en el servicio para permitir hacer "overzoom"
});

viewer.imageryLayers.addImageryProvider(osmProvider);
```
</details>  

<details>
  <summary>rectangle ➡️ "MaxExtent"</summary>
  Restringe la visualización a una región específica.
  [📘 Doc](https://cesium.com/learn/cesiumjs/ref-doc/UrlTemplateImageryProvider.html?classFilter=UrlTemplateImageryProvider#rectangle)

```javascript
const osmProvider = new Cesium.UrlTemplateImageryProvider({
   url: 'http://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',
   rectangle : Cesium.Rectangle.fromDegrees(96.799393, -43.598214999057824, 153.63925700000001, -9.2159219997013)
});

viewer.imageryLayers.addImageryProvider(osmProvider);
```
</details>  

**Ejemplos:**  
▶️ [openstreetmap](https://github.com/AlvaroCodes/cesiumJS_notebook/blob/main/05_Capas_raster/examples/01_UrlTemplateImageryProvider.html)  
▶️ [mierune + credit](https://github.com/AlvaroCodes/cesiumJS_notebook/blob/main/05_Capas_raster/examples/02_UrlTemplateImageryProvider.html)

### 5.2.5. SingleTileImageryProvider | WMS - WMTS | [📘 Doc](https://cesium.com/learn/ion-sdk/ref-doc/SingleTileImageryProvider.html)  
Proporciona un único mosaico de imágenes (WGS84 / EPSG:4326).  

**Ejemplos:**  
▶️ [Dog Img](https://github.com/AlvaroCodes/cesiumJS_notebook/blob/main/05_Capas_raster/examples/04_SingleTileImageryProvider.html)  

### WebMapTileServiceImageryProvider | WMTS | [📘 Doc](https://cesium.com/learn/ion-sdk/ref-doc/WebMapTileServiceImageryProvider.html)

### 5.2.6. Providers Visuales
* TileCoordinatesImageryProvider | [📘 Doc](https://cesium.com/learn/ion-sdk/ref-doc/TileCoordinatesImageryProvider.html)  
* GridImageryProvider  | [📘 Doc](https://cesium.com/learn/ion-sdk/ref-doc/GridImageryProvider.html)  

### 5.2.7. Otros Providers
* **Mapbox**
  * MapboxStyleImageryProvider | [📘 Doc](https://cesium.com/learn/ion-sdk/ref-doc/MapboxStyleImageryProvider.html)  
  * MapboxImageryProvider | [📘 Doc](https://cesium.com/learn/ion-sdk/ref-doc/MapboxImageryProvider.html?classFilter=mapbox)  
* **Bingmapsportal**
   * BingMapsImageryProvider | [📘 Doc](https://cesium.com/learn/ion-sdk/ref-doc/BingMapsImageryProvider.html?classFilter=Bingmaps)  
* **Cesium**
   * IonImageryProvider | [📘 Doc](https://cesium.com/learn/ion-sdk/ref-doc/IonImageryProvider.html?classFilter=ionima)  
* **ArcGis**
  * ArcGisMapServerImageryProvider | [📘 Doc](https://cesium.com/learn/ion-sdk/ref-doc/ArcGisMapServerImageryProvider.html?classFilter=arc)  
* **GoogleEarth**
  * GoogleEarthEnterpriseImageryProvider | [📘 Doc](https://cesium.com/learn/ion-sdk/ref-doc/GoogleEarthEnterpriseImageryProvider.html)  
  * GoogleEarthEnterpriseMapsProvider | [📘 Doc](https://cesium.com/learn/ion-sdk/ref-doc/GoogleEarthEnterpriseMapsProvider.html)
