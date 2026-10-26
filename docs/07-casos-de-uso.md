# Casos de uso

## Proyecto: Sistema de Gestión — "Dulce Espera - Moda Infantil"

> Este documento detalla los casos de uso del MVP a partir de las historias de usuario ([`06-historias-de-usuario.md`](./06-historias-de-usuario.md)), los requisitos ([`04-requisitos.md`](./04-requisitos.md)) y las reglas de negocio ([`05-reglas-de-negocio.md`](./05-reglas-de-negocio.md)).

## 1. Actores

| Actor | Tipo | Descripción |
|-------|------|-------------|
| Propietaria (Silvia) | Principal | Única usuaria del sistema. Administra el catálogo y el stock, consulta disponibilidad, registra ventas, ventas fiadas, pagos y anulaciones. |

No hay actores secundarios en el MVP: WhatsApp e Instagram son canales externos que no interactúan con el sistema, y las personas con ventas fiadas no acceden a él.

## 2. Convenciones

- Todos los casos de uso presuponen que la propietaria accedió al sistema con su cuenta (RNF-08) y que lo utiliza con conexión a internet (RNF-01).
- Los casos de uso se derivan de las historias de usuario. La numeración CU coincide con la de las HU, excepto en CU-09, que se nombra por la acción de negocio (registrar una venta fiada).
- Los valores de rendimiento son cualitativos y se precisarán durante el diseño o el piloto, como indican los requisitos no funcionales.

## 3. Resumen y trazabilidad

| CU | Nombre | HU | Requisitos principales | Reglas de negocio |
|----|--------|----|------------------------|-------------------|
| CU-01 | Registrar un producto con sus variantes | HU-01 | RF-CAT-01 a 10 | RN13, RN15, RN16, RN18 |
| CU-02 | Cargar el stock inicial mediante una planilla | HU-02 | RF-STK-01, 02, 10, 11, 12 | RN21 |
| CU-03 | Asignar stock a un producto o variante nueva | HU-03 | RF-STK-02, 03, 12 | RN18 |
| CU-04 | Corregir manualmente el stock | HU-04 | RF-STK-06, 07, 13, 14, 15 | RN19, RN20 |
| CU-05 | Buscar productos combinando filtros | HU-05 | RF-BUS-01 a 07, 09 a 13 | RN04 |
| CU-06 | Identificar productos con stock bajo o agotado | HU-06 | RF-BUS-08, 14 | — |
| CU-07 | Registrar una venta cobrada | HU-07 | RF-VTA-01 a 09, 11, 12, 14 a 16; RF-STK-16 | RN14, RN22 a RN26 |
| CU-08 | Confirmar una venta con transferencia pendiente | HU-08 | RF-VTA-13, 17 | RN27, RN40 |
| CU-09 | Registrar una venta fiada asociada a una persona | HU-09 | RF-VTA-10; RF-FIA-01 a 03, 07 | RN01, RN06 a RN09, RN12, RN29 |
| CU-10 | Consultar la cuenta corriente de una persona | HU-10 | RF-FIA-04, 05, 06, 08, 09 | RN11, RN28 |
| CU-11 | Modificar los datos de una persona | HU-11 | RF-FIA-10 | RN09, RN10 |
| CU-12 | Registrar un pago de la deuda de una persona | HU-12 | RF-PAG-01 a 08 | RN30, RN31, RN32 |
| CU-13 | Anular una venta | HU-13 | RF-ANU-01 a 06, 09 | RN33 a RN38 |
| CU-14 | Anular una venta fiada con pagos registrados | HU-14 | RF-ANU-07, 08 | RN39 |

### 3.1. Relaciones entre casos de uso

- CU-03 se puede invocar desde CU-01 para asignar cantidades a las variantes recién creadas (extiende).
- CU-06 reutiliza el motor de búsqueda de CU-05 con un objetivo distinto (reposición).
- CU-08 completa a CU-07 cuando el medio de pago es una transferencia no acreditada al momento de la entrega (extiende).
- CU-09 es la variante de CU-07 para ventas fiadas; incluye la identificación de la persona.
- CU-12 requiere una persona con saldo, originado en CU-09.
- CU-14 es la variante de CU-13 para ventas fiadas con pagos registrados (extiende).

---

## CU-01 — Registrar un producto con sus variantes

| Campo | Detalle |
|-------|---------|
| Identificador | CU-01 |
| Nombre | Registrar un producto con sus variantes |
| Descripción | La propietaria da de alta un producto con sus datos generales (nombre, categoría, marca, precio, temporada, grupo) y define sus variantes mediante talle, color, género y estampado, para poder venderlo y controlar su stock. |
| Actores | Principal: Propietaria / Secundario: Ninguno |
| Precondiciones | La propietaria accedió al sistema. Existen cargados los valores de referencia necesarios (categorías, temporadas, talles, géneros, colores y, si corresponde, grupos y estampados). |
| Postcondiciones | Éxito: el producto queda registrado con un código interno único, una única temporada y sus variantes. Fallo: no se registra ningún dato y el producto no existe en el sistema. |

### Secuencia normal

