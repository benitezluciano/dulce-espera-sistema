## 2026-10-24 — Sesión 4
**Duración aprox.:** ~1 h 30 min · **Quién:** Usuario

- **Objetivo de la sesión:** Continuar la redacción de Historias de Usuario en la rama `docs/HU`, cerrando los módulos STK, BUS y VTA.
- **Hecho:**
  - Se cerró el módulo STK con tres historias (`HU-02` a `HU-04`): carga inicial por planilla, asignación de stock a un producto o variante nueva en cualquier momento, y corrección manual con motivo e historial. Se detectó y resolvió un vacío: el motivo obligatorio aplica solo a corregir una cantidad existente, no a asignarla por primera vez (se documentó en `04-requisitos.md`).
  - Se cerró el módulo BUS con dos historias (`HU-05`, `HU-06`): responder consultas de clientes combinando filtros, e identificar stock bajo/agotado para decidir reposición (reemplazo directo del módulo de reportes descartado).
  - Se cerró el módulo VTA con dos historias (`HU-07`, `HU-08`): registrar una venta cobrada con uno o más medios de pago, y confirmar una venta con transferencia pendiente. Se detectó un vacío: no existía ningún requisito para cerrar el estado "pendiente de confirmación" de una transferencia; se resolvió agregando `RF-VTA-17` y `RN40`, optando por la alternativa más simple (cambio de estado) para no sumar complejidad de desarrollo.
  - Se discutió la conveniencia de adelantar wireframes de UI; se acordó esperar a tener al menos un Caso de Uso y delegar inicialmente solo los módulos ya cerrados (CAT + STK) para no comprometer un diseño prematuro.
- **Decidido:** (ver DECISIONES.md)
  - DEC-004 — Cierre del estado "transferencia pendiente" mediante una confirmación simple de estado, sin flujo de conciliación adicional.
- **Cerrado:**
  - Módulos STK, BUS y VTA de Historias de Usuario (`HU-02` a `HU-08`).
- **Pendiente / abierto:**
  - Redactar las Historias de Usuario de los módulos FIA, PAG y ANU.
  - Redactar al menos un Caso de Uso antes de delegar wireframes.
  - Armar el encargo acotado de wireframes (CAT + STK) para una tercera persona.
  - Seguir validando la convención de en qué rama registrar `gestion/` si `docs/HU` se extiende más sesiones.
- **Problemas o aprendizajes:**
  - El mismo patrón de "vacío de requisito" (un estado o acción sin su contraparte de cierre) volvió a aparecer, igual que en la sesión anterior con la carga de stock nuevo vs. corrección. Redactar Historias de Usuario a partir de los RF es una buena forma de detectar estos huecos antes de llegar a diseño.
  - Los wireframes deben apoyarse en Casos de Uso, no solo en Historias de Usuario, para no rediseñar pantallas cuando aparezcan los módulos de ventas fiadas y pagos.
- **Próximo paso:** Redactar la Historia de Usuario representativa del módulo FIA.
- **Dudas para retomar:** Ninguna nueva; se mantiene la de la sesión anterior sobre la convención de rama para `gestion/`.

---

## 2026-10-05 — Sesión 3
**Duración aprox.:** ~1 h · **Quién:** Usuario

- **Objetivo de la sesión:** Cerrar formalmente los requisitos funcionales y no funcionales, y arrancar la redacción de Historias de Usuario.
- **Hecho:**
  - Se evaluó el módulo de reportes mensuales (`REP`) y se descartó del MVP: la necesidad real (detectar stock bajo para decidir reposición) queda cubierta agregando `RF-BUS-14` (ordenar resultados de búsqueda de menor a mayor cantidad). Se documentó como mejora futura fuera del MVP en `01-alcance.md`.
  - Se definió una política de seguridad de acceso y resguardo de datos para la alternativa Google Sheets + Apps Script: login con recomendación de 2FA (`RNF-08`) y copias de seguridad periódicas automáticas independientes del historial de versiones (`RNF-09`).
  - Se dieron por cerrados los requisitos funcionales y no funcionales (`docs/04-requisitos.md`).
  - Se creó la rama `docs/HU` para trabajar exclusivamente la etapa de Historias de Usuario.
  - Se explicó la metodología INVEST y se discutió el criterio de corte de historias (vertical vs. horizontal), aplicándolo para definir y cerrar `HU-01` del módulo CAT (alta completa de un producto con sus variantes) en `docs/06-historias-de-usuario.md`.
- **Decidido:** (ver DECISIONES.md)
  - DEC-003 — Criterio de corte vertical para Historias de Usuario: una historia se separa de otra solo cuando el fragmento resultante sigue siendo útil y verificable por sí mismo.
