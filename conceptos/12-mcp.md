# MCP (Model Context Protocol)

## ¿Qué es MCP?

**Definición simple:** Un protocolo estándar que permite a los modelos de IA conectarse y usar herramientas externas de forma segura.

**Analogía:**
- **Sin MCP** = Un mecánico experto sin herramientas (solo puede dar consejos)
- **Con MCP** = El mismo mecánico con un taller completo (puede arreglar el coche)

Imagina que MCP es como el USB-C de la IA: un estándar que permite conectar cualquier herramienta a cualquier modelo sin necesidad de integraciones personalizadas para cada combinación.

## El Problema que Resuelve

### Antes de MCP ❌

Cada IA necesitaba su propia integración para cada herramienta:

```
ChatGPT Plugin para GitHub
  ≠
Claude Plugin para GitHub
  ≠
Gemini Plugin para GitHub

Resultado: 3 implementaciones diferentes de la misma funcionalidad
```

**Problemas:**
- Duplicación de esfuerzo
- Incompatibilidad entre plataformas
- Difícil de mantener
- Ecosistema fragmentado

### Después de MCP ✅

Un solo servidor MCP puede ser usado por cualquier cliente:

```
GitHub MCP Server
  ↓
  ├─→ ChatGPT
  ├─→ Claude
  ├─→ Gemini
  └─→ Cualquier IA que soporte MCP

Resultado: Una implementación, múltiples clientes
```

**Beneficios:**
- Escribes una vez, funciona en todas partes
- Estándar abierto
- Fácil de mantener
- Ecosistema unificado

## ¿Cómo Funciona MCP?

### Arquitectura Básica

```
┌─────────────────┐
│   Tu Aplicación │  (Ej: Claude Desktop, IDE, etc.)
│   (MCP Client)  │
└────────┬────────┘
         │
         │ MCP Protocol
         │
┌────────┴────────┐
│   MCP Server    │  (Ej: GitHub, Database, File System)
│   (Herramienta) │
└─────────────────┘
```

### Componentes

**1. MCP Client (Cliente)**
- La aplicación que usa IA (Claude Desktop, VSCode, etc.)
- Hace peticiones al servidor
- Recibe respuestas y las presenta

**2. MCP Server (Servidor)**
- La herramienta o servicio que expone funcionalidad
- Puede ser: sistema de archivos, base de datos, API, etc.
- Responde a peticiones del cliente

**3. MCP Protocol (Protocolo)**
- Lenguaje común entre cliente y servidor
- Define cómo se comunican
- Basado en JSON-RPC 2.0

## Tipos de Capacidades

Un servidor MCP puede exponer tres tipos de funcionalidades:

### 1. Resources (Recursos)
**Qué son:** Datos que el modelo puede leer

**Ejemplos:**
```
📄 Archivos del proyecto
📊 Datos de base de datos
📝 Documentación
🌐 Contenido de URLs
```

**Caso de uso:**
```
Tú: "¿Qué dice el README?"
IA: [usa MCP para leer README.md directamente]
```

### 2. Tools (Herramientas)
**Qué son:** Acciones que el modelo puede ejecutar

**Ejemplos:**
```
🔧 Ejecutar comandos shell
✏️ Editar archivos
🗃️ Queries a base de datos
📧 Enviar emails
```

**Caso de uso:**
```
Tú: "Crea un archivo config.json"
IA: [usa MCP tool para crear el archivo]
```

### 3. Prompts (Plantillas)
**Qué son:** Prompts pre-configurados con contexto

**Ejemplos:**
```
💼 "Analiza este PR"
🐛 "Debug este error"
📋 "Genera changelog"
```

**Caso de uso:**
```
Tú: Seleccionas "Analiza este PR"
IA: [ejecuta prompt con contexto del PR actual]
```

## Ejemplo Real: Servidor MCP de GitHub

### Capacidades que Expone

**Resources:**
```
- Leer Issues
- Leer Pull Requests
- Ver contenido de archivos
- Listar commits
```

**Tools:**
```
- Crear Issue
- Comentar en PR
- Crear branch
- Merge PR
- Actualizar labels
```

**Prompts:**
```
- "Review this PR"
- "Summarize recent issues"
- "Generate release notes"
```

### Flujo de Uso

```
1. Tú: "¿Cuáles son los Issues abiertos del proyecto?"

2. Cliente MCP: Envía request al servidor GitHub MCP
   {
     "method": "resources/list",
     "params": { "uri": "github://owner/repo/issues" }
   }

3. Servidor GitHub MCP: Llama a GitHub API

4. Servidor GitHub MCP: Responde con datos
   {
     "result": [
       { "number": 42, "title": "Fix login bug", ... },
       { "number": 43, "title": "Add dark mode", ... }
     ]
   }

5. Cliente MCP: Pasa datos al modelo

6. Modelo: Genera respuesta natural
   "Hay 2 issues abiertos:
   - #42: Fix login bug
   - #43: Add dark mode"
```

