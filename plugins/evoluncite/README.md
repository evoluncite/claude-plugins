# Guía: Evoluncite en Claude (Cowork y Claude Code)

Con el plugin de Evoluncite le pides a Claude, en tus palabras, cosas de tu empresa en
Evoluncite: «¿qué clientes tienen cuotas vencidas esta semana?», «deja una nota en el negocio de
Ana Gómez», «crea una tarea en el sprint actual». Claude trabaja **con tu usuario y tus
permisos**, en **una** de tus empresas, y te pide confirmación antes de cualquier cosa que salga de
Evoluncite o que no tenga vuelta atrás.

Esta guía explica cómo instalarlo, qué datos salen hacia Claude y cómo desconectarlo.

## Antes de empezar

- Un usuario **activo** en Evoluncite, en la empresa con la que vas a trabajar.
- Una cuenta de Claude con un plan que permita agregar conectores: Pro, Max, Team o Enterprise.
- Para Claude Code: Claude Code instalado (terminal, o la pestaña Code de Claude Desktop).

Datos que vas a necesitar:

| Qué | Valor |
| --- | --- |
| URL del conector | `https://romulo.evo-app.cloud/api/v1/mcp` |
| Marketplace del plugin | `evoluncite/claude-plugins` |
| Nombre del plugin | `evoluncite` |

## Cómo funciona la conexión

1. Agregas Evoluncite en Claude (como plugin o como conector).
2. La primera vez, Claude abre Evoluncite en el navegador. Inicias sesión como siempre y ves una
   pantalla que dice qué Claude se quiere conectar.
3. **Eliges con cuál de tus empresas** va a trabajar Claude (viene marcada la que tienes activa).
4. Apruebas. Desde ese momento, ese Claude trabaja con tu usuario en esa empresa.

Si trabajas en varias empresas, puedes **cambiar la empresa de una conexión cuando quieras**, sin
volver a conectar: en «Tus conexiones de Claude» (ver _Cómo desconectar o revocar_). La siguiente
petición de Claude ya trabaja en la empresa nueva. Si le preguntas a Claude en qué empresa está,
te lo dice y te da el enlace a esa pantalla.

Claude **nunca** recibe tu contraseña: recibe una credencial que dura una hora y se renueva sola
mientras la uses. Si pasan 30 días sin usarla, tienes que volver a aprobar.

## Instalación en Claude Cowork

Hay dos caminos. Si tu empresa usa Claude Team o Enterprise, pregúntale primero a quien
administra Claude en tu organización: puede que ya lo haya dejado listo.

### Opción A: conector personalizado (cada persona)

1. En Claude, abre **Configuración › Conectores**.
2. Elige **Agregar conector personalizado**.
3. Nombre: `Evoluncite`. URL: `https://romulo.evo-app.cloud/api/v1/mcp`. Guarda.
4. Pulsa **Conectar** junto a Evoluncite y aprueba en Evoluncite como se explica arriba.
5. En una conversación de Cowork, revisa que el conector Evoluncite esté activo y pide algo
   sencillo, por ejemplo: «¿qué puedo hacer en Evoluncite desde aquí?».

En Team y Enterprise, puede que solo quien administra la organización pueda agregar conectores
personalizados. En ese caso lo agrega una vez para todos y cada persona solo hace el paso 4.

### Opción B: plugin de la organización (quien administra Claude)

El plugin trae el conector y además le enseña a Claude cómo trabajar con Evoluncite (skills) y
agrega los comandos `/evo-conectar`, `/evo-oficina` y `/evo-bandeja`.

1. En la administración de plugins de tu organización en Claude, agrega el marketplace
   `evoluncite/claude-plugins`.
2. Habilita el plugin `evoluncite` para las personas que lo van a usar.
3. Cada persona conecta su cuenta la primera vez que Claude use Evoluncite, o con
   `/evo-conectar`.

## Instalación en Claude Code

1. Agrega el marketplace e instala el plugin:

   ```
   /plugin marketplace add evoluncite/claude-plugins
   /plugin install evoluncite@evoluncite
   ```