| # | Acción (actor) | Reacción (sistema) |
|---|----------------|--------------------|
| 1 | Elige la opción de registrar un producto nuevo. | Muestra el formulario de producto. |
| 2 | Ingresa nombre, marca y precio vigente. | Valida el formato de los datos ingresados. |
| 3 | Selecciona la categoría, la temporada y, si corresponde, el grupo. | Muestra las opciones cargadas para cada valor de referencia. |
| 4 | Agrega una variante indicando los atributos aplicables: talle, color, género y estampado. | Valida que la combinación de atributos no esté repetida dentro del producto y agrega la variante a la lista. |
| 5 | Repite el paso 4 para cada variante restante. Si el producto no tiene talle, género o color, define una variante única con "No aplica" en ese atributo. | Muestra la lista de variantes definidas. |
| 6 | Solicita guardar el producto. | Valida los datos obligatorios, genera el código interno único y registra el producto con todas sus variantes. |
| 7 | — | Informa que el producto fue registrado, muestra su código y ofrece asignar las cantidades de las variantes (CU-03). |

### Excepciones

| # | Situación | Respuesta del sistema |
|---|-----------|-----------------------|
| E1 | Falta el nombre, la categoría o el precio. | Indica los datos faltantes y no permite confirmar la carga. |
| E2 | El precio no es un valor numérico válido. | Informa el error y solicita corregirlo. |
| E3 | La combinación de atributos de una variante ya fue definida en el mismo producto. | Informa que la variante está duplicada y no la agrega. |
| E4 | Se intenta guardar un producto sin ninguna variante. | Indica que debe definirse al menos una variante (con "No aplica" si corresponde). |
| E5 | La propietaria cancela la carga. | Descarta los datos ingresados sin registrar nada. |
| E6 | Se pierde la conexión al guardar. | Informa que no pudo guardar y no registra datos parciales. |

| Campo | Detalle |
|-------|---------|
| Rendimiento | Guardado ágil desde el celular, sin esperas perceptibles; valor objetivo a definir. |
| Frecuencia | Esporádica, asociada a cada reposición de mercadería y a la puesta en marcha del catálogo. |
| Importancia | Alta: sin productos cargados no hay stock ni ventas. |
| Urgencia | Alta: es la base del sistema. |

---

## CU-02 — Cargar el stock inicial mediante una planilla

| Campo | Detalle |
|-------|---------|
| Identificador | CU-02 |
| Nombre | Cargar el stock inicial mediante una planilla |
| Descripción | La propietaria incorpora de una sola vez el inventario inicial (productos, variantes y cantidades) mediante una planilla con formato definido, que el sistema valida antes de incorporar cualquier dato. |
| Actores | Principal: Propietaria / Secundario: Ninguno |
| Precondiciones | La propietaria accedió al sistema. Existen cargados los valores de referencia (categorías, temporadas, talles, géneros, colores). Dispone de la planilla completada con el formato definido. |
| Postcondiciones | Éxito: todos los productos y variantes de la planilla quedan registrados con su cantidad disponible. Fallo: no se incorpora ningún dato al inventario. |

### Secuencia normal

| # | Acción (actor) | Reacción (sistema) |
|---|----------------|--------------------|
| 1 | Elige la opción de carga inicial de stock. | Muestra el formato definido de la planilla y la opción de cargarla. |
| 2 | Carga la planilla completada. | Valida estructura, valores permitidos, datos obligatorios y variantes repetidas, sin incorporar todavía nada al inventario. |
| 3 | — | Muestra el resultado de la validación: cantidad de productos y variantes detectados, sin errores. |
| 4 | Revisa el resumen y confirma la carga. | Incorpora los productos, las variantes y sus cantidades, y genera el código interno de cada producto. |
| 5 | — | Informa que la carga finalizó e indica que los productos faltantes pueden completarse luego desde la interfaz (CU-01 y CU-03). |

### Excepciones

| # | Situación | Respuesta del sistema |
|---|-----------|-----------------------|
| E1 | La planilla no respeta el formato definido (columnas faltantes o distintas). | Informa que el formato no es válido y no procesa la planilla. |
| E2 | La planilla contiene errores en algunas filas (datos faltantes, valores no permitidos, cantidades inválidas o variantes repetidas). | Muestra la lista de errores indicando fila y motivo, y no incorpora ningún dato. |
| E3 | La planilla está vacía. | Informa que no hay datos para cargar. |
| E4 | La propietaria cancela antes de confirmar. | No incorpora ningún dato al inventario. |
| E5 | Se pierde la conexión durante la incorporación. | Informa el error y no deja datos parciales incorporados. |

| Campo | Detalle |
|-------|---------|
| Rendimiento | Validación e incorporación sin bloqueos prolongados para el volumen de un local pequeño; tiempo a definir. |
| Frecuencia | Una sola vez, al iniciar el uso del sistema. |
| Importancia | Alta: evita cargar cada variante a mano. |
| Urgencia | Alta: es previa a la primera prueba en entorno real. |

---

## CU-03 — Asignar stock a un producto o variante nueva

| Campo | Detalle |
|-------|---------|
| Identificador | CU-03 |
| Nombre | Asignar stock a un producto o variante nueva |
| Descripción | La propietaria asigna por primera vez la cantidad disponible de una variante que no formó parte de la carga inicial, o agrega variantes faltantes a un producto ya cargado, sin afectar las variantes que ya tienen stock. |
| Actores | Principal: Propietaria / Secundario: Ninguno |
| Precondiciones | La propietaria accedió al sistema. El producto existe y está activo. |
| Postcondiciones | Éxito: la variante queda con su cantidad disponible, sin registrarse como corrección. Fallo: las cantidades existentes no se modifican. |