## Casos de Uso Comunes

### Desarrollo

**File System MCP**
```
✓ Leer archivos del proyecto
✓ Editar código
✓ Crear nuevos archivos
✓ Navegar estructura de directorios
```

**Git MCP**
```
✓ Ver historia de commits
✓ Crear branches
✓ Hacer commits
✓ Ver diffs
```

**Database MCP**
```
✓ Ejecutar queries
✓ Ver schemas
✓ Insertar/actualizar datos
✓ Analizar performance
```

### Productividad

**Calendar MCP**
```
✓ Ver agenda
✓ Crear eventos
✓ Buscar slots disponibles
✓ Enviar invitaciones
```

**Email MCP**
```
✓ Leer emails
✓ Enviar respuestas
✓ Buscar conversaciones
✓ Organizar inbox
```

**Slack MCP**
```
✓ Leer mensajes
✓ Enviar mensajes
✓ Buscar información
✓ Crear threads
```

## Creando Tu Propio Servidor MCP

### Ejemplo Básico (Node.js)

```javascript
import { Server } from "@modelcontextprotocol/sdk/server";
import { StdioServerTransport } from "@modelcontextprotocol/sdk/server/stdio";

// Crear servidor
const server = new Server({
  name: "my-calculator",
  version: "1.0.0"
});

// Definir herramientas
server.setRequestHandler("tools/list", async () => ({
  tools: [{
    name: "add",
    description: "Suma dos números",
    inputSchema: {
      type: "object",
      properties: {
        a: { type: "number" },
        b: { type: "number" }
      }
    }
  }]
}));

// Implementar herramienta
server.setRequestHandler("tools/call", async (request) => {
  if (request.params.name === "add") {
    const { a, b } = request.params.arguments;
    return {
      content: [{
        type: "text",
        text: `${a} + ${b} = ${a + b}`
      }]
    };
  }
});

// Iniciar servidor
const transport = new StdioServerTransport();
await server.connect(transport);
```

### Ejemplo Básico (Python)

```python
from mcp.server import Server
from mcp.types import Tool, TextContent

app = Server("my-calculator")

@app.list_tools()
async def list_tools():
    return [
        Tool(
            name="add",
            description="Suma dos números",
            inputSchema={
                "type": "object",
                "properties": {
                    "a": {"type": "number"},
                    "b": {"type": "number"}
                }
            }
        )
    ]

@app.call_tool()
async def call_tool(name: str, arguments: dict):
    if name == "add":
        a = arguments["a"]
        b = arguments["b"]
        return [TextContent(
            type="text",
            text=f"{a} + {b} = {a + b}"
        )]
```

## Configuración en Claude Desktop

Para usar un servidor MCP en Claude Desktop, añádelo a la configuración:

**macOS:** `~/Library/Application Support/Claude/claude_desktop_config.json`

```json
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_TOKEN": "tu-token-aqui"
      }
    },
    "filesystem": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-filesystem", "/ruta/a/tu/proyecto"]
    }
  }
}
```

**Después de guardar:**
1. Reinicia Claude Desktop
2. El icono del servidor aparecerá en la interfaz
3. Claude ahora puede usar esas herramientas

## Servidores MCP Populares

### Oficiales (Anthropic)

```
@modelcontextprotocol/server-filesystem
- Acceso a archivos locales

@modelcontextprotocol/server-github
- Integración con GitHub

@modelcontextprotocol/server-gitlab
- Integración con GitLab

@modelcontextprotocol/server-postgres
- Base de datos PostgreSQL

@modelcontextprotocol/server-sqlite
- Base de datos SQLite

@modelcontextprotocol/server-fetch
- Hacer HTTP requests

@modelcontextprotocol/server-brave-search
- Búsqueda web
```

### Comunidad

```
mcp-server-git
- Operaciones Git avanzadas

mcp-server-jira
- Gestión de proyectos

mcp-server-confluence
- Wiki y documentación

mcp-server-docker
- Contenedores y orchestration
```

## Seguridad

### Principios Importantes

**1. Permisos Explícitos**
```
Un servidor MCP solo puede acceder a lo que le permites
Ejemplo: Filesystem solo puede acceder a carpetas que especifiques
```

**2. Review de Código**
```
Antes de instalar un servidor MCP:
✓ Revisa el código fuente
✓ Verifica que sea de fuente confiable
✓ Lee qué permisos necesita
```

**3. Tokens y Credenciales**
```
✓ Usa variables de entorno
✓ Nunca hardcodees tokens
✓ Usa scopes mínimos necesarios
✓ Rota credenciales regularmente
```

