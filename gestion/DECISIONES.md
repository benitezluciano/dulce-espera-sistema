### DEC-000 — Título corto y claro *(plantilla de ejemplo, no es una decisión real, no se borra)*

- **Fecha:** AAAA-MM-DD
- **Estado:** Propuesta | Cerrada | Reemplazada por DEC-000
- **Participantes:** quiénes intervinieron
- **Contexto:** qué problema o necesidad motivó la decisión.
- **Decisión:** qué se resolvió, en una o dos frases.
- **Alternativas consideradas:**
  - Opción A: por qué se descartó.
  - Opción B: por qué se descartó.
- **Consecuencias:** qué implica (ventajas, costos, riesgos, tareas derivadas).
- **Relacionado con:** Issues, PRs u otras decisiones (#12, DEC-002).

---

### DEC-001 — Adoptar una metodología de gestión liviana con GitHub Issues como unidad de tarea

- **Fecha:** 2026-09-25
- **Estado:** Cerrada
- **Participantes:** Usuario (rol de PM/analista funcional del proyecto)
- **Contexto:** El historial de conversaciones de Copilot no es persistente entre sesiones; al retomar el proyecto después de un tiempo sin abrirlo, se perdió el registro de qué se había decidido y por qué. Además, se prevé sumar a una segunda persona (desarrolladora) al proyecto, por lo que la información de avance no puede depender de la memoria de una sola persona ni de un chat.
- **Decisión:** Crear la carpeta `gestion/` con tres archivos versionados (`DECISIONES.md`, `ESTADO.md`, `BITACORA.md`) más un `README.md` con las reglas de uso. El flujo de trabajo se organiza como un Kanban liviano (Backlog → Por Hacer → En curso → En revisión → Hecho), usando los Issues de GitHub —que ya se venían usando en el proyecto— como la unidad atómica de tarea.
- **Alternativas consideradas:**
  - Confiar en el historial de chat de Copilot: descartada porque no persiste de forma confiable entre sesiones.
  - Usar solo Issues de GitHub sin un registro de decisiones aparte: descartada porque un Issue documenta una tarea, pero no el razonamiento de por qué se eligió un camino y se descartó otro.
  - Sumar una herramienta externa de gestión (Trello, Notion, etc.): descartada por ahora para no fragmentar la información fuera del repositorio versionado.
- **Consecuencias:** Cada sesión relevante debe cerrar con una actualización de `ESTADO.md` y una entrada en `BITACORA.md`. Las decisiones de fondo (alcance, tecnología, reglas de negocio) deben quedar registradas acá con un ID `DEC-XXX` antes de considerarse cerradas.
- **Relacionado con:** #23

---

### DEC-002 — Posponer GitHub Projects (tablero Kanban) hasta sumar a la segunda persona

- **Fecha:** 2026-10-01
- **Estado:** Cerrada
- **Participantes:** Usuario (rol de PM/analista funcional del proyecto)
- **Contexto:** Se evaluó crear el tablero de GitHub Projects ahora para representar las columnas del Kanban (Backlog → Por Hacer → En curso → En revisión → Hecho). El usuario está trabajando solo en la etapa de análisis funcional y considera que montar el tablero en este momento es burocracia innecesaria que le resta foco a terminar el análisis, además de no tener aún claro cómo usarlo en la práctica.
- **Decisión:** No crear el GitHub Project por ahora. Mientras el usuario trabaje en solitario, se sigue solo el flujo interno de `gestion/` (`ESTADO.md` + `BITACORA.md` en cada sesión, `DECISIONES.md` para decisiones de fondo), sin tablero ni labels de Kanban. El tablero se retoma y se estudia en profundidad recién cuando se sume la segunda persona (desarrolladora) y haya tareas reales de desarrollo que coordinar entre dos.
- **Alternativas consideradas:**
  - Crear el Project ahora, vacío, para tenerlo listo: descartada porque un tablero sin contenido real no valida si el flujo de 5 columnas funciona, y agrega carga de configuración sin beneficio inmediato trabajando en solitario.
  - Usar labels (`backlog`, `por-hacer`, `en-curso`) sin tablero visual: descartada por ahora también, ya que ni siquiera esa capa liviana es necesaria mientras hay una sola persona trabajando.
- **Consecuencias:** Se actualiza `ESTADO.md` para sacar el Project de los pendientes. Cuando se sume la segunda persona, habrá que retomar este punto como una nueva tarea/Issue antes de empezar a coordinar trabajo entre dos.
- **Relacionado con:** DEC-001

---

### DEC-003 — Criterio de corte para redactar Historias de Usuario (vertical slicing)

- **Fecha:** 2026-10-05
- **Estado:** Cerrada
- **Participantes:** Usuario (rol de PM/analista funcional del proyecto)
- **Contexto:** Al redactar la primera Historia de Usuario del módulo CAT, surgió la duda de si separar en historias distintas el alta de datos básicos de un producto (nombre, categoría, variantes) y el alta de sus atributos comerciales (precio, marca, temporada), ya que cada uno agrupa RF distintos.
- **Decisión:** Las Historias de Usuario se dividen por **valor de negocio completo y usable (corte vertical)**, no por agrupación técnica o tipo de atributo (corte horizontal). Una historia solo se separa de otra cuando el fragmento resultante sigue siendo útil y verificable por sí mismo sin obligar a la usuaria a completar otra historia antes de poder usarlo. Por eso, el alta completa de un producto (datos básicos + atributos comerciales + variantes) queda en una sola historia (HU-01), ya que un producto sin precio o sin variantes no es vendible ni stockeable por sí solo.
- **Alternativas consideradas:**
  - Separar en dos historias (datos básicos vs. atributos comerciales): descartada porque ninguna de las dos mitades resultantes es útil de forma independiente; viola el criterio "Valiosa" de INVEST.
- **Consecuencias:** Este criterio se aplica como estándar para el resto de las Historias de Usuario del proyecto (`docs/06-historias-de-usuario.md`), incluidas las de los módulos STK, BUS, VTA, FIA, PAG y ANU aún pendientes de redactar.
- **Relacionado con:** #23, `docs/06-historias-de-usuario.md`

---

### DEC-004 — Cierre del estado "transferencia pendiente" mediante una confirmación simple

- **Fecha:** 2026-10-24
- **Estado:** Cerrada
- **Participantes:** Usuario (rol de PM/analista funcional del proyecto)
- **Contexto:** Al redactar la Historia de Usuario de ventas (módulo VTA) se detectó que `RF-VTA-13` permitía registrar una venta con transferencia pendiente de confirmación, pero ningún requisito definía cómo se cerraba ese estado una vez acreditado el pago.
- **Decisión:** Se agrega `RF-VTA-17` y la regla `RN40`: el sistema debe permitir marcar como confirmada una venta con transferencia pendiente, sin modificar ningún otro dato de la venta. Se optó explícitamente por la alternativa más simple (un cambio de estado) para no agregar complejidad de desarrollo evitable.
- **Alternativas consideradas:**
  - No contemplar ninguna acción de cierre y dejar el estado "pendiente" sin resolución formal en el MVP: descartada porque una venta real quedaría para siempre sin poder contabilizarse como cobrada.
  - Diseñar un flujo más completo de conciliación de transferencias (con comprobantes, fechas de acreditación, etc.): descartada por desproporcionada para el volumen y el contexto de una única usuaria; se prioriza la opción de menor esfuerzo de implementación.
- **Consecuencias:** Se actualizan `docs/04-requisitos.md` (RF-VTA-17), `docs/05-reglas-de-negocio.md` (RN40) y `docs/06-historias-de-usuario.md` (HU-08).
- **Relacionado con:** #23, `docs/06-historias-de-usuario.md`