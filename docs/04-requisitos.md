# Requisitos del sistema

## 1. Descripción del sistema

Dulce Espera necesita una herramienta interna para administrar y consultar el
stock de indumentaria y accesorios infantiles. El sistema permitirá a la
propietaria consultar rápidamente la disponibilidad desde el celular, tanto
dentro como fuera del local, responder consultas de clientes y verificar la
existencia de productos antes de decidir nuevas compras.

La solución será utilizada inicialmente por una única usuaria y requerirá
conexión a internet. No será una tienda online ni incluirá integración
automática con WhatsApp o Instagram.

Este documento utiliza una adaptación de la estructura de una SRS basada en
IEEE 830. El alcance, el relevamiento y las reglas de negocio se mantienen en
documentos separados; aquí se especifica el comportamiento que deberá ofrecer
el sistema.

### 1.1. Referencias

- [`01-alcance.md`](./01-alcance.md): límites, objetivos y funcionalidades del MVP.
- [`03-relevamiento.md`](./03-relevamiento.md): necesidades y contexto operativo.
- [`05-reglas-de-negocio.md`](./05-reglas-de-negocio.md): reglas que condicionan estos requisitos.

## 2. Requisitos funcionales

Los requisitos se expresan con la fórmula "El sistema deberá" para que puedan
ser verificados posteriormente mediante casos de prueba o casos de uso.

### Módulo CAT — Catálogo y productos

| ID | Requisito |
|----|-----------|
| RF-CAT-01 | El sistema deberá permitir registrar un producto asociado a una categoría. |
| RF-CAT-02 | El sistema deberá permitir registrar la marca del producto. |
| RF-CAT-03 | El sistema deberá generar automáticamente un código interno único para cada producto. |
| RF-CAT-04 | El sistema deberá permitir registrar el nombre del producto. |
| RF-CAT-05 | El sistema deberá permitir asociar una única temporada al producto. |
| RF-CAT-06 | El sistema deberá permitir asociar un grupo comercial al producto cuando corresponda. |
| RF-CAT-07 | El sistema deberá permitir registrar un precio vigente para el producto. |
| RF-CAT-08 | El sistema deberá permitir crear múltiples variantes para un mismo producto. |
| RF-CAT-09 | El sistema deberá permitir definir para cada variante los atributos aplicables de talle, color, género y estampado. |
| RF-CAT-10 | Cuando un atributo no corresponda a una categoría, el sistema deberá permitir registrarlo como "No aplica" dentro de la variante única del producto. |
| RF-CAT-11 | El sistema deberá permitir modificar los datos actuales de un producto, incluido su precio vigente. |
| RF-CAT-12 | El sistema deberá permitir marcar un producto como inactivo sin eliminarlo ni alterar su historial. |
| RF-CAT-13 | El sistema deberá permitir administrar categorías, grupos, talles, géneros, colores, temporadas y estampados desde un apartado específico. |
| RF-CAT-14 | El sistema deberá permitir buscar productos por nombre, código interno, marca y categoría. |

### Módulo STK — Stock y variantes

| ID | Requisito |
|----|-----------|
| RF-STK-01 | El sistema deberá permitir cargar el stock inicial de los productos y sus variantes. |
| RF-STK-02 | El sistema deberá permitir completar posteriormente la carga de productos o variantes que no hayan sido registrados inicialmente. |
| RF-STK-03 | El sistema deberá permitir registrar una cantidad disponible para cada variante. |
| RF-STK-04 | El sistema deberá identificar una variante mediante la combinación de los atributos aplicables a su producto: talle, color, género y estampado. |
| RF-STK-05 | El sistema deberá conservar una variante con cantidad cero para que pueda ser consultada como agotada. |
| RF-STK-06 | El sistema deberá permitir corregir manualmente la cantidad disponible de una variante cuando existan diferencias con el stock físico. |
| RF-STK-07 | El sistema deberá impedir que la cantidad disponible de una variante sea inferior a cero. |
| RF-STK-08 | El sistema deberá mostrar la cantidad disponible junto con la identificación del producto y de la variante. |
| RF-STK-09 | El sistema deberá mantener asociada la temporada del producto a todas sus variantes, sin permitir temporadas diferentes dentro del mismo producto. |
| RF-STK-10 | El sistema deberá permitir importar el stock inicial mediante una planilla con formato definido. |
| RF-STK-11 | El sistema deberá validar la planilla de carga inicial e informar los errores antes de incorporar sus datos al inventario. |
| RF-STK-12 | El sistema deberá permitir completar o corregir productos y variantes posteriormente desde la interfaz. |
| RF-STK-13 | El sistema deberá solicitar un motivo obligatorio al realizar una corrección manual de stock mediante opciones simples. |
| RF-STK-14 | El sistema deberá conservar un historial de las correcciones manuales de stock. |
| RF-STK-15 | El historial de correcciones deberá registrar como mínimo la fecha, la variante, la cantidad anterior, la cantidad nueva y el motivo seleccionado. |
| RF-STK-16 | El sistema no deberá permitir confirmar una venta cuando la cantidad solicitada de una variante sea superior a su cantidad disponible. |

