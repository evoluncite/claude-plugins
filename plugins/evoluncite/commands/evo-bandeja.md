---
description: Trabaja ahora la bandeja de un agente de la Oficina de Evoluncite en este computador.
argument-hint: <id del agente, por ejemplo gp-01>
---

La persona quiere que trabajes ahora la bandeja de un agente de la Oficina de Evoluncite.

Agente recibido: «$ARGUMENTS»

1. Si no hay id de agente, pídeselo. Los agentes de este computador son los que se configuraron
   al vincularlo (`/evo-oficina`); si no sabe cuál, que lo revise en la Oficina en Evoluncite.
2. Si no tienes las herramientas del conector «evoluncite», dile que primero conecte Evoluncite
   (`/evo-conectar`) y detente.
3. Sigue el protocolo de la skill `evoluncite-oficina`: `iniciar_sesion` con ese agente.
   - Si responde que no hay trabajo, díselo y termina.
   - Si este computador no está vinculado a la Oficina o el agente no es de esta máquina,
     explícale que primero hay que vincularlo con `/evo-oficina` y termina.
4. Antes de trabajar, muéstrale a la persona un resumen corto de la bandeja (cuántas tareas, de
   qué se tratan y de dónde vienen: rutina o conversación de un cliente) y trabaja siguiendo el
   guion: reporta cada tarea y cierra la sesión al final.
