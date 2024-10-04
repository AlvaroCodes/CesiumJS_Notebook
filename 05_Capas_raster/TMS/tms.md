# TMS

<details>
  <summary>ℹ️ ¿Qué es un TMS?</summary>

Un TMS es un servicio de mapas que proporciona mapas como mosaicos (tiles). El mapa se divide en pequeñas imágenes o "cuadrículas" (tiles) que se cargan individualmente para mejorar la velocidad de visualización en la web.  

Estas imágenes se obtienen en función de un esquema predefinido de niveles de zoom, coordenadas y tiles.
    
</details>

## ImageryLayer  

[📘 Documentación ImageryLayer CESIUM](https://cesium.com/learn/cesiumjs/ref-doc/ImageryLayer.html?classFilter=ImageryLaye)  

Capa Rástes que recibe un provedor ```(new Cesium.ImageryLayer(imageryProvider, options))```.  

**Parámetros de la capa:**  

![Parámetros de la capa](../ImageryLayer_Properties.png)

<details>
  <summary>minimumTerrainLevel y maximumTerrainLevel</summary>

    - minimumTerrainLevel: El nivel mínimo de detalle del terreno en el que se mostrará esta capa de imágenes, o indefinido para mostrarla en todos los niveles. 
    - maximumTerrainLevel: El nivel máximo de detalle del terreno en el que se mostrará esta capa de imágenes, o indefinido para mostrarla en todos los niveles.

</details>

<details>
  <summary>rectangle</summary>

🧭 "MaxExtent en Openlayers"

Restringe la visualización a una región específica. 

[📘 Documentación rectangle CESIUM](https://cesium.com/learn/cesiumjs/ref-doc/TileMapServiceImageryProvider.html?classFilter=tilemaps#rectangle)

```javascript
const tms = new Cesium.ImageryLayer(
    TileMapServiceImageryProvider,
    {
      rectangle : Cesium.Rectangle.fromDegrees(96.799393, -43.598214999057824, 153.63925700000001, -9.2159219997013),
    }
);

viewer.imageryLayers.add(tms);
```

</details>

<details>
  <summary>Alpha</summary>

Valor Alpha, se puede utilizar para dar opacidad a la capa. Valor por defecto 1.0.  
  
🧭 "Opacity en Openlayers"

 [📘 Documentación alpha CESIUM](https://cesium.com/learn/cesiumjs/ref-doc/ImageryLayer.html?classFilter=ImageryLayer#alpha)
  
```javascript
const tms = new Cesium.ImageryLayer(
    TileMapServiceImageryProvider,
    {
      alpha: 0.5,
    }
);

viewer.imageryLayers.add(tms);
```  

</details>  

<details>
  <summary>Show</summary>
Determina si se muestra o no la capa.

🧭 "Visibility en Openlayers"
  
 [📘 Documentación show CESIUM](https://cesium.com/learn/cesiumjs/ref-doc/ImageryLayer.html?classFilter=ImageryLayer#show)
  
```javascript
const tms = new Cesium.ImageryLayer(
    TileMapServiceImageryProvider,
    {
      show: false,
    }
);

viewer.imageryLayers.add(tms);
```  
</details> 


## TileMapServiceImageryProvider

[📘 Documentación TileMapServiceImageryProvider CESIUM](https://cesium.com/learn/cesiumjs/ref-doc/TileMapServiceImageryProvider.html?classFilter=TileMapServiceImageryProvider)

Se utiliza para cargar imágenes de teselas desde un servidor con la especificicación TMS.

```javascript
const tmsProvider = new Cesium.TileMapServiceImageryProvider({
    url: 'https://tms-ign-base.idee.es/1.0.0/IGNBaseTodo/{z}/{x}/{reverseY}.jpeg',
});
```

**TileMapServiceImageryProvider contiene los siguientes parámetros:**

<details>
  <summary>URL</summary>

ℹ️ Para los valores negativos "{-z}", "{-x}" y "{-y}" se tiene que sustituir por "{reverseZ}", "{reverseX}" y "{reverseY}".
```javascript
const reverseRepleceUrl = (url) => {
return url
        .replace('{-z}', '{reverseZ}')
        .replace('{-x}', '{reverseX}')
        .replace('{-y}', '{reverseY}')
}
```

</details>

<details>
  <summary>tileWidth y tileHeight</summary>

🧭 "TileSize en Openlayers"

Tamaño de la tesela, por defecto los valores son 256.

[📘 Documentación tileHeight](https://cesium.com/learn/cesiumjs/ref-doc/TileMapServiceImageryProvider.html?classFilter=tilemaps#tileWidth)  

[📘 Documentación tileHeight](https://cesium.com/learn/cesiumjs/ref-doc/TileMapServiceImageryProvider.html?classFilter=tilemaps#tileHeight)


```javascript
const osmProvider = new Cesium.TileMapServiceImageryProvider({
   url: 'https://tms-ign-base.idee.es/1.0.0/IGNBaseTodo/{z}/{x}/{reverseY}.jpeg',
   tileWidth: 256,
   tileHeight: 256
});

viewer.imageryLayers.addImageryProvider(osmProvider);
```

</details>

<details> 
  <summary>maximumLevel y minimumLevel</summary>

🧭 "TileGridMaxZoom y TileGridMinZoom en Openlayers"

 Zoom máximo y mínimo de la tesela en forma de rejilla. 

[📘 Documentación maximumLevel](https://cesium.com/learn/cesiumjs/ref-doc/TileMapServiceImageryProvider.html?classFilter=TileMapServiceImageryProvider#maximumLevel)  

[📘 Documentación minimumLevel](https://cesium.com/learn/cesiumjs/ref-doc/TileMapServiceImageryProvider.html?classFilter=TileMapServiceImageryProvider#maximumLevel)  

```javascript
const osmProvider = new Cesium.TileMapServiceImageryProvider({
   url: 'https://tms-ign-base.idee.es/1.0.0/IGNBaseTodo/{z}/{x}/{reverseY}.jpeg',
   maximumLevel:  17, // especifica el nivel máximo creado en el servicio para permitir hacer "overzoom"
});

viewer.imageryLayers.addImageryProvider(osmProvider);
```

</details>

## Proxy (Resource)

<details>
  <summary>ℹ️ Uso del Proxy en las TMS</summary>

Debido a que la [política del mismo origen](https://en.wikipedia.org/wiki/Same-origin_policy) no restringe las solicitudes de imágenes, en general, un TMS no tendrá problemas con la política del mismo origen para cargar mosaicos desde dominios diferentes (no se hacen solicitudes complejas que devuelvan XML, GML u otros tipos de datos estructurados).

En TMS, estás solicitando principalmente mosaicos que son imágenes raster (archivos PNG, JPEG, etc.), lo cual no suele estar restringido por la política del mismo origen. 

Cuando puede ser necesario un proxy en TMS: 

- Control de acceso: Si los mosaicos contienen información sensible o si el servicio TMS está restringido para ciertos usuarios.
- Distribución de carga: Si se está sirviendo un gran volumen de mosaicos y se quiere evitar que los usuarios accedan directamente al servidor TMS, se puede usar un proxy para distribuir las solicitudes o cachéar los mosaicos para mejorar el rendimiento. 

</details>

**Resource**

[📘 Documentación Resource CESIUM](https://cesium.com/learn/cesiumjs/ref-doc/Resource.html)

Esta clase permite configurar parámetros como URL, encabezados, y proxies, así como manejar solicitudes con opciones avanzadas.

También incluye métodos para obtener diferentes tipos de datos, como JSON, blobs e imágenes, y puede manejar solicitudes de cross-origin (CORS) si están habilitadas.

```javascript
const urlService = 'URL DEL SERVICIO';

const url = new Resource({
    url: urlService,
    proxy: new DefaultProxy('/proxyPost?url='),
});

const tile = new TileMapServiceImageryProvider({ url });
```
