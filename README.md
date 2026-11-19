# pixela

Tienda web de mosaicos de bloques hechos con la foto del cliente, pensada para un negocio de dropshipping en México.

Abre `index.html` en el navegador. No necesita servidor ni dependencias.

## Lo que ve el cliente

- Sube su foto y la ve convertida en mosaico al instante (la foto se procesa en su dispositivo).
- Elige estilo (a todo color, pop, pastel, vintage, blanco y negro), tamaño (de 13 a 77 cm) y acabado de las piezas.
- Ve el precio en MXN y pide por WhatsApp con un código de diseño.
- Ve cómo son sus instrucciones: secciones de 16 × 16 con el número de color en cada cuadrito.

## Panel de la dueña

Al final de la página, o en `index.html#duena`:

- Proveedor (Webrick o MOC Brick Store, ambos con piezas Gobricks), costo por pieza y por base, envío, tipo de cambio, margen y piezas extra. Se guardan en el navegador.
- Costo, precio al cliente y ganancia del pedido actual.
- Marcar colores agotados y elegir el sustituto más parecido, o recalcular sin ese color.
- Lista de piezas en CSV (formato Rebrickable) para hacer el pedido con la dirección del cliente.
- Descarga del plano completo, la sección actual y la vista previa en PNG.

## Colores

Los 40 colores son del catálogo real de Gobricks, con su número de Gobricks y sus equivalentes de LEGO, BrickLink y Rebrickable. El color más parecido se elige con la fórmula CIEDE2000.

## Pendiente antes de vender

- Confirmar con Webrick que envían a México y su precio real por pieza y por base.
- Poner tu número de WhatsApp en el panel.
