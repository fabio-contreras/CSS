## Documentación del archivo styles.css
Este es el archivo de estilos de mi página del catálogo de café. Lo fui armando por partes y lo organicé para que fuera fácil de leer y de cambiar.

### La tipografía
Lo primero que hice fue traer la fuente **Roboto** desde Google Fonts con un `@import`. La elegí porque se ve limpia y tiene muchos pesos, así que puedo usar negrita o letra delgada según lo necesite. Le puse `display=swap` para que, mientras la fuente carga, el navegador muestre una temporal y la página no se quede en blanco.

### Una regla para todos
Después escribí una regla universal con `box-sizing: border-box`. Con eso, cuando le doy un ancho a una caja, el relleno y el borde ya cuentan dentro de ese ancho, y las cajas no se agrandan solas ni se desajusta el diseño.

### Mi paleta de colores
En `:root` guardé todos los colores y espacios del proyecto como variables. Así, si quiero cambiar un color, lo cambio una sola vez y se actualiza en toda la página.

- **Café oscuro** (`--color`): el fondo general de la página.
- **Café y café claro**: los enlaces del encabezado y del pie de página.
- **Mostaza**: los enlaces de las categorías.
- **Verdes** (normal, claro y oscuro): el botón de compra, el menú lateral y el footer.
- **Negro y rojo**: el fondo del encabezado y del contenido principal.
- **Amarillo**: el borde de cada producto.
- Dos variables de espacio, `--espacio-grande` (30px) y `--espacio-medio` (15px).

### Los enlaces
A cada zona de la página le di su propio color de enlace para que se distingan. A todos les quité el subrayado por defecto porque se ve más limpio, y al pasar el cursor por encima el subrayado aparece de nuevo (`a:hover`), así el usuario sabe que puede hacer clic.

### La estructura de la página
- **Header:** puse la imagen `cafe-granos.webp` de fondo. Con `cover` ocupa todo el ancho, con `center` queda centrada y con `no-repeat` no se repite. Le di 200px de alto y un fondo negro por si la imagen no carga.
- **Main, aside y footer:** les puse colores de fondo distintos. Por ahora son de prueba, pero me ayudan a ver dónde empieza y dónde termina cada parte.

### Las tarjetas de producto
Cada producto (`.producto`) tiene 20px de relleno para que el contenido no quede pegado al borde, 15px de margen arriba y abajo con `auto` a los lados para centrarlo, y un borde amarillo delgado que lo separa del resto.

### Lo que aprendí con esta actividad
- Usar variables CSS para mantener los colores consistentes.
- Cómo funciona el modelo de caja (`padding`, `margin`, `border` y `box-sizing`).
- Combinar selectores de elemento, de clase y descendentes.
- Poner una imagen de fondo y controlar cómo se ajusta.
- Usar `:hover` para dar respuesta visual a los enlaces.


## Hallazgos: Pseudoclases y Pseudoelementos
1. Diferencia entre pseudoclase y pseudoelemento

Una pseudoclase sirve para darle estilo a un elemento según el estado en que se encuentra o la acción que el usuario hace sobre él. El elemento ya existe en el HTML, y lo que cambia es cómo se ve cuando el usuario pasa el cursor (:hover), hace clic (:active) o llega a él con el teclado (:focus). Es una reacción a un evento.

Un pseudoelemento sirve para crear contenido virtual o seleccionar una parte de un elemento, sin escribir nada nuevo en el HTML. Con ::before y ::after puedo insertar un símbolo o una insignia desde el CSS, y el navegador lo dibuja como si fuera parte de la página. Es una inyección de contenido.

En resumen, la pseudoclase responde a cuándo está el elemento en cierto estado, y el pseudoelemento agrega qué contenido se ve.

2. Importancia técnica de :focus en accesibilidad

Muchas personas no usan el mouse: navegan con la tecla Tab porque tienen una discapacidad motriz, usan lector de pantalla o simplemente prefieren el teclado. Para ellas, :focus es el único indicador de en qué parte de la página están ubicadas. Si un enlace no muestra un contorno visible al recibir el foco, el usuario se pierde y no sabe qué elemento activará al presionar Enter.

Por eso es una buena práctica de accesibilidad (y un requisito de las pautas WCAG) no quitar el outline sin dar una alternativa. En mi proyecto usé un outline con el color secundario, que se ve claramente sobre el fondo del menú lateral.

3. Por qué inyectar elementos decorativos con ::before y ::after
HTML limpio y semántico: el HTML debe describir el contenido y su significado. Una viñeta o una etiqueta de “¡Oferta!” es decoración, y meterla en etiquetas vacías o <span> extra ensucia la estructura.
Mejor accesibilidad: los lectores de pantalla no se llenan de elementos sin valor informativo.
Mantenimiento más fácil: si quiero cambiar el símbolo del menú o el texto de la insignia, lo modifico en un solo lugar del CSS, en vez de editar cada etiqueta del HTML.
Separación de responsabilidades: el HTML se encarga de la estructura y el CSS de la apariencia.