# Estado actual

**Última actualización:** 2026-10-25
**Versión / hito actual:** Etapa de análisis funcional en curso, trabajando en solitario. Historias de Usuario completas (`HU-01` a `HU-14`) en la rama `docs/HU`, pendiente de mergear a `main`.

## Objetivo del momento
Mergear `docs/HU` a `main` y continuar con Casos de Uso (`docs/07-casos-de-uso.md`).

## En curso
- [ ] Mergear la rama `docs/HU` a `main` mediante Pull Request (responsable: usuario)

## Pendiente (en orden de prioridad)
1. Redactar al menos un Caso de Uso (`docs/07-casos-de-uso.md`)
2. Armar un encargo acotado de wireframes (módulos CAT + STK, ya cerrados) para delegar a una tercera persona
3. Redactar Modelo de Datos
4. Sumar a la segunda persona (desarrolladora) al repositorio
5. _(Pospuesto hasta sumar a la segunda persona)_ Crear el GitHub Project (tablero Kanban) y definir la convención de columnas — ver DEC-002

## Bloqueado
- Ninguno por el momento.

## Cerrado recientemente
- HU-09 a HU-14 (módulos FIA, PAG y ANU) — asociar persona, consultar cuenta corriente, modificar datos, registrar pago, anular venta (caso general y caso con pagos parciales) — 2026-10-25
- Documento `docs/06-historias-de-usuario.md` completo: las 7 módulos cubiertos con 14 Historias de Usuario (HU-01 a HU-14)
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
Mergear `docs/HU` a `main` (ver Pull Request sugerido en BITACORA.md) y luego arrancar Casos de Uso.

## Dudas / riesgos abiertos
- Convención sobre en qué rama registrar los cambios de `gestion/`: con el merge de `docs/HU` a `main`, este ciclo queda resuelto para esta rama; a confirmar el mismo criterio (registrar en la rama de trabajo y mergear pronto) para la próxima rama de Casos de Uso.

## Enlaces útiles
- [DECISIONES.md](./DECISIONES.md)
- [BITACORA.md](./BITACORA.md)
- [docs/04-requisitos.md](../docs/04-requisitos.md)
- [docs/06-historias-de-usuario.md](../docs/06-historias-de-usuario.md)