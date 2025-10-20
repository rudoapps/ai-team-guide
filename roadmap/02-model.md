# Modelo

## La Analogía Sencilla

Si un LLM es el concepto general de "un motor de coche", entonces un **modelo** es una implementación específica del motor, como:

- **Modelo Económico**: Cumple el trabajo eficientemente (rápido, barato)
- **Modelo de Lujo**: Salida de alta calidad con características premium
- **Modelo Deportivo**: Especializado para tareas específicas de alto rendimiento
- **Modelo Híbrido**: Enfoque equilibrado para uso general

Cada modelo tiene diferentes fortalezas, costes y casos de uso ideales.

## Lo que Hace Diferentes a los Modelos

### Datos de Entrenamiento y Tamaño
- **Modelos más grandes**: Más datos de entrenamiento, mejores en tareas complejas, más caros
- **Modelos más pequeños**: Más rápidos, más baratos, buenos para tareas sencillas
- **Modelos especializados**: Entrenados en dominios específicos (legal, médico, programación)

### Características de Rendimiento
- **Velocidad**: Qué tan rápido responden
- **Coste**: Cuánto cobran por uso
- **Precisión**: Qué tan fiables son sus resultados
- **Capacidades**: Qué tipos de tareas dominan

## Modelos Populares para Trabajo de Oficina

### Modelos de Propósito General

**GPT (OpenAI)**
- **Mejor para**: Escritura compleja, análisis, resolución de problemas
- **Piensa**: El consultor premium - caro pero muy capaz
- **Usar cuando**: La calidad importa más que la velocidad/coste

**GPT-3.5 (OpenAI)**
- **Mejor para**: Tareas de escritura cotidianas, respuestas rápidas
- **Piensa**: El generalista fiable - buen equilibrio de calidad y coste
- **Usar cuando**: Necesitas resultados rápidos y suficientemente buenos

**Claude (Anthropic)**
- **Mejor para**: Documentos largos, análisis cuidadoso, seguir instrucciones precisamente
- **Piensa**: El investigador meticuloso - gran atención al detalle
- **Usar cuando**: Trabajando con textos largos o necesitas seguimiento muy preciso de instrucciones complejas

**Gemini (Google)**
- **Mejor para**: Integración con Google Workspace, búsqueda web
- **Piensa**: El especialista del ecosistema Google
- **Usar cuando**: Vives en Gmail, Google Docs y Google Sheets

### Modelos Especializados

**Codex/GitHub Copilot/Claude Code**
- **Mejor para**: Generación de código y tareas de programación
- **Usar cuando**: Escribiendo o depurando código

**DALL-E, Midjourney**
- **Mejor para**: Generación de imágenes
- **Usar cuando**: Necesitas creación de contenido visual

**Nano-banana**
- **Mejor para**: Edición de imágenes
- **Usar cuando**: Necesitas modificación de contenido visual


## Cómo Podría Usar Modelos Tu Empresa

### Modelos Listos para Usar
Tu empresa usa modelos existentes (como ChatGPT) tal como están:
```
Empleado → ChatGPT → Respuestas generales
```

### Modelos Afinados
Tu empresa entrena un modelo con tus datos específicos:
```
Empleado → TuEmpresa-GPT → Respuestas en el estilo/conocimiento de tu empresa
```

**Ejemplo**: Un bufete de abogados podría afinar un modelo con sus expedientes pasados para ayudar a redactar contratos que coincidan con el estilo y precedentes del bufete.

## Eligiendo el Modelo Correcto para Tu Tarea

### Árbol de Decisiones Rápido

**¿Lo necesitas rápido y barato?**
→ Usa modelos más pequeños/simples (GPT-4o-mini, Claude Instant)

**¿La calidad es crítica?**
→ Usa modelos premium (GPT-5, Claude 4 Sonnet)

**¿Trabajando con documentos largos?**
→ Usa modelos con ventanas de contexto grandes (Claude 4 Sonnet 1M)

**¿Necesitas información web actual?**
→ Usa modelos con acceso web (Bing Chat, Bard)

**¿Tarea altamente técnica/especializada?**
→ Usa modelos específicos del dominio (Claude Code para programación)

## Ejemplos Prácticos de Oficina

### Escritura de Correos
- **Respuesta simple**: GPT-4o-mini (rápido, barato)
- **Comunicación importante con cliente**: GPT-5 (mayor calidad)
- **Correspondencia legal**: Modelo legal afinado

### Análisis de Documentos
- **Resumen rápido**: Claude Instant
- **Análisis detallado**: Claude 3 Opus
- **Documento financiero**: Modelo especializado en finanzas

### Tareas Creativas
- **Lluvia de ideas**: Cualquier modelo general
- **Copia de marketing**: GPT-4.1 (más creativo)
- **Escritura técnica**: Claude (más preciso)

## Consideraciones de Coste

**Estructura de Costes Típica**:
- **Tokens de entrada**: Lo que envías al modelo
- **Tokens de salida**: Lo que el modelo te devuelve
- **Nivel del modelo**: Los modelos premium cuestan 10-20 veces más que los básicos

**Consejos para Ahorrar Dinero**:
1. Usa modelos más simples para tareas simples
2. Sé conciso en tus prompts
3. No regeneres respuestas innecesariamente
4. Usa el modelo adecuado para el trabajo

## Conclusión Clave

Piensa en los modelos como **diferentes especialistas en tu oficina**:
- El becario rápido para tareas simples
- El analista senior para trabajo complejo
- El experto del dominio para necesidades especializadas

Elige basándote en tus necesidades específicas: velocidad, calidad, coste y especialización.

---

**Siguiente**: Aprende sobre [Tokens](./03-token.md) y cómo la IA procesa y cobra por el texto.
