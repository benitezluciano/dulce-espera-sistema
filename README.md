# Dulce Espera — Sistema de gestión de stock y ventas

Sistema interno para la gestión de inventario y ventas de un emprendimiento de indumentaria infantil.

## Sobre el proyecto

Dulce Espera es un emprendimiento de venta de indumentaria y accesorios infantiles. Actualmente, la consulta del stock depende principalmente del conocimiento de la propietaria y de la revisión física del local.

El proyecto propone una herramienta accesible desde el celular para consultar rápidamente la disponibilidad de productos, talles, colores y variantes, registrar ventas y mantener actualizado el inventario.

El objetivo principal es que la propietaria pueda responder consultas de clientes y tomar decisiones de reposición sin tener que revisar físicamente toda la mercadería.

## Alcance del MVP

El sistema contempla inicialmente:

- Administración de categorías, productos y variantes.
- Registro de stock por talle, género, color y temporada.
- Búsqueda y filtrado de productos.
- Registro de ventas y actualización automática del stock.
- Registro de ventas fiadas y cobros pendientes.
- Correcciones manuales de inventario.
- Identificación de productos con stock bajo o agotado mediante el orden de los resultados de búsqueda (en reemplazo de un módulo de reportes, descartado del MVP).
- Anulación de ventas con restitución de stock.
- Uso prioritario desde dispositivos móviles.

El sistema será de uso interno y no funcionará como una tienda online pública.

## Estado actual

- Relevamiento del negocio: completado.
- Alcance funcional inicial: definido y aprobado.
- Procesos AS-IS y TO-BE: diagramados (consulta de stock y venta).
- Requisitos funcionales y no funcionales, reglas de negocio: completos.
- Historias de usuario (20) y casos de uso (20): completos.
- Diseño de interfaz: en elaboración (mapa de navegación, inventario de pantallas y fichas UI-01 a UI-03; wireframes pendientes).
- Modelo de datos: pendiente.
- Implementación del MVP: próxima etapa.

## Mi participación

Proyecto realizado como parte de mi formación en análisis funcional de sistemas.

Mi participación incluye:

- Relevamiento del negocio y entrevistas.
- Identificación de actores, problemas y necesidades.
- Definición del alcance del MVP.
- Análisis de procesos actuales y propuestos.
- Elaboración de requisitos funcionales.
- Redacción de historias de usuario y casos de uso.
- Modelado de datos y documentación de reglas de negocio.
- Análisis de alternativas de solución.

## Documentación

- [Alcance del proyecto](docs/01-alcance.md)
- [Stakeholders](docs/02-stakeholders.md)
- [Relevamiento del negocio](docs/03-relevamiento.md)
- [Requisitos](docs/04-requisitos.md)
- [Reglas de negocio](docs/05-reglas-de-negocio.md)
- [Historias de usuario](docs/06-historias-de-usuario.md)
- [Casos de uso](docs/07-casos-de-uso.md)
- [Modelo de datos](docs/08-modelo-de-datos.md)
- [Diseño de interfaz](docs/09-interfaz-usuario.md)
- [Alternativas de solución](docs/10-alternativas-de-solucion.md)

## Enfoque de implementación

Para la primera versión se seleccionó una alternativa de bajo costo basada en Google Sheets y Google Apps Script, con una interfaz web responsive accesible desde el celular.

A futuro, el sistema podría evolucionar hacia una aplicación web con una base de datos estructurada y mayor capacidad de crecimiento.

## Contexto académico

El proyecto continúa en desarrollo. La documentación se actualiza progresivamente a medida que se validan los requisitos y se construye el MVP.