### Ejemplo de Configuración Segura

```json
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_TOKEN": "${GITHUB_MCP_TOKEN}"
      }
    }
  }
}
```

Luego define `GITHUB_MCP_TOKEN` en tu shell:
```bash
export GITHUB_MCP_TOKEN="ghp_tu_token_aqui"
```

## Debugging MCP

### Ver Logs en Claude Desktop

**macOS:**
```bash
tail -f ~/Library/Logs/Claude/mcp*.log
```

**Windows:**
```bash
Get-Content "$env:APPDATA\Claude\logs\mcp*.log" -Wait
```

### Problemas Comunes

**Error: "Server not found"**
```
Solución:
✓ Verifica que el comando existe (npx, python, etc.)
✓ Revisa la ruta en args
✓ Reinicia Claude Desktop
```

**Error: "Permission denied"**
```
Solución:
✓ Verifica tokens/credenciales
✓ Revisa permisos de archivos
✓ Confirma scopes del token
```

**Error: "Timeout"**
```
Solución:
✓ El servidor puede estar bloqueado
✓ Verifica logs del servidor
✓ Aumenta timeout si es necesario
```

## Ventajas de MCP

### Para Usuarios
```
✅ Más herramientas disponibles
✅ Integración seamless
✅ Funcionalidades consistentes
✅ Fácil de configurar
```

### Para Desarrolladores
```
✅ Estándar abierto
✅ Escribe una vez, funciona en todos lados
✅ SDKs en múltiples lenguajes
✅ Comunidad activa
✅ Documentación completa
```

### Para Organizaciones
```
✅ Control de acceso granular
✅ Auditable
✅ Escalable
✅ Seguro por diseño
```

## Limitaciones

### Actualmente MCP NO Puede:
```
❌ Streaming de respuestas en tiempo real (viene pronto)
❌ Comunicación bidireccional push (servidor → cliente)
❌ Estado compartido entre múltiples clientes
❌ Transacciones distribuidas
```

### Workarounds:
```
✓ Polling para updates
✓ Webhooks externos
✓ Estado en el servidor
✓ Transacciones por servidor
```

## Futuro de MCP

### En Desarrollo
```
🔮 Soporte para streaming
🔮 WebSocket transport
🔮 Mejor manejo de archivos grandes
🔮 Más SDKs oficiales
🔮 Marketplace de servidores
```

### Adopción
```
Empresas usando MCP:
- Anthropic (Claude)
- Varios IDE y editores
- Herramientas de desarrollo

Crecimiento:
- 100+ servidores comunitarios
- Nuevos servidores semanalmente
- Soporte en más plataformas
```

## Comenzando

### Paso 1: Usa Servidores Existentes
```
1. Instala Claude Desktop
2. Configura servidor filesystem
3. Prueba comandos básicos
4. Añade más servidores según necesites
```

### Paso 2: Explora Servidores
```
Visita: https://github.com/modelcontextprotocol
Explora servidores de la comunidad
Prueba los que sean relevantes para ti
```

### Paso 3: Crea Tu Propio Servidor (Opcional)
```
Si tienes una herramienta interna:
1. Sigue el tutorial oficial
2. Implementa funcionalidad básica
3. Prueba localmente
4. Comparte con tu equipo
```

## Recursos de Aprendizaje

**Documentación Oficial:**
- https://modelcontextprotocol.io
- https://spec.modelcontextprotocol.io

**Ejemplos:**
- https://github.com/modelcontextprotocol/servers

**Tutoriales:**
- Building your first MCP server
- MCP best practices
- Security guidelines

## Conclusión

MCP es un **cambio fundamental** en cómo las IAs interactúan con herramientas:

**Antes:** Cada IA necesitaba integraciones custom
**Ahora:** Un estándar universal

**Impacto:**
- 🚀 Más herramientas disponibles más rápido
- 🔧 Ecosistema unificado de extensiones
- 🔐 Seguridad por diseño
- 📈 Adopción acelerada

**Piénsalo así:** MCP es para IAs lo que HTTP fue para la web. Un protocolo estándar que permite que todo se conecte con todo.

## Relación con Otros Conceptos

- **[Agente](./08-agente.md)**: Los agentes usan MCP para acceder a herramientas
- **[Herramienta](./07-herramienta.md)**: MCP es el protocolo que expone herramientas
- **[Contexto](./04-contexto.md)**: MCP permite acceder a contexto externo
- **[LLM](./01-llm.md)**: El LLM usa MCP para ejecutar acciones

---

**Siguiente**: Aprende sobre [RAG](./13-rag.md) para entender cómo darle conocimiento específico a la IA.

[← Volver a Conceptos](../README.md#conceptos)