2. Reinicia Claude Code si te lo pide.
3. Ejecuta `/mcp`, elige `evoluncite` y **Authenticate**. Se abre el navegador: aprueba en
   Evoluncite.
4. Ejecuta `/evo-conectar` para comprobar que todo quedó bien.

Sin el plugin (solo el conector, sin skills ni comandos):

```bash
claude mcp add --transport http evoluncite https://romulo.evo-app.cloud/api/v1/mcp
```

## Qué le puedes pedir

- **CRM**: buscar clientes y negocios, ver un negocio con su historial, dejar notas, crear tareas,
  mover un negocio de etapa (con las automatizaciones de esa etapa, igual que en el tablero) y
  completar el documento que una automatización dejó pendiente.
- **Cartera**: quién está en mora, el estado de cuenta de un negocio, registrar una llamada o una
  promesa de pago, programar un seguimiento de cobro.
- **Proyectos**: ver proyectos, sprints y tareas; crear, editar, comentar y mover tareas.
- **Más acciones de la app**: jurídico, PQR, tickets, agenda, mensajería y campañas,
  importaciones, reportes, documentos, contabilidad, nómina, talento humano, inventario, ventas,
  solicitudes, formación y otras que tu usuario puede hacer en Evoluncite. Claude las busca entre
  las que tienes permitidas.
- **Archivos**: Claude puede subir un archivo que le compartas a una acción que lo necesite, y
  cuando una acción genera un PDF o un reporte te entrega un enlace de descarga que vence en 15
  minutos.
- **Oficina de agentes**: vincular tu computador para que los agentes de tu empresa trabajen en él
  (`/evo-oficina` con el código de invitación) y trabajar la bandeja de un agente
  (`/evo-bandeja`). Un agente puede lo que tú puedes **y** lo que la Oficina le concede por
  módulo y tipo de acción; lo que sale de Evoluncite o borra siempre pasa por una aprobación.

Claude **solo ve lo que tu usuario puede ver y hacer** en Evoluncite: tu rol y lo que incluye la
suscripción de tu empresa. Si algo no lo puedes hacer en la app, tampoco lo puede hacer Claude por
ti.

### Confirmaciones

- Las consultas se hacen directo.
- Antes de crear o cambiar algo que no pediste de forma explícita, Claude te pregunta.
- Lo que **sale de Evoluncite** (un WhatsApp, un correo o un SMS a un cliente) o lo que **no tiene
  vuelta atrás** (borrar) nunca se hace en un paso: Claude te muestra una vista previa y solo
  sigue si le dices que sí.
- **Mover un negocio de etapa** corre las automatizaciones que tu empresa configuró en esa etapa,
  igual que si lo movieras en el tablero: según la configuración, eso puede enviarle al cliente un
  correo o un documento. Claude te confirma el movimiento antes de hacerlo y después te cuenta qué
  automatizaciones corrieron y cuáles quedaron pendientes.
- Todo lo que Claude cambie queda en la auditoría de Evoluncite a tu nombre, marcado como hecho
  desde Claude.

## Qué datos salen hacia Claude

- **Solo lo que Claude pide para responderte.** Cuando le haces una pregunta, Claude llama a
  Evoluncite y recibe la respuesta de esa consulta: por ejemplo, el nombre del cliente, el negocio,
  su saldo y sus cuotas. No recibe tu base de datos completa ni datos que tu usuario no puede ver.
- **Datos personales de tus clientes.** Las respuestas pueden incluir nombres, documentos,
  teléfonos, correos y montos de tus clientes y deudores, igual que en la pantalla. Esos datos
  quedan en la conversación de Claude y los trata Anthropic según las condiciones de **tu cuenta
  de Claude** (retención, uso para entrenamiento, etc.). Revisa esas opciones con quien administra
  Claude en tu empresa antes de usarlo con datos de clientes.
