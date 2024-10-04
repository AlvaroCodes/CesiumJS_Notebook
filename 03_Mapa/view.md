### 🌐 Vista (View): 

[📘 Documentación View CESIUM](https://cesium.com/learn/cesiumjs/ref-doc/Viewer.html?classFilter=view)

Se refiere a la forma en que se muestra el globo terrestre y los objetos geoespaciales en la pantalla. Puede haber diferentes tipos de vistas, como la vista en perspectiva (3D) o la vista en ortografía (2D). La vista se configura a través del objeto Viewer o CesiumWidget, que proporciona métodos para cambiar entre diferentes vistas, como la vista 3D, 2D o en primer plano.  

Creación de la vista y algunas de sus propiedades:

```javascript
new Viewer(
  idContenedor, // El ID del contenedor HTML donde se va a renderizar el globo o mapa de Cesium.
  {
    animation: false, // Deshabilita la barra de animación del tiempo (control de simulación del tiempo).
    fullscreenButton: false, // Deshabilita el botón para ver la vista en pantalla completa.
    vrButton: false, // Deshabilita el botón para activar la visualización en Realidad Virtual (VR).
    homeButton: false, // Deshabilita el botón de "Home", que devuelve la vista a la posición inicial.
    selectionIndicator: false, // Deshabilita el indicador visual que aparece cuando seleccionas un objeto en el mapa.
    skyBox: false, // Deshabilita la caja de cielo (skybox) que se muestra en el fondo del globo para representar el espacio.
    baseLayerPicker: false, // Deshabilita el selector de capas base, que permite cambiar entre diferentes fuentes de mapas (satélite, calles, etc.).
    geocoder: false, // Deshabilita el geocodificador que permite buscar lugares por nombre o coordenadas.
    infoBox: false, // Deshabilita el cuadro de información que aparece cuando seleccionas un objeto.
    sceneModePicker: false, // Deshabilita el selector de modo de escena (permite cambiar entre vista 2D, 3D y Columbus View).
    timeline: false, // Deshabilita la línea de tiempo que permite avanzar o retroceder en el tiempo cuando se visualizan datos con marcas temporales.
    navigationHelpButton: false, // Deshabilita el botón de ayuda de navegación que muestra instrucciones sobre cómo moverse en el mapa.
    navigationInstructionsInitiallyVisible: false, // Indica si las instrucciones de navegación deben estar visibles al principio (también desactivado).
    scene3DOnly: false, // Permite usar solo la vista 3D, si es true deshabilita otros modos como 2D y Columbus View.
    shouldAnimate: false, // Desactiva la animación automática en la escena, ideal para aplicaciones estáticas o que no requieran movimiento continuo.
    baseLayer: false, // Desactiva la capa base predeterminada (por defecto, se carga una capa de imágenes satelitales).
    mapProjection, // Proyección del mapa, define cómo se proyectan las coordenadas (puede ser EPSG:4326, EPSG:3857, etc.).
  }
)

```



#### 🔍 Escala (Scale)
La escala permite a los usuarios interpretar correctamente las distancias y tamaños de los objetos mostrados en el mapa.

Para calcular la distancia entre dos puntos en la superficie del globo, se utiliza **_EllipsoidGeodesic_**. Este objeto permite calcular la distancia geodésica (la distancia más corta sobre la superficie del elipsoide) entre dos puntos.

```javascript
/*
Para calcular distancias sobre la superficie del globo (Ellipsoid.WGS84)
      
📘 Doc: https://cesium.com/learn/ion-sdk/ref-doc/EllipsoidGeodesic.html
*/
const geodesic = new Cesium.EllipsoidGeodesic();

/*
Coordenadas del borde inferior de la pantalla para obtener las posiciones de 
la izquierda y la derecha en el globo 
         
📘 Doc getPickRay: https://cesium.com/learn/cesiumjs/ref-doc/Camera.html#getPickRay
📘 Doc pick: https://cesium.com/learn/cesiumjs/ref-doc/Globe.html?classFilter=GLOBE#pick
*/

const left = scene.camera.getPickRay(new Cesium.Cartesian2((width / 2) | 0, height - 1));
const right = scene.camera.getPickRay(new Cesium.Cartesian2((1 + width / 2) | 0, height - 1));
const leftPosition = globe.pick(left, scene);
const rightPosition = globe.pick(right, scene);

/*
Las posiciones en coordenadas cartesianas se convierten a coordenadas cartográficas 
y se utilizan para calcular la distancia geodésica en la superficie del elipsoide.
*/
const leftCartographic = globe.ellipsoid.cartesianToCartographic(leftPosition);
const rightCartographic = globe.ellipsoid.cartesianToCartographic(rightPosition);

geodesic.setEndPoints(leftCartographic, rightCartographic);
const pixelDistance = geodesic.surfaceDistance; // Distancia en metros
```  
▶️ scaleLine: [📋 HTML](https://github.com/AlvaroCodes/cesiumJS_notebook/blob/main/03_Vista_camara_y_escena/examples/09_scaleLine.html)  | 🚀[CodePen](https://codepen.io/AlvaroCodes/pen/PovNOyX)