### Secuencia normal

| # | Acción (actor) | Reacción (sistema) |
|---|----------------|--------------------|
| 1 | Selecciona el producto (desde el resultado de una búsqueda o al finalizar CU-01). | Muestra sus variantes con la cantidad actual, indicando las que no tienen cantidad asignada. |
| 2 | Si falta una variante, elige agregar una nueva e indica sus atributos de talle, color, género y estampado. | Valida que la combinación no esté repetida y agrega la variante sin cantidad. |
| 3 | Ingresa la cantidad disponible de cada variante sin cantidad asignada. | Valida que cada cantidad sea un número entero mayor o igual a cero. |
| 4 | Confirma la asignación. | Registra las cantidades sin solicitar motivo, ya que no se modifica un valor anterior, y deja intactas las variantes que ya tenían stock. |
| 5 | — | Muestra el stock actualizado del producto. |

### Excepciones

| # | Situación | Respuesta del sistema |
|---|-----------|-----------------------|
| E1 | La cantidad es negativa, decimal o no numérica. | Informa el error y solicita corregirla. |
| E2 | La variante ya tiene una cantidad asignada. | Informa que para modificarla debe realizarse una corrección de stock (CU-04). |
| E3 | La nueva variante repite la combinación de atributos de otra existente. | Informa que la variante ya existe y no la agrega. |
| E4 | La propietaria cancela antes de confirmar. | No modifica ninguna cantidad. |
| E5 | Se pierde la conexión al confirmar. | Informa que no pudo guardar y no registra datos parciales. |

| Campo | Detalle |
|-------|---------|
| Rendimiento | Respuesta ágil desde el celular; valor objetivo a definir. |
| Frecuencia | Cada vez que ingresa mercadería nueva o se detectan variantes sin cargar. |
| Importancia | Alta: mantiene el stock completo sin depender solo de la planilla inicial. |
| Urgencia | Alta. |

---

## CU-04 — Corregir manualmente el stock

| Campo | Detalle |
|-------|---------|
| Identificador | CU-04 |
| Nombre | Corregir manualmente el stock |
| Descripción | La propietaria corrige la cantidad disponible de una variante cuando detecta una diferencia con la mercadería física, indicando un motivo. El sistema conserva un historial de cada corrección. |
| Actores | Principal: Propietaria / Secundario: Ninguno |
| Precondiciones | La propietaria accedió al sistema. La variante existe y ya tiene una cantidad asignada. |
| Postcondiciones | Éxito: la variante queda con la nueva cantidad y se registra en el historial la fecha, la variante, la cantidad anterior, la cantidad nueva y el motivo. Fallo: la cantidad de la variante no cambia y no se registra ninguna corrección. |

### Secuencia normal

| # | Acción (actor) | Reacción (sistema) |
|---|----------------|--------------------|
| 1 | Selecciona la variante a corregir (desde una búsqueda). | Muestra la identificación del producto y de la variante, y su cantidad actual. |
| 2 | Elige la opción de corregir cantidad e ingresa la cantidad real. | Valida que sea un número entero mayor o igual a cero. |
| 3 | — | Solicita seleccionar un motivo de una lista de opciones simples. |
| 4 | Selecciona el motivo. | Muestra un resumen con la cantidad anterior, la nueva y el motivo, y solicita confirmación. |
| 5 | Confirma la corrección. | Actualiza la cantidad de la variante y registra la corrección en el historial. |
| 6 | — | Informa que el stock fue actualizado y muestra la nueva cantidad. |

### Excepciones

| # | Situación | Respuesta del sistema |
|---|-----------|-----------------------|
| E1 | La cantidad ingresada es negativa, decimal o no numérica. | Informa el error y no permite continuar. |
| E2 | No se selecciona un motivo. | No permite confirmar la corrección. |
| E3 | La cantidad ingresada es igual a la actual. | Informa que no hay cambios y no registra una corrección. |
| E4 | La variante no tiene una cantidad asignada previamente. | Indica que debe asignarse el stock por primera vez (CU-03). |
| E5 | La propietaria cancela antes de confirmar. | Mantiene la cantidad original sin registrar nada. |
| E6 | Se pierde la conexión al confirmar. | Informa que no pudo guardar; no modifica la cantidad ni el historial. |

| Campo | Detalle |
|-------|---------|
| Rendimiento | Respuesta ágil desde el celular; valor objetivo a definir. |
| Frecuencia | Ocasional, cuando se detectan diferencias físicas (por ejemplo, al revisar el local antes de una compra). |
| Importancia | Alta: sostiene la confiabilidad del stock, objetivo central del proyecto. |
| Urgencia | Alta. |

---

## CU-05 — Buscar productos combinando filtros

| Campo | Detalle |
|-------|---------|
| Identificador | CU-05 |
| Nombre | Buscar productos combinando filtros |
| Descripción | La propietaria consulta el stock buscando por nombre, código, marca o categoría y combinando filtros (grupo, género, talle, color, temporada, disponibilidad) para responder consultas de clientes por WhatsApp o Instagram y para verificar si ya posee un producto antes de comprarlo. |
| Actores | Principal: Propietaria / Secundario: Ninguno |
| Precondiciones | La propietaria accedió al sistema desde un dispositivo con conexión a internet, dentro o fuera del local. |
| Postcondiciones | Éxito: el sistema muestra los productos y variantes que cumplen todos los criterios ingresados. Fallo: no se muestran resultados y no se modifican datos. |

