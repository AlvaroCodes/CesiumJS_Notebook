# ⛰️ Escena (Scene):  

[📘 Documentación Scene CESIUM](https://cesium.com/learn/cesiumjs/ref-doc/Scene.html?classFilter=scene)

Es el lienzo en el que se renderizan todos los elementos gráficos, como el globo terrestre, los modelos 3D, ...  

<details>
  <summary>🖱️ Control de la escena (periféricos de entrada). </summary>

  
**screenSpaceCameraController**: Gestiona la interacción del usuario con la cámara a través de dispositivos de entrada como el mouse y el teclado.

[📘 Documentación screenSpaceCameraController CESIUM](https://cesium.com/learn/ion-sdk/ref-doc/ScreenSpaceCameraController.html)

**Ejemplos:**  
▶️ MinZoom y MaxZoom: [📋 HTML](https://github.com/AlvaroCodes/cesiumJS_notebook/blob/main/03_Vista_camara_y_escena/examples/11_minMaxZooms.html)  | 🚀[CodePen](https://codepen.io/AlvaroCodes/pen/PovbOLE)  
▶️ Ejemplo Cesium - Camera Tutorial: 🚀[sandcastle Cesium](https://sandcastle.cesium.com/?src=Camera%20Tutorial.html)  
  
</details>

## 🌎 El globo (globe) 

[📘 Documentación screenSpaceCameraController CESIUM](https://cesium.com/learn/cesiumjs/ref-doc/Globe.html)  

**Opciones del globo**

<details>
  <summary>🖼️ Límitar extensión (maxExtent / viewExtent)</summary>
  
**Usando cartographicLimitRectangle**  

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
  [📘 Documentación cartographicLimitRectangle CESIUM](https://cesium.com/learn/cesiumjs/ref-doc/Globe.html#cartographicLimitRectangle)  || [📋 HTML](https://github.com/AlvaroCodes/cesiumJS_notebook/blob/main/03_Vista_camara_y_escena/examples/08_cartographicLimitRectangle.html)   || 🚀[CodePen](https://codepen.io/AlvaroCodes/pen/qBGqVRW)


**Usando clippingPlanes**  

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
[📘 Documentación clippingPlanes CESIUM](https://cesium.com/learn/cesiumjs/ref-doc/Globe.html#clippingPlanes)  || [📋 HTML](https://github.com/AlvaroCodes/cesiumJS_notebook/blob/main/03_Vista_camara_y_escena/examples/07_clippingPlane.html)  || 🚀[CodePen](https://codepen.io/AlvaroCodes/pen/GRaNyoQ)
    
</details>

## 🌌 Atmósfera (atmosphere)  

[📘 Documentación atmosphere CESIUM](https://cesium.com/learn/cesiumjs/ref-doc/SkyAtmosphere.html?classFilter=skyAtmosphere)  

Proporciona una representación realista de la atmósfera del cielo, incluyendo efectos como la dispersión de la luz y la iluminación atmosférica.

▶️ Ejemplo Cesium - Atmosphere: 🚀[sandcastle Cesium](https://sandcastle.cesium.com/?src=Atmosphere.html)  


