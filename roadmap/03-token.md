# Token

## La Analogía Sencilla

Los tokens son como **piezas de puzzle** que la IA usa para procesar texto. Así como podrías dividir un puzzle complejo en piezas manejables, la IA divide tu texto en fragmentos llamados tokens.

Piénsalo como las "unidades de lectura" de la IA - no siempre palabras completas, sino fragmentos significativos que la IA puede entender y procesar.

## Cómo las Palabras se Convierten en Tokens

### Ejemplos Sencillos

**Palabras cortas/comunes** = 1 token cada una:
- "el" = 1 token
- "y" = 1 token  
- "gato" = 1 token

**Palabras más largas** podrían ser 1 token:
- "elefante" = 1 token
- "maravilloso" = 1 token

**Palabras complejas/poco comunes** se dividen:
- "antropomorfismo" = 2 tokens: "antropo" + "morfismo"
- "telecomunicaciones" = 3 tokens: "tele" + "comuni" + "caciones"

**Números y puntuación**:
- "123" = 1 token
- "1.234.567" = 4 tokens: "1" + "." + "234" + "." + "567"
- "!!!" = 3 tokens: "!" + "!" + "!"

### Desglose de Ejemplo Real

**Texto**: "¡Hola! ¿Cómo estás hoy?"

**Tokens**: 
1. "¡Hola"
2. "!"
3. "¿"
4. "Cómo"
5. "estás" 
6. "hoy"
7. "?"

**Total**: 7 tokens

## Por qué los Tokens Importan para Tu Trabajo

### 1. Impacto en el Coste 💰

Los servicios de IA cobran por token:
- **Tokens de entrada**: Lo que envías (tu prompt)
- **Tokens de salida**: Lo que la IA devuelve (la respuesta)

**Ejemplo de Cálculo de Coste**:
```
Tu prompt: 100 tokens
Respuesta de IA: 300 tokens
Total: 400 tokens cobrados

Si el modelo cuesta €0,002 por 1.000 tokens:
Tu coste = 400 × €0,002 ÷ 1.000 = €0,0008 (menos de un céntimo)
```

### 2. Límites de Longitud 📏

Cada modelo tiene una **ventana de contexto** - tokens máximos que puede manejar:

| Modelo | Ventana de Contexto | Páginas Equivalentes |
|--------|-------------------|---------------------|
| GPT-3.5 | 4.000 tokens | ~3 páginas |
| GPT-4 | 8.000-32.000 tokens | ~6-25 páginas |
| Claude 3 | 200.000 tokens | ~150 páginas |

**¿Qué pasa cuando excedes el límite?**
- La IA "olvida" partes anteriores de conversaciones largas
- Los documentos grandes se truncan
- Las tareas complejas fallan al completarse

### 3. Impacto en el Rendimiento ⚡

Más tokens = tiempo de respuesta más lento y mayor coste
- Mantén los prompts concisos pero claros
- Divide tareas grandes en fragmentos más pequeños
- Usa modelos apropiados para el tamaño del documento

## Estrategias Prácticas de Oficina

### Escribir Prompts Eficientes

**Ineficiente** (desperdicia tokens):
```
"Realmente agradecería si pudieras por favor ayudarme a escribir un correo a nuestro cliente sobre la reunión que teníamos programada para el próximo martes, y necesito reprogramarla para el jueves, y quiero asegurarme de que el tono sea profesional y de disculpa."
```
*Conteo de tokens: ~50*

**Eficiente** (ahorra tokens):
```
"Escribe un correo profesional y de disculpa reprogramando la reunión del cliente del martes al jueves."
```
*Conteo de tokens: ~15*

### Gestionar Documentos Largos

**Problema**: Informe de 50 páginas excede el límite de tokens

**Soluciones**:
1. **Fragmentarlo**: Analizar 10 páginas a la vez
2. **Resumir primero**: Hacer que la IA cree un resumen ejecutivo, luego hacer preguntas detalladas
3. **Extraer secciones clave**: Centrarse en capítulos/secciones específicos
4. **Usar modelos de alta capacidad**: Claude 3 para documentos muy largos

### Consejos de Estimación de Tokens

**Estimación rápida**:
- **1 token ≈ 4 caracteres** (incluyendo espacios)
- **1 token ≈ 0,75 palabras** en promedio
- **100 palabras ≈ 130-150 tokens**

**Herramientas para verificar el conteo exacto**:
- Herramienta tokenizadora de OpenAI
- Conteo de caracteres/palabras ÷ 4 (estimación aproximada)

## Problemas Comunes Relacionados con Tokens

### Error "Conversación Demasiado Larga"
**Problema**: Conversación de múltiples turnos excede la ventana de contexto
**Solución**: Iniciar conversación nueva o resumir la discusión previa

### "Respuesta Incompleta" 
**Problema**: La IA se detiene a mitad de oración
**Solución**: Pedir a la IA que continúe, o dividir la solicitud en partes más pequeñas

### Costes Inesperadamente Altos
**Problema**: Las facturas son más altas de lo esperado
**Solución**: Monitorear el uso de tokens, usar modelos más simples para tareas simples

## Consejos para Ahorrar Dinero con Tokens

1. **Sé conciso**: Elimina palabras innecesarias de los prompts
2. **Usa ejemplos con moderación**: Cada ejemplo añade tokens
3. **Elige el modelo correcto**: No uses GPT-4 para tareas simples
4. **Reutiliza contexto**: Construye sobre respuestas previas en vez de repetir contexto
5. **Agrupa solicitudes similares**: Maneja múltiples tareas similares en un prompt

## Conclusión Clave

Los tokens son la **moneda** de la interacción con IA:
- Determinan tus costes
- Limitan cuánto puedes procesar a la vez
- Afectan la velocidad de respuesta

Piensa en los tokens como **uso de datos de texto** - sé consciente pero no te obsesiones con cada token individual.

---

**Siguiente**: Aprende sobre [Contexto](./04-context-concept.md) para dar más información a la IA.