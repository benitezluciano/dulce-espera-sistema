# Alcance del proyecto

## Proyecto: Sistema de Gestión — "Dulce Espera - Moda Infantil"

**Versión:** 1.0  
**Estado:** Aprobado por la propietaria  
**Fecha de aprobación:** 04/09/2026
**Usuaria principal:** Silvia Benítez, propietaria del negocio

---

## 1. Descripción del problema

### 1.1. Problema principal

Dulce Espera no dispone de un mecanismo confiable y ágil para consultar y controlar el stock disponible. Actualmente, la propietaria depende principalmente de su conocimiento personal y de revisiones físicas del local para confirmar qué productos tiene y en qué cantidad.

Esta situación se vuelve más compleja en productos con muchas variantes, como las medias, y cuando recibe consultas por WhatsApp o Instagram sobre la disponibilidad de un talle, color o género. Para responder, debe revisar físicamente la mercadería antes de poder confirmar la información.

### 1.2. Problema relacionado

La falta de información actualizada sobre el stock también dificulta la toma de decisiones para realizar nuevas compras. Cuando la propietaria encuentra una oferta de un proveedor, necesita verificar si ya posee ese producto antes de adquirirlo. Sin un inventario organizado y confiable, puede comprar mercadería que ya tiene o no identificar correctamente qué variantes necesita reponer.

### 1.3. Necesidad de negocio

La propietaria necesita una herramienta que le permita administrar y consultar el stock desde el celular, tanto dentro como fuera del local, para responder consultas de clientes y contar con información suficiente antes de decidir nuevas compras.

---

## 2. Objetivos y metas del proyecto

### 2.1. Objetivo general

Mejorar el control y la consulta del stock de Dulce Espera mediante una herramienta de uso interno, accesible desde el celular y capaz de mostrar de forma rápida y confiable la disponibilidad de los productos.

### 2.2. Metas específicas

- Centralizar la información del inventario en un único sistema.
- Registrar productos y variantes considerando categoría, grupo, talle, género, color, temporada, estampado cuando corresponda y cantidad.
- Consultar el stock desde el local o desde cualquier otro lugar con conexión a internet.
- Realizar búsquedas generales por categoría y búsquedas específicas combinando filtros.
- Actualizar automáticamente la cantidad disponible al registrar una venta.
- Facilitar la respuesta a consultas recibidas por WhatsApp e Instagram.
- Permitir verificar la existencia de un producto antes de comprar nueva mercadería.
- Permitir corregir manualmente las cantidades cuando se detecten diferencias físicas.
- Consultar productos agotados y reportes mensuales.
- Mantener una solución simple e intuitiva para una única usuaria.

---

## 3. Usuaria y contexto de uso

- La usuaria inicial será exclusivamente la propietaria.
- El dispositivo principal será el celular.
- La administración completa del sistema deberá poder realizarse desde el celular.
- La consulta podrá realizarse dentro o fuera del local.
- La conexión habitual será mediante wifi o datos móviles.
- No se considera necesario el funcionamiento sin conexión para el MVP.
- WhatsApp e Instagram continuarán siendo canales externos de comunicación y difusión.
- El sistema será de uso interno y no funcionará como una tienda online pública.

---

## 4. Entregas del proyecto

Las entregas documentales previstas son:

1. Documento de alcance.
2. Documento de relevamiento del negocio.
3. Requisitos funcionales y no funcionales.
4. Reglas de negocio.
5. Historias de usuario.
6. Casos de uso.
7. Modelado del proceso actual AS-IS.
8. Propuesta del proceso mejorado TO-BE.
9. Modelo de datos.
10. Diseño de interfaz priorizado para celular.
11. Diagramas del sistema.

La entrega de cada documento deberá mantener coherencia con el alcance aprobado y con la información obtenida durante el relevamiento.

La decisión sobre la alternativa tecnológica para la primera implementación y la solución objetivo se documenta en [`10-alternativas-de-solucion.md`](./10-alternativas-de-solucion.md). Esta decisión no modifica el alcance funcional: establece cómo se implementará inicialmente el MVP y cómo podría evolucionar posteriormente.

---

## 5. Funcionalidades incluidas

### 5.1. Administración del catálogo

El sistema permitirá administrar:

- categorías o tipos de producto, como body, remera, pantalón o medias;
- grupos comerciales, como bebé nena, bebé varón, junior, teen o neutro;
- talles;
- géneros: nena, varón y neutro;
- colores;
- temporadas;
- estampados cuando correspondan;
- productos y sus variantes.

La categoría representará el tipo de producto y el grupo representará una clasificación comercial o etaria. Por ejemplo, un body podrá pertenecer al grupo bebé nena.

### 5.2. Administración del stock

El sistema permitirá:

- cargar el stock inicial de una vez;
- completar posteriormente los productos que no hayan sido cargados en la primera carga;
- registrar cantidades por variante;
- diferenciar la cantidad por talle, color y género;
- asociar cada existencia a una temporada;
- registrar siempre el color;
- registrar un estampado de forma opcional;
- corregir manualmente una cantidad cuando exista una diferencia con el stock físico;
- conservar en las búsquedas los productos cuya cantidad sea cero.

### 5.3. Consulta y búsqueda

La propietaria podrá:

- iniciar una búsqueda por categoría;
- consultar todos los productos de una categoría;
- realizar búsquedas generales;
- combinar filtros según la necesidad;
- filtrar por grupo, género, talle, color, temporada y disponibilidad;
- consultar el stock desde fuera del local;
- consultar productos disponibles y agotados.

