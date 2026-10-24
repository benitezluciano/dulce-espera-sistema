# Estado actual

**Última actualización:** 2026-10-24
**Versión / hito actual:** Etapa de análisis funcional en curso, trabajando en solitario. Historias de Usuario en redacción en la rama `docs/HU`: completos los módulos CAT, STK, BUS y VTA (HU-01 a HU-08).

## Objetivo del momento
Redactar al menos una Historia de Usuario representativa por módulo (CAT, STK, BUS, VTA, FIA, PAG, ANU) en `docs/06-historias-de-usuario.md`, aplicando el criterio de corte vertical definido en DEC-003.

## En curso
- [ ] Redactar Historias de Usuario de los módulos FIA, PAG y ANU (responsable: usuario, con asistencia de Copilot) — rama `docs/HU`

## Pendiente (en orden de prioridad)
1. Completar Historias de Usuario de FIA, PAG y ANU
2. Redactar al menos un Caso de Uso (`docs/07-casos-de-uso.md`)
3. Armar un encargo acotado de wireframes (módulos CAT + STK, ya cerrados) para delegar a una tercera persona
4. Redactar Modelo de Datos
5. Sumar a la segunda persona (desarrolladora) al repositorio
6. _(Pospuesto hasta sumar a la segunda persona)_ Crear el GitHub Project (tablero Kanban) y definir la convención de columnas — ver DEC-002

## Bloqueado
- Ninguno por el momento.

## Cerrado recientemente
- HU-05 a HU-08 (módulos BUS y VTA) — búsqueda, stock bajo, venta cobrada y confirmación de transferencia pendiente — 2026-10-24
- DEC-004 — Cierre del estado "transferencia pendiente" con una confirmación simple (RF-VTA-17, RN40) — 2026-10-24
- HU-02 a HU-04 (módulo STK) — carga por planilla, asignación de stock nuevo y corrección con motivo — 2026-10-24
- HU-01 (módulo CAT) — alta completa de un producto con sus variantes — 2026-10-05
- DEC-003 — Criterio de corte vertical para Historias de Usuario — 2026-10-05
- Requisitos funcionales y no funcionales (`docs/04-requisitos.md`), incluyendo descarte del módulo de reportes y agregado de RNF de seguridad/backup
- DEC-002 — Posponer GitHub Projects hasta sumar a la segunda persona — 2026-10-01
- DEC-001 — Adoptar metodología de gestión liviana (Kanban + decisiones + bitácora) — 2026-09-25
- #23 — Definir requisitos funcionales y no funcionales

## Próximo paso concreto
Continuar en la rama `docs/HU` definiendo la Historia de Usuario representativa del módulo FIA (ventas fiadas y cuenta corriente), siguiendo el mismo proceso de borrador + validación INVEST antes de escribirla.

## Dudas / riesgos abiertos
- Convención sobre en qué rama registrar los cambios de `gestion/` (¿en la rama de trabajo como `docs/HU`, o directo en `main`?). Mientras `docs/HU` siga activa y acumulando sesiones, se sigue registrando `gestion/` en esa misma rama; a revisar si se extiende demasiado antes del próximo merge.

## Enlaces útiles
- [DECISIONES.md](./DECISIONES.md)
- [BITACORA.md](./BITACORA.md)
- [docs/04-requisitos.md](../docs/04-requisitos.md)
- [docs/06-historias-de-usuario.md](../docs/06-historias-de-usuario.md)