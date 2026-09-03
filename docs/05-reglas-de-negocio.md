# Reglas de Negocio

## Proyecto: Sistema de Gestión — "Dulce Espera - Moda Infantil"

> Este documento consolida las reglas de negocio identificadas durante el relevamiento (ver [`03-relevamiento.md`](./03-relevamiento.md)). Estas reglas condicionan el diseño de los requisitos funcionales, el modelo de datos y los casos de uso, y deben respetarse en cualquier propuesta de solución.

| Código | Regla | Origen / Justificación |
|---|---|---|
| RN01 | Las ventas fiadas se registran de forma diferenciada y solo se consolidan al total de ventas en el momento del cobro efectivo. | Sección 3 del relevamiento. La propietaria distingue explícitamente el fiado del resto de las ventas hasta que se efectiviza el cobro. |
| RN02 | Los descuentos no responden a una lógica automática; son decisiones discrecionales de la propietaria, condicionadas en algunos casos al medio y momento de pago. | Sección 3 del relevamiento. Existen dos escenarios de descuento (fin de temporada con pago inmediato, y "gentileza" del 10% en compras grandes), pero ninguno sigue una regla sistemática que pueda automatizarse sin intervención humana. |
| RN03 | El sistema de talles no es estándar entre proveedores; los talles numéricos (4, 6, 9, 10, 12) no siempre son exactos entre marcas. | Sección 6 del relevamiento. Impacta el modelo de datos: el talle debe tratarse como una categoría de referencia, no como una medida exacta y universal. |
| RN04 | Se mantiene stock de más de una temporada disponible simultáneamente, debido a la variabilidad climática de la región. | Sección 5 del relevamiento. La convivencia de temporadas es estructural al negocio, no una excepción — el modelo de stock debe contemplar el atributo temporada como parte regular de cada ítem. |
| RN05 | No se otorga mercadería a crédito por parte de los proveedores: toda reposición se abona en el momento de la compra. | Sección 7 del relevamiento. Descarta la necesidad de un módulo de cuentas por pagar a proveedores dentro del alcance del proyecto. |
| RN06 | Toda venta fiada debe estar asociada a una persona identificable. | Sección 8.1 del relevamiento. Es necesario identificar a la persona responsable del pago pendiente. |
| RN07 | Para identificar a una persona asociada a una venta fiada se requiere nombre, apellido y número de teléfono. | Sección 8.1 del relevamiento. La propietaria definió estos datos como necesarios, con el teléfono de carácter obligatorio. |
| RN08 | Una persona identificada puede ser asociada a nuevas ventas fiadas sin volver a registrarse como una persona diferente. | Sección 8.1 del relevamiento. La misma persona puede realizar nuevas compras fiadas y sus datos deben reutilizarse. |
| RN09 | El número de teléfono identifica de manera única a la persona registrada para ventas fiadas. | Sección 8.1 del relevamiento. El teléfono permite distinguir personas con nombres iguales y evitar duplicaciones. |
| RN10 | La actualización de los datos personales de una persona no modifica las ventas fiadas ni los cobros registrados previamente. | Sección 8.1 del relevamiento. La información actual puede cambiar sin perder el historial de operaciones. |
| RN11 | Una misma persona puede tener varias ventas fiadas pendientes simultáneamente. | Sección 8.1 del relevamiento. La propietaria confirmó que una persona puede mantener más de una venta pendiente. |
| RN12 | Una venta fiada descuenta la mercadería entregada, pero permanece pendiente hasta que se registra su cobro. | Secciones 3, 4 y 8.1 del relevamiento. La entrega de mercadería y el ingreso efectivo del dinero son hechos distintos. |

## Notas de aplicación

- **RN01 y RN02** son las reglas con mayor impacto sobre los casos de uso de registro de venta: el sistema debe permitir marcar una venta como fiada y diferenciarla del total hasta su cobro, y debe permitir aplicar un descuento manual editable, nunca una lógica de descuento automática.
- **RN03 y RN04** son las de mayor impacto sobre el modelo de datos (`08-modelo-de-datos.md`): el talle debe modelarse como una lista de valores de referencia (no un rango numérico estricto), y cada producto/stock debe poder asociarse a una temporada sin que eso implique ocultar automáticamente las demás.
- **RN05** delimita negativamente el alcance: no es necesario diseñar entidades ni pantallas para gestión de deuda con proveedores en el MVP.
- **RN06 a RN12** delimitan el registro de personas asociado a ventas fiadas: no se requiere una gestión comercial general, pero sí identificar a quien mantiene pagos pendientes y conservar la trazabilidad de sus operaciones.
