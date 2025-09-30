# Nivel 1: Chat Básico

**Lo que aprenderás:** Cómo usar un chat de IA (ChatGPT, Claude) para resolver problemas de forma efectiva.

**Para quién:** Todos (desarrolladores + diseñadores)

**Tiempo:** 2-3 días de uso diario para dominarlo

---

## 🎯 Qué es Este Nivel

Este es donde todos empiezan: abres ChatGPT o Claude, haces una pregunta, copias la respuesta, la pegas en tu código/diseño.

**El problema común:**
- Prompts vagos → respuestas inútiles
- Copian sin entender
- No verifican si funciona
- Se frustran cuando falla

**Lo que aprenderás:** Hacer copy/paste como profesional.

---

## 💬 Anatomía de un Prompt Efectivo

Un prompt útil tiene 3 componentes:

```
[CONTEXTO] + [TAREA ESPECÍFICA] + [FORMATO/RESTRICCIONES]
```

### Para Desarrolladores

❌ **Mal:**
```
función de red
```

✅ **Bien:**
```
Crea una función que haga un GET request a una API REST.
Debe usar async/await, manejar errores de red, y parsear JSON.
Lenguaje: [tu lenguaje]
```

⭐ **Excelente:**
```
Contexto: Estoy construyendo una app móvil que consume una API de productos.
Tarea: Crea una función que obtenga la lista de productos desde /api/products
Requisitos:
- Usa async/await
- Maneja timeout (5s), errores de red, y 404
- Parsea JSON a un modelo Product
- Retorna Result/Either type
Lenguaje: [tu lenguaje]
```

---

### Para Diseñadores

❌ **Mal:**
```
sistema de botones
```

✅ **Bien:**
```
Necesito especificaciones para un sistema de botones en Figma.
Debe incluir: estados (default, hover, pressed, disabled),
3 tamaños (S, M, L), 3 estilos (primary, secondary, outline).
Dame naming convention y estructura de componentes.
```

---

## 🔄 El Ciclo Básico

```
1. Escribes prompt específico
   ↓
2. IA responde con código/solución
   ↓
3. Copias la respuesta
   ↓
4. Pegas en tu proyecto
   ↓
5. Pruebas si funciona
   ↓
6. ¿Funciona?
   ├─ SÍ → Entiéndelo antes de usar
   └─ NO → Vuelve al chat con el error
```

### Ejemplo: Debugging

**Tú:**
```
Este código da NullPointerException al obtener el nombre del usuario:

val name = user.name.uppercase()

¿Cómo lo hago null-safe?
Stack: Kotlin
```

**IA:**
```
Usa el safe call operator y elvis operator:

val name = user?.name?.uppercase() ?: "Sin nombre"
```

**Tú:** Copias, pruebas, funciona. ✅

---

## 🛡️ Las Reglas de Oro

### ✅ SÍ hacer:

**1. Dar contexto completo**
```
- Stack/lenguaje: "En Swift con SwiftUI", "Python con FastAPI"
- Versión: "Kotlin 1.9", "React 18"
- Restricciones: "Sin librerías externas", "Debe ser performante"
- Objetivo: "Para una app con 10k usuarios concurrentes"
```

**2. Ser específico con formato**
```
- "Usa async/await, no callbacks"
- "Retorna Result type, no nil"
- "Sigue patrón Repository"
- "Incluye manejo de errores explícito"
```

**3. Probar SIEMPRE**
- No copies a producción sin verificar
- Prueba casos extremos (null, vacío, errores de red)

**4. Pedir explicaciones**
```
"Explica por qué elegiste este approach"
"¿Qué hace esta línea específicamente?"
```

**5. Iterar cuando no funciona**
```
"Esto da error: [pega mensaje completo]"
"Funciona pero es muy lento con 10k items, optimízalo"
```

---

### ❌ NO hacer:

**1. Copiar sin entender**
- Si no entiendes, pide explicación línea por línea

**2. Confiar ciegamente**
- La IA comete errores de sintaxis, lógica, seguridad

**3. Prompts vagos**
- "hacer login" → Inútil
- "Implementar autenticación con JWT en [framework]" → Útil

