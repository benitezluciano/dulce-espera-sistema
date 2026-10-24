# Historias de usuario
_Cada historia debe incluir formato clásico, criterios de aceptación y validación INVEST._

---

## HU-01 — Registrar un producto completo con sus variantes

| Campo | Detalle |
|-------|---------|
| Historia | Como propietaria, quiero registrar un producto completo (nombre, categoría, marca, precio, temporada y variantes de talle/color/género), para poder venderlo y controlar su stock desde el momento en que lo cargo. |
| Módulo | CAT |
| Requisitos relacionados | RF-CAT-01, RF-CAT-02, RF-CAT-03, RF-CAT-04, RF-CAT-05, RF-CAT-06, RF-CAT-07, RF-CAT-08, RF-CAT-09, RF-CAT-10 |

### Criterios de aceptación

1. Dado que cargo un nuevo producto, puedo asignarle categoría, nombre, marca, precio vigente y una única temporada.
2. Dado que el producto tiene variantes, puedo definir talle, color y género para cada una.
3. Dado que un atributo no aplica al producto, el sistema permite usar "No aplica" en la variante única.
4. Dado que guardo el producto, el sistema genera automáticamente su código interno único.
5. Dado que intento guardar sin nombre, categoría o precio, el sistema no permite confirmar la carga.

### Validación INVEST

| Criterio | ¿Se cumple? | Observación |
|----------|-------------|-------------|
| Independiente | Sí | Es la base del sistema; no depende de otra historia. |
| Negociable | Sí | El diseño del formulario puede ajustarse en UI. |
| Valiosa | Sí | Al finalizar, el producto ya es vendible y stockeable. |
| Estimable | Sí | Alcance acotado y claro. |
| Pequeña | Sí | Es una única acción de negocio, sin mezclar tareas de otro momento (baja, catálogos). |
| Verificable | Sí | Criterios de aceptación objetivos. |

---

## HU-02 — Cargar el stock inicial mediante una planilla

| Campo | Detalle |
|-------|---------|
| Historia | Como propietaria, quiero cargar el stock inicial de mis productos mediante una planilla, para no tener que ingresar cada variante manualmente una por una. |
| Módulo | STK |
| Requisitos relacionados | RF-STK-01, RF-STK-02, RF-STK-10, RF-STK-11, RF-STK-12 |

### Criterios de aceptación

1. Dado que subo una planilla con el formato definido, el sistema valida sus datos antes de incorporarlos al inventario.
2. Dado que la planilla tiene errores, el sistema me informa cuáles son antes de cargar cualquier dato.
3. Dado que la planilla no contempla todos mis productos, puedo completar los faltantes posteriormente desde la interfaz.
4. Dado que la carga se confirma, cada variante queda registrada con su cantidad disponible.

### Validación INVEST

| Criterio | ¿Se cumple? | Observación |
|----------|-------------|-------------|
| Independiente | Sí (con dependencia natural) | Requiere que los productos ya existan (HU-01), pero no depende de otra historia de stock. |
| Negociable | Sí | El formato exacto de columnas se define en diseño (ver 4.2 de requisitos). |
| Valiosa | Sí | Evita una carga manual tediosa; resuelve un dolor real de arranque. |
| Estimable | Sí | Alcance acotado. |
| Pequeña | Sí | Es la carga inicial, separada de la asignación posterior y de la corrección recurrente. |
| Verificable | Sí | Criterios objetivos. |

---

## HU-03 — Asignar stock a un producto o variante nueva en cualquier momento

| Campo | Detalle |
|-------|---------|
| Historia | Como propietaria, quiero asignar la cantidad disponible de un producto o variante que no formó parte de la carga inicial, para mantener el stock completo sin depender únicamente de la planilla. |
| Módulo | STK |
| Requisitos relacionados | RF-STK-02, RF-STK-03, RF-STK-12 |

### Criterios de aceptación

1. Dado que doy de alta un producto o variante nueva (fuera de la carga inicial), puedo asignarle una cantidad disponible desde la interfaz.
2. Dado que un producto ya cargado tiene variantes faltantes, puedo agregar la cantidad de esas variantes sin afectar las que ya tienen stock.
3. Dado que asigno una cantidad por primera vez, el sistema no exige un motivo de corrección, porque no estoy modificando un valor anterior, sino creando uno nuevo.

### Validación INVEST

