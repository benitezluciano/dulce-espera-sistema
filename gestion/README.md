# Registro de decisiones
 
> **Para qué sirve:** guardar *qué* se decidió y *por qué*, para no volver a discutirlo ni perderlo si se cierra un chat o pasan semanas.
>
> **Reglas:**
> 1. Una entrada por decisión, con ID correlativo (DEC-001, DEC-002...).
> 2. Se registra **en el momento** en que se decide, no al final de la semana.
> 3. **Nunca se borra** una decisión. Si cambia, se marca como `Reemplazada` y se enlaza la nueva.
> 4. Estados posibles: `Propuesta` (en discusión) · `Cerrada` (vigente) · `Reemplazada` (ya no vale).
> 5. Si una decisión no tiene "alternativas consideradas", probablemente no se pensó lo suficiente.
 
---
# Estado actual del proyecto
 
> **Para qué sirve:** una foto corta de "dónde estamos hoy". Es lo primero que se lee al empezar una sesión y lo que se le pide a Copilot que lea antes de trabajar.
>
> **Reglas:**
> 1. Se **reescribe** en cada sesión (no es un historial: el historial va en `BITACORA.md`).
> 2. Tiene que entrar en una pantalla. Si crece, se resume o los detalles pasan a Issues.
> 3. Cada ítem pendiente debería apuntar a un Issue o a una decisión cuando exista.
> 4. Si algo lleva mucho tiempo en "Bloqueado", es una señal para actuar, no para dejarlo ahí.
 
---

# Bitácora de sesiones
 
> **Para qué sirve:** registro cronológico de qué se hizo en cada sesión de trabajo. Es la memoria de largo plazo que reemplaza al historial de chat.
>
> **Reglas:**
> 1. Una entrada por sesión de trabajo (no hace falta que sea diaria; sí que sea cada vez que trabajás).
> 2. Las entradas **nuevas van arriba**, así lo último se ve primero.
> 3. Se escribe al **cerrar** la sesión (10 minutos). Podés pedirle a Copilot que arme el borrador a partir de lo que se hizo, pero revisalo vos.
> 4. Las entradas viejas **no se editan**: si algo cambió, se aclara en la entrada nueva.
> 5. Lo que se decidió va a `DECISIONES.md` y se enlaza acá; no se duplica el detalle.
> 6. Es una bitácora de trabajo, no un diario personal: cualquiera con acceso al repo puede leerla.

---

# Cómo se integra esto con los Issues de GitHub

> **Para qué sirve:** los tres archivos anteriores registran *decisiones* y *avance*, pero la unidad de trabajo del día a día sigue siendo el **Issue**. Este archivo explica cómo se conectan.

## El Kanban liviano

```
Backlog → Por Hacer → En curso → En revisión → Hecho
```

- **Backlog**: ideas o tareas identificadas pero todavía no priorizadas. Es un Issue abierto sin asignar y sin planificar para el corto plazo.
- **Por Hacer**: el Issue ya está redactado, priorizado y listo para que alguien lo tome.
- **En curso**: alguien lo está trabajando activamente ahora mismo.
- **En revisión**: el trabajo está terminado y se está verificando (por ejemplo, revisar un documento o probar una funcionalidad) antes de cerrarlo.
- **Hecho**: el Issue se cierra. Si generó una decisión de fondo, esa decisión queda en `DECISIONES.md`; si fue relevante para el avance general, se refleja en `ESTADO.md` y se resume en `BITACORA.md`.

Cómo representar estas columnas en GitHub: la forma más simple es un **GitHub Project (tablero)** con una columna por estado, moviendo el Issue de columna a medida que avanza. Como alternativa más liviana (sin tablero), se pueden usar **labels** (`backlog`, `por-hacer`, `en-curso`, `en-revision`) sobre cada Issue.

## Cómo escribir un buen Issue

El Issue #23 ("Definir requisitos funcionales y no funcionales") es un buen ejemplo a repetir. Su estructura es reutilizable para cualquier tarea nueva:

```md
## Objetivo
Una frase: qué se busca lograr con esta tarea.

## Tareas
- Paso concreto 1
- Paso concreto 2

## Criterios de aceptación
- Condición verificable 1
- Condición verificable 2
```

Un Issue así redactado responde solo, sin necesitar contexto adicional: dice para qué es, qué hay que hacer y cómo se sabe que está terminado.

## Cómo se conecta con los otros tres archivos

- En `ESTADO.md`, cada tarea de "En curso" o "Pendiente" referencia su número de Issue (`#23`).
- En `BITACORA.md`, cada sesión menciona qué Issues se abrieron, avanzaron o cerraron.
- En `DECISIONES.md`, el campo "Relacionado con" enlaza al Issue que originó o que quedó afectado por la decisión.
- Al cerrar un Issue con un commit o PR, usar `closes #23` en el mensaje para que GitHub lo cierre automáticamente y quede el enlace entre el código y la tarea.

---