# Sesión 1

## Charter
Explorar el funcionamiento del carrito de compras en la PetStore mediante distintos cambios de estado y combinaciones de acciones, como agregar productos, eliminarlos o modificar sus cantidades, con el objetivo de identificar inconsistencias, pérdida de información y comportamientos no esperados.

## ÁREAS
Carrito de compras – JPetStore

## INICIO
22/04/2026 – (Duración: 45 minutos)

## TESTER
José Fernando Paniagua Benitez

## DESGLOSE DE TAREAS
- 25 min: Incorporación de productos al carrito desde diferentes categorías, tanto con sesión iniciada como sin autenticación
- 10 min: Actualización de cantidades y eliminación de productos
- 10 min: Revisión de la navegación, persistencia del carrito y validaciones en escenarios límite

## ARCHIVOS DE DATOS
Productos disponibles en el catálogo de la JPetStore (sin uso de archivos externos)

## NOTAS DE PRUEBA
Se realizó una prueba agregando el producto Large Angelfish (EST-1, FI-SW-01, $16.50) desde el catálogo mediante la opción "Add to Cart". Aunque el sistema redirigió correctamente a la vista del carrito, el producto no se incorporó y el carrito se mostró vacío, con un Sub Total de $0.00.

Luego se repitió la misma validación con el producto Poodle (EST-8, K9-PO-02, $18.50). El resultado fue el mismo: redirección al carrito sin que el artículo apareciera cargado.

El flujo fue verificado tanto sin haber iniciado sesión como con un usuario autenticado. En ambos escenarios se observó el mismo problema, por lo que se descarta que esté relacionado con autenticación.

También se probó la modificación de cantidad de un producto dentro del carrito ingresando el valor 0. Como resultado, el sistema eliminó el producto sin mostrar advertencia ni solicitar confirmación previa.

La misma prueba se ejecutó ingresando valores negativos, por ejemplo -1. Nuevamente, el artículo fue eliminado de manera silenciosa y sin una validación visible para el usuario.

Por último, se agregó un producto al carrito con la sesión iniciada y posteriormente se cerró sesión. Al ingresar nuevamente con el mismo usuario, el carrito apareció vacío, lo que indica que su contenido no se mantiene entre sesiones.

## LISTA DE RIESGOS
- El flujo principal de compra se encuentra comprometido, ya que los productos no se agregan al carrito
- Los productos pueden eliminarse de forma silenciosa al ingresar cantidades 0 o negativas, sin advertencia previa
- La falta de persistencia del carrito al cerrar sesión puede generar frustración y abandono del proceso de compra

## DEFECTOS (BUGS)

**Bug 1: "Add to Cart" no agrega el producto al carrito**
- **Productos afectados:** Large Angelfish (EST-1), Poodle (EST-8); el comportamiento observado no parece limitarse a un producto específico
- **Pasos para reproducir:** Ingresar al catálogo → seleccionar cualquier producto → hacer clic en "Add to Cart"
- **Resultado esperado:** El producto debería visualizarse en el carrito con cantidad 1 y el subtotal actualizado
- **Resultado actual:** El sistema redirige a la pantalla del carrito, pero este permanece vacío ("Your cart is empty", Sub Total: $0.00)
- **Condiciones probadas:** Sin sesión iniciada y con sesión iniciada; el defecto se presenta en ambos casos
- **Impacto:** Alto – el flujo principal de compra queda inutilizable

**Bug 2: Cantidad 0 o negativa elimina el producto sin advertencia**
- **Pasos para reproducir:** Contar con un producto en el carrito → cambiar la cantidad a 0 o a un número negativo → presionar "Update Cart"
- **Resultado esperado:** El sistema debería bloquear la acción y mostrar un mensaje de validación adecuado
- **Resultado actual:** El producto es retirado del carrito de manera inmediata, sin aviso alguno
- **Impacto:** Medio – existe riesgo de pérdida accidental de productos seleccionados

## INCIDENTES (ISSUES)
- El carrito no conserva su contenido al cerrar sesión. No se puede determinar con certeza si se trata de un comportamiento esperado o de un defecto, ya que no se dispone de documentación ni de un criterio definido al respecto.