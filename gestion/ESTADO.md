# Estado actual

**Última actualización:** 2026-11-20
**Versión / hito actual:** Diseño de interfaz en curso en la rama `docs/UI`. Inventario, mapa de navegación y fichas UI-01 y UI-02 redactados. La Issue coordinadora es #29.

## Objetivo del momento
Coordinar el diseño de UI mediante la Issue #29 y sus issues hijos, completar las fichas antes de delegar wireframes y sumar a Gabi al flujo de colaboración.

## En curso
- [ ] Crear en GitHub los issues hijos ya redactados: "Inventario de pantallas y mapa de navegación" y "Definir ficha UI-01 Buscar stock", vinculándolos a #29.
- [ ] Incorporar a Gabi al repositorio y asignarle los wireframes cuando las fichas estén listas.

## Pendiente (en orden de prioridad)
1. Redactar la ficha UI-03 (Alta y edición de producto) y continuar con UI-04 a UI-07 antes de delegar los wireframes de Entrega 1.
2. Crear los issues hijos de wireframe para UI-01 y UI-02; las fichas están hechas, los wireframes no.
3. Continuar con las fichas y wireframes de VTA, FIA, PAG y ANU (UI-08 a UI-13), según el alcance de #29.
4. Redactar el Modelo de Datos (`docs/08-modelo-de-datos.md` y `diagramas/er.puml` siguen siendo la plantilla vacía) y el diagrama de casos de uso (`diagramas/casos-de-uso.puml`, también plantilla).
5. Definir los vacíos de diseño abiertos: columnas y valores permitidos de la planilla de carga inicial, y listas de motivos para correcciones de stock y anulaciones.
5b. Armar un prototipo mínimo de Apps Script para verificar los dos puntos abiertos de DEC-006 (propiedad del script y varias cuentas de Google en el celular).
6. Incorporar formalmente a Gabi al repositorio y al flujo de PR.

## Bloqueado
- Ninguno por el momento.

## Cerrado recientemente
- Autenticación definida (DEC-006): acceso con la cuenta de Google, sin login propio; RNF-08, mapa de navegación y alcance actualizados.
- Eliminados `RECURSOS.md` e `integrantes.md`, restos de la plantilla académica que solo existían en local.
- Ficha detallada UI-02 Detalle de producto y variantes.
- Inventario de pantallas y mapa de navegación para los 19 CU en `docs/09-interfaz-usuario.md`.
- Ficha detallada UI-01 Buscar: objetivo, patrones, justificación, interacciones, validaciones, estados, accesibilidad y prueba del recorrido crítico.
- Revisión de consistencia documental: link roto y estado del README, typo en RN44 y eliminación de menciones residuales a reportes mensuales (descartados del MVP).
- GitHub Project Kanban Liviano creado; se comenzará a utilizar con la incorporación de Gabi — DEC-005.
- Historias de Usuario y Casos de Uso completos (19 HU y 19 CU).
- Requisitos funcionales y no funcionales (`docs/04-requisitos.md`) y reglas de negocio (`docs/05-reglas-de-negocio.md`) cerrados.

## Próximo paso concreto
Redactar la ficha UI-03 (Alta y edición de producto); en paralelo, crear y vincular a #29 los dos issues hijos ya redactados.

## Dudas / riesgos abiertos
- Falta confirmar la incorporación de Gabi al repositorio y definir cómo recibirá/revisará cada entrega.
- Los números de los dos issues hijos aún no se conocen; agregarlos a este estado y a la bitácora cuando se creen en GitHub.
- DEC-006 define el acceso con la cuenta de Google, pero depende de dos supuestos de Apps Script aún sin verificar en la práctica: el script debe pertenecer a la cuenta de Silvia y debe funcionar con varias cuentas de Google en el celular.

## Enlaces útiles
- [DECISIONES.md](./DECISIONES.md)
- [BITACORA.md](./BITACORA.md)
- [docs/04-requisitos.md](../docs/04-requisitos.md)
- [docs/06-historias-de-usuario.md](../docs/06-historias-de-usuario.md)
- [docs/07-casos-de-uso.md](../docs/07-casos-de-uso.md)
- [docs/09-interfaz-usuario.md](../docs/09-interfaz-usuario.md)
