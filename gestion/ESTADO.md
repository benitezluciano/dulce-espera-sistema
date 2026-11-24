# Estado actual

**Última actualización:** 2026-11-24
**Versión / hito actual:** Ficha UI-03 redactada en la rama `docs/UI-03`, pendiente de revisión y merge. `main` incluye el mapa de navegación, el inventario de pantallas, las fichas UI-01 y UI-02 y la autenticación definida (DEC-006). La Issue coordinadora de UI es #29.

## Objetivo del momento
Completar las fichas de UI antes de delegar los wireframes a Gabi. Se trabaja con una rama por tarea (DEC-007) y se conversan los puntos abiertos antes de redactar (DEC-008).

## En curso
- [ ] Revisar y mergear la rama `docs/UI-03` (ficha UI-03 más los cambios de requisitos derivados: DEC-009 y DEC-010).
- [ ] Crear en GitHub el Issue de UI-03 (texto ya preparado), vinculado a #29, y los dos issues hijos pendientes de #29: "Inventario de pantallas y mapa de navegación" y "Definir ficha UI-01 Buscar stock".
- [ ] Incorporar a Gabi al repositorio y asignarle los wireframes cuando las fichas estén listas.

## Pendiente (en orden de prioridad)
1. Ficha UI-04 (Carga inicial de stock) y siguientes: UI-05 a UI-07 antes de delegar los wireframes de Entrega 1.
2. Crear los issues hijos de wireframe para UI-01, UI-02 y UI-03 (las fichas están hechas, los wireframes no).
3. Fichas y wireframes de VTA, FIA, PAG y ANU (UI-08 a UI-13), según el alcance de #29.
4. Redactar el Modelo de Datos (`docs/08-modelo-de-datos.md` y `diagramas/er.puml` siguen siendo la plantilla vacía), incluyendo el estado activo/inactivo de productos y variantes, y el diagrama de casos de uso (`diagramas/casos-de-uso.puml`, también plantilla).
5. Definir columnas y valores permitidos de la planilla de carga inicial, y las listas de motivos para correcciones de stock y anulaciones.
6. Armar un prototipo mínimo de Apps Script para verificar los dos puntos abiertos de DEC-006.
7. Decidir qué hacer con la rama remota `docs/add-wireframe-link` (referencia a un wireframe de Figma, no fusionada).
8. Activar en GitHub "Automatically delete head branches".

## Bloqueado
- Ninguno por el momento.

## Cerrado recientemente
- Ficha UI-03 (Alta y edición de producto), con alta, edición y agregado de variantes.
- Inactivación de variantes (DEC-009): HU-20, CU-20, RF-CAT-25 a 28, RF-STK-21, RF-VTA-23, RN46 y RN47.
- Criterios del formulario de producto (DEC-010): "No aplica" literal, alta rápida de valores de catálogo, precio mayor a cero (RN48), marca opcional de texto libre y Administración como menú (UI-14).
- Ramas ordenadas y flujo de una rama por tarea (DEC-007); regla de conversar antes de redactar (DEC-008).
- Autenticación con la cuenta de Google, sin login propio (DEC-006).
- Historias de Usuario y Casos de Uso completos (20 HU y 20 CU); requisitos y reglas de negocio actualizados.

## Próximo paso concreto
Revisar el diff de `docs/UI-03`, mergear con merge commit y pasar a la ficha UI-04 (Carga inicial de stock). Antes de redactarla, conversar los puntos abiertos que aparezcan, en particular las columnas y valores permitidos de la planilla.

## Dudas / riesgos abiertos
- Falta confirmar la incorporación de Gabi al repositorio y definir cómo recibirá y revisará cada entrega.
- Los números de los issues (UI-03 y los dos hijos de #29) aún no se conocen; agregarlos acá y en la bitácora cuando se creen.
- DEC-006 depende de dos supuestos de Apps Script sin verificar: el script debe pertenecer a la cuenta de Silvia y debe funcionar con varias cuentas de Google en el celular.
- El alcance aprobado (`01-alcance.md`) no menciona la inactivación de variantes. Está cubierta por "administrar productos y sus variantes" (sección 5.1), pero conviene avisarle a Silvia en la próxima validación.

## Enlaces útiles
- [DECISIONES.md](./DECISIONES.md)
- [BITACORA.md](./BITACORA.md)
- [docs/04-requisitos.md](../docs/04-requisitos.md)
- [docs/06-historias-de-usuario.md](../docs/06-historias-de-usuario.md)
- [docs/07-casos-de-uso.md](../docs/07-casos-de-uso.md)
- [docs/09-interfaz-usuario.md](../docs/09-interfaz-usuario.md)
