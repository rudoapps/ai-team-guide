# Modelo

## ¿Qué es un Modelo?

**Definición simple:** Una implementación específica de un LLM, optimizada para ciertas tareas.

**Analogía:** Si un LLM es el concepto de "motor de coche", un modelo es una implementación específica:
- **Modelo Económico**: Eficiente, rápido, barato (GPT-3.5, Claude Instant)
- **Modelo de Lujo**: Alta calidad, características premium (GPT-4, Claude Opus)
- **Modelo Especializado**: Optimizado para tareas específicas (Codex para código)

## Qué Hace Diferentes a los Modelos

### Tamaño y Entrenamiento
- **Modelos grandes**: Más datos, mejor calidad, más caros, más lentos
- **Modelos pequeños**: Más rápidos, más baratos, suficiente para tareas simples
- **Modelos especializados**: Entrenados en dominios específicos

### Características Clave
- **Velocidad**: Qué tan rápido responden
- **Coste**: Cuánto cobran por uso (por token)
- **Precisión**: Qué tan fiables son sus resultados
- **Ventana de contexto**: Cuánto texto pueden procesar a la vez

## Modelos Populares para Desarrollo

### OpenAI GPT

**GPT-4 / GPT-4 Turbo**
- **Mejor para**: Tareas complejas, razonamiento avanzado
- **Ventana de contexto**: 8K - 128K tokens
- **Piensa en él como**: El consultor senior - caro pero muy capaz
- **Usar cuando**: La calidad es más importante que el coste

**GPT-3.5 Turbo**
- **Mejor para**: Tareas cotidianas, respuestas rápidas
- **Ventana de contexto**: 16K tokens
- **Piensa en él como**: El generalista eficiente - buen balance
- **Usar cuando**: Necesitas rapidez y calidad decente

### Anthropic Claude

**Claude 3 Opus**
- **Mejor para**: Análisis profundo, tareas complejas
- **Ventana de contexto**: 200K tokens (~150 páginas)
- **Piensa en él como**: El investigador meticuloso
- **Usar cuando**: Trabajas con documentos largos o necesitas precisión

**Claude 3 Sonnet**
- **Mejor para**: Balance de velocidad y calidad
- **Ventana de contexto**: 200K tokens
- **Piensa en él como**: El profesional versátil
- **Usar cuando**: Necesitas calidad con buen rendimiento

**Claude 3 Haiku**
- **Mejor para**: Tareas simples y rápidas
- **Ventana de contexto**: 200K tokens
- **Piensa en él como**: El asistente ágil
- **Usar cuando**: Velocidad es prioridad

### Google Gemini

**Gemini Pro**
- **Mejor para**: Integración con Google Workspace
- **Ventana de contexto**: 32K tokens
- **Piensa en él como**: El especialista del ecosistema Google
- **Usar cuando**: Tu stack incluye Gmail, Docs, Sheets

### Modelos Especializados

**GitHub Copilot / Codex**
- **Especializado en**: Generación de código
- **Usar para**: Autocompletar código, sugerencias

**Claude Code**
- **Especializado en**: Agente de desarrollo
- **Usar para**: Tareas de desarrollo autónomas

## Eligiendo el Modelo Correcto

### Árbol de Decisiones

**¿Necesitas velocidad y bajo coste?**
→ GPT-3.5 Turbo, Claude Haiku

**¿La calidad es crítica?**
→ GPT-4, Claude Opus

**¿Trabajas con documentos largos o muchos archivos?**
→ Claude (200K tokens de contexto)

**¿Necesitas razonamiento complejo?**
→ GPT-4, Claude Opus

**¿Tarea específica de código?**
→ GitHub Copilot, Claude Code

## Ejemplos Prácticos por Rol

### Para Desarrolladores

**Generar función simple:**
- Usa: GPT-3.5 Turbo (rápido, barato)

**Refactorizar proyecto completo:**
- Usa: Claude Opus (contexto grande, análisis profundo)

**Debugging complejo:**
- Usa: GPT-4 o Claude Opus (razonamiento avanzado)

**Autocompletar mientras codeas:**
- Usa: GitHub Copilot

### Para Diseñadores

**Naming conventions:**
- Usa: GPT-3.5 o Claude Haiku (tarea simple)

**Review de design system:**
- Usa: GPT-4 o Claude Opus (análisis profundo)

**Documentación de componentes:**
- Usa: Claude Sonnet (balance velocidad/calidad)

### Para Gestión

**Escribir correos:**
- Usa: GPT-3.5 (rápido, suficiente calidad)

**Analizar documentos largos:**
- Usa: Claude Opus (200K contexto)

**Crear documentación técnica:**
- Usa: GPT-4 o Claude Opus (precisión importante)

## Consideraciones de Coste

**Estructura de Costes Típica:**
- **Tokens de entrada**: Lo que envías
- **Tokens de salida**: Lo que recibes
- **Nivel del modelo**: Premium = 10-20x más caro que básico

**Consejos para Ahorrar:**
1. Usa modelos simples para tareas simples
2. Sé conciso en prompts
3. No regeneres innecesariamente
4. Cachea respuestas cuando sea posible

## Comparación Rápida

| Modelo | Velocidad | Coste | Calidad | Contexto | Mejor Para |
|--------|-----------|-------|---------|----------|------------|
| GPT-4 | ⚡⚡ | 💰💰💰 | ⭐⭐⭐⭐⭐ | 128K | Tareas complejas |
| GPT-3.5 | ⚡⚡⚡⚡ | 💰 | ⭐⭐⭐ | 16K | Uso general |
| Claude Opus | ⚡⚡ | 💰💰💰 | ⭐⭐⭐⭐⭐ | 200K | Análisis profundo |
| Claude Sonnet | ⚡⚡⚡ | 💰💰 | ⭐⭐⭐⭐ | 200K | Balance |
| Claude Haiku | ⚡⚡⚡⚡⚡ | 💰 | ⭐⭐⭐ | 200K | Velocidad |

## Conclusión Clave

Piensa en los modelos como **diferentes especialistas en tu equipo**:
- El junior rápido para tareas simples
- El senior experto para trabajo complejo
- El especialista para necesidades específicas

**Regla de oro:** Usa el modelo más simple que cumpla tus requisitos de calidad.

## Relación con Otros Conceptos

- **[LLM](./01-llm.md)**: Concepto general del que los modelos son implementaciones
- **[Token](./03-token.md)**: Los modelos cobran por token procesado
- **[Contexto](./04-contexto.md)**: Los modelos tienen límites de contexto diferentes

---

**Siguiente**: Aprende sobre [Tokens](./03-token.md) y cómo afectan coste y rendimiento.

[← Volver a Conceptos](../README.md#conceptos)