### Secuencia normal

| # | Acción (actor) | Reacción (sistema) |
|---|----------------|--------------------|
| 1 | Abre el buscador de productos. | Muestra los criterios disponibles: nombre, código interno, marca, categoría, grupo, género, talle, color, temporada, disponibilidad e inclusión de inactivos. |
| 2 | Completa al menos un criterio (por ejemplo, solo la categoría "body") y, si lo necesita, agrega otros. | Aplica únicamente los criterios completados. |
| 3 | Solicita buscar. | Busca los productos que cumplen todos los criterios ingresados, admite coincidencias parciales en el nombre y oculta los productos inactivos salvo que se haya pedido incluirlos. |
| 4 | — | Muestra los resultados con nombre, marca, temporada, variantes, cantidad disponible de cada variante y precio vigente. |
| 5 | Consulta los resultados y, si lo desea, ajusta los filtros. | Actualiza los resultados según los nuevos criterios. |

### Excepciones

| # | Situación | Respuesta del sistema |
|---|-----------|-----------------------|
| E1 | No se completó ningún criterio. | Indica que debe ingresarse al menos un criterio. |
| E2 | Ningún producto cumple los criterios. | Informa que no se encontraron coincidencias. |
| E3 | Se pierde la conexión durante la consulta. | Informa que no se pudo realizar la búsqueda y permite reintentar. |

| Campo | Detalle |
|-------|---------|
| Rendimiento | Resultados en pocos segundos desde el celular, para poder responder a una clienta sin demora; valor objetivo a definir. |
| Frecuencia | Alta: cada consulta de disponibilidad de una clienta y cada evaluación de compra a un proveedor. |
| Importancia | Alta: resuelve el problema principal relevado. |
| Urgencia | Alta. |

---

## CU-06 — Identificar productos con stock bajo o agotado

| Campo | Detalle |
|-------|---------|
| Identificador | CU-06 |
| Nombre | Identificar productos con stock bajo o agotado |
| Descripción | La propietaria filtra por disponibilidad y ordena los resultados de menor a mayor cantidad, solos o combinados con otros filtros, para decidir qué reponer cuando dispone de dinero para comprar a sus proveedores. Reutiliza el motor de búsqueda de CU-05. |
| Actores | Principal: Propietaria / Secundario: Ninguno |
| Precondiciones | La propietaria accedió al sistema. Existen productos cargados. |
| Postcondiciones | Éxito: el sistema muestra los productos filtrados y ordenados por menor cantidad disponible. Fallo: no se muestran resultados y no se modifican datos. |

### Secuencia normal

| # | Acción (actor) | Reacción (sistema) |
|---|----------------|--------------------|
| 1 | Abre el buscador de productos. | Muestra los criterios de búsqueda (CU-05). |
| 2 | Selecciona el filtro de disponibilidad "Agotados" o "Disponibles" y, si lo necesita, otros filtros como la categoría. | Registra los criterios seleccionados. |
| 3 | Elige ordenar los resultados de menor a mayor cantidad disponible. | Busca con todos los criterios a la vez y muestra los resultados ordenados. |
| 4 | Revisa el listado. | Presenta primero las variantes agotadas o con menor cantidad, para identificar visualmente el stock bajo. |

### Excepciones

| # | Situación | Respuesta del sistema |
|---|-----------|-----------------------|
| E1 | Ningún producto cumple los criterios (por ejemplo, no hay productos agotados en la categoría elegida). | Informa que no se encontraron coincidencias. |
| E2 | Se pierde la conexión durante la consulta. | Informa que no se pudo realizar la búsqueda y permite reintentar. |

| Campo | Detalle |
|-------|---------|
| Rendimiento | Resultados en pocos segundos; valor objetivo a definir. |
| Frecuencia | Baja a media: cada ciclo de reposición, cuando la propietaria junta el dinero para comprar. |
| Importancia | Media: reemplaza al módulo de reportes descartado y apoya la decisión de compra. |
| Urgencia | Media. |

---

## CU-07 — Registrar una venta cobrada

| Campo | Detalle |
|-------|---------|
| Identificador | CU-07 |
| Nombre | Registrar una venta cobrada |
| Descripción | La propietaria registra una venta indicando productos, variantes, cantidades, precio, descuento opcional y uno o más medios de pago. El sistema calcula el total y descuenta el stock automáticamente. |
| Actores | Principal: Propietaria / Secundario: Ninguno |
| Precondiciones | La propietaria accedió al sistema. Existen productos activos con stock disponible. |
| Postcondiciones | Éxito: la venta queda registrada con fecha actual, detalle completo, precios aplicados y medios de pago, sin asociarse a un nombre de cliente, y el stock de cada variante disminuye. Fallo: no se registra la venta y el stock no cambia. |

### Secuencia normal

