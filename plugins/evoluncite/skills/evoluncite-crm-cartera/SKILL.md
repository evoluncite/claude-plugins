---
name: evoluncite-crm-cartera
description: Cómo consultar y gestionar el CRM, la cartera (cobros, mora, estados de cuenta, promesas de pago) y los proyectos de Evoluncite. Úsala cuando la persona hable de clientes, negocios, embudos, etapas, cuotas vencidas, gestiones de cobro, recordatorios, proyectos, sprints o tareas de Evoluncite.
---

# CRM, cartera y proyectos en Evoluncite

Lee primero la skill `evoluncite`: aquí solo está lo propio de estos módulos. Todas estas
herramientas actúan con los permisos de la persona; si una no aparece, su rol no la incluye.

## CRM

| Para | Herramienta |
| --- | --- |
| Encontrar un cliente por nombre, documento, teléfono o correo | `buscar_clientes` |
| Encontrar negocios por nombre, cliente, etapa o responsable | `buscar_negocios` |
| Ver un negocio con sus actividades y notas | `ver_negocio` |
| Conocer los embudos y sus etapas (para filtrar o mover) | `ver_etapas` |
| Crear una tarea con fecha en un negocio | `crear_actividad_negocio` |
| Dejar una nota en el muro del negocio | `agregar_nota_negocio` |
| Mover un negocio a otra etapa de su embudo | `mover_negocio_etapa` |
| Completar el documento que dejó pendiente una automatización de la etapa | `generar_documento_paso` |

- Para buscar por cliente, el nombre y el apellido van por separado y con al menos 3 letras.
- Antes de mover un negocio, muéstrale a la persona el negocio y la etapa destino y espera su
  «sí» en un mensaje aparte, **aunque el pedido ya nombre el negocio y la etapa** («Mueve el
  negocio X a la etapa Y» no es la confirmación: es el pedido). Nunca llames a
  `mover_negocio_etapa` en el mismo turno en que te lo pidieron. **Mover desde Claude corre las automatizaciones de la etapa**, igual que en el tablero: según
  lo que la empresa configuró, eso puede enviar al cliente un correo prediseñado o un documento,
  crear tareas o cambiar campos. Si no sabes qué hace la etapa, díselo a la persona antes de
  confirmar.
- La respuesta de `mover_negocio_etapa` dice qué automatizaciones corrieron, cuáles fallaron
  (con el motivo) y cuáles quedaron como **paso manual** con una tarea al responsable. Cuéntaselo
  a la persona tal cual; no digas que algo se envió si la respuesta no lo dice.
- Si un paso manual es un documento por generar, usa `generar_documento_paso` con el
  `id_tarea` que devolvió el movimiento: sin valores, te dice qué campos pide la plantilla (o si
  ya se generó); con los valores, lo genera **una sola vez**, lo adjunta al negocio y cierra la
  tarea. **Pide los valores a la persona, no los inventes.** Si la regla además envía el
  documento por correo, sale al generarlo: confírmalo antes.
- Las notas y tareas quedan firmadas como escritas con Claude.

## Cartera

| Para | Herramienta |
| --- | --- |
| Ver quién está en mora, el más atrasado primero | `consultar_cartera_vencida` |
| Ver saldo, cuotas, pagos, promesas y reestructuraciones de un negocio | `ver_estado_cuenta` |
| Registrar una llamada, un mensaje o una promesa de pago | `registrar_gestion_cobro` |
| Programar una tarea de seguimiento de cobro | `programar_recordatorio_cobro` |

- Sin permiso de cartera de toda la empresa, la persona solo ve su propia cartera: díselo si
  pregunta por «toda la cartera».
- `registrar_gestion_cobro` **nunca registra pagos ni cambia montos**. Una promesa de pago es
  solo la promesa del cliente (fecha y monto); puede disparar un recordatorio por WhatsApp al
  cliente si la empresa lo configuró, así que confírmala antes.
- Los saldos y cuotas son **netos** (lo que paga el cliente). Si el negocio tiene retención en la
  fuente, el valor bruto es otro dato: no los sumes ni los restes entre sí.
- Para registrar pagos, reversos o acuerdos usa las acciones de la app (`evo_buscar_acciones`),
  que piden confirmación cuando corresponde.

## Proyectos

| Para | Herramienta |
| --- | --- |
| Ver los proyectos que la persona puede ver | `listar_proyectos` |
| Ver los sprints de un proyecto y sus tipos de tarea | `listar_sprints` |
| Ver un sprint | `ver_sprint` |
| Listar o filtrar tareas | `listar_items` |
| Ver una tarea por su clave | `ver_item` |
| Crear una tarea | `crear_item` |
| Cambiar campos de una tarea | `editar_item` |
| Moverla de estado o de columna | `cambiar_estado_item` |
| Leer o dejar comentarios | `listar_comentarios_item`, `comentar_item` |

El punto de entrada es `listar_proyectos`; de ahí salen los ids para lo demás.

## Lo demás

Jurídico, PQR, tickets, agenda, documentos y certificados, reportes, mensajería y el resto de lo
que la persona puede hacer en la app se alcanza
con las acciones generales (`evo_buscar_acciones` → `evo_describir_accion` → `evo_ejecutar`),
como explica la skill `evoluncite`.

## Ejemplos de pedidos

- «¿Qué clientes tienen cuotas vencidas de más de 30 días?» → `consultar_cartera_vencida`.
- «Deja una nota en el negocio de Carlos Pérez: llamó y paga el viernes» → `buscar_negocios`,
  confirmar cuál es, `agregar_nota_negocio`; si además quiere la promesa, `registrar_gestion_cobro`
  con la fecha concreta, confirmada.
- «Mueve el negocio de Ana Gómez a Ganado» → `buscar_negocios`, `ver_etapas`, confirmar,
  `mover_negocio_etapa`, y contarle qué automatizaciones corrieron.
- «Genera el contrato que quedó pendiente en ese negocio» → `generar_documento_paso` sin valores
  para ver los campos, pedírselos a la persona y volver a llamarla con ellos.
- «Dame en PDF el informe ejecutivo de cartera de septiembre» → `evo_buscar_acciones` (dominio
  `cartera`), `evo_describir_accion`, `evo_ejecutar`, y compartir el enlace temporal de descarga.