| Criterio | ¿Se cumple? | Observación |
|----------|-------------|-------------|
| Independiente | Sí | Depende de que el producto/variante exista (HU-01), no de HU-02 ni de HU-04. |
| Negociable | Sí | El detalle de la pantalla se define en diseño. |
| Valiosa | Sí | Evita que productos nuevos queden incompletos por depender solo de la planilla inicial. |
| Estimable | Sí | Alcance acotado. |
| Pequeña | Sí | Es un alta de cantidad, no una corrección ni una carga masiva. |
| Verificable | Sí | Criterios objetivos. |

---

## HU-04 — Corregir manualmente el stock con motivo e historial

| Campo | Detalle |
|-------|---------|
| Historia | Como propietaria, quiero corregir la cantidad disponible de una variante indicando un motivo, para mantener el stock actualizado cuando detecto diferencias con la mercadería física, conservando un registro de los cambios. |
| Módulo | STK |
| Requisitos relacionados | RF-STK-06, RF-STK-07, RF-STK-13, RF-STK-14, RF-STK-15 |

### Criterios de aceptación

1. Dado que detecto una diferencia física, puedo corregir la cantidad disponible de una variante que ya tenía una cantidad cargada.
2. Dado que hago una corrección, el sistema me exige elegir un motivo de una lista de opciones simples.
3. Dado que confirmo la corrección, el sistema no permite que la cantidad resultante sea negativa.
4. Dado que se guarda la corrección, el sistema registra fecha, variante, cantidad anterior, cantidad nueva y motivo en un historial.

### Validación INVEST

| Criterio | ¿Se cumple? | Observación |
|----------|-------------|-------------|
| Independiente | Sí | Requiere que la variante ya tenga una cantidad asignada (HU-03), no depende de otra corrección. |
| Negociable | Sí | La pantalla de historial puede ajustarse en diseño (ver 4.2 de requisitos). |
| Valiosa | Sí | Resuelve el dolor de fondo del proyecto: confiabilidad del stock. |
| Estimable | Sí | Alcance acotado. |
| Pequeña | Sí | Una sola acción correctiva, no mezcla con la carga ni con el alta inicial. |
| Verificable | Sí | Criterios objetivos. |

---

## HU-05 — Buscar productos combinando filtros para responder consultas de clientes

| Campo | Detalle |
|-------|---------|
| Historia | Como propietaria, quiero buscar productos combinando criterios como categoría, talle, color y disponibilidad, para responder rápidamente las consultas de mis clientas por WhatsApp o Instagram. |
| Módulo | BUS |
| Requisitos relacionados | RF-BUS-01, RF-BUS-02, RF-BUS-03, RF-BUS-04, RF-BUS-05, RF-BUS-06, RF-BUS-07, RF-BUS-09, RF-BUS-10, RF-BUS-11, RF-BUS-12, RF-BUS-13 |

### Criterios de aceptación

1. Dado que ingreso al menos un criterio de búsqueda, el sistema muestra los productos que cumplen todos los criterios seleccionados.
2. Dado que no completo un filtro, el sistema no lo aplica como restricción.
3. Dado que busco por nombre, el sistema admite coincidencias parciales.
4. Dado que ningún producto cumple los criterios, el sistema me informa que no hay coincidencias.
5. Dado que veo los resultados, el sistema muestra marca, temporada, variantes, cantidad disponible y precio vigente.
6. Dado que no indico lo contrario, el sistema oculta los productos inactivos; puedo incluirlos mediante un filtro específico.

### Validación INVEST

| Criterio | ¿Se cumple? | Observación |
|----------|-------------|-------------|
| Independiente | Sí | Depende de que existan productos cargados (HU-01), no de otra historia de búsqueda. |
| Negociable | Sí | El diseño visual de filtros se resuelve en UI. |
| Valiosa | Sí | Resuelve el dolor principal relevado: responder sin revisar físicamente el local. |
| Estimable | Sí | Alcance acotado. |
| Pequeña | Sí | Un único objetivo: responder consultas, sin mezclar la decisión de reposición. |
| Verificable | Sí | Criterios objetivos. |

---

## HU-06 — Identificar productos con stock bajo o agotado para decidir reposición

| Campo | Detalle |
|-------|---------|
| Historia | Como propietaria, quiero ver los productos con menor cantidad disponible o agotados, para decidir qué reponer cuando junto el dinero para comprarle a mis proveedores. |
| Módulo | BUS |
| Requisitos relacionados | RF-BUS-08, RF-BUS-14 |

### Criterios de aceptación

1. Dado que filtro por "Agotados", veo únicamente los productos sin stock disponible.
2. Dado que ordeno los resultados de menor a mayor cantidad, identifico visualmente las variantes con stock bajo.
3. Dado que combino este orden con otros filtros (por ejemplo, categoría), el sistema respeta ambos criterios a la vez.

