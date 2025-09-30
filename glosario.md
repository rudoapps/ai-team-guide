# Glosario: Términos que Debes Conocer

Antes de empezar, familiarízate con estos términos. Los encontrarás en toda la guía.

---

## 🤖 IA (Inteligencia Artificial)

**Definición simple:** Software que puede hacer tareas que normalmente requieren pensamiento humano.

**Ejemplos cotidianos:**
- El autocorrector de tu teléfono
- Las recomendaciones de Netflix
- El reconocimiento facial para desbloquear tu teléfono

**En desarrollo:** Herramientas que entienden código, generan funciones, encuentran bugs, etc.

---

## 💬 LLM (Large Language Model / Modelo de Lenguaje Grande)

**Definición simple:** Una IA entrenada con millones de textos para entender y escribir como humano.

**Ejemplos concretos:**
- ChatGPT (de OpenAI)
- Claude (de Anthropic)
- Gemini (de Google)

**Analogía:** Es como un compañero que leyó toda la documentación de todos los lenguajes de programación y puede ayudarte a escribir código.

---

## 💭 Prompt

**Definición simple:** Lo que tú le escribes a la IA para pedirle algo.

**Ejemplos:**

❌ **Prompt malo:**
```
hacer login
```

✅ **Prompt bueno:**
```
Crea una función de login en JavaScript que:
- Reciba email y password
- Valide formato de email
- Haga una petición POST a /api/login
- Maneje errores de red y credenciales inválidas
```

**Regla de oro:** Mientras más claro seas, mejores resultados obtienes.

---

## 🎯 Contexto

**Definición simple:** La información extra que le das a la IA para que entienda tu situación.

**Sin contexto:**
```
¿Cómo optimizo esto?
[código]
```

**Con contexto:**
```
Estoy usando React 18 con TypeScript. Esta función se ejecuta
en cada render y causa lag. ¿Cómo puedo optimizarla?
[código]
```

**Por qué importa:** Es la diferencia entre preguntarle a un extraño vs. a alguien que conoce tu proyecto.

---

## 🔄 Iterar / Iteración

**Definición simple:** Mejorar algo poco a poco, en varios pasos.

**Ejemplo:**
```
Tú: "Crea función de validación de password"
IA: [genera función básica]

Tú: "Agrega que requiera mínimo 8 caracteres"
IA: [mejora la función]

Tú: "Ahora que también requiera un número y un símbolo"
IA: [versión final]
```

**Lección:** No esperes perfección en el primer intento. Refina paso a paso.

---

## 🔍 Token

**Definición simple:** Las piezas pequeñas en que la IA divide el texto para procesarlo.

**Analogía:** Como dividir una oración en palabras.

**Ejemplo:**
- `"Hola mundo"` = ~2-3 tokens
- Una línea de código promedio = ~10-20 tokens
- Este archivo completo = ~500-700 tokens

**Por qué importa:**
- Los modelos tienen límites (ej: 200,000 tokens)
- Si mandas mucho código, puedes exceder el límite

**Regla práctica:**
- 1 token ≈ 0.75 palabras en español
- 1 token ≈ 4 caracteres en código

---

## 🎲 Temperatura

**Definición simple:** Qué tan "creativa" o "predecible" quieres que sea la IA.

**Escala:**

**Baja (0.0 - 0.3):** Más predecible, consistente
- 🎯 Usar para: Código, correcciones, respuestas técnicas
- Ejemplo: Pedirle que corrija un bug

**Media (0.4 - 0.7):** Balance entre creatividad y coherencia
- 🎯 Usar para: Refactorización, propuestas de arquitectura
- Ejemplo: Pedirle ideas de cómo estructurar un proyecto

**Alta (0.8 - 1.0):** Más creativa, variada
- 🎯 Usar para: Brainstorming, nombrar variables, contenido
- Ejemplo: Pedirle 10 nombres para una función

> **Nota:** La mayoría de chats usan temperatura media por defecto.

---

## 🤖 Asistente vs Copiloto vs Agente

Estos términos se confunden mucho. Aquí la diferencia:

### Asistente (Assistant)
**Qué es:** Responde preguntas cuando le preguntas.
**Ejemplo:** ChatGPT, Claude en su web
**Nivel de autonomía:** 🔵⚪⚪ Bajo (solo responde)

### Copiloto (Copilot)
**Qué es:** Te ayuda mientras trabajas, sugiere código en tiempo real.
**Ejemplo:** GitHub Copilot, Cursor
**Nivel de autonomía:** 🔵🔵⚪ Medio (sugiere, tú decides)

