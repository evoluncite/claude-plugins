---
description: Verifica la conexión de Claude con Evoluncite y explica cómo conectar, reconectar o cambiar de empresa.
---

Ayuda a la persona a dejar conectado Evoluncite en este Claude. Habla en español, en pasos cortos.

1. Revisa si tienes disponibles las herramientas del conector «evoluncite» (por ejemplo
   `evo_buscar_acciones`).
2. **Si las tienes**, comprueba la conexión con lecturas sin efectos: llama a `listar_empresas`
   y a `evo_buscar_acciones` con la consulta «ver mis tareas». Luego dile a la persona:
   - que la conexión funciona y actúa con **sus permisos** en la empresa que dice
     `listar_empresas`;
   - qué módulos ve (por los dominios de las acciones que volvieron);
   - si tiene otras empresas, que puede cambiar la de esta conexión en el enlace que devolvió
     `listar_empresas`, **sin reconectar** Claude.
3. **Si no las tienes, o la llamada responde que no está autorizada**, explícale cómo conectar
   según dónde esté:
   - **Claude Code**: ejecutar `/mcp`, elegir `evoluncite` y «Authenticate». Se abre el
     navegador en Evoluncite: iniciar sesión, elegir la empresa con la que trabajará Claude y
     aprobar.
   - **Claude Cowork o claude.ai**: Configuración › Conectores › Evoluncite › Conectar. Si
     Evoluncite no aparece, agregarlo como conector personalizado con la URL
     `https://romulo.evo-app.cloud/api/v1/mcp`, o pedirle a quien administra la organización que
     habilite el plugin.
   Después de aprobar, vuelve a correr `/evo-conectar`.
4. **Si responde que el servicio no está disponible**, no reintentes: dile que Evoluncite no
   responde en este momento y que lo intente más tarde o escriba a soporte de Evoluncite.

Recuérdale al final que puede ver y revocar sus conexiones de Claude en Evoluncite, en la
pantalla «Tus conexiones de Claude»: https://leads-up.evoluncite.com/#/dashboard/claude-connect
