# Reglas de Negocio

## Proyecto: Sistema de Gestión — "Dulce Espera - Moda Infantil"

> Este documento consolida las reglas de negocio identificadas durante el relevamiento (ver [`03-relevamiento.md`](./03-relevamiento.md)). Estas reglas condicionan el diseño de los requisitos funcionales, el modelo de datos y los casos de uso, y deben respetarse en cualquier propuesta de solución.

| Código | Regla | Origen / Justificación |
|---|---|---|
| RN01 | Las ventas fiadas se registran de forma diferenciada desde la entrega de la mercadería, pero solo se consideran cobradas por el importe de los pagos efectivamente registrados. | Sección 3 del relevamiento y decisión sobre cuenta corriente. La entrega, la venta y el cobro son hechos relacionados pero diferenciados. |
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
| RN13 | El precio vigente se asocia al producto y es común a todas sus variantes. | Decisión tomada durante la especificación de requisitos. Las prendas iguales mantienen el mismo precio aunque cambie el talle; el volumen del negocio no justifica repetir el precio por variante. |
| RN14 | Cada venta conserva el precio aplicado en el momento de la operación, aunque luego se modifique el precio vigente del producto. | Necesidad de identificar correctamente operaciones históricas y reportes de meses anteriores. |
| RN15 | Cada producto pertenece a una única temporada, que es común a todas sus variantes. | Aclaración de la propietaria sobre productos de verano e invierno, por ejemplo remeras mangas cortas y remeras mangas largas. |
| RN16 | Los productos que no requieren talle, género o color se registran mediante una única variante y el atributo correspondiente toma el valor "No aplica". | Decisión tomada durante la especificación de requisitos para mantener una estructura uniforme de stock. |
| RN17 | Un producto inactivo no se elimina y conserva sus variantes, ventas y demás información histórica. | Decisión de la propietaria para preservar el historial. |
| RN18 | Una variante se identifica por la combinación de los atributos aplicables a su producto: talle, color, género y estampado. | Decisión derivada de la necesidad de controlar cantidades por variante. |
| RN19 | Toda corrección manual de stock debe registrar un motivo seleccionado de una lista de opciones simples. | Decisión tomada durante la especificación de requisitos para mantener trazabilidad sin sobrecargar la operación cotidiana. |
| RN20 | Cada corrección manual de stock debe conservarse en un historial con la fecha, la variante, la cantidad anterior, la cantidad nueva y el motivo. | Principio de trazabilidad de los movimientos de inventario y necesidad de explicar diferencias entre el stock registrado y el físico. |
| RN21 | La carga inicial de stock debe realizarse mediante una planilla validada antes de incorporar los datos al inventario. | Decisión tomada durante la especificación de requisitos para facilitar la carga inicial y reducir errores masivos. |
| RN22 | No se puede confirmar una venta si alguna cantidad solicitada supera la cantidad disponible de la variante correspondiente. | Principio de integridad del stock y prevención de ventas de mercadería no registrada como disponible. |
| RN23 | El descuento de una venta se registra únicamente como porcentaje y no se calcula mediante reglas automáticas. | Decisión tomada durante la especificación de requisitos y RN02. |
| RN24 | El precio aplicado durante una venta puede modificarse manualmente si la propietaria lo decide, y el valor aplicado debe conservarse en el historial de la venta. | Decisión tomada durante la especificación de requisitos para contemplar acuerdos puntuales sin alterar el precio vigente del catálogo. |
| RN25 | La fecha de una venta o pago corresponde a la fecha actual del sistema y no puede modificarse manualmente. | Decisión tomada durante la especificación de requisitos. |
| RN26 | Una venta puede registrar uno o más medios de pago entre efectivo, transferencia y tarjeta de débito. | Decisión tomada durante la especificación de requisitos a partir de los medios relevados. |
| RN27 | Una transferencia pendiente de confirmación no se considera cobrada, aunque la venta pueda registrarse y la mercadería entregada descuente stock. | Sección 4 del relevamiento y decisión sobre entregas a clientes de confianza. |
| RN28 | Las ventas fiadas de una persona se administran en una única cuenta corriente con historial permanente; no se crean nuevos historiales cuando el saldo llega a cero. | Decisión tomada durante la especificación de requisitos para conservar trazabilidad y evitar fragmentar la deuda. |
| RN29 | Una persona puede registrar nuevas ventas fiadas aunque mantenga saldo pendiente. | Necesidad expresada por el usuario y coherente con el funcionamiento habitual de clientes de confianza. |
| RN30 | Los pagos parciales se aplican a la deuda total de la persona comenzando por las ventas fiadas más antiguas. | Recomendación aceptada durante la especificación de requisitos para simplificar la operación cotidiana. |
| RN31 | Un pago no puede superar el saldo pendiente de la persona. | Principio de integridad de la cuenta corriente y prevención de saldos negativos. |
| RN32 | Una venta fiada se considera cancelada cuando los pagos aplicados alcanzan su importe pendiente. | Decisión derivada del modelo de cuenta corriente y pagos parciales. |

## Notas de aplicación

- **RN01 y RN02** son las reglas con mayor impacto sobre los casos de uso de registro de venta: el sistema debe permitir marcar una venta como fiada y diferenciarla del total hasta su cobro, y debe permitir aplicar un descuento manual editable, nunca una lógica de descuento automática.
- **RN03 y RN04** son las de mayor impacto sobre el modelo de datos (`08-modelo-de-datos.md`): el talle debe modelarse como una lista de valores de referencia (no un rango numérico estricto), y la temporada debe asociarse al producto completo.
- **RN05** delimita negativamente el alcance: no es necesario diseñar entidades ni pantallas para gestión de deuda con proveedores en el MVP.
- **RN06 a RN12** delimitan el registro de personas asociado a ventas fiadas: no se requiere una gestión comercial general, pero sí identificar a quien mantiene pagos pendientes y conservar la trazabilidad de sus operaciones.
- **RN13 a RN18** definen la relación entre producto, precio, temporada, variante y conservación del historial. Estas reglas deben reflejarse en el modelo de datos y en la carga inicial del catálogo.
- **RN19 y RN20** definen la trazabilidad mínima de las correcciones manuales de stock. El motivo debe seleccionarse antes de confirmar el cambio y el historial no debe reemplazarse por el valor actual.
- **RN21 y RN22** protegen la integridad de la carga inicial y de las ventas: los datos importados se validan antes de incorporarse y una venta con stock insuficiente no puede confirmarse.
- **RN23 a RN27** definen el cálculo, fecha, medios de pago y estado de cobro de las ventas normales.
- **RN28 a RN32** definen la cuenta corriente de ventas fiadas, la aplicación de pagos y la conservación del historial.
