# Plugins de Claude de Evoluncite

Marketplace oficial de Evoluncite para Claude Cowork y Claude Code. Trae el plugin
**`evoluncite`**, que conecta Claude con tu cuenta de Evoluncite: CRM, cartera, proyectos, las
acciones de la app y la Oficina de agentes, siempre con tu usuario y tus permisos.

Con el plugin le pides a Claude, en tus palabras, cosas de tu empresa en Evoluncite («¿qué
clientes tienen cuotas vencidas esta semana?», «deja una nota en el negocio de Ana Gómez») y
Claude las hace directamente, sin que tengas que abrir la app en el navegador.

## Instalar

**Claude Team o Enterprise** (quien administra Claude): descarga
[evoluncite-plugin.zip](https://github.com/evoluncite/claude-plugins/releases/latest/download/evoluncite-plugin.zip)
y súbelo en **Organization settings › Plugins & skills › Add › Upload a plugin**. Después, cada
persona abre el plugin en Cowork, pestaña **Connectors**, y conecta Evoluncite.

**Claude Pro o Max en Cowork**: **Customize › Plugins › Add › Add marketplace** con
`evoluncite/claude-plugins`, e instala `evoluncite` desde **Discover**.

**Solo el conector** (cualquier plan): Configuración › Conectores › Agregar conector
personalizado, con el nombre `Evoluncite` y la URL:

```
https://romulo.evo-app.cloud/api/v1/mcp
```

**Claude Code**:

```
/plugin marketplace add evoluncite/claude-plugins
/plugin install evoluncite@evoluncite
/evo-conectar
```

La primera vez, Claude abre Evoluncite en el navegador: inicias sesión, eliges la empresa y
apruebas. Claude nunca recibe tu contraseña.

La guía completa (qué datos salen hacia Claude, confirmaciones, cómo desconectar y preguntas
frecuentes) está en [plugins/evoluncite/README.md](plugins/evoluncite/README.md).

## Contenido

```
.claude-plugin/marketplace.json     marketplace «evoluncite»
plugins/evoluncite/
  .claude-plugin/plugin.json        manifiesto del plugin
  .mcp.json                         conector MCP remoto (OAuth)
  skills/                           cómo trabajar con Evoluncite, CRM y cartera, Oficina de agentes
  commands/                         /evo-conectar, /evo-oficina, /evo-bandeja
  README.md                         guía para clientes
```

Soporte: escribe a soporte de Evoluncite desde la app.