### Módulo BUS — Búsqueda y consulta

| ID | Requisito |
|----|-----------|
| RF-BUS-01 | El sistema deberá permitir buscar productos utilizando al menos un criterio de búsqueda. |
| RF-BUS-02 | El sistema deberá permitir buscar por nombre, código interno, marca, categoría y características de la variante. |
| RF-BUS-03 | El sistema deberá permitir iniciar una búsqueda utilizando únicamente una categoría, únicamente un nombre o una combinación de ambos. |
| RF-BUS-04 | El sistema deberá permitir combinar los filtros de categoría, grupo, género, talle, color, temporada y disponibilidad. |
| RF-BUS-05 | El sistema deberá aplicar únicamente los filtros que la propietaria haya completado o seleccionado. |
| RF-BUS-06 | El sistema deberá combinar los filtros seleccionados mediante una condición que exija cumplir todos los criterios ingresados. |
| RF-BUS-07 | El sistema deberá informar que no se encontraron coincidencias cuando ningún producto cumpla los criterios seleccionados. |
| RF-BUS-08 | El sistema deberá permitir filtrar los resultados por `Disponibles`, `Agotados` y `Todos`. |
| RF-BUS-09 | El sistema deberá ocultar los productos inactivos en las búsquedas normales. |
| RF-BUS-10 | El sistema deberá permitir incluir productos inactivos mediante un filtro específico. |
| RF-BUS-11 | El sistema deberá admitir coincidencias parciales al buscar por nombre. |
| RF-BUS-12 | El sistema deberá mostrar el precio vigente junto con la información del producto. |
| RF-BUS-13 | El sistema deberá mostrar la marca, temporada, variantes y cantidad disponible de los productos encontrados. |

### Módulo VTA — Registro de ventas

| ID | Requisito |
|----|-----------|
| RF-VTA-01 | El sistema deberá permitir registrar una venta seleccionando uno o más productos y sus variantes. |
| RF-VTA-02 | El sistema deberá permitir indicar la cantidad vendida para cada variante seleccionada. |
| RF-VTA-03 | El sistema deberá mostrar el precio vigente del producto al preparar la venta. |
| RF-VTA-04 | El sistema deberá permitir modificar manualmente el precio aplicado a un producto durante la venta cuando la propietaria lo decida. |
| RF-VTA-05 | El sistema deberá conservar en la venta el precio aplicado al momento de confirmarla, aunque luego se modifique el precio vigente del producto. |
| RF-VTA-06 | El sistema deberá calcular el importe total a partir de los productos, cantidades y precios aplicados. |
| RF-VTA-07 | El sistema deberá permitir aplicar un descuento expresado como porcentaje antes de confirmar la venta. |
| RF-VTA-08 | El sistema deberá mostrar el subtotal, el porcentaje de descuento aplicado y el total final. |
| RF-VTA-09 | El sistema deberá registrar la venta utilizando automáticamente la fecha actual. |
| RF-VTA-10 | El sistema deberá permitir registrar una venta cobrada o una venta fiada. |
| RF-VTA-11 | El sistema deberá permitir registrar pagos mediante efectivo, transferencia o tarjeta de débito. |
| RF-VTA-12 | El sistema deberá permitir registrar una venta utilizando más de un medio de pago. |
| RF-VTA-13 | El sistema deberá permitir registrar una venta entregada cuyo pago por transferencia se encuentre pendiente de confirmación. |
| RF-VTA-14 | El sistema deberá descontar automáticamente del stock las cantidades vendidas al confirmar la entrega de la mercadería. |
| RF-VTA-15 | El sistema deberá conservar el detalle de productos, variantes, cantidades, precios, descuento e importe total de cada venta. |
| RF-VTA-16 | El sistema no deberá registrar el nombre de un cliente en las ventas normales en el MVP. |

### Módulo FIA — Ventas fiadas y cuenta corriente

| ID | Requisito |
|----|-----------|
| RF-FIA-01 | El sistema deberá permitir asociar cada venta fiada a una persona identificable. |
| RF-FIA-02 | El sistema deberá permitir buscar y reutilizar una persona registrada mediante nombre, apellido o número de teléfono. |
| RF-FIA-03 | El sistema deberá permitir registrar una nueva persona para una venta fiada indicando nombre, apellido y número de teléfono. |
| RF-FIA-04 | El sistema deberá permitir que una persona tenga varias ventas fiadas pendientes. |
| RF-FIA-05 | El sistema deberá mostrar el historial completo de ventas fiadas y pagos de una persona. |
| RF-FIA-06 | El sistema deberá calcular y mostrar el saldo pendiente acumulado de una persona. |
| RF-FIA-07 | El sistema deberá permitir registrar nuevas ventas fiadas para una persona aunque tenga saldo pendiente. |
| RF-FIA-08 | El sistema deberá actualizar automáticamente el saldo después de registrar una nueva venta fiada o un pago. |
| RF-FIA-09 | El sistema deberá conservar el historial completo de una persona aunque su saldo pendiente llegue a cero. |
| RF-FIA-10 | El sistema deberá permitir modificar los datos personales de una persona sin alterar sus ventas ni pagos históricos. |