**4. Ignorar errores**
- Si falla, no lo ignores. Vuelve al chat con el stack trace completo

**5. Usar código inseguro**
- `eval()`, SQL sin prepared statements, XSS vulnerabilities → 🚩 Rechaza y pide alternativa

---

## 🎯 Casos de Uso Comunes

### 1. Generar Código Base
```
Crea una clase Repository para operaciones CRUD de una entidad User.
Incluye: create, read, update, delete, findAll, findById
Framework: [tu framework]
Base de datos: [tu DB]
```

### 2. Entender Código Existente
```
Explica qué hace este código línea por línea:

[pega código complejo]

Explícalo en español simple, asume que conozco lo básico del lenguaje.
```

### 3. Debugging
```
Este código lanza [error]:

[pega código + stack trace]

Contexto:
- Ocurre cuando [situación]
- Variables en ese momento: [valores]
- Ya intenté: [lo que probaste]

¿Cuál es el problema y cómo lo soluciono?
```

### 4. Optimización
```
Este código es lento con 10,000 registros:

[pega código]

Tarda: [tiempo]
Objetivo: [tiempo deseado]

Optimízalo manteniendo la misma funcionalidad.
```

### 5. Convertir Entre Lenguajes
```
Convierte este código de [lenguaje A] a [lenguaje B]:

[código]

Mantén la misma lógica pero usa idioms nativos de [lenguaje B].
```

### 6. Generar Tests
```
Genera tests unitarios para esta función:

[tu función]

Framework de testing: [framework]
Incluye: happy path, edge cases (null, vacío), casos de error
```

---

## 🎨 Casos para Diseñadores

### 1. Design Tokens
```
Dame estructura de design tokens en JSON:
- Colors (semantic: primary, secondary, error, etc. + neutrals)
- Typography (families, scales, weights, line-heights)
- Spacing (escala basada en 4px)
- Shadows (elevation system)
- Border radius
```

### 2. Componentes en Figma
```
Describe cómo estructurar un Button component en Figma:
- Estados: default, hover, active, disabled, loading
- Tamaños: sm, md, lg
- Variantes: primary, secondary, ghost, outline
- Con/sin icono (left/right)
- Auto layout config para que crezca con contenido
```

### 3. Naming Conventions
```
Dame convención de nombres para proyecto Figma:
- Páginas
- Frames/Sections
- Components
- Layers
- Variants

Objetivo: que cualquier diseñador entienda la estructura.
```

### 4. Responsive Design
```
Best practices para hacer un card component responsive:
- Mobile: 320px
- Tablet: 768px
- Desktop: 1440px+

Incluye: constraints, auto layout, content scaling.
```

---

## 🚩 Señales de Alerta

La IA NO es perfecta. Detecta estos problemas:

### 1. Código que No Compila
```
// ❌ APIs inventadas o sintaxis incorrecta
let data = JSONDecoder.decodeFrom(url)  // No existe
```
**Solución:** Pega el error de compilación en el chat.

---

### 2. Versiones Incorrectas
```
// ❌ Código de versiones antiguas/deprecadas
var name: String = null  // Ya no se hace así
```
**Solución:** Especifica versión: "Usando [lenguaje] [versión]"

---

### 3. Lógica Errónea
```
# ❌ Hace lo contrario de lo pedido
def get_active_users(users):
    return [u for u in users if not u.is_active]  # Retorna inactivos!
```
**Solución:** Prueba con datos reales, detecta, regresa al chat.

---

### 4. Vulnerabilidades de Seguridad
```
// ❌ SQL injection
$query = "SELECT * FROM users WHERE id = " . $_GET['id'];

// ❌ XSS
element.innerHTML = userInput;

// ❌ Eval
eval(userInput);
```
**Solución:** 🚩 Rechaza y pide alternativa segura.

---

### 5. Soluciones Innecesariamente Complicadas
```
// ❌ Over-engineering
const sum = arr.reduce((a,b) => [...a, b].reduce((x,y) => x+y), []).reduce((x,y) => x+y)

// ✅ Simple
const sum = arr.reduce((a, b) => a + b, 0)
```
**Solución:** Pide: "Simplifica esto"

