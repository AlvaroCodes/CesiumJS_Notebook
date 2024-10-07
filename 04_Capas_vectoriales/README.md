# Entity

## Estílos / Materiales
### Genéricos

<details>
  <summary>ColorMaterialProperty: Aplicar un color sólido</summary>

```javascript
// Coordenadas para una línea que esté en Madrid
const positions = Cesium.Cartesian3.fromDegreesArray([
    -3.7038, 40.4168,  // Madrid centro
    -3.6883, 40.4295   // Otra posición cercana en Madrid
]);

// Añadir la entidad de polilínea con ColorMaterialProperty
viewer.entities.add({
    polyline: {
        positions: positions,
        width: 5,  // Ancho de la polilínea
        material: new Cesium.ColorMaterialProperty(Cesium.Color.RED)  // Color sólido rojo
    }
});

// Centrarse en la entidad creada
viewer.zoomTo(viewer.entities);
```

Ejemplo: https://codepen.io/AlvaroCodes/pen/bGXeywb
</details>

<details>
  <summary>ImageMaterialProperty: Aplicar una imagen como textura.</summary>

```javascript
// Coordenadas para una línea que esté en Madrid
const positions = Cesium.Cartesian3.fromDegreesArray([
    -3.7038, 40.4168,  // Madrid centro
    -3.6883, 40.4295   // Otra posición cercana en Madrid
]);

// Añadir la entidad de polilínea con ImageMaterialProperty
viewer.entities.add({
    polyline: {
        positions: positions,
        width: 10,  // Ancho de la polilínea
        material: new Cesium.ImageMaterialProperty({
            image: 'https://i.imgur.com/Gd6YzZq.png',  // URL de la imagen (una textura de rayas blancas y negras)
            repeat: new Cesium.Cartesian2(10.0, 1.0),  // Repetir la imagen a lo largo de la polilínea
            transparent: true  // Permitir transparencia en la imagen
        })
    }
});

// Centrarse en la entidad creada
viewer.zoomTo(viewer.entities);
```

Ejemplo: https://codepen.io/AlvaroCodes/pen/mdNEgYG

</details>

<details>
  <summary>StripeMaterialProperty: Aplicar un patrón de rayas alternantes</summary>

```javascript
// Coordenadas para una línea que esté en Madrid
const positions = Cesium.Cartesian3.fromDegreesArray([
    -3.7038, 40.4168,  // Madrid centro
    -3.6883, 40.4295   // Otra posición cercana en Madrid
]);

// Añadir la entidad de polilínea con StripeMaterialProperty
viewer.entities.add({
    polyline: {
        positions: positions,
        width: 5,  // Ancho de la polilínea
        material: new Cesium.StripeMaterialProperty({
            evenColor: Cesium.Color.YELLOW,   // Color de las rayas pares
            oddColor: Cesium.Color.BLACK,     // Color de las rayas impares
            repeat: 10,                       // Número de repeticiones del patrón a lo largo de la línea
            orientation: Cesium.StripeOrientation.HORIZONTAL  // Orientación de las rayas
        })
    }
});

// Centrarse en la entidad creada
viewer.zoomTo(viewer.entities);
```


Ejemplo: https://codepen.io/AlvaroCodes/pen/mdNEYOv
</details>

<details>
  <summary>CheckerboardMaterialProperty: Patrón de tablero de ajedrez</summary>

```javascript
// Coordenadas para una línea que esté en Madrid
const positions = Cesium.Cartesian3.fromDegreesArray([
    -3.7038, 40.4168,  // Madrid centro
    -3.6883, 40.4295   // Otra posición cercana en Madrid
]);

// Añadir la entidad de polilínea con CheckerboardMaterialProperty
viewer.entities.add({
    polyline: {
        positions: positions,
        width: 5,  // Ancho de la polilínea
        material: new Cesium.CheckerboardMaterialProperty({
            evenColor: Cesium.Color.WHITE,   // Color de los cuadros pares
            oddColor: Cesium.Color.BLACK,    // Color de los cuadros impares
            repeat: new Cesium.Cartesian2(10.0, 1.0)  // Número de repeticiones del patrón
        })
    }
});

// Centrarse en la entidad creada
viewer.zoomTo(viewer.entities);
```

Ejemplo: https://codepen.io/AlvaroCodes/pen/QWeERvj
</details>

<details>
  <summary>GridMaterialProperty: Aplicar un patrón de cuadrícula</summary>

