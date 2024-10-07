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

ImageMaterialProperty

Ejemplo: https://codepen.io/AlvaroCodes/pen/mdNEgYG

StripeMaterialProperty

CheckerboardMaterialProperty

GridMaterialProperty

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




