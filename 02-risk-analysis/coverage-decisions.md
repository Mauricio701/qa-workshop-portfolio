# Coverage Decisions

## Riesgos que se atenderán en primer lugar
- Existe la posibilidad de que el usuario sea cobrado sin recibir una confirmación de compra
- El sistema podría habilitar la compra de productos que no cuentan con stock disponible
- Datos sensibles podrían transmitirse sin el debido cifrado
- Mensajes de error ambiguos o poco comprensibles podrían provocar el abandono de la compra

## ¿Por qué estos riesgos tienen mayor prioridad?
Estos riesgos fueron considerados prioritarios por su elevado impacto tanto en el negocio como en la experiencia del usuario. Los problemas vinculados con pagos y seguridad pueden ocasionar pérdidas económicas, generar reclamos y deteriorar la confianza del cliente. Del mismo modo, los fallos relacionados con inventario y usabilidad afectan de forma directa la conversión de ventas y el nivel de satisfacción del usuario. Por esa razón, las pruebas se concentrarán primero en los flujos críticos de compra, pago, gestión de stock y experiencia de usuario.

## Qué se probará en menor medida o quedará fuera en esta etapa
- Cambios menores en el diseño visual
- Funcionalidades con escaso uso por parte de los usuarios
- Casos extremos con baja probabilidad de ocurrencia en el cálculo del total del pedido

## Justificación de las exclusiones
Estas exclusiones se consideran adecuadas para una fase inicial, ya que representan un menor impacto y una menor probabilidad de ocurrencia. El esfuerzo de testing se enfocará primero en los riesgos críticos que comprometen ingresos, seguridad y experiencia de usuario. Las funcionalidades que queden fuera podrán incluirse en ciclos posteriores de prueba.