```javascript
// Coordenadas para un polígono en Madrid
const polygonPositions = Cesium.Cartesian3.fromDegreesArray([
    -3.7038, 40.4168,  // Madrid centro
    -3.7038, 40.4268,  // Punto hacia el norte
    -3.6938, 40.4268,  // Punto hacia el este
    -3.6938, 40.4168   // Punto hacia el sur
]);

// Añadir el polígono con GridMaterialProperty
viewer.entities.add({
    polygon: {
        hierarchy: polygonPositions,
        material: new Cesium.GridMaterialProperty({
            color: Cesium.Color.YELLOW,  // Color de las líneas de la cuadrícula
            cellAlpha: 0.2,  // Transparencia de las celdas
            lineCount: new Cesium.Cartesian2(8, 8),  // Número de líneas en X e Y
            lineThickness: new Cesium.Cartesian2(1.0, 1.0),  // Grosor de las líneas de la cuadrícula
            lineOffset: new Cesium.Cartesian2(0.0, 0.0)  // Desplazamiento de las líneas
        })
    }
});

// Centrarse en la entidad creada
viewer.zoomTo(viewer.entities);
```

  Ejemplo: https://codepen.io/AlvaroCodes/pen/eYqzaRW
  
</details>


### Líneas

<details>
  <summary>PolylineArrowMaterialProperty: Permite dibujar una flecha a lo largo de una línea (polyline).</summary>

```javascript
// Coordenadas para una línea que esté en Madrid
const positions = Cesium.Cartesian3.fromDegreesArray([
    -3.7038, 40.4168,  // Madrid centro
    -3.6883, 40.4295   // Otra posición cercana en Madrid
]);

viewer.entities.add({
    polyline: {
        positions: positions,
        width: 5,
        material: new Cesium.PolylineArrowMaterialProperty(Cesium.Color.RED)  // Color rojo para la flecha
    }
});

viewer.zoomTo(viewer.entities);
```

Ejemplo: https://codepen.io/AlvaroCodes/pen/KKOMYBO
  
</details>

<details>
  <summary>PolylineGlowMaterialProperty: La línea tendrá un efecto de resplandor (neon).</summary>

```javascript
// Coordenadas para una línea que esté en Madrid
const positions = Cesium.Cartesian3.fromDegreesArray([
    -3.7038, 40.4168,  // Madrid centro
    -3.6883, 40.4295   // Otra posición cercana en Madrid
]);

viewer.entities.add({
    polyline: {
        positions: positions,
        width: 10,  // Ancho de la línea
        material: new Cesium.PolylineGlowMaterialProperty({
            glowPower: 0.3,      // Intensidad del resplandor
            color: Cesium.Color.BLUE  // Color del resplandor (azul)
        })
    }
});

viewer.zoomTo(viewer.entities);
```
  
Ejemplo: https://codepen.io/AlvaroCodes/pen/gOVMyZd

</details>

<details>
  <summary>PolylineOutlineMaterialProperty: Permite crear un PolyLine con color principal y un borde de un color diferente.</summary>


```javascript
// Coordenadas para una línea que esté en Madrid
const positions = Cesium.Cartesian3.fromDegreesArray([
    -3.7038, 40.4168,  // Madrid centro
    -3.6883, 40.4295   // Otra posición cercana en Madrid
]);

// Añadir la entidad de polilínea con PolylineOutlineMaterialProperty
viewer.entities.add({
    polyline: {
        positions: positions,
        width: 5,  // Ancho de la polilínea
        material: new Cesium.PolylineOutlineMaterialProperty({
            color: Cesium.Color.YELLOW,      // Color principal de la polilínea
            outlineWidth: 2,                 // Ancho del borde de la polilínea
            outlineColor: Cesium.Color.BLACK // Color del borde
        })
    }
});

// Centrarse en la entidad creada
viewer.zoomTo(viewer.entities);
```
</details>

<details>
  <summary>PolylineDashMaterialProperty: Permite dibujar un patrón de líneas discontinuas.</summary>


```javascript
viewer.entities.add({
  name: 'Línea Discontinua en Madrid',
  polyline: {
    positions: positions,
    width: 5, // Ancho de la línea
    material: new Cesium.PolylineDashMaterialProperty({
          color: Cesium.Color.YELLOW,
         dashLength: 16, // Longitud de los guiones
      gapColor: Cesium.Color.TRANSPARENT // Color del espacio entre guiones
    })
  }
});
```

Ejemplo: https://codepen.io/AlvaroCodes/pen/GRVqeaE
https://cesium.com/learn/cesiumjs/ref-doc/PolylineDashMaterialProperty.html
</details>

# Primitive

PolylineMaterialAppearance: No es compatible directamente con las entities.