| # | Acción (actor) | Reacción (sistema) |
|---|----------------|--------------------|
| 1 | Elige la opción de registrar una venta. | Muestra una venta nueva con la fecha actual. |
| 2 | Busca y selecciona un producto y una variante. | Muestra el precio vigente y la cantidad disponible de la variante. |
| 3 | Indica la cantidad vendida. | Valida que no supere la cantidad disponible, agrega el ítem y calcula el subtotal. |
| 4 | Repite los pasos 2 y 3 para cada producto o variante adicional. | Actualiza el subtotal con cada ítem agregado. |
| 5 | Si lo decide, modifica manualmente el precio aplicado de un ítem. | Recalcula el subtotal con el precio indicado, sin alterar el precio vigente del producto. |
| 6 | Si lo decide, ingresa un descuento expresado como porcentaje. | Muestra el subtotal, el porcentaje de descuento y el total final. |
| 7 | Selecciona uno o más medios de pago (efectivo, transferencia o tarjeta de débito) e indica el importe de cada uno. | Valida que los importes cubran el total final. |
| 8 | Confirma la venta. | Registra la venta con la fecha actual, el detalle, los precios aplicados, el descuento, el total y los medios de pago. Descuenta del stock las cantidades vendidas. |
| 9 | — | Informa que la venta fue registrada. |

### Excepciones

| # | Situación | Respuesta del sistema |
|---|-----------|-----------------------|
| E1 | La cantidad solicitada de una variante supera su cantidad disponible. | Informa la cantidad disponible y no permite agregar ni confirmar ese ítem. |
| E2 | Se intenta confirmar una venta sin ítems. | Indica que debe agregarse al menos un producto. |
| E3 | El precio aplicado no es un valor numérico válido. | Informa el error y solicita corregirlo. |
| E4 | El porcentaje de descuento es negativo o mayor que 100. | Informa el error y no aplica el descuento. |
| E5 | No se selecciona ningún medio de pago, o los importes no cubren el total final. | No permite confirmar hasta que los importes coincidan con el total. |
| E6 | El pago es por transferencia y todavía no está acreditado al momento de entregar la mercadería. | Permite registrar la venta como "pendiente de confirmación": descuenta el stock y no la considera cobrada hasta su confirmación (CU-08). |
| E7 | La propietaria cancela la venta antes de confirmar. | Descarta la venta sin modificar el stock. |
| E8 | Se pierde la conexión al confirmar. | Informa que no pudo registrar la venta y no descuenta stock ni deja datos parciales. |

| Campo | Detalle |
|-------|---------|
| Rendimiento | Registro ágil mientras la clienta está presente; valor objetivo a definir. |
| Frecuencia | Media: ventas de bajo volumen diario, con días sin ventas. |
| Importancia | Alta: controla las ventas y mantiene el stock actualizado. |
| Urgencia | Media: se implementa luego de la consulta y administración básica de stock. |

---

## CU-08 — Confirmar una venta con transferencia pendiente

| Campo | Detalle |
|-------|---------|
| Identificador | CU-08 |
| Nombre | Confirmar una venta con transferencia pendiente |
| Descripción | La propietaria marca como confirmada una venta ya entregada cuyo pago por transferencia estaba pendiente, una vez que el dinero se acreditó. |
| Actores | Principal: Propietaria / Secundario: Ninguno |
| Precondiciones | La propietaria accedió al sistema. Existe una venta en estado "pendiente de confirmación". |
| Postcondiciones | Éxito: la venta pasa a considerarse cobrada, sin modificarse el resto de sus datos. Fallo: la venta continúa pendiente de confirmación. |

### Secuencia normal

| # | Acción (actor) | Reacción (sistema) |
|---|----------------|--------------------|
| 1 | Accede a las ventas pendientes de confirmación. | Muestra el listado de ventas con transferencia pendiente. |
| 2 | Selecciona la venta cuya transferencia fue acreditada. | Muestra el detalle de la venta. |
| 3 | Elige marcarla como confirmada. | Solicita confirmación de la acción. |
| 4 | Confirma. | Cambia el estado de la venta a cobrada sin modificar productos, cantidades, precios, descuento ni importes. |
| 5 | — | Informa que la venta fue confirmada. |

### Excepciones

| # | Situación | Respuesta del sistema |
|---|-----------|-----------------------|
| E1 | No hay ventas pendientes de confirmación. | Informa que no existen ventas pendientes. |
| E2 | La venta ya fue confirmada o fue anulada. | No permite confirmarla e informa su estado actual. |
| E3 | La transferencia no se acredita. | No se ofrece confirmar la venta; la propietaria puede anularla (CU-13), con restitución del stock. |
| E4 | La propietaria cancela la acción. | La venta continúa pendiente de confirmación. |
| E5 | Se pierde la conexión al confirmar. | Informa que no pudo actualizar el estado y la venta continúa pendiente. |

| Campo | Detalle |
|-------|---------|
| Rendimiento | Cambio de estado inmediato; valor objetivo a definir. |
| Frecuencia | Baja: solo ventas entregadas con transferencia sin acreditar. |
| Importancia | Media: evita ventas que queden pendientes para siempre. |
| Urgencia | Media. |

---

## CU-09 — Registrar una venta fiada asociada a una persona

