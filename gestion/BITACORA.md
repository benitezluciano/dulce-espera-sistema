## 2026-11-24 — Sesión 9
**Duración aprox.:** No registrada · **Quién:** Usuario con asistencia de Claude Code

- **Objetivo de la sesión:** Resolver conversando los puntos abiertos de UI-03 y redactar la ficha (DEC-008).
- **Hecho:**
  - Se explicaron y resolvieron los cinco puntos abiertos de UI-03 en el chat, antes de escribir nada. Se descartó el borrador previo de la ficha.
  - Se redactó la ficha UI-03 (Alta y edición de producto) sin lista de dudas pendientes, con tres modos: alta, edición y agregar variante.
  - Se agregó la inactivación de variantes: HU-20, CU-20, RF-CAT-25 a RF-CAT-28, RF-STK-21, RF-VTA-23, RN46 y RN47; se extendieron RF-BUS-09 y RF-BUS-10 y se ajustaron CU-03, CU-04, CU-05 y CU-07, y las fichas UI-01 y UI-02.
  - Se aplicaron los criterios de formulario: precio mayor a cero (RF-CAT-07, RN48), marca opcional de texto libre (RF-CAT-02), RNF-04 aclarado para permitir el alta rápida de valores de catálogo, y la sección 4.1 de requisitos corregida.
  - Se agregó UI-14 (menú de Administración) al inventario y se ajustó el mapa de navegación.
  - Se corrigió el typo "variamtes" en la ficha UI-01 y se actualizó el README (20 HU y 20 CU).
  - Tras el merge del PR #43, se detectó que la ficha UI-02 no indicaba cuándo ocultar "Agregar variante" (producto inactivo o con variante única activa), a diferencia de UI-03. Se corrigió en la rama `docs/UI-02-ajuste-agregar-variante` (PR #44) y se redactó un sub-issue de ajuste del wireframe para Gabi, que ya había terminado UI-02 antes de DEC-009.
  - Se mergearon en `main` los PR #43 (ficha UI-03) y #44 (ajuste de UI-02), ambos con merge commit. Se borraron, en local y remoto, las ramas `docs/UI-03`, `docs/UI-02-ajuste-agregar-variante` y `docs/add-wireframe-link` (fusionada en el PR #38). Queda solo `main`.
  - Por indicación del usuario, la actualización del estado del wireframe en la ficha UI-02 (elaborado en Figma, pendiente de ajuste por DEC-009) se hizo directo en `main`, por ser un cambio de una sola línea. El push no fue rechazado: `main` no tiene protección de rama.
- **Decidido:** (ver DECISIONES.md)
  - DEC-009 — Las variantes se inactivan y se reactivan; no se eliminan.
  - DEC-010 — Criterios del formulario de producto ("No aplica" literal, alta rápida de valores, precio mayor a cero, marca opcional, Administración como menú).
- **Cerrado:**
  - Ficha UI-03.
  - Vacío de requisito sobre corregir o retirar variantes.
- **Pendiente / abierto:**
  - Crear en GitHub, si aún no existen, los sub-issues de #29: ficha UI-03, wireframe UI-03, ajuste del wireframe UI-02 (texto preparado) y los dos hijos pendientes ("Inventario de pantallas y mapa de navegación" y "Definir ficha UI-01 Buscar stock"). Registrar sus números en `ESTADO.md`.
  - Actualizar en la ficha UI-01 el estado de su wireframe (ya elaborado en Figma) y sumar UI-03 al `wireframe.md` cuando Gabi lo entregue.
  - Redactar UI-04 a UI-13, el Modelo de Datos y el diagrama de casos de uso. El modelo de datos debe reflejar el estado activo/inactivo de las variantes.
  - Verificar con un prototipo mínimo los dos puntos abiertos de DEC-006.
  - Definir planilla de carga inicial y listas de motivos.
  - Activar en GitHub "Automatically delete head branches" (sugerido).
- **Problemas o aprendizajes:**
  - Cuando un entregable ya fue tomado por otra persona (el wireframe de UI-02 por Gabi), un cambio posterior en la ficha obliga a abrir un ajuste explícito; conviene comparar la versión anterior con la nueva y listar qué debe rehacer quien ya terminó.
  - Resolver los puntos abiertos antes de escribir evitó redactar una ficha que habría quedado desactualizada: dos de las cinco dudas cambiaron documentos ya cerrados (RN16 se mantuvo y se creó la inactivación de variantes).
  - Un mismo patrón de vacío apareció de nuevo: se definía cómo crear algo (variantes) pero no cómo retirarlo.
