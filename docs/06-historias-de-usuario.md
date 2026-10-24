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

## HU-02 — [Nombre de la historia]

| Campo | Detalle |
|-------|---------|
| Historia | Como [rol], quiero [acción], para [objetivo]. |
| Módulo | |
| Requisitos relacionados | RF-XX, RF-XX |

### Criterios de aceptación

1. 
2. 
3. 

### Validación INVEST

| Criterio | ¿Se cumple? | Observación |
|----------|-------------|-------------|
| Independiente | | |
| Negociable | | |
| Valiosa | | |
| Estimable | | |
| Pequeña | | |
| Verificable | | |