---

## 💡 Técnicas para Mejorar Prompts

### Técnica 1: Añadir Restricciones
```
Crea una función de autenticación que:
✅ Use async/await (no callbacks)
✅ Valide input antes de llamar API
✅ Maneje 3 casos: success, unauthorized, network error
✅ Use tipos estrictos
✅ No dependa de librerías externas (solo std lib)
```

---

### Técnica 2: Dar Ejemplos del Output Esperado
```
Función para formatear nombres:

Input → Output esperado:
"john doe" → "John Doe"
"JANE SMITH" → "Jane Smith"
"" → "Sin nombre"
"null" → "Sin nombre"

Hazlo en [lenguaje].
```

---

### Técnica 3: Pedir Alternativas
```
Dame 3 formas de implementar caché en memoria:

1. Diccionario simple (sin expiración)
2. Con TTL (time-to-live)
3. LRU (least recently used)

Para cada una:
- Ejemplo de código
- Pros/contras
- Cuándo usarla
```

---

### Técnica 4: Especificar Formato de Salida
```
Explica el patrón MVVM.

Formato:
1. Definición (1-2 líneas)
2. Componentes y responsabilidades
3. Diagrama ASCII del flujo
4. Ejemplo mínimo en código
5. Cuándo usarlo vs MVC
6. Trade-offs
```

---

## ✅ Resumen: Dominas Nivel 1 Cuando...

### Entiendes:
- ✅ Qué hace un buen prompt: contexto + tarea + formato
- ✅ El ciclo: prompt → código → probar → refinar
- ✅ La IA es una herramienta, no una fuente de verdad absoluta

### Puedes:
- ✅ Generar funciones/código básico útil
- ✅ Explicar código que no entiendes
- ✅ Debuggear con ayuda de IA
- ✅ Iterar hasta obtener lo que necesitas
- ✅ Detectar código incorrecto/inseguro

### Evitas:
- ✅ Prompts vagos
- ✅ Copiar sin entender
- ✅ Confiar ciegamente
- ✅ Usar sin probar

---

## 📊 Limitaciones de Este Nivel

### Lo que PUEDES hacer:
- ✅ Generar código simple (funciones, clases, queries)
- ✅ Debug de problemas puntuales
- ✅ Explicaciones de código
- ✅ Conversiones de sintaxis

### Lo que NO puedes hacer (todavía):
- ❌ Conversaciones largas manteniendo contexto
- ❌ Refactorizar proyectos completos
- ❌ Trabajar con múltiples archivos simultáneamente
- ❌ Integrar IA mientras codeas (sin copiar/pegar)
- ❌ Automatizar flujos de trabajo

**Para eso necesitas:** [Nivel 2: Chat Avanzado](./nivel-2-chat-avanzado.md)

---

## 🆘 Problemas Comunes

**"No genera código que funcione"**
→ Dale más contexto: lenguaje, versión, framework, restricciones, objetivo

**"Respuestas muy genéricas"**
→ Sé más específico con tu stack y patrones que sigues

**"No entiendo el código"**
→ "Explica línea por línea como si fuera junior developer"

**"Genera código diferente cada vez"**
→ Normal (LLMs son probabilísticos). Sé más específico para más consistencia.

**"No sigue mis convenciones"**
→ Especifica: "Siguiendo [patrón/arquitectura]", "Usando naming convention [estilo]"

---

## 🎯 Próximo Paso

**Cuando domines este nivel** (2-3 días de uso consistente), avanza a:

→ [Nivel 2: Chat Avanzado](./nivel-2-chat-avanzado.md)

Aprenderás:
- Mantener contexto en conversaciones largas
- Técnicas avanzadas: chain-of-thought, few-shot, role prompting
- Refactorizar proyectos completos
- Trabajar con múltiples archivos
- Cuándo usar chat vs otras herramientas

---

[← Glosario](./glosario.md) | [Inicio](./README.md) | [Siguiente: Nivel 2 →](./nivel-2-chat-avanzado.md)