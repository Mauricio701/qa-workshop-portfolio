# Risk Matrix
| ID | Riesgo                              | Impacto| Probabilidad | Nivel| Mitigación                     |
|----|-------------------------------------|--------|--------------|----- |--------------------------------|
| R1 | Producto solicitado no procesado    | 4      | 5            | 20   | test Charter, pruebas de APIs, verificación de request y response de servicios  |
| R2 | Usuario bloqueado sin opción para autogestión de desbloqueo| 5 | 5 | 25| Parametría que que permita advertir sobre cantidad de intentos fallidos, incorporar menupoints de desbloqueo de usuarios|
| R3 | Mal cálculo de costo de productos ante selección de variables de productos varios | 4 | 4 | 16 | Pruebas exploratorias, Test cases y charters definidos, identificar ajustes requeridos en frontend y backend |
| R4 | Producto abonado y datos de clientes no registrados | 5| 3| 15 | Validiciones en pruebas explotarias utilizando usuarios con nombres largos y apellidos compuestos, Generar almacenamiento en backend o retornar warning en caso de error para aviso de valor no registrado. API Testing, Test Cases and charter |
| R5 | Proceso de confirmación de producto realizado pero cobro no procesado al cliente | 5 | 4 | 20 | Test Cases con pagos simulados sobre distintos afinidades de tarjetas, API Testing, validaciones de pagos con y sin decimales y cifras de mil |


