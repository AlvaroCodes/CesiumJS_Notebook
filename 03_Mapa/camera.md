# 📷 Cámara (Camera): 
Define la posición, orientación y campo de visión del observador virtual dentro del mundo 3D. Puedes controlar la cámara para cambiar la perspectiva del usuario sobre el globo terrestre o cualquier otro objeto en la escena. Puedes ajustar la posición y orientación de la cámara programáticamente para enfocarte en áreas específicas del globo o para seguir objetos en movimiento.  

[📘 Doc](https://cesium.com/learn/cesiumjs/ref-doc/Camera.html)   

<details>
  <summary>⚙️ Valores por defecto</summary>

  * **Cesium.Camera.DEFAULT_OFFSET**  
  [📘 Doc](https://cesium.com/learn/cesiumjs/ref-doc/Camera.html#.DEFAULT_OFFSET)  

  *  **Cesium.Camera.DEFAULT_VIEW_FACTOR**  
  [📘 Doc](https://cesium.com/learn/cesiumjs/ref-doc/Camera.html#.DEFAULT_OFFSET)  

  *  **Cesium.Camera.DEFAULT_VIEW_RECTANGLE:** Te informa de la vista predeterminada de la cámara, propiedad solo de lectura.  
  [📘 Doc](https://cesium.com/learn/cesiumjs/ref-doc/Camera.html#.DEFAULT_OFFSET) || [📂 Ejemplo](https://github.com/AlvaroCodes/cesiumJS_notebook/blob/main/03_Vista_camara_y_escena/examples/02_dafault_view_rectangle.html)
</details>    

<details>
  <summary>🔍 Opciones de zooms</summary>  

* **Modificar el zoom (en métros)**:
```javascript
cesiumMap.camera.setView({
      destination: Cartesian3.fromDegrees(
      CesiumMath.toDegrees(center.longitude),
      CesiumMath.toDegrees(center.latitude),
      meters,
    ),
});
```  
  
* **Cantidad de zoom** [📘 Doc](https://cesium.com/learn/ion-sdk/ref-doc/Cartographic.html#Cartographic)
```javascript
// Obtener el nivel de zoom (lo muestra en metros)
//  Te informa de la vista predeterminada de la cámara, propiedad solo de lectura.
console.log(viewer.camera.positionCartographic.height);
```  
  
* **zoomIn(amount)** [📘 Doc](https://cesium.com/learn/ion-sdk/ref-doc/Camera.html?classFilter=came#zoomIn)
  
```javascript
function setZoomIn(zoom) {
  // Cambiar nivel de zoom: Si no se pasa ningún valor por defecto viewer.camera.defaultZoomAmount (100000.0) 
  viewer.camera.zoomIn(zoom);
}
```

*  **zoomOut(amount)** [📘 Doc](https://cesium.com/learn/ion-sdk/ref-doc/Camera.html?classFilter=came#zoomOut)
  
```javascript
function setZoomOut(zoom) {
  // Cambiar nivel de zoom: Si no se pasa ningún valor por defecto viewer.camera.defaultZoomAmount (100000.0) 
  viewer.camera.zoomOut(zoom);
}
```

Si se quiere usar los niveles de zoom de Openlayers:
```javascript
const zoom_meters = {
      0: 251229000,
      1: 125614900,
      2: 62807900,
      3: 31404300,
      4: 15702500,
      5: 9470100,
      6: 5029700,
      7: 2573100,
      8: 1299200,
      9: 652600,
      10: 327150,
      11: 164400,
      12: 82450,
      13: 41350,
      14: 20750,
      15: 10400,
      16: 5200,
      17: 2600,
      18: 1300,
      19: 650,
      20: 325,
      21: 160,
      22: 80,
      23: 40,
      24: 20,
      25: 10,
      26: 5,
      27: 2,
      28: 1,
    }
```

**📂 Ejemplos:**  
* Control del Zoom: [📋 HTML](https://github.com/AlvaroCodes/cesiumJS_notebook/blob/main/03_Vista_camara_y_escena/examples/01_Zoom.html) | 🚀[CodePen](https://codepen.io/mangelescarrillo/pen/LYvwdeN)

</details>   


<details>
  <summary>🟦 Bounding Box (bbox)</summary>

Un BBOX define los límites geoespaciales de un área.

```javascript
// setBbox
cesiumMap.camera.setView({
  destination: new Rectangle.fromDegrees(extent[0], extent[1], extent[2], extent[3]),
});
```

</details>

<details>
  <summary>🎯 Centrar el mapa (center)</summary>

```javascript
// setCenter
cesiumMap.camera.setView({
  destination: Cartesian3.fromDegrees(center.x, center.y, height),
});
```

</details>



---

**Ejemplos Cesium:**    
▶️ [Manejo de la cámara con el teclado](https://sandcastle.cesium.com/?src=Camera%20Tutorial.html&label=All)  
▶️ [Opciones vuelos cámara](https://sandcastle.cesium.com/?src=Camera.html&label=All)
