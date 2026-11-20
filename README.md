# PIX·L — mosaicos de bloques

Página donde el cliente sube una foto, la ve convertida en mosaico de piezas 1×1 y ordena su kit con bases e instrucciones numeradas.

## Qué hace

- **Subir imagen** (botón o arrastrar y soltar) y encuadrarla arrastrando sobre la vista previa, con zoom, brillo, contraste, saturación y difuminado opcional.
- **Tallas XS, S, M, L y XL** en cuadrado, vertical u horizontal (como brick.me), o bases a la medida hasta 20 por lado.
- **Bases (building plates)** de 16×16, 24×24, 32×32 o 48×48, cada una con su precio, inventario por color y nota. El cliente elige el tipo de base y el tamaño del mosaico (en cm) se arma como acomodo de esas bases, hasta 192 piezas por lado. Al cambiar de base se conserva el tamaño lo más parecido posible.
- **Piezas 1×1**, redondas o cuadradas (98138 / 3024). El inventario de cada forma se lleva por separado.
- **Solo usa los colores del catálogo.** La conversión compara colores con CIEDE2000, que se parece a cómo los percibe el ojo.
- **Revisa el inventario en tiempo real.** Si un color no alcanza, sugiere el más parecido que sí tenga piezas suficientes. El cliente lo acepta con "Sí, sustituir" o pide "Otra opción". No se puede ordenar hasta resolverlo.
- **Pedido**: piezas con repuesto (3 %, mínimo 2 por color), bases del color elegido (incluye transparentes), descuento por tamaño, recargo si pasa de 25 colores, envío, total en MXN, tiempo de armado aproximado y lo que incluye el kit. Al confirmar se descarga `PXL-….json` con el diseño exacto y se abre WhatsApp con el resumen.
- **Instrucciones imprimibles**: portada con el mapa de bases (A1, A2…), y una hoja por base (del tamaño que se eligió) con cada cuadrito numerado. Con bases de 16×16 o 24×24 también imprime **plantillas a tamaño real** (8 mm por pieza) para poner la base transparente encima y armar como pintar por números, coordenadas y líneas cada 8 piezas.

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