- **Próximo paso:** Ficha UI-04 (Carga inicial de stock), en una rama nueva desde `main`, conversando antes las columnas y valores permitidos de la planilla.
- **Dudas para retomar:** Ninguna nueva.

---

## 2026-11-20 — Sesión 8
**Duración aprox.:** No registrada · **Quién:** Usuario con asistencia de Claude Code

- **Objetivo de la sesión:** Recorrer todo el proyecto para recuperar el contexto, corregir las inconsistencias documentales, definir la autenticación, ordenar las ramas y preparar el inicio de la ficha UI-03.
- **Hecho:**
  - Se recorrió el repositorio completo (docs, gestión, diagramas y cuestionario) y se contrastó el estado real con lo registrado en `ESTADO.md` y el README.
  - Se reescribió `ESTADO.md`: figura la ficha UI-02 como cerrada, se agregaron los pendientes de modelo de datos, diagrama de casos de uso y vacíos de diseño (autenticación, planilla de carga inicial, listas de motivos).
  - Se corrigió el link del README al documento de interfaz (`09-interfaz-usuario.md`) y se actualizó su sección de estado y alcance del MVP.
  - Se eliminaron las menciones residuales a "reportes mensuales" que contradecían su descarte (README, `01-alcance.md`, RF-ANU-05, RN37, `10-alternativas-de-solucion.md`). Las menciones históricas en la bitácora y en HU-06/CU-06 se conservan porque documentan el descarte.
  - Se corrigió el typo "inacgittivo" en RN44.
  - Se deja constancia de trabajo previo sin entrada propia en la bitácora: la ampliación a HU-15 a HU-19 y CU-15 a CU-19 (la Sesión 6 registra solo 14 CU; hoy son 19) y la ficha UI-02 (commit `4d18adc`).
  - Se creó la rama `docs/UI-acceso-y-limpieza` (a partir de `docs/UI`) para separar este trabajo del PR de UI.
  - Se eliminaron `RECURSOS.md` e `integrantes.md` (restos de la plantilla académica; estaban en `.gitignore`, solo existían en local) y se limpió el `.gitignore`. El proyecto pasa a tener enfoque de portfolio profesional.
  - Se definió la autenticación: sin pantalla de login propia, acceso con la cuenta de Google. Se reformuló RNF-08, se actualizó el mapa de navegación (nuevo estado transversal "Acceso no autorizado") y se agregó un supuesto en `01-alcance.md`.
  - Se fusionaron en `main` los PR de `docs/UI` y `docs/UI-acceso-y-limpieza` (PR #40) con merge commit.
  - Se borraron, en local y remoto, las ramas ya fusionadas: `docs/UI`, `docs/UI-acceso-y-limpieza`, `docs/CU`, `docs/CU-HU-17-19`, `docs/alcance`, `docs/requisitos` y `diagramas`. Las dos últimas tenían commits locales que no estaban en su remota; se verificó que todos estaban en `main` antes de forzar el borrado.
  - Se creó la rama `docs/UI-03` desde `main` actualizada y se redactó el texto del Issue "Definir ficha UI-03 Alta y edición de producto" (pendiente de crear en GitHub, como parte de #29).
  - Se redactó un borrador completo de la ficha UI-03 en `docs/09-interfaz-usuario.md`, con una lista de puntos a validar. El usuario indicó que no debía escribirse antes de resolver esos puntos conversando; el borrador quedó **sin commitear** y se rehará (ver DEC-008).
- **Decidido:** (ver DECISIONES.md)
  - DEC-006 — Autenticación mediante la cuenta de Google, sin pantalla de login propia.
  - DEC-007 — Una rama por tarea, desde `main` actualizada, fusionada con merge commit.
  - DEC-008 — Conversar los puntos abiertos antes de redactar un entregable.
- **Cerrado:**
  - Revisión de consistencia documental.
  - Definición de la pantalla inicial y del mecanismo de acceso.
  - Limpieza de ramas y definición del flujo de ramas.
- **Pendiente / abierto:**
  - Conversar los puntos abiertos de UI-03 antes de redactar la ficha (ver "Dudas para retomar"). Decidir si se descarta el borrador sin commitear de `docs/09-interfaz-usuario.md`.
  - Crear en GitHub el Issue de UI-03 y los dos issues hijos pendientes de #29; abrir los de wireframe de UI-01 y UI-02.
  - Redactar UI-04 a UI-13, el Modelo de Datos y el diagrama de casos de uso.
  - Verificar con un prototipo mínimo los dos puntos abiertos de DEC-006 (propiedad del script y varias cuentas de Google).
  - Definir planilla de carga inicial y listas de motivos.
  - Decidir qué hacer con la rama remota `docs/add-wireframe-link` (referencia a un wireframe de Figma, no fusionada).
  - Activar en GitHub "Automatically delete head branches" (sugerido).
  - Typo menor sin corregir: "variamtes" en la ficha UI-01 de `09-interfaz-usuario.md`.
- **Problemas o aprendizajes:**
  - El trabajo de las sesiones intermedias no quedó registrado en `gestion/`, por lo que `ESTADO.md` y el README fueron quedando atrás. Conviene cerrar cada sesión actualizando `ESTADO.md` y la bitácora antes del commit.
  - Pedir "empezamos a trabajar en una ficha" no equivale a pedir su redacción: si hay puntos sin definir, primero se conversa (DEC-008).
  - Un "squash and merge" rompería la ascendencia de los commits y generaría conflictos en las ramas derivadas; por eso se usa merge commit (DEC-007).
- **Próximo paso:** Conversar los puntos abiertos de UI-03 y, con una confirmación final, redactar la ficha.
- **Dudas para retomar:** Puntos sobre UI-03 detectados al preparar el borrador, a resolver conversando: (1) si "No aplica" es por atributo o por producto (RN16 y RF-CAT-10 hablan de "variante única", pero una vincha podría no tener talle y venir en varios colores); (2) cómo corregir o retirar una variante cargada por error, que ningún requisito cubre (RF-STK-12); (3) qué es la pantalla Administración, que figura en el mapa pero no en el inventario de pantallas; (4) si se puede agregar un valor de catálogo desde el formulario de producto, dado RNF-04; (5) reglas finas de datos: si el precio cero es válido y si la marca lleva sugerencias de las ya usadas.

---

## 2026-11-02 — Sesión 7
**Duración aprox.:** No registrada · **Quién:** Usuario

- **Objetivo de la sesión:** Ordenar el avance de diseño UI bajo la Issue coordinadora #29, documentar los dos trabajos ya completados y adaptar la gestión a la incorporación próxima de Gabi.
- **Hecho:**
  - Se acordó Buscar como pantalla inicial, la navegación principal Buscar / Ventas / Fiados / Administración y el término visible "Cliente".
  - Se incorporaron a `docs/09-interfaz-usuario.md` los criterios globales, el mapa de navegación y el inventario de 13 pantallas/flujo trazado a las 19 HU y los 19 CU.
  - Se redactó la ficha de UI-01 Buscar con patrones, justificación, interacciones, filtros, validaciones, estados, accesibilidad y una prueba del recorrido crítico.
  - Se prepararon dos borradores de issues hijos para #29: "Inventario de pantallas y mapa de navegación" y "Definir ficha UI-01 Buscar stock". Sus números quedan pendientes de creación en GitHub.
  - Se aclaró que el wireframe visual de UI-01 aún no está hecho y debe tener un issue de entrega separado; no se cerrará como realizado por la ficha solamente.
  - El usuario creó el GitHub Project Kanban Liviano y prevé sumar a Gabi para colaborar en diseño y wireframes.
- **Decidido:** (ver DECISIONES.md)
  - DEC-005 — Utilizar GitHub Projects para coordinar el trabajo con Gabi; DEC-002 queda reemplazada.
- **Cerrado:**
  - Inventario de pantallas y mapa de navegación en el documento UI.
  - Ficha de interfaz UI-01 Buscar.
- **Pendiente / abierto:**
  - Crear en GitHub los dos issues hijos ya redactados, vincularlos a #29 y cerrarlos una vez registrados como completados.
  - Crear un issue separado para el wireframe visual de UI-01 y asignarlo cuando Gabi se incorpore.
  - Completar las fichas UI-02 a UI-07 antes de delegar esos wireframes.
  - Incorporar formalmente a Gabi al repositorio y al flujo de PR; añadir los números de Issues a `ESTADO.md` cuando existan.
  - Avanzar en paralelo con el Modelo de Datos.
- **Problemas o aprendizajes:**
  - Una ficha de interfaz y su wireframe son entregables distintos: documentar el comportamiento de UI-01 no significa que ya exista su diseño visual.
  - El Project visualiza el flujo de Issues entre colaboradores; `gestion/` sigue conservando el estado del proyecto y las decisiones duraderas.
- **Próximo paso:** Crear los dos issues hijos usando los borradores preparados, enlazarlos a #29 y abrir la tarea visual de UI-01 para Gabi.
- **Dudas para retomar:** Definir con Gabi el formato de entrega del wireframe (archivo editable/exportación o enlace) al asignar la tarea.

---

## 2026-10-26 — Sesión 6
**Duración aprox.:** No registrada · **Quién:** Usuario

- **Objetivo de la sesión:** Registrar el cierre de la tarea de Casos de Uso.
- **Hecho:**
  - Se completó `docs/07-casos-de-uso.md` con 14 casos de uso (CU-01 a CU-14), trazados a las Historias de Usuario, requisitos y reglas de negocio.
  - El usuario confirmó que los casos cumplen los criterios de aceptación del Issue correspondiente.
  - Quedó habilitado el siguiente trabajo acordado: preparar wireframes únicamente para los módulos ya elaborados, comenzando por CAT y STK.
- **Decidido:** No surgieron decisiones de fondo nuevas; no se agrega una entrada a `DECISIONES.md`.
- **Cerrado:**
  - Tarea de Casos de Uso: 14 CU completos.
- **Pendiente / abierto:**
  - Revisar y mergear la rama `docs/CU` a `main`.
  - Crear la tarea/módulo de diseño UI y preparar el encargo de wireframes para CAT y STK.
  - Elaborar el Modelo de Datos.
- **Problemas o aprendizajes:**
  - La trazabilidad CU → HU → RF y reglas de negocio permite revisar que los escenarios detallados cubran el comportamiento acordado, además de servir como base para wireframes.
- **Próximo paso:** Revisar el Pull Request de `docs/CU` y, tras el merge, preparar el trabajo de wireframes de CAT y STK.
- **Dudas para retomar:** Ninguna nueva.

---

## 2026-10-25 — Sesión 5
**Duración aprox.:** ~1 h · **Quién:** Usuario

- **Objetivo de la sesión:** Cerrar la redacción de Historias de Usuario completando los módulos FIA, PAG y ANU, y dejar la rama `docs/HU` lista para mergear a `main`.
- **Hecho:**
  - Se cerró el módulo FIA con tres historias (`HU-09` a `HU-11`): asociar una venta fiada a una persona (existente o nueva), consultar el historial y saldo de la cuenta corriente, y modificar los datos personales sin alterar el historial.
  - Se cerró el módulo PAG con una sola historia (`HU-12`): registrar un pago parcial o total, ya que todos sus RF describen un único acto de negocio indivisible.
  - Se cerró el módulo ANU con dos historias (`HU-13`, `HU-14`): anulación general de una venta, y el caso especial de anular una venta fiada con pagos parciales mediante un ajuste separado.
  - Con esto, `docs/06-historias-de-usuario.md` queda completo: 14 Historias de Usuario cubriendo los 7 módulos del sistema (CAT, STK, BUS, VTA, FIA, PAG, ANU).
- **Decidido:** Ninguna decisión de fondo nueva en esta sesión; se aplicó el criterio ya vigente de DEC-003 para los módulos restantes.
- **Cerrado:**
  - Documento completo de Historias de Usuario (`HU-01` a `HU-14`).
  - Rama `docs/HU` lista para Pull Request y merge a `main`.
- **Pendiente / abierto:**
  - Mergear `docs/HU` a `main`.
  - Redactar al menos un Caso de Uso antes de delegar wireframes.
  - Armar el encargo acotado de wireframes (CAT + STK) para una tercera persona.
- **Problemas o aprendizajes:**
  - No todos los módulos requieren el mismo número de historias: cuando todos los RF de un módulo describen un único acto indivisible (como en PAG), alcanza con una sola historia bien delimitada; forzar una división ahí sería un corte artificial sin valor, igual que fusionar sin criterio sería forzar demasiado junto.
- **Próximo paso:** Mergear `docs/HU` a `main` y arrancar la redacción de Casos de Uso.
- **Dudas para retomar:** Confirmar el mismo criterio de registrar `gestion/` en la próxima rama de trabajo (Casos de Uso) y mergearla pronto.

---

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