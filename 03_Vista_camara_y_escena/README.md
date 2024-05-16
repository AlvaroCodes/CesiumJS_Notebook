# Vista, cámara y escena. los marcadores

![scheme](./scheme.png)

## 🌐 Vista (View): 
Se refiere a la forma en que se muestra el globo terrestre y los objetos geoespaciales en la pantalla. Puede haber diferentes tipos de vistas, como la vista en perspectiva (3D) o la vista en ortografía (2D). La vista se configura a través del objeto Viewer o CesiumWidget, que proporciona métodos para cambiar entre diferentes vistas, como la vista 3D, 2D o en primer plano.  

[📘 Doc](https://cesium.com/learn/cesiumjs/ref-doc/Viewer.html?classFilter=view)

##  📷 Cámara (Camera): 
Define la posición, orientación y campo de visión del observador virtual dentro del mundo 3D. Puedes controlar la cámara para cambiar la perspectiva del usuario sobre el globo terrestre o cualquier otro objeto en la escena. Puedes ajustar la posición y orientación de la cámara programáticamente para enfocarte en áreas específicas del globo o para seguir objetos en movimiento.  

[📘 Doc](https://cesium.com/learn/cesiumjs/ref-doc/Camera.html)   

**Opciones de la Cámara**
<details>
  <summary>Valores por defecto</summary>

  * **Cesium.Camera.DEFAULT_OFFSET**  
  [📘 Doc](https://cesium.com/learn/cesiumjs/ref-doc/Camera.html#.DEFAULT_OFFSET)  

  *  **Cesium.Camera.DEFAULT_VIEW_FACTOR**  
  [📘 Doc](https://cesium.com/learn/cesiumjs/ref-doc/Camera.html#.DEFAULT_OFFSET)  

  *  **Cesium.Camera.DEFAULT_VIEW_RECTANGLE:** Te informa de la vista predeterminada de la cámara, propiedad solo de lectura.  
  [📘 Doc](https://cesium.com/learn/cesiumjs/ref-doc/Camera.html#.DEFAULT_OFFSET) || [📂 Ejemplo](https://github.com/AlvaroCodes/cesiumJS_notebook/blob/main/03_Vista_camara_y_escena/examples/02_dafault_view_rectangle.html)
</details>    

---
**📂 Ejemplos:**  
▶️ [Control del Zoom](https://github.com/AlvaroCodes/cesiumJS_notebook/blob/main/03_Vista_camara_y_escena/examples/01_Zoom.html)  

**Ejemplos Cesium:**    
▶️ [Manejo de la cámara con el teclado](https://sandcastle.cesium.com/?src=Camera%20Tutorial.html&label=All)  
▶️ [Opciones vuelos cámara](https://sandcastle.cesium.com/?src=Camera.html&label=All)


## ⛰️ Escena (Scene):
Es el lienzo en el que se renderizan todos los elementos gráficos, como el globo terrestre, los modelos 3D, ...  

[📘 Doc](https://cesium.com/learn/cesiumjs/ref-doc/Scene.html?classFilter=scene)

### Elementos de la escena:
#### 🌎 El globo (globe)  
[📘 Doc](https://cesium.com/learn/cesiumjs/ref-doc/Globe.html)

**Opciones del globo - Límitar extensión**
<details>
  <summary>cartographicLimitRectangle</summary>
  Recorta el globo a una zona concreta, por defecto ```Rectangle.MAX_VALUE```.

  ```javascript
  const viewer = new Cesium.Viewer('cesiumContainer');
  const scene = viewer.scene;
  const globe = scene.globe;

  const spainRectangle = Cesium.Rectangle.fromDegrees(
    -9.392883673530648,
    35.946850083961464,
    3.0394840836805496,
    43.74833771420099
  );

    globe.cartographicLimitRectangle = spainRectangle;
    scene.skyAtmosphere.show = false;
  ```
  
  [📘 Doc](https://cesium.com/learn/cesiumjs/ref-doc/Globe.html#cartographicLimitRectangle)  || [📂 Ejemplo](https://github.com/AlvaroCodes/cesiumJS_notebook/blob/main/03_Vista_camara_y_escena/examples/02_dafault_view_rectangle.html)
</details> 

<details>
  <summary>clippingPlanes</summary>
  Delimita la representación del plano ("recorta").

  ```javascript
   const viewer = new Cesium.Viewer('cesiumContainer');

    // Crear un conjunto de clipping planes
    const clippingPlanes = new Cesium.ClippingPlaneCollection({
        planes : [
            new Cesium.ClippingPlane(new Cesium.Cartesian3(1.0, 0.0, 0.0), 0.0),
            new Cesium.ClippingPlane(new Cesium.Cartesian3(-1.0, 0.0, 0.0), -4000000.0),
            new Cesium.ClippingPlane(new Cesium.Cartesian3(0.0, 1.0, 0.0), 0.0),
            new Cesium.ClippingPlane(new Cesium.Cartesian3(0.0, -1.0, 0.0), -4000000.0)
        ],
        edgeWidth: 1.0,
        edgeColor: Cesium.Color.WHITE
    });

    // Aplicar los clipping planes al globo
    viewer.scene.globe.clippingPlanes = clippingPlanes;
  ```
  
  [📘 Doc](https://cesium.com/learn/cesiumjs/ref-doc/Globe.html#clippingPlanes)  || [📂 Ejemplo](https://github.com/AlvaroCodes/cesiumJS_notebook/blob/main/03_Vista_camara_y_escena/examples/02_dafault_view_rectangle.html)
</details> 
