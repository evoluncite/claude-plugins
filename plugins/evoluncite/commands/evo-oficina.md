---
description: Vincula este computador a la Oficina de agentes de Evoluncite con un código de invitación.
argument-hint: <código de invitación, por ejemplo 7F3-K9>
---

La persona quiere vincular este computador a la Oficina de agentes de Evoluncite.

Código recibido: «$ARGUMENTS»

1. Si no hay código, pídeselo y explícale que lo genera quien administra la Oficina en
   Evoluncite, al agregar este computador como máquina. No sigas sin código.
2. Si no tienes las herramientas del conector «evoluncite», dile que primero conecte Evoluncite
   (`/evo-conectar`) y detente.
3. Llama a `iniciar_configuracion` con el código y **sigue al pie de la letra el guion que
   devuelve**, paso a paso, como explica la skill `evoluncite-oficina`. No te saltes pasos ni
   inventes otros.
4. Al terminar, muéstrale el resumen que devuelve `terminar_configuracion`.

Si el código venció o ya se usó, díselo y pídele uno nuevo.
