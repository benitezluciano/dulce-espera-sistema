# Alternativas de solución y decisión de arquitectura

## 1. Propósito

Este documento registra las alternativas consideradas para resolver el problema de negocio de Dulce Espera y deja constancia de la decisión adoptada para la primera implementación.

Las alternativas parten de la misma base funcional: la propietaria, el problema identificado, los objetivos, el alcance y las reglas de negocio son comunes. La diferencia está en la forma de implementar y sostener la solución.

## 2. Base común

Ambas alternativas contemplan:

- Silvia Benítez como usuaria inicial y principal.
- Una herramienta interna para consultar y administrar el stock.
- Uso prioritario desde el celular.
- Consulta por producto y variante, incluyendo talle, género, color, temporada y cantidad.
- Registro de ventas y actualización del stock según el alcance aprobado.
- Registro de ventas fiadas y reportes básicos, sujetos a la especificación de requisitos.
- Las reglas de negocio documentadas en [`05-reglas-de-negocio.md`](./05-reglas-de-negocio.md).
- Los mismos criterios de aceptación y de éxito del producto.

La necesidad funcional no depende de la tecnología elegida: Silvia debe poder consultar la disponibilidad y actualizar la información sin revisar físicamente el local cada vez que recibe una consulta.

## 3. Alternativa A: implementación real con presupuesto nulo

### Google Sheets + Google Apps Script

Esta alternativa utiliza servicios del ecosistema de Google para construir un MVP funcional y probarlo en el contexto real del negocio.

| Aspecto | Descripción |
|---|---|
| Presupuesto inicial | $0, sujeto a las condiciones vigentes de los servicios utilizados |
| Almacenamiento | Google Sheets |
| Lógica de negocio | Google Apps Script |
| Interfaz | Aplicación web responsive accesible desde el celular |
| Usuaria inicial | Una única usuaria: Silvia |
| Conectividad | Requiere conexión a internet |
| Alcance recomendado | Consulta y administración básica de stock; luego ventas y reportes |

### Adecuación al contexto

La alternativa es adecuada para una primera versión porque el negocio tiene bajo volumen operativo, una única usuaria y una necesidad concreta. Permite validar si la consulta digital del stock resuelve el problema antes de asumir costos o complejidad adicional.

### Condiciones y riesgos

- La información debe administrarse preferentemente desde la interfaz y no editando directamente las hojas.
- Se deberá conservar un historial de movimientos para poder explicar los cambios de stock.
- Será necesario definir un procedimiento de copias de seguridad.
- La solución dependerá de la disponibilidad de la cuenta de Google y de los límites de Apps Script.
- La alternativa no se considera adecuada, sin una revisión posterior, para múltiples usuarios, varios locales o un crecimiento importante del volumen de operaciones.

## 4. Alternativa B: solución objetivo para un presupuesto ideal

### Aplicación web con base de datos estructurada

Esta alternativa representa una solución objetivo con mayor inversión inicial y mayor capacidad de evolución. La tecnología concreta se definirá cuando se completen los requisitos no funcionales, el modelo de datos y la evaluación técnica.

| Aspecto | Descripción |
|---|---|
| Presupuesto inicial | Presupuesto ideal para desarrollo, alojamiento y mantenimiento |
| Almacenamiento | Base de datos estructurada |
| Lógica de negocio | Backend o servicios de aplicación propios |
| Interfaz | Aplicación web responsive |
| Usuarias/os potenciales | Silvia inicialmente, con posibilidad de incorporar otros perfiles |
| Conectividad | Requiere conexión a internet, salvo que una etapa posterior defina otra necesidad |
| Alcance recomendado | El mismo alcance funcional inicial, con capacidad de evolución |

### Adecuación al contexto

Esta alternativa ofrece mayor control sobre los datos, la seguridad, los permisos, las copias de respaldo y la evolución del sistema. Sería conveniente si el uso real justificara incorporar más usuarios, mayor volumen, varios locales o nuevas funciones.

### Costos y riesgos

- Requiere más tiempo de análisis, desarrollo, pruebas y mantenimiento.
- Puede implicar costos de alojamiento, base de datos, dominio y servicios complementarios.
- Introduce mayor complejidad técnica para un negocio que actualmente tiene una sola usuaria y bajo volumen.
- Existe el riesgo de sobredimensionar la primera solución si no se valida antes el uso real.

## 5. Comparación

| Criterio | Google Sheets + Apps Script | Aplicación web con base de datos estructurada |
|---|---|---|
| Costo inicial | Muy favorable | Requiere presupuesto |
| Tiempo hasta una primera prueba | Corto | Medio o largo |
| Adecuación al problema actual | Alta | Alta |
| Complejidad inicial | Baja o media | Media o alta |
| Control técnico | Medio | Alto |
| Escalabilidad | Limitada | Mayor |
| Mantenimiento | Simple para el MVP | Requiere mayor especialización |
| Riesgo para el piloto | Bajo | Medio |
| Valor demostrativo para el portfolio | Bueno | Muy alto |

## 6. Decisión adoptada

Se selecciona **Google Sheets + Google Apps Script** para la primera implementación debido al presupuesto nulo, el bajo volumen operativo y la existencia de una única usuaria.

La solución objetivo basada en una aplicación web con base de datos estructurada se conserva como alternativa de evolución. No se implementará inicialmente porque sus beneficios principales están relacionados con necesidades que todavía no fueron confirmadas para el contexto actual, como múltiples usuarios, mayor escala o reglas de acceso más complejas.

Esta decisión no modifica el problema ni el alcance funcional del proyecto. Define la alternativa tecnológica y operativa con la que se construirá el MVP.

## 7. Impacto sobre la documentación posterior

La documentación funcional continuará siendo común a ambas alternativas:

- alcance y relevamiento;
- stakeholders y perfiles de usuario;
- procesos AS-IS y TO-BE;
- requisitos funcionales;
- reglas de negocio;
- historias de usuario;
- casos de uso;
- criterios de aceptación;
- modelo conceptual del negocio.

Se diferenciarán posteriormente, si resulta necesario:

- arquitectura técnica;
- modelo lógico y físico de datos;
- autenticación y permisos;
- despliegue y alojamiento;
- copias de seguridad;
- requisitos no funcionales específicos;
- riesgos, costos y esfuerzo de implementación.

Por lo tanto, no se documentan dos proyectos independientes. Se documenta un único problema de negocio con una alternativa seleccionada para el MVP y una alternativa objetivo para una posible evolución.

## 8. Criterio para revisar la decisión

La decisión podrá revisarse cuando la primera versión se pruebe con Silvia y exista evidencia sobre:

- frecuencia de uso;
- volumen de productos, variantes y movimientos;
- cantidad de personas que necesitarían acceder;
- necesidad de permisos diferenciados;
- dificultades de mantenimiento o respaldo;
- nuevas necesidades que no pueda resolver razonablemente la alternativa seleccionada.