# Estado actual

**Última actualización:** 2026-11-24
**Versión / hito actual:** `main` incluye el mapa de navegación, el inventario de pantallas, las fichas UI-01 a UI-03, la inactivación de variantes (DEC-009) y la autenticación definida (DEC-006). No hay ramas abiertas: solo existe `main`. La Issue coordinadora de UI es #29.

## Objetivo del momento
Completar las fichas de UI antes de delegar los wireframes a Gabi. Se trabaja con una rama por tarea (DEC-007) y se conversan los puntos abiertos antes de redactar (DEC-008).

## En curso
- [ ] Crear en GitHub, si aún no existen, los sub-issues de #29: ficha UI-03, wireframe UI-03, ajuste del wireframe UI-02 para Gabi (texto preparado) y los dos hijos pendientes: "Inventario de pantallas y mapa de navegación" y "Definir ficha UI-01 Buscar stock". Registrar sus números acá.
- [ ] Incorporar a Gabi al repositorio y definir cómo recibe y revisa cada entrega. Ya elaboró los wireframes de UI-01 y UI-02 en Figma (enlace en `diagramas/wireframes/wireframe.md`).

## Pendiente (en orden de prioridad)
1. Ficha UI-04 (Carga inicial de stock) y siguientes: UI-05 a UI-07 antes de delegar los wireframes de Entrega 1.
2. Wireframes de UI-03 y ajuste del de UI-02 por la inactivación de variantes (a cargo de Gabi).
3. Fichas y wireframes de VTA, FIA, PAG y ANU (UI-08 a UI-13), según el alcance de #29.
4. Redactar el Modelo de Datos (`docs/08-modelo-de-datos.md` y `diagramas/er.puml` siguen siendo la plantilla vacía), incluyendo el estado activo/inactivo de productos y variantes, y el diagrama de casos de uso (`diagramas/casos-de-uso.puml`, también plantilla).
5. Definir columnas y valores permitidos de la planilla de carga inicial, y las listas de motivos para correcciones de stock y anulaciones.
6. Armar un prototipo mínimo de Apps Script para verificar los dos puntos abiertos de DEC-006.
7. Actualizar en la ficha UI-01 el estado de su wireframe y sumar UI-03 al `wireframe.md` cuando Gabi lo entregue.
8. Activar en GitHub "Automatically delete head branches".

## Bloqueado
- Ninguno por el momento.

## Cerrado recientemente
- PR #43 (ficha UI-03, DEC-009 y DEC-010) y PR #44 (ajuste de UI-02: ocultar "Agregar variante" en producto inactivo o con variante única) mergeados en `main`.
- Ramas limpias: eliminadas todas las ramas fusionadas, local y remoto. Solo queda `main`.
- Ficha UI-02: estado del wireframe actualizado (elaborado en Figma, pendiente de ajuste por DEC-009).
- Ficha UI-03 (Alta y edición de producto), con alta, edición y agregado de variantes.
- Inactivación de variantes (DEC-009): HU-20, CU-20, RF-CAT-25 a 28, RF-STK-21, RF-VTA-23, RN46 y RN47.
- Criterios del formulario de producto (DEC-010) y autenticación con cuenta de Google (DEC-006).
- Flujo de una rama por tarea (DEC-007) y regla de conversar antes de redactar (DEC-008).

## Próximo paso concreto
Crear una rama nueva desde `main` para la ficha UI-04 (Carga inicial de stock). Antes de redactarla, conversar los puntos abiertos, en particular las columnas y valores permitidos de la planilla y el formato del archivo (RF-STK-10 y RF-STK-11).

## Dudas / riesgos abiertos
- Falta confirmar la incorporación de Gabi al repositorio y definir cómo recibirá y revisará cada entrega.
- Los números de los sub-issues aún no se registraron acá; agregarlos cuando se confirmen en GitHub.
- DEC-006 depende de dos supuestos de Apps Script sin verificar: el script debe pertenecer a la cuenta de Silvia y debe funcionar con varias cuentas de Google en el celular.
- El alcance aprobado (`01-alcance.md`) no menciona la inactivación de variantes. Está cubierta por "administrar productos y sus variantes" (sección 5.1), pero conviene avisarle a Silvia en la próxima validación.
- `main` no tiene protección de rama, por lo que se puede pushear directo. Conviene usarlo solo para cambios mínimos y mantener los PR para el resto (DEC-007).

## Enlaces útiles
- [DECISIONES.md](./DECISIONES.md)
- [BITACORA.md](./BITACORA.md)
- [docs/04-requisitos.md](../docs/04-requisitos.md)
- [docs/06-historias-de-usuario.md](../docs/06-historias-de-usuario.md)
- [docs/07-casos-de-uso.md](../docs/07-casos-de-uso.md)
- [docs/09-interfaz-usuario.md](../docs/09-interfaz-usuario.md)
