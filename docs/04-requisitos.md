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

### 4.2. Alcance pendiente del módulo de stock

- Definir durante el diseño qué columnas tendrá la planilla y cuáles serán sus valores permitidos.
- Definir durante el diseño la pantalla o consulta desde la que se visualizará el historial de correcciones.