| Campo | Detalle |
|-------|---------|
| Identificador | CU-09 |
| Nombre | Registrar una venta fiada asociada a una persona |
| Descripción | La propietaria registra una venta entregada sin cobro inmediato y la asocia a una persona identificable, buscándola entre las ya registradas o registrándola si es nueva. El sistema descuenta el stock y deja el importe pendiente de cobro en la cuenta corriente de la persona. |
| Actores | Principal: Propietaria / Secundario: Ninguno |
| Precondiciones | La propietaria accedió al sistema. Existen productos activos con stock disponible. |
| Postcondiciones | Éxito: la venta queda registrada como fiada y pendiente de cobro, asociada a una persona; el stock disminuye y el saldo pendiente de la persona aumenta por el total de la venta. Fallo: no se registra la venta, no se asocia ninguna persona nueva y el stock no cambia. |

### Secuencia normal

| # | Acción (actor) | Reacción (sistema) |
|---|----------------|--------------------|
| 1 | Elige registrar una venta y carga los productos, variantes y cantidades; opcionalmente modifica precios y aplica un descuento (pasos 1 a 6 de CU-07). | Valida el stock, calcula el subtotal y el total final. |
| 2 | Selecciona la opción "Fiado". | Muestra el buscador de personas con autocompletado. |
| 3 | Escribe nombre, apellido o teléfono de la persona. | Muestra las coincidencias a medida que escribe. |
| 4 | Selecciona la persona. | Muestra sus datos y su saldo pendiente actual, sin pedir que los cargue de nuevo. |
| 5 | Confirma la venta. | Registra la venta como fiada y pendiente de cobro, con fecha actual y detalle completo, asociada a la persona. Descuenta del stock las cantidades entregadas. |
| 6 | — | Actualiza el saldo pendiente de la persona e informa que la venta fiada fue registrada. |

### Excepciones

| # | Situación | Respuesta del sistema |
|---|-----------|-----------------------|
| E1 | La persona no existe. | Ofrece "Registrar cliente" y solicita nombre, apellido y teléfono, todos obligatorios. Si los datos son válidos, registra a la persona y continúa en el paso 5. |
| E2 | Falta el nombre, el apellido o el teléfono de la nueva persona. | Indica los datos faltantes y no la registra. |
| E3 | El teléfono ingresado ya pertenece a una persona registrada. | Informa la coincidencia y ofrece seleccionar a esa persona en lugar de crear un duplicado. |
| E4 | No se selecciona ninguna persona. | No permite confirmar la venta fiada. |
| E5 | La persona ya tiene saldo pendiente. | Permite registrar la nueva venta fiada y acumula el importe en su cuenta corriente. |
| E6 | La cantidad solicitada supera el stock disponible, o los datos de la venta son inválidos. | Aplica las mismas validaciones que CU-07 (E1 a E4) y no permite confirmar. |
| E7 | La propietaria cancela antes de confirmar. | Descarta la venta sin modificar stock ni cuenta corriente. |
| E8 | Se pierde la conexión al confirmar. | Informa que no pudo registrar la venta; no descuenta stock ni deja datos parciales. |

| Campo | Detalle |
|-------|---------|
| Rendimiento | Búsqueda con autocompletado fluida y registro ágil; valor objetivo a definir. |
| Frecuencia | Baja: el fiado es poco frecuente y solo con clientes de confianza. |
| Importancia | Media: permite llevar el registro de quién debe sin cargar datos repetidos. |
| Urgencia | Media a baja: se implementa después de las ventas cobradas. |

---

## CU-10 — Consultar la cuenta corriente de una persona

| Campo | Detalle |
|-------|---------|
| Identificador | CU-10 |
| Nombre | Consultar la cuenta corriente de una persona |
| Descripción | La propietaria consulta el historial completo de ventas fiadas y pagos de una persona, junto con su saldo pendiente acumulado. |
| Actores | Principal: Propietaria / Secundario: Ninguno |
| Precondiciones | La propietaria accedió al sistema. La persona está registrada. |
| Postcondiciones | Éxito: el sistema muestra el historial y el saldo actualizado de la persona. Fallo: no se muestra información y no se modifican datos. |

### Secuencia normal

| # | Acción (actor) | Reacción (sistema) |
|---|----------------|--------------------|
| 1 | Elige consultar cuentas corrientes y busca a la persona por nombre, apellido o teléfono. | Muestra las coincidencias. |
| 2 | Selecciona la persona. | Muestra sus datos, su saldo pendiente acumulado y el historial completo de ventas fiadas y pagos. |
| 3 | Si lo desea, selecciona una venta fiada del historial. | Muestra el detalle de la venta y su estado de cobro. |

### Excepciones

| # | Situación | Respuesta del sistema |
|---|-----------|-----------------------|
| E1 | No hay personas que coincidan con la búsqueda. | Informa que no se encontraron coincidencias. |
| E2 | La persona tiene saldo cero. | Muestra igualmente el historial completo, con saldo cero. |
| E3 | La persona tiene varias ventas fiadas pendientes. | Las muestra todas juntas dentro de su única cuenta corriente. |
| E4 | Se pierde la conexión durante la consulta. | Informa que no se pudo obtener la información y permite reintentar. |

| Campo | Detalle |
|-------|---------|
| Rendimiento | Resultados en pocos segundos; valor objetivo a definir. |
| Frecuencia | Baja: ante un cobro o para saber cuánto debe una persona. |
| Importancia | Media: permite saber cuánto se debe y decidir cómo proceder. |
| Urgencia | Media a baja. |

