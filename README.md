# PIX·L — mosaicos de bloques

Página donde el cliente sube una foto, la ve convertida en mosaico de piezas 1×1 y ordena su kit con bases e instrucciones numeradas.

## Qué hace

Flujo pensado para el celular, con tema oscuro:

1. **Inicio**: subir foto (o arrastrarla), galería de ejemplos o continuar un borrador.
2. **Elegir modo**: vista de la foto con *Rotar* y *Cambiar foto*. Después, **Editor PIX·L** (control total) o **Diseño automático**, que elige orientación según la foto, talla M y contraste automático.
3. **Editor en 3 pasos**. La barra de arriba muestra medidas, precio con descuento y **Finalizar**. Cada herramienta abre una hoja desde abajo con *Deshacer* y *Listo*:
   - **Paso 1 · Prepara**
     - **Tamaño**: cuadrado, horizontal, vertical o a la medida. Base de 16, 24, 32 o 48. Tarjetas XS–XL con cm, bases, piezas, precio y "Ahorra X %". Las líneas sobre el mosaico marcan cada base.
     - **Recorte**: zoom, arrastrar para mover, rotar, centrar y usar la orientación de la foto.
   - **Paso 2 · Afina**
     - **Colores**: avisos de inventario con sustituciones, pieza cuadrada o redonda, máximo de colores y paleta para quitar o volver a usar colores.
     - **Ajustes**: contraste automático, brillo, contraste, saturación y difuminado.
     - **Filtros**: Original, Vivo, Blanco y negro, Sepia, Pop, Frío y Cálido, con vista previa de cada uno.
   - **Paso 3 · Avanzado**
     - **Pintar**: pincel, tomar color y borrar, pieza por pieza.
     - **Borradores**: guarda hasta 8 diseños en el dispositivo.
4. **Tu kit**: vista previa, medidas, piezas, colores y tiempo de armado. Avisos de inventario (no deja ordenar sin resolverlos), color de base (incluye transparente), resumen con descuento por tamaño, recargo por colores y envío, lo que incluye el kit, lista de piezas e instrucciones imprimibles.
5. **Ordenar**: pide los datos de envío, descarga `PXL-….json` con el diseño exacto y abre WhatsApp con el resumen.

Las **instrucciones** traen una portada con el mapa de bases (A1, A2…) y una hoja por base con cada pieza numerada. Con bases de 16×16 o 24×24 también imprimen **plantillas a tamaño real** (8 mm por pieza) para armar encima de una base transparente.

## Inventario: `catalog.json`

Es lo único que necesitas editar día a día:

- `colores[].stock.redondo` / `.cuadrado`: las piezas que tienes. Ponlo en `0` y el color aparece como agotado.
- `colores[].activo: false`: oculta un color.
- `placas.tamanos[]`: tamaños de base (studs, nombre, nota, precio). `placas.porDefecto` es la que aparece seleccionada.
- `placas.tallas`: cuántas bases lleva cada talla (XS…XL) con base de 24×24.
- `placas.colores[]`: colores de base con stock por tamaño (`"stock": {"16": 300, "24": 150, …}`).
- `tienda`: descuentos por número de bases, recargo por colores, lo que incluye el kit, precio por pieza, envío, envío gratis desde cierto monto y **tu número de WhatsApp** (con lada, p. ej. `5215512345678`).
- `proveedor`: tamaño y costo de cada lote, para calcular tu compra.

La página vuelve a leer `catalog.json` cada 60 s y cuando el cliente regresa a la pestaña. Si cambiaste el stock, el mosaico abierto se revisa de nuevo solo.

> Hay una copia del catálogo dentro de `index.html` (`#catalogo-embebido`). Solo se usa si la página no puede leer `catalog.json`, por ejemplo al abrirla desde el disco. Después de editar el catálogo, actualízala.

## Modo tienda (`index.html?admin`)

- Editar el inventario desde la página (se guarda en ese navegador) y **descargar el `catalog.json`** para subirlo al repo.
- **Compra al proveedor**: los lotes por color que necesitas para el diseño actual, con su costo estimado, un enlace de búsqueda y la opción de exportarlo a CSV.

## Proveedor

Lotes de piezas 1×1 compatibles (round tile 98138 / plate 3024) de vendedores MOC en AliExpress. Hay lotes de 500 a 1000 piezas por color, con decenas de colores y envío a México. Los precios del catálogo son estimados: cámbialos por lo que pagues de verdad.

## Publicar

Settings → Pages → *Deploy from branch* → `main` / root. No necesita servidor ni compilar nada.
