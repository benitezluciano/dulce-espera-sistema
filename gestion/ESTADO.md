# Estado actual

**Última actualización:** 2026-11-20
**Versión / hito actual:** `main` incluye el mapa de navegación, el inventario de 13 pantallas y las fichas UI-01 y UI-02, más la autenticación definida (DEC-006). Rama de trabajo actual: `docs/UI-03`. La Issue coordinadora de UI es #29.

## Objetivo del momento
Completar las fichas de UI antes de delegar los wireframes a Gabi. Se trabaja con una rama por tarea (DEC-007) y se conversan los puntos abiertos antes de redactar (DEC-008).

## En curso
- [ ] Ficha UI-03 (Alta y edición de producto) en la rama `docs/UI-03`: en etapa de conversación; **no está redactada**. Hay un borrador sin commitear en `docs/09-interfaz-usuario.md` que se rehará o descartará (`git checkout docs/09-interfaz-usuario.md`).
- [ ] Crear en GitHub el Issue de UI-03 (texto ya preparado) y los dos issues hijos pendientes de #29: "Inventario de pantallas y mapa de navegación" y "Definir ficha UI-01 Buscar stock".
- [ ] Incorporar a Gabi al repositorio y asignarle los wireframes cuando las fichas estén listas.

## Pendiente (en orden de prioridad)
1. Resolver conversando los puntos abiertos de UI-03 (ver "Dudas / riesgos abiertos") y, con una confirmación final, redactar la ficha.
2. Continuar con las fichas UI-04 a UI-07 antes de delegar los wireframes de Entrega 1.
3. Crear los issues hijos de wireframe para UI-01, UI-02 y UI-03 cuando sus fichas estén cerradas.
4. Fichas y wireframes de VTA, FIA, PAG y ANU (UI-08 a UI-13), según el alcance de #29.
5. Redactar el Modelo de Datos (`docs/08-modelo-de-datos.md` y `diagramas/er.puml` siguen siendo la plantilla vacía) y el diagrama de casos de uso (`diagramas/casos-de-uso.puml`, también plantilla).
6. Definir columnas y valores permitidos de la planilla de carga inicial, y las listas de motivos para correcciones de stock y anulaciones.
7. Armar un prototipo mínimo de Apps Script para verificar los dos puntos abiertos de DEC-006.
8. Decidir qué hacer con la rama remota `docs/add-wireframe-link` (referencia a un wireframe de Figma, no fusionada).
9. Activar en GitHub "Automatically delete head branches" y corregir el typo "variamtes" en la ficha UI-01.

## Bloqueado
- Ninguno por el momento.

## Cerrado recientemente
- Ramas ordenadas: borradas las ya fusionadas, flujo de una rama por tarea definido — DEC-007.
- Regla de trabajo acordada: conversar los puntos abiertos antes de redactar — DEC-008.
- Autenticación definida (DEC-006): acceso con la cuenta de Google, sin login propio; RNF-08, mapa de navegación y alcance actualizados.
- Eliminados `RECURSOS.md` e `integrantes.md`, restos de la plantilla académica.
- Revisión de consistencia documental (README, reportes mensuales descartados, typo de RN44).
- Fichas UI-01 y UI-02, inventario de pantallas y mapa de navegación para los 19 CU.
- Historias de Usuario y Casos de Uso completos (19 HU y 19 CU); requisitos y reglas de negocio cerrados.

## Próximo paso concreto
Retomar la conversación sobre UI-03 empezando por los dos puntos que pueden modificar documentos cerrados: si "No aplica" es por atributo o por producto, y cómo corregir o retirar una variante cargada por error.

## Dudas / riesgos abiertos
- **UI-03, a resolver conversando:** (1) "No aplica" por atributo o por producto (RN16 y RF-CAT-10); (2) corregir o retirar una variante cargada por error, sin requisito que lo cubra (RF-STK-12); (3) qué es la pantalla Administración, que está en el mapa pero no en el inventario; (4) agregar un valor de catálogo desde el formulario de producto frente a RNF-04; (5) precio cero y sugerencias de marca.
- Falta confirmar la incorporación de Gabi al repositorio y definir cómo recibirá y revisará cada entrega.
- Los números de los issues (UI-03 y los dos hijos de #29) aún no se conocen; agregarlos acá y en la bitácora cuando se creen.
- DEC-006 depende de dos supuestos de Apps Script sin verificar: el script debe pertenecer a la cuenta de Silvia y debe funcionar con varias cuentas de Google en el celular.

## Enlaces útiles
- [DECISIONES.md](./DECISIONES.md)
- [BITACORA.md](./BITACORA.md)
- [docs/04-requisitos.md](../docs/04-requisitos.md)
- [docs/06-historias-de-usuario.md](../docs/06-historias-de-usuario.md)
- [docs/07-casos-de-uso.md](../docs/07-casos-de-uso.md)
- [docs/09-interfaz-usuario.md](../docs/09-interfaz-usuario.md)
