# Plugins de Claude de Evoluncite

Marketplace oficial de Evoluncite para Claude Cowork y Claude Code. Trae el plugin
**`evoluncite`**, que conecta Claude con tu cuenta de Evoluncite: CRM, cartera, proyectos, las
acciones de la app y la Oficina de agentes, siempre con tu usuario y tus permisos.

Con el plugin le pides a Claude, en tus palabras, cosas de tu empresa en Evoluncite («¿qué
clientes tienen cuotas vencidas esta semana?», «deja una nota en el negocio de Ana Gómez») y
Claude las hace directamente, sin que tengas que abrir la app en el navegador.

## Instalar

**Claude Cowork o claude.ai** (cada persona): Configuración › Conectores › Agregar conector
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
