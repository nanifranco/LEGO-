# PIX·L

Tienda web de mosaicos de bloques hechos con la foto del cliente. Modelo con inventario propio: compras piezas por mayoreo, las tienes en casa y envías cada pedido desde México.

Abre `index.html` en el navegador. No necesita servidor ni dependencias.

## Lo que ve el cliente

- Sube su foto y ve cómo las piezas caen y encajan sobre la base hasta formar su mosaico (la foto se procesa en su dispositivo).
- Elige estilo (a todo color, pop, pastel, vintage, blanco y negro), tamaño (de 13 a 77 cm) y tipo de pieza.
- Ve el precio en MXN con envío incluido y pide por WhatsApp con un código de diseño.
- Ve cómo son sus instrucciones: secciones de 16 × 16 con el número de color en cada cuadrito.

## Panel de la dueña

Al final de la página, o en `index.html#duena`. Se guarda solo en el navegador donde lo uses.

- **Costos:** bolsa de 1,000 piezas, bases, impuesto de importación, tipo de cambio, empaque, envío nacional, margen y piezas extra. Calcula costo, precio y ganancia.
- **Inventario por color:** los clientes solo ven colores con existencia. Si un diseño necesita más piezas de las que tienes, te propone el color más parecido que sí tienes, o recalcular sin ese color.
- **Surtir pedido:** lista por color (y en gramos si calibras la báscula con 100 piezas), y botón para descontarlo del inventario.
- **Para resurtir:** colores con menos de 300 piezas.
- **Archivos:** plano completo, sección actual y vista previa en PNG.

## Colores

40 colores del catálogo Gobricks con sus equivalentes de BrickLink y Rebrickable. El color más parecido se elige con la fórmula CIEDE2000. Si tu proveedor usa otros colores, ajusta la lista `PAL` en `index.html`.

## Marca

No uses la palabra LEGO, su logo ni figuras tipo minifigura. Para describir las piezas usa "compatibles con las principales marcas de bloques".