- **Lo que guarda Evoluncite.** La conexión (qué Claude, cuándo se conectó y cuándo se usó por
  última vez) y la auditoría de lo que Claude cambió a tu nombre. Evoluncite no guarda tus
  conversaciones con Claude.
- **Lo que nunca sale.** Tu contraseña, los datos de otras empresas y los de otras personas que tu
  rol no permite ver.

Tu empresa es responsable de los datos personales de sus clientes. Úsalo solo para tareas en las
que esos datos hagan falta.

## Cómo desconectar o revocar

**Desde Evoluncite** (corta de inmediato):

1. Entra a «Tus conexiones de Claude»:
   `https://leads-up.evoluncite.com/#/dashboard/claude-connect`.
2. Verás cada Claude que conectaste, con la fecha de conexión y el último uso.
3. Pulsa **Revocar** en la que quieras cortar y confirma. La siguiente vez que ese Claude intente
   usar Evoluncite, la petición no se autoriza.

**Desde Claude**:

- Cowork o claude.ai: **Configuración › Conectores › Evoluncite › Desconectar** (o quitar el
  conector).
- Claude Code: `/mcp` → `evoluncite` → borrar la autenticación; o desinstalar el plugin con
  `/plugin uninstall evoluncite@evoluncite`.

Desconectar en Claude borra la credencial en Claude. Para estar seguro de que nadie la puede
seguir usando, revócala también en Evoluncite.

Además, si tu usuario se desactiva o sale de la empresa en Evoluncite, la conexión deja de
funcionar sola.

## Preguntas frecuentes

**Claude trabaja en la empresa equivocada.**
Cámbiala en «Tus conexiones de Claude», en la fila de esa conexión. No hace falta reconectar: la
siguiente petición ya trabaja en la empresa elegida. Si tienes agentes de la Oficina trabajando
en este momento, o un computador tuyo vinculado como máquina activa de la Oficina en la empresa
actual, la pantalla no deja cambiarla hasta que terminen o lo desactives.

**¿Puedo usar dos empresas a la vez?**
No con la misma conexión: cada conexión trabaja en una empresa a la vez. Puedes cambiarla cuando
quieras, o conectar otro Claude con la otra empresa.

**Claude dice que no puede hacer algo que yo sí hago en la app.**
Puede que esa acción todavía no esté disponible desde Claude. Si en la app tampoco te aparece, es
un permiso de tu rol: pídeselo a quien administra los roles en tu empresa.

**Me pide volver a conectar.**
Pasa si revocaste la conexión, si pasaron 30 días sin usarla o si tu usuario cambió de estado en
la empresa. Vuelve a conectar (`/evo-conectar` te guía).

**Dice que Evoluncite no está disponible.**
El servicio no respondió. Espera unos minutos y vuelve a intentar; si sigue, escribe a soporte de
Evoluncite.

**¿Claude puede enviar mensajes a mis clientes sin que yo sepa?**
No. Todo envío por WhatsApp, correo o SMS que Claude haga necesita que confirmes la vista previa
en la conversación. La única forma indirecta es la misma que en la app: si tu empresa configuró
que una etapa envíe un correo o un documento al cliente, mover el negocio a esa etapa lo envía.
Claude te pregunta antes de mover y te cuenta lo que corrió.

**¿Mi empresa puede impedir que alguien conecte Claude?**
Hoy cualquier usuario activo puede conectar su propio Claude, y Claude solo puede hacer lo que ese
usuario ya puede hacer en la app. Quien administra los roles controla lo que cada persona, y por
lo tanto su Claude, puede ver y hacer.

**¿Funciona el reporte de uso de la cuenta de Claude en Cowork?**
No. Ese reporte solo funciona en Claude Code; en Cowork el panel de la Oficina lo muestra
«sin dato».

**¿Tengo que reinstalar algo cuando Evoluncite agrega funciones?**
No. Las acciones nuevas aparecen solas. Si actualizamos el plugin, Claude Code lo actualiza desde
el marketplace (`/plugin marketplace update evoluncite`).