La búsqueda tendrá dos objetivos: responder consultas de clientes y verificar si un producto ya existe antes de comprarlo.

### 5.4. Registro de ventas

El sistema permitirá:

- registrar los productos y cantidades vendidos;
- registrar el precio de venta;
- registrar la fecha y el medio de pago;
- aplicar descuentos manuales cuando corresponda;
- registrar ventas fiadas;
- disminuir automáticamente el stock al registrar la venta;
- registrar posteriormente el cobro de una venta fiada;
- permitir la anulación de una venta, contemplando la restitución correspondiente del stock.

### 5.5. Registro mínimo para ventas fiadas

No se incluirá una base comercial general de clientes. Sí se incluirá un registro mínimo asociado exclusivamente a las ventas fiadas, que permitirá:

- asociar una venta fiada a una persona identificable;
- reutilizar los datos de una persona ya registrada;
- registrar una nueva persona cuando sea necesario;
- consultar las ventas fiadas pendientes;
- permitir varias ventas fiadas pendientes para una misma persona;
- registrar pagos parciales o totales, según el detalle que se defina en la etapa de requisitos;
- modificar los datos personales sin alterar el historial de ventas y cobros.

Los datos definidos como necesarios para una nueva persona son nombre, apellido y número de teléfono, siendo obligatorio este último.

### 5.6. Reportes mensuales

El MVP incluirá reportes mensuales básicos para consultar la información registrada durante un período. El contenido exacto de los reportes, sus filtros y los datos que mostrarán se definirán durante la especificación de requisitos.

---

## 6. Funcionalidades excluidas

Quedan fuera del MVP:

- venta online;
- carrito de compra;
- pagos online;
- gestión de envíos y pedidos;
- catálogo público para clientes;
- integración automática con WhatsApp o Instagram;
- respuestas automáticas y campañas de difusión;
- gestión comercial general de clientes;
- gestión formal de proveedores y cuentas por pagar;
- comparación automática de precios de proveedores;
- facturación electrónica y comprobantes fiscales;
- descuentos automáticos;
- funcionamiento sin conexión;
- múltiples usuarios y permisos complejos;
- aplicación móvil nativa específica para Android o iOS.

El sistema podrá ayudar a decidir una compra mostrando el stock existente, pero no administrará la relación completa con los proveedores.

---

## 7. Supuestos

Se adoptan los siguientes supuestos para esta versión del alcance:

- Silvia será la única usuaria inicial del sistema.
- La propietaria tendrá acceso habitual a internet mediante wifi o datos móviles.
- El celular será suficiente para administrar el catálogo, el stock, las ventas y las ventas fiadas.
- La propietaria será responsable de mantener actualizadas las cantidades registradas.
- La carga inicial del stock se realizará de una vez.
- Podrán agregarse posteriormente los productos que no hayan sido cargados en la primera instancia.
- Las redes sociales continuarán utilizándose fuera del sistema.
- El sistema se utilizará para gestión interna y no para vender directamente a clientes.
- Los reportes mensuales serán de carácter básico y su contenido se precisará más adelante.

---

## 8. Restricciones

El proyecto estará condicionado por las siguientes restricciones:

- La solución deberá priorizar el uso desde celular.
- El MVP requerirá conexión a internet.
- El sistema estará diseñado inicialmente para una única usuaria.
- El alcance se concentrará en stock, ventas, ventas fiadas y reportes básicos.
- No se incorporarán integraciones con redes sociales, proveedores ni servicios de facturación.
- La información de stock dependerá de que la propietaria registre correctamente las altas, ventas, anulaciones y correcciones.
- El modelo de talles deberá contemplar que los valores pueden variar entre proveedores y no representan medidas universales.
- El proyecto deberá permitir una primera prueba en un entorno real aunque todavía queden productos pendientes de cargar.

---

## 9. Preguntas abiertas para etapas posteriores

Estas cuestiones no impiden cerrar el alcance inicial, pero deberán resolverse durante la especificación de requisitos y el diseño:

- Cómo se registrarán los pagos parciales de una venta fiada.
- Si una anulación podrá realizarse en cualquier estado de la venta o requerirá condiciones específicas.
- Qué información exacta incluirán los reportes mensuales.
- Cómo se resolverá la identificación cuando varias personas de una familia compartan el mismo número de teléfono.
- Qué datos adicionales, además de nombre, apellido y teléfono, podrían ser necesarios en casos excepcionales.
- Qué reglas se aplicarán para recuperar stock al anular una venta.

---

## 10. Criterios preliminares de cierre

El alcance podrá considerarse validado cuando:

- la propietaria confirme que el problema y la necesidad están correctamente descritos;
- se aprueben las funcionalidades incluidas y excluidas;
- se validen los supuestos y restricciones principales;
- se acepte que el uso prioritario será desde el celular;
- se confirme que los reportes mensuales forman parte del MVP;
- se reconozca que los pagos parciales, la anulación de ventas y el teléfono compartido se detallarán en una etapa posterior.

## 11. Validación de la propietaria

El alcance prelimir fue presentado a Silvia Benitez propietaria de Dulce Espera, quien manifestó su conformidad con el problema, los objetivos, las funcionales incluidas y excluidas, los supuestos y las restricciones documentadas.

Las preguntas abiertas quedan reservadas para las etapas de requisitos funcionales y diseño detallado.