### Validación INVEST

| Criterio | ¿Se cumple? | Observación |
|----------|-------------|-------------|
| Independiente | Sí | Usa el mismo motor de búsqueda de HU-05, pero con un objetivo de usuario distinto. |
| Negociable | Sí | El detalle visual (orden, resaltado) se resuelve en UI. |
| Valiosa | Sí | Reemplaza directamente al módulo de reportes descartado; conecta con el criterio real de reposición de Silvia. |
| Estimable | Sí | Alcance acotado. |
| Pequeña | Sí | Un único objetivo: decidir reposición, sin mezclar con responder consultas. |
| Verificable | Sí | Criterios objetivos. |

---

## HU-07 — Registrar una venta cobrada con uno o más medios de pago

| Campo | Detalle |
|-------|---------|
| Historia | Como propietaria, quiero registrar una venta indicando productos, cantidades, precio y medio de pago, para llevar un control de lo que vendo y actualizar el stock automáticamente. |
| Módulo | VTA |
| Requisitos relacionados | RF-VTA-01, RF-VTA-02, RF-VTA-03, RF-VTA-04, RF-VTA-05, RF-VTA-06, RF-VTA-07, RF-VTA-08, RF-VTA-09, RF-VTA-11, RF-VTA-12, RF-VTA-14, RF-VTA-15, RF-VTA-16 |

### Criterios de aceptación

1. Dado que selecciono uno o más productos y variantes, indico la cantidad vendida de cada uno.
2. Dado que preparo la venta, el sistema me muestra el precio vigente, permitiéndome modificarlo manualmente si lo decido.
3. Dado que aplico un descuento, lo expreso como porcentaje y veo el subtotal, el descuento y el total final.
4. Dado que confirmo la venta, el sistema registra la fecha actual automáticamente y descuenta del stock las cantidades vendidas.
5. Dado que la venta tiene uno o más medios de pago (efectivo, transferencia, débito), el sistema los registra todos.
6. Dado que confirmo la venta, el sistema conserva el detalle completo (productos, variantes, cantidades, precios, descuento, total) sin asociarla a un nombre de cliente.

### Validación INVEST

| Criterio | ¿Se cumple? | Observación |
|----------|-------------|-------------|
| Independiente | Sí | Depende de que existan productos y stock (HU-01 a HU-04), no de otra historia de ventas. |
| Negociable | Sí | El diseño de pantalla se resuelve en UI. |
| Valiosa | Sí | Es el corazón del sistema: controlar ventas y mantener el stock actualizado. |
| Estimable | Sí | Alcance acotado, aunque amplio en cantidad de RF. |
| Pequeña | Sí | Agrupa varios RF, pero todos pertenecen a un único acto indivisible: cerrar una venta. Separarlos dejaría una venta a medio confirmar, sin valor de uso. |
| Verificable | Sí | Criterios objetivos. |

---

## HU-08 — Confirmar una venta con transferencia pendiente

| Campo | Detalle |
|-------|---------|
| Historia | Como propietaria, quiero marcar como confirmada una venta entregada cuyo pago por transferencia estaba pendiente, para registrar el cobro real una vez que se acredita el dinero. |
| Módulo | VTA |
| Requisitos relacionados | RF-VTA-13, RF-VTA-17 |

### Criterios de aceptación

1. Dado que entrego la mercadería y el pago es por transferencia, puedo registrar la venta como "pendiente de confirmación" sin que eso impida descontar el stock.
2. Dado que la transferencia se acredita, puedo marcar esa venta como confirmada.
3. Dado que marco la venta como confirmada, el sistema la considera cobrada a partir de ese momento, sin modificar ningún otro dato de la venta original.

### Validación INVEST

| Criterio | ¿Se cumple? | Observación |
|----------|-------------|-------------|
| Independiente | Sí | Depende de que exista una venta registrada con transferencia pendiente (HU-07), no de otra historia. |
| Negociable | Sí | Puede resolverse con una simple acción de cambio de estado en la interfaz, sin pantallas adicionales. |
| Valiosa | Sí | Evita que una venta real quede para siempre como "pendiente" sin forma de cerrarse. |
| Estimable | Sí | Es una acción simple (cambio de estado), bajo esfuerzo de implementación. |
| Pequeña | Sí | Una única acción: confirmar un estado ya existente. |
| Verificable | Sí | Criterios objetivos. |

---

## HU-09 — [Nombre de la historia]