### Módulo PAG — Pagos de ventas fiadas

| ID | Requisito |
|----|-----------|
| RF-PAG-01 | El sistema deberá permitir registrar pagos parciales o totales de la deuda de una persona. |
| RF-PAG-02 | El sistema deberá registrar la fecha actual, el importe y el medio de pago de cada pago. |
| RF-PAG-03 | El sistema deberá permitir registrar pagos mediante efectivo, transferencia o tarjeta de débito. |
| RF-PAG-04 | El sistema deberá aplicar cada pago a la deuda total de la persona comenzando por las ventas fiadas más antiguas. |
| RF-PAG-05 | El sistema deberá actualizar automáticamente el saldo pendiente después de registrar un pago. |
| RF-PAG-06 | El sistema no deberá permitir registrar un pago superior al saldo pendiente de la persona. |
| RF-PAG-07 | El sistema deberá considerar una venta fiada como cancelada cuando el total de sus pagos aplicados alcance su importe pendiente. |
| RF-PAG-08 | El sistema deberá contabilizar como cobrado únicamente el importe efectivamente registrado mediante pagos. |

## 3. Requisitos no funcionales

Los siguientes requisitos surgen del alcance aprobado y del contexto de uso.
Los valores cuantitativos de rendimiento podrán precisarse durante el diseño o
la validación del MVP.

### 3.1. Disponibilidad y conectividad

| ID | Requisito |
|----|-----------|
| RNF-01 | El sistema deberá poder utilizarse desde un celular con conexión a internet mediante wifi o datos móviles. |
| RNF-02 | El sistema no deberá requerir funcionamiento sin conexión para el MVP. |

### 3.2. Usabilidad

| ID | Requisito |
|----|-----------|
| RNF-03 | La interfaz deberá permitir administrar el catálogo y el stock desde un celular. |
| RNF-04 | La administración de categorías, grupos, talles, géneros, colores, temporadas y estampados deberá encontrarse en un apartado separado de la operación cotidiana. |
| RNF-05 | La información de producto, variante y cantidad deberá presentarse de forma clara para facilitar una consulta rápida. |

### 3.3. Integridad y conservación de la información

| ID | Requisito |
|----|-----------|
| RNF-06 | El sistema deberá conservar los productos inactivos y sus datos históricos. |
| RNF-07 | El sistema deberá conservar el precio aplicado en una venta aunque posteriormente se modifique el precio vigente del producto. |

## 4. Decisiones confirmadas y temas pendientes

### 4.1. Decisiones confirmadas

- El precio pertenece al producto y es común a sus variantes.
- La marca forma parte de la identificación del producto.
- La temporada pertenece al producto completo y es común a sus variantes.
- Los productos sin talle, género o color tendrán una variante única con esos atributos como "No aplica".
- Los productos se marcarán como inactivos en lugar de eliminarse.
- La carga inicial del stock se realizará mediante una planilla validada.
- Las correcciones manuales de stock requerirán un motivo seleccionado de una lista de opciones simples.
- Se conservará un historial de las correcciones manuales de stock.
- No se confirmarán ventas cuya cantidad supere el stock disponible.
- La búsqueda deberá aceptar al menos un criterio y permitirá combinar criterios opcionales.
- Los criterios seleccionados se aplicarán conjuntamente y los no seleccionados no restringirán los resultados.
- Los productos inactivos estarán ocultos en la búsqueda normal y podrán incluirse mediante un filtro específico.
- La disponibilidad podrá filtrarse como `Disponibles`, `Agotados` o `Todos`.
- La búsqueda por nombre admitirá coincidencias parciales.
- Los resultados mostrarán el precio vigente del producto.
- El descuento de una venta se registrará como porcentaje.
- El precio aplicado podrá modificarse manualmente durante una venta si la propietaria lo decide y ese valor quedará conservado en el historial.
- Las ventas normales no se asociarán a una persona en el MVP.
- Una venta podrá utilizar uno o más medios de pago.
- Una venta entregada con transferencia pendiente podrá registrarse como pendiente de confirmación.
- Las ventas fiadas se administrarán mediante una cuenta corriente única por persona.
- Los pagos parciales se aplicarán a la deuda total comenzando por las ventas fiadas más antiguas.
- Una persona podrá generar nuevas ventas fiadas aunque mantenga deuda activa.
- La fecha de ventas y pagos será la fecha actual del sistema.

### 4.2. Alcance pendiente del módulo de stock

- Definir durante el diseño qué columnas tendrá la planilla y cuáles serán sus valores permitidos.
- Definir durante el diseño la pantalla o consulta desde la que se visualizará el historial de correcciones.