---

## CU-11 — Modificar los datos de una persona

| Campo | Detalle |
|-------|---------|
| Identificador | CU-11 |
| Nombre | Modificar los datos de una persona |
| Descripción | La propietaria corrige o actualiza el nombre, el apellido o el teléfono de una persona registrada, sin alterar su historial de ventas fiadas y pagos. |
| Actores | Principal: Propietaria / Secundario: Ninguno |
| Precondiciones | La propietaria accedió al sistema. La persona está registrada. |
| Postcondiciones | Éxito: la persona queda con los datos nuevos y su historial permanece sin cambios. Fallo: los datos anteriores se mantienen. |

### Secuencia normal

| # | Acción (actor) | Reacción (sistema) |
|---|----------------|--------------------|
| 1 | Busca y selecciona a la persona. | Muestra sus datos actuales. |
| 2 | Elige editar sus datos y modifica nombre, apellido o teléfono. | Valida que los tres datos estén completos y que el teléfono no pertenezca a otra persona. |
| 3 | Confirma los cambios. | Guarda los nuevos datos sin modificar ventas fiadas ni pagos históricos. |
| 4 | — | Informa que los datos fueron actualizados. |

### Excepciones

| # | Situación | Respuesta del sistema |
|---|-----------|-----------------------|
| E1 | Se deja vacío el nombre, el apellido o el teléfono. | Indica el dato faltante y no guarda los cambios. |
| E2 | El teléfono ingresado ya pertenece a otra persona. | Informa la coincidencia y no guarda los cambios. |
| E3 | La propietaria cancela la edición. | Mantiene los datos anteriores. |
| E4 | Se pierde la conexión al guardar. | Informa que no pudo guardar y mantiene los datos anteriores. |

| Campo | Detalle |
|-------|---------|
| Rendimiento | Guardado inmediato; valor objetivo a definir. |
| Frecuencia | Muy baja: ante errores de carga o cambios de contacto. |
| Importancia | Baja: evita errores de contacto que compliquen reclamar una deuda. |
| Urgencia | Baja. |

---

## CU-12 — Registrar un pago de la deuda de una persona

| Campo | Detalle |
|-------|---------|
| Identificador | CU-12 |
| Nombre | Registrar un pago de la deuda de una persona |
| Descripción | La propietaria registra un pago parcial o total de la deuda de una persona. El sistema lo aplica a la deuda total comenzando por las ventas fiadas más antiguas y actualiza el saldo. |
| Actores | Principal: Propietaria / Secundario: Ninguno |
| Precondiciones | La propietaria accedió al sistema. La persona está registrada y tiene saldo pendiente mayor a cero. |
| Postcondiciones | Éxito: el pago queda registrado con fecha actual, importe y medio de pago; se aplica a las ventas más antiguas, el saldo disminuye y las ventas totalmente pagadas se consideran canceladas. Fallo: no se registra el pago y el saldo no cambia. |

### Secuencia normal

| # | Acción (actor) | Reacción (sistema) |
|---|----------------|--------------------|
| 1 | Busca y selecciona a la persona. | Muestra su saldo pendiente y sus ventas fiadas pendientes. |
| 2 | Elige registrar un pago e indica el importe. | Valida que sea mayor a cero y no supere el saldo pendiente. |
| 3 | Selecciona el medio de pago (efectivo, transferencia o tarjeta de débito). | Registra la selección. |
| 4 | Confirma el pago. | Registra el pago con la fecha actual y lo aplica a la deuda total, comenzando por las ventas fiadas más antiguas. |
| 5 | — | Marca como canceladas las ventas cuyo importe pendiente quedó cubierto y actualiza el saldo. |
| 6 | — | Muestra el nuevo saldo pendiente y confirma el registro del pago. |

### Excepciones

| # | Situación | Respuesta del sistema |
|---|-----------|-----------------------|
| E1 | El importe es mayor al saldo pendiente. | No permite registrar el pago e informa el saldo pendiente. |
| E2 | El importe es cero, negativo o no numérico. | Informa el error y solicita corregirlo. |
| E3 | No se selecciona el medio de pago. | No permite confirmar el pago. |
| E4 | La persona no tiene saldo pendiente. | Informa que no hay deuda y no permite registrar el pago. |
| E5 | La propietaria cancela antes de confirmar. | No registra el pago. |
| E6 | Se pierde la conexión al confirmar. | Informa que no pudo registrar el pago y no modifica el saldo. |

| Campo | Detalle |
|-------|---------|
| Rendimiento | Registro y actualización del saldo inmediatos; valor objetivo a definir. |
| Frecuencia | Baja: cada vez que una persona abona parte o la totalidad de su deuda. |
| Importancia | Media a alta: cierra el ciclo de la venta fiada y es la única forma de bajar el saldo. |
| Urgencia | Media a baja. |

---

## CU-13 — Anular una venta

| Campo | Detalle |
|-------|---------|
| Identificador | CU-13 |
| Nombre | Anular una venta |
| Descripción | La propietaria anula una venta ya registrada indicando un motivo, para corregir errores sin perder la trazabilidad. El sistema restituye el stock y excluye la venta de las ventas válidas. |
| Actores | Principal: Propietaria / Secundario: Ninguno |
| Precondiciones | La propietaria accedió al sistema. La venta está registrada y no fue anulada. Si es una venta fiada, no tiene pagos registrados (en ese caso corresponde CU-14). |
| Postcondiciones | Éxito: la venta queda anulada conservando su detalle, motivo y fecha de anulación; se restituye el stock de las variantes; se excluye de las ventas válidas; y, si era fiada sin pagos, su importe se descuenta de la deuda de la persona. Fallo: la venta continúa vigente y no se modifica el stock. |

