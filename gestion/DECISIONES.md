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
- **Estado:** Reemplazada por DEC-005
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

---

### DEC-005 — Usar GitHub Projects para coordinar el trabajo con Gabi

- **Fecha:** 2026-11-02
- **Estado:** Cerrada
- **Participantes:** Usuario (responsable del análisis y coordinación del proyecto)
- **Contexto:** DEC-002 pospuso el tablero mientras el usuario trabajaba en solitario. Ahora se creó un GitHub Project con un Kanban liviano y se prevé sumar a Gabi para colaborar en el diseño y los wireframes.
- **Decisión:** Utilizar el GitHub Project creado para visualizar y coordinar las Issues del trabajo de interfaz cuando Gabi se incorpore. Mantener `gestion/` como registro versionado del estado y las decisiones; las Issues siguen siendo las unidades de trabajo y cada entrega se revisa mediante PR.
- **Alternativas consideradas:**
  - Continuar solo con `ESTADO.md` y `BITACORA.md`, sin tablero: descartada porque habrá trabajo distribuido entre dos personas y entregas dependientes.
  - Usar únicamente Issues sin una vista Kanban: descartada porque el Project ya está creado y permite ver el avance y las dependencias de las entregas.
- **Consecuencias:** DEC-002 queda reemplazada. Se organizará el trabajo de UI bajo la Issue coordinadora #29 y sus Issues hijas; antes de asignar trabajo, se completará la incorporación de Gabi al repositorio y al flujo de revisión.
- **Relacionado con:** DEC-001, DEC-002, Issue #29

---

### DEC-006 — Autenticación mediante la cuenta de Google, sin pantalla de login propia

- **Fecha:** 2026-11-20
- **Estado:** Cerrada
- **Participantes:** Usuario (responsable del análisis y coordinación del proyecto)
- **Contexto:** El mapa de navegación de `docs/09-interfaz-usuario.md` dejaba pendiente si la pantalla inicial debía tener un login propio. RNF-08 exigía "usuario y contraseña", sin precisar el mecanismo. La alternativa elegida (Google Sheets + Apps Script, ver `10-alternativas-de-solucion.md`) no ofrece un lugar seguro para guardar credenciales, y el objetivo de UI-01 es responder una consulta con pocos toques.
- **Decisión:** No habrá pantalla de login propia. El acceso se controla con la autenticación de Google: la aplicación web se publica con acceso restringido a la cuenta de la propietaria, la planilla de datos se comparte únicamente con esa cuenta y se recomienda activar la verificación en dos pasos. Opcionalmente, el servidor verifica que el correo de quien accede sea el autorizado. La pantalla inicial es Buscar (UI-01); el rechazo de una cuenta no autorizada es un estado transversal.
- **Alternativas consideradas:**
  - Login propio con usuario y contraseña guardados en una hoja de cálculo: descartada porque almacenar credenciales en Sheets es menos seguro que no tener login propio, y agrega pasos al recorrido crítico de consulta.
  - Aplicación publicada con acceso abierto y un PIN o clave dentro de la aplicación: descartada por la misma razón y porque expone los datos a cualquiera que tenga el enlace.
  - Sin ninguna restricción de acceso: descartada porque la información de stock, ventas y deudas de terceras personas es sensible.
- **Consecuencias:** Se reformula RNF-08 y se actualizan el mapa de navegación de `docs/09-interfaz-usuario.md` y los supuestos de `docs/01-alcance.md`. Quedan dos puntos a verificar con un prototipo mínimo antes de implementar: (1) el script debe pertenecer a la cuenta de Silvia, o transferirse, para publicarse con acceso restringido a ella; (2) el comportamiento de Apps Script cuando el celular tiene varias cuentas de Google con sesión abierta.
- **Relacionado con:** RNF-08, DEC-001, `docs/10-alternativas-de-solucion.md`

---

### DEC-007 — Una rama por tarea, desde `main` actualizada, fusionada con merge commit

- **Fecha:** 2026-11-20
- **Estado:** Cerrada
- **Participantes:** Usuario (responsable del análisis y coordinación del proyecto)
- **Contexto:** Se venía reutilizando la rama `docs/UI` para varias tareas y se acumularon ramas ya fusionadas sin borrar. Al separar el trabajo de autenticación y limpieza, se comprobó que reutilizar una rama larga obliga a verificar a mano qué commits están o no en `main`, y que un "squash and merge" reescribiría los commits y generaría conflictos en las ramas que parten de ellos.
- **Decisión:** Cada tarea (normalmente una Issue) tiene su propia rama, creada desde `main` actualizada (`git checkout main`, `git pull`) y nombrada con el patrón `docs/<tarea>` (por ejemplo, `docs/UI-03`). Se integra con un Pull Request usando **"Create a merge commit"**, nunca squash ni rebase. Después del merge se actualiza `main` y se borra la rama, local y remota, con `git branch -d`, que se niega a borrar si hay commits sin fusionar.
- **Alternativas consideradas:**
  - Reutilizar una rama larga para varias tareas (`docs/UI`): descartada porque mezcla trabajo nuevo con commits ya fusionados y complica el historial de cada PR.
  - Squash and merge: descartada porque rompe la ascendencia de los commits y genera conflictos en las ramas derivadas.
- **Consecuencias:** Quedan eliminadas las ramas ya fusionadas (`docs/UI`, `docs/UI-acceso-y-limpieza`, `docs/CU`, `docs/CU-HU-17-19`, `docs/alcance`, `docs/requisitos`, `diagramas`). Se recomienda activar en GitHub "Automatically delete head branches" (pendiente de confirmar por el usuario). La rama `docs/add-wireframe-link` no está fusionada y se decide aparte.
- **Relacionado con:** DEC-005, Issue #29

---

### DEC-008 — Conversar los puntos abiertos antes de redactar un entregable

- **Fecha:** 2026-11-20
- **Estado:** Cerrada
- **Participantes:** Usuario (responsable del análisis y coordinación del proyecto)
- **Contexto:** Al iniciar la ficha UI-03 se redactó el documento completo y se dejó al final una lista de "puntos a validar". Varios de esos puntos podían modificar documentos ya cerrados (RN16, RF-CAT-10, RF-STK-12), por lo que debían resolverse antes de escribir.
- **Decisión:** Cuando una tarea tenga decisiones sin definir o inconsistencias con documentos cerrados, no se redacta en los archivos. Primero se conversa en el chat y se hacen las preguntas necesarias; cuando haya información suficiente, se pide una confirmación final antes de redactar. Los documentos no incluyen secciones de dudas pendientes: lo resuelto queda como decisión (`DECISIONES.md`) o como requisito.
- **Alternativas consideradas:**
  - Redactar con una sección de "puntos a validar" al final: descartada porque deja dudas dentro de entregables que se delegan (por ejemplo, a Gabi) y puede propagar supuestos sin validar.
  - Que el asistente decida por defecto todo lo no definido: descartada porque algunas decisiones modifican requisitos y reglas ya aprobados.
- **Consecuencias:** Se espera una etapa de preguntas antes de cada ficha o documento nuevo. Los detalles menores con una opción razonable por defecto se resuelven y se informan sin consulta previa. Aplica también a quien colabore con el repositorio.
- **Relacionado con:** DEC-003, Issue #29