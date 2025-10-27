# Token

## ¿Qué es un Token?

**Definición simple:** Las piezas pequeñas en que la IA divide el texto para procesarlo.

**Analogía:** Como dividir un puzzle complejo en piezas manejables, o como las "unidades de lectura" de la IA.

## Cómo Funcionan los Tokens

Los tokens **no son siempre palabras completas**, sino fragmentos significativos:

### Ejemplos de Tokenización

**Palabras comunes** = 1 token:
- "el" = 1 token
- "y" = 1 token
- "gato" = 1 token
- "código" = 1 token

**Palabras largas** pueden ser 1 o más tokens:
- "desarrollador" = 1-2 tokens
- "refactorización" = 2-3 tokens
- "telecomunicaciones" = 3 tokens

**Código** tiene su propia lógica:
```javascript
function suma(a, b) { return a + b; }
```
≈ 15-20 tokens (espacios, paréntesis, palabras clave)

**Números y símbolos**:
- "123" = 1 token
- "1.234,56" = 4-5 tokens
- "!!!" = 3 tokens

### Desglose Real

**Texto**: `"¡Hola! ¿Cómo estás?"`

**Tokens**:
1. "¡Hola"
2. "!"
3. "¿"
4. "Cómo"
5. "estás"
6. "?"

**Total**: 6 tokens

## Por Qué Importan los Tokens

### 1. Impacto en el Coste 💰

Los servicios de IA cobran por token procesado:
- **Input tokens**: Tu prompt
- **Output tokens**: La respuesta

**Ejemplo de coste:**
```
Tu prompt: 100 tokens
Respuesta: 500 tokens
Total: 600 tokens

Si GPT-4 cuesta $0.03 por 1K tokens input y $0.06 por 1K output:
Coste = (100 × 0.03/1000) + (500 × 0.06/1000)
      = $0.003 + $0.03
      = $0.033 (≈ 3 céntimos)
```

### 2. Límites de Longitud 📏

Cada modelo tiene una **ventana de contexto** (máximo de tokens):

| Modelo | Contexto Máximo | Equivalente |
|--------|----------------|-------------|
| GPT-3.5 | 16K tokens | ~12 páginas |
| GPT-4 | 8K-128K tokens | ~6-100 páginas |
| Claude 3 | 200K tokens | ~150 páginas |

**¿Qué pasa si excedes el límite?**
- La IA "olvida" mensajes antiguos
- Documentos grandes se truncan
- Conversaciones largas pierden contexto inicial

### 3. Impacto en Rendimiento ⚡

Más tokens = más lento y más caro

**Buena práctica:**
- Prompts concisos pero claros
- Divide tareas grandes en chunks pequeños
- Usa el modelo apropiado para el tamaño

## Estimación de Tokens

**Reglas rápidas:**
- **1 token ≈ 4 caracteres** (incluyendo espacios)
- **1 token ≈ 0.75 palabras** (en español)
- **100 palabras ≈ 130-150 tokens**
- **1 página de código ≈ 500-800 tokens**

**Herramientas:**
- OpenAI Tokenizer (online)
- Palabra/caracteres ÷ 4 (estimación rápida)

## Estrategias Prácticas

### Escribir Prompts Eficientes

❌ **Ineficiente** (desperdicia tokens):
```
Realmente agradecería si pudieras por favor ayudarme
a escribir una función que sume dos números en JavaScript
porque no estoy seguro de cómo hacerlo y sería genial
si me explicaras también cómo funciona.
```
*~50 tokens*

✅ **Eficiente** (ahorra tokens):
```
Crea una función en JavaScript que sume dos números.
Incluye explicación breve.
```
*~15 tokens*

### Manejar Documentos Largos

**Problema**: Archivo de 100 páginas excede límite

**Soluciones**:
1. **Fragmentar**: Procesar 20 páginas a la vez
2. **Resumir primero**: Extraer puntos clave, luego profundizar
3. **Extraer secciones**: Trabajar solo con partes relevantes
4. **Usar modelos grandes**: Claude 3 (200K contexto)

### Optimizar Conversaciones Largas

**Problema**: Conversación de 50 mensajes pierde contexto inicial

**Soluciones**:
1. **Reset periódico**: Iniciar nueva conversación
2. **Checkpoint summaries**: Resumir cada 10-15 mensajes
3. **Context anchoring**: Recordar información clave

Ejemplo:
```
Recordatorio del contexto:
- Proyecto: App de ecommerce en React Native
- Stack: Node.js + PostgreSQL
- Trabajando en: Sistema de pagos

Ahora, continuando con...
```

## Casos de Uso por Rol

### Desarrolladores

**Código simple** (~100-500 tokens):
```
Crea función de validación de email en Python.
Usa regex, retorna bool.
```

**Refactoring** (~2K-10K tokens):
```
[Pega clase completa]
Refactoriza siguiendo principios SOLID.
```

**Code review** (~5K-20K tokens):
```
[Pega múltiples archivos]
Revisa y sugiere mejoras.
```

### Diseñadores

**Design tokens** (~500-1K tokens):
```
Genera estructura de design tokens en JSON.
Incluye: colors, typography, spacing.
```

**Component specs** (~1K-3K tokens):
```
Describe sistema de componentes de botones.
Estados, tamaños, variantes.
```

## Problemas Comunes

### "Conversación Demasiado Larga"
**Síntoma**: Error de límite de contexto
**Solución**: Nueva conversación + resumen del contexto

### "Respuesta Incompleta"
**Síntoma**: IA se detiene a mitad
**Solución**: "Continúa" o divide solicitud

### Costes Inesperados
**Síntoma**: Factura alta
**Solución**:
- Monitorear uso
- Usar modelos económicos para tareas simples
- Prompts más concisos

## Consejos para Ahorrar Tokens (y Dinero)

1. **Sé conciso**: Elimina palabras innecesarias
2. **Reutiliza contexto**: Construye sobre respuestas previas
3. **Elige modelo correcto**: No uses GPT-4 para tareas simples
4. **Agrupa solicitudes**: Múltiples preguntas en un prompt
5. **Usa ejemplos con moderación**: Cada ejemplo suma tokens

## Conclusión Clave

Los tokens son la **moneda de la IA**:
- Determinan tus costes
- Limitan cuánto procesas
- Afectan velocidad

**Regla práctica:** Sé consciente de tokens, pero no te obsesiones. Enfócate en claridad primero, optimización después.

## Relación con Otros Conceptos

- **[Modelo](./02-modelo.md)**: Cada modelo cobra diferente por token
- **[Contexto](./04-contexto.md)**: El contexto consume tokens
- **[Prompt](./05-prompt.md)**: Prompts más largos = más tokens = más coste

---

**Siguiente**: Aprende sobre [Contexto](./04-contexto.md) y cómo dar información efectiva a la IA.

[← Volver a Conceptos](../README.md#conceptos)