### Secuencia normal

| # | Acción (actor) | Reacción (sistema) |
|---|----------------|--------------------|
| 1 | Accede a las ventas registradas y selecciona la venta a anular, sin límite de tiempo desde su registro. | Muestra el detalle de la venta y su estado. |
| 2 | Elige la opción de anular. | Solicita seleccionar un motivo de una lista de opciones simples. |
| 3 | Selecciona el motivo. | Muestra un resumen de los efectos: restitución del stock, exclusión de las ventas válidas y, si corresponde, descuento de la deuda. Solicita confirmación. |
| 4 | Confirma la anulación. | Marca la venta como anulada, conserva su detalle junto con el motivo y la fecha de anulación, restituye al stock las cantidades de las variantes vendidas y la excluye del total de ventas válidas. |
| 5 | — | Si la venta era fiada y no tiene pagos, descuenta su importe de la deuda de la persona. |
| 6 | — | Informa que la venta fue anulada. |

### Excepciones

| # | Situación | Respuesta del sistema |
|---|-----------|-----------------------|
| E1 | La venta ya está anulada. | No permite anularla de nuevo e informa su estado. |
| E2 | No se selecciona un motivo. | No permite confirmar la anulación. |
| E3 | La venta es fiada y tiene pagos registrados. | Advierte la situación y deriva al procedimiento de CU-14. |
| E4 | La venta está pendiente de confirmación de transferencia. | Permite anularla (por ejemplo, si el pago nunca se acredita) y restituye el stock. |
| E5 | La propietaria cancela antes de confirmar. | La venta continúa vigente sin cambios. |
| E6 | Se pierde la conexión al confirmar. | Informa que no pudo anular; la venta, el stock y la deuda no se modifican. |

| Campo | Detalle |
|-------|---------|
| Rendimiento | Anulación y restitución de stock inmediatas; valor objetivo a definir. |
| Frecuencia | Muy baja: ante errores de registro o devoluciones. |
| Importancia | Media: permite corregir errores sin perder trazabilidad. |
| Urgencia | Media a baja. |

---

## CU-14 — Anular una venta fiada con pagos registrados

| Campo | Detalle |
|-------|---------|
| Identificador | CU-14 |
| Nombre | Anular una venta fiada con pagos registrados |
| Descripción | La propietaria anula una venta fiada que ya tiene pagos registrados. El sistema la advierte y registra un ajuste separado, sin modificar el importe original de la venta ni los pagos ya recibidos. |
| Actores | Principal: Propietaria / Secundario: Ninguno |
| Precondiciones | La propietaria accedió al sistema. La venta fiada está registrada, no fue anulada y tiene al menos un pago aplicado. |
| Postcondiciones | Éxito: la venta queda anulada con su motivo y fecha; se restituye el stock; se excluye de las ventas válidas; se registra un ajuste separado en la cuenta corriente; y ni el importe original de la venta ni los pagos recibidos se modifican. Fallo: la venta y la cuenta corriente permanecen sin cambios. |

### Secuencia normal

| # | Acción (actor) | Reacción (sistema) |
|---|----------------|--------------------|
| 1 | Selecciona la venta fiada a anular y elige anular. | Detecta que la venta tiene pagos registrados y muestra una advertencia con el detalle de los pagos recibidos. |
| 2 | Acepta continuar con la anulación. | Solicita seleccionar un motivo de una lista de opciones simples. |
| 3 | Selecciona el motivo. | Muestra el resumen de efectos: restitución del stock y registro de un ajuste separado en la cuenta corriente. Solicita confirmación. |
| 4 | Confirma la anulación. | Marca la venta como anulada con su motivo y fecha, restituye el stock y la excluye de las ventas válidas. |
| 5 | — | Registra un ajuste separado, sin modificar el importe original de la venta ni los pagos ya recibidos, y actualiza el saldo de la persona. |
| 6 | — | Informa que la venta fue anulada y muestra la cuenta corriente actualizada. |

### Excepciones

| # | Situación | Respuesta del sistema |
|---|-----------|-----------------------|
| E1 | La venta ya está anulada. | No permite anularla de nuevo e informa su estado. |
| E2 | La propietaria no acepta la advertencia. | Cancela la anulación y la venta continúa vigente. |
| E3 | No se selecciona un motivo. | No permite confirmar la anulación. |
| E4 | La venta fiada no tiene pagos registrados. | Indica que corresponde la anulación general (CU-13). |
| E5 | Se pierde la conexión al confirmar. | Informa que no pudo anular; no modifica la venta, el stock ni la cuenta corriente. |

| Campo | Detalle |
|-------|---------|
| Rendimiento | Anulación y registro del ajuste inmediatos; valor objetivo a definir. |
| Frecuencia | Excepcional: combina fiado, pagos parciales y un error posterior. |
| Importancia | Baja a media: protege la integridad del historial de pagos. |
| Urgencia | Baja. |