### Agente (Agent)
**Qué es:** Ejecuta tareas completas por ti, puede usar herramientas.
**Ejemplo:** Claude Code, Devin
**Nivel de autonomía:** 🔵🔵🔵 Alto (hace, tú supervisas)

**Analogía:**
- **Asistente:** Consultor que responde preguntas
- **Copiloto:** Compañero que te ayuda a escribir
- **Agente:** Junior dev que completa tareas

---

## 🔌 MCP (Model Context Protocol)

**Definición simple:** Una forma de darle "superpoderes" a la IA conectándola con herramientas externas.

**Sin MCP:**
```
Tú: "¿Cuál es el bug en el archivo server.js?"
IA: "No puedo ver tus archivos, cópiame el código"
```

**Con MCP:**
```
Tú: "¿Cuál es el bug en el archivo server.js?"
IA: [lee el archivo directamente y encuentra el bug]
```

**Ejemplos de lo que MCP permite:**
- Leer/editar archivos de tu proyecto
- Ejecutar comandos en tu terminal
- Conectarse a bases de datos
- Buscar en tu documentación
- Hacer git commits

**Analogía:** Es como darle a la IA acceso a las mismas herramientas que tú usas.

> Lo veremos en detalle en el [Nivel 6](./nivel-6-mcp.md)

---

## 🎨 Generativo vs Discriminativo

### Generativo
**Qué hace:** Crea contenido nuevo.
**Ejemplos:**
- Escribir una función desde cero
- Generar documentación
- Crear nombres de variables

### Discriminativo
**Qué hace:** Analiza y clasifica contenido existente.
**Ejemplos:**
- "¿Este código tiene bugs?" (Sí/No + explicación)
- "¿Qué hace esta función?" (Análisis)
- "¿Este código sigue las mejores prácticas?" (Evaluación)

**La mayoría de LLMs modernos hacen ambas cosas.**

---

## 🧠 Fine-tuning vs RAG

Dos formas de "enseñarle" a la IA sobre tu proyecto específico.

### Fine-tuning
**Qué es:** Re-entrenar el modelo con tus datos.
**Pros:** Muy preciso para tu caso
**Contras:** Caro, requiere muchos datos, técnico
**Ejemplo:** Entrenar un modelo solo para tu empresa

### RAG (Retrieval-Augmented Generation)
**Qué es:** La IA busca información relevante antes de responder.
**Pros:** Más barato, más fácil, más flexible
**Contras:** Menos preciso que fine-tuning
**Ejemplo:** La IA busca en tu documentación antes de responder

> Para la mayoría de casos, RAG es suficiente.

---

## 🛠️ API vs Chat vs CLI

Tres formas de interactuar con IA:

### Chat (Web)
**Qué es:** Página web donde conversas (ChatGPT, Claude.ai)
**Mejor para:** Aprender, explorar, prototipar
**Nivel:** 1-2

### CLI (Command Line Interface)
**Qué es:** Herramienta de terminal (Claude Code, Warp AI)
**Mejor para:** Integrar en tu flujo de trabajo
**Nivel:** 4-5

### API (Application Programming Interface)
**Qué es:** Conectar IA a tu aplicación mediante código
**Mejor para:** Automatización, productos
**Nivel:** 6

---

## 📊 Embeddings

**Definición simple:** Convertir texto en números para que la IA pueda entenderlo y compararlo.

**Para qué sirve:**
- Búsqueda semántica ("encuentra código similar a este")
- Clasificación de código
- Detección de duplicados

**Ejemplo práctico:**
```javascript
// Estos dos códigos hacen lo mismo pero escrito diferente
// Los embeddings ayudan a la IA a detectar que son similares

// Versión 1
function suma(a, b) { return a + b; }

// Versión 2
const add = (x, y) => x + y;
```

> Es un concepto avanzado. No te preocupes por esto al principio.

---

## ✅ Checklist de Términos

Asegúrate de entender estos antes de continuar:

- [ ] Sé qué es un LLM y puedo nombrar 3 ejemplos
- [ ] Entiendo qué es un prompt y la diferencia entre uno bueno y uno malo
- [ ] Sé qué significa "dar contexto"
- [ ] Entiendo la diferencia entre Asistente, Copiloto y Agente
- [ ] Tengo una idea básica de qué es MCP

**Si marcaste todos,** estás listo para → [Nivel 1: Chat Básico](./nivel-1-chat-basico.md)

**Si tienes dudas,** vuelve a leer las secciones que no quedaron claras.

---

[← Volver al inicio](./README.md) | [Siguiente: Nivel 1 →](./nivel-1-chat-basico.md)