- **Cerrado:**
  - Requisitos funcionales y no funcionales del MVP (#23).
  - HU-01 (módulo CAT).
- **Pendiente / abierto:**
  - Redactar las Historias de Usuario de los módulos STK, BUS, VTA, FIA, PAG y ANU.
  - Definir si las actualizaciones de `gestion/` se registran en la rama de trabajo (ej. `docs/HU`) o directo en `main`. Criterio inicial para sesiones cortas y ramas de corta duración: registrar junto con el trabajo funcional en la misma rama y fusionar a `main` pronto, para que `ESTADO.md` no quede desactualizado en `main` por mucho tiempo. Si una rama se extiende por varias sesiones, conviene reevaluar y volcar los archivos de `gestion/` directo en `main` en cada cierre de sesión, ya que son de proceso y no un entregable funcional atado a esa rama.
- **Problemas o aprendizajes:**
  - Separar una Historia de Usuario por tipo de atributo (ej. "datos básicos" vs. "atributos comerciales") es un corte horizontal que no aporta valor real: el criterio correcto es si el fragmento resultante ya es usable por sí solo.
- **Próximo paso:** Continuar en `docs/HU` con la Historia de Usuario representativa del módulo STK.
- **Dudas para retomar:** Confirmar convención de rama para los archivos de `gestion/` (ver punto pendiente arriba).

---

## 2026-10-01 — Sesión 2
**Duración aprox.:** ~30 min · **Quién:** Usuario

- **Objetivo de la sesión:** Repasar la metodología de `gestion/` y resolver la duda sobre crear o no el tablero de GitHub Projects.
- **Hecho:**
  - Se recorrió `gestion/` completa (README, DECISIONES, ESTADO, BITACORA) y se confirmó el estado dejado por la sesión anterior.
  - Se discutió si crear el GitHub Project ahora; el usuario planteó que es burocracia excesiva trabajando en solitario.
- **Decidido:** (ver DECISIONES.md)
  - DEC-002 — Posponer el GitHub Project (tablero Kanban) hasta sumar a la segunda persona; mientras tanto, seguir solo con ESTADO + BITÁCORA + DECISIONES.
- **Cerrado:**
  - La duda abierta sobre Project vs. labels, registrada en la sesión anterior.
- **Pendiente / abierto:**
  - Revisar qué requisitos o reglas de negocio quedan sin validar en `docs/` para continuar el análisis.
- **Problemas o aprendizajes:**
  - El nivel de proceso debe ajustarse al tamaño del equipo: con una sola persona trabajando, el tablero Kanban no resuelve ningún problema real todavía.
- **Próximo paso:** Continuar la etapa de análisis funcional revisando `docs/` pendientes.
- **Dudas para retomar:** Ninguna por el momento.

---

## 2026-09-25 — Sesión 1
**Duración aprox.:** ~1 h · **Quién:** Usuario

- **Objetivo de la sesión:** Resolver la pérdida del historial de chat y definir una metodología de gestión que no dependa de él.
- **Hecho:**
  - Se confirmó que el proyecto y sus archivos siguen intactos; lo que no persistió fue el historial de conversaciones de Copilot.
  - Se diseñó un Kanban liviano (Backlog → Por Hacer → En curso → En revisión → Hecho) apoyado en los Issues de GitHub como unidad de tarea.
  - Se creó la carpeta `gestion/` con `DECISIONES.md`, `ESTADO.md`, `BITACORA.md` y `README.md`.
- **Decidido:** (ver DECISIONES.md)
  - DEC-001 — Adoptar el sistema de gestión en `gestion/` con Issues de GitHub como unidad de tarea.
- **Cerrado:**
  - Puesta en marcha de la carpeta `gestion/` y sus plantillas.
- **Pendiente / abierto:**
  - Cargar las primeras tareas reales como Issues y mapearlas a las columnas del Kanban.
  - Confirmar si se va a usar GitHub Projects para visualizar el tablero.
- **Problemas o aprendizajes:**
  - Un repositorio Git no da privacidad por archivo: `BITACORA.md` es visible para cualquiera con acceso al repo, así que se trata como bitácora de trabajo, no como notas personales.
- **Próximo paso:** Abrir el primer Issue de esta etapa y probar el flujo completo con un caso real.
- **Dudas para retomar:** ¿Qué convención de labels o columnas se va a usar en GitHub para representar cada estado del Kanban?

---

## AAAA-MM-DD — Sesión N *(plantilla de ejemplo, no es una sesión real, no se borra)*
**Duración aprox.:** X h · **Quién:** nombres

- **Objetivo de la sesión:**
- **Hecho:**
  -
- **Decidido:** (ver DECISIONES.md)
  - DEC-000 — título
- **Cerrado:**
  -
- **Pendiente / abierto:**
  -
- **Problemas o aprendizajes:**
  -
- **Próximo paso:**
- **Dudas para retomar:**