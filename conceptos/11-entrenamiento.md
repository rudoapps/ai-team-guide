# Entrenamiento

## ¿Qué es el Entrenamiento?

**Definición simple:** El proceso de enseñar a un modelo de IA a realizar tareas mediante exposición masiva a ejemplos y ajuste de sus parámetros internos.

**Analogía:** Como enseñar a alguien a programar mostrándole **millones de ejemplos** de código hasta que aprenda patrones y pueda generar código por sí mismo.

```
Humano aprende: Lee 100 tutoriales → Práctica 1000 horas → Experto
IA aprende: Procesa 100M ejemplos → Ajusta parámetros → Modelo entrenado
```

## El Proceso de Aprendizaje

### Fase 1: Recolección de Datos 📚

**Para modelo de código**:
```
Input: Todo GitHub público
- Millones de repos
- Miles de millones de líneas de código
- Múltiples lenguajes
- Diferentes estilos y patterns

Resultado: Dataset masivo de código
```

**Para modelo general**:
```
Input: Internet
- Wikipedia
- Libros digitalizados
- Artículos científicos
- Código open source
- Documentación técnica
- Conversaciones (Reddit, Stack Overflow)

Resultado: Conocimiento humano digitalizado
```

### Fase 2: Pre-entrenamiento 🧠

**Qué sucede**:
```python
# Simplificado
for millions_of_examples in dataset:
    input_text = "function calculate"
    expected_next = "Sum"

    model_predicts = model.predict_next(input_text)
    error = expected_next - model_predicts

    model.adjust_parameters(error)
    # Repite millones de veces
```

**Recursos necesarios**:
```
GPT-4 training:
- Tiempo: Varios meses
- GPUs: Miles de GPUs A100
- Coste: Estimado $100M+
- Energía: Megawatts
- Dataset: Terabytes de texto

Por eso tú NO entrenas GPT-4 desde cero
```

**Resultado**:
```
Modelo que "entiende":
✓ Sintaxis de lenguajes de programación
✓ Patrones comunes de código
✓ Buenas prácticas generales
✓ Documentación y APIs públicas
✓ Relaciones entre conceptos

Pero NO conoce:
✗ Tu código específico
✗ Tu arquitectura
✗ Tus convenciones
✗ Eventos después de training cutoff
```

### Fase 3: Fine-tuning (Opcional) 🎯

**Especialización**:
```
Pre-trained model: Conoce código en general
      ↓
Fine-tuning con tu código
      ↓
Specialized model: Conoce TU manera de codificar
```

### Fase 4: RLHF (Reinforcement Learning from Human Feedback) 🎮

**Qué es**:
```
Humanos evalúan outputs:

Output A: "Aquí está el código [genera código correcto]"
Output B: "No puedo ayudar con eso"

Humanos marcan A como mejor
↓
Modelo aprende a preferir respuestas útiles
```

**Por qué es importante**:
```
Sin RLHF: Modelo técnicamente correcto pero puede ser:
- Verboso
- Poco útil
- Ignora instrucciones
- Genera código inseguro

Con RLHF: Modelo que:
✓ Sigue instrucciones
✓ Es conciso y útil
✓ Rechaza peticiones peligrosas
✓ Admite cuando no sabe
```

## Cómo los Datos de Entrenamiento Afectan el Comportamiento

### Ejemplo 1: Lenguajes de Programación

**Datos de entrenamiento**:
```
JavaScript: 40% del código de entrenamiento
Python: 30%
Java: 15%
Rust: 2%
Lenguaje obscuro X: 0.01%
```

**Resultado en el modelo**:
```
Tú: "Escribe servidor web"

JS/Python: ✅ Excelente código, múltiples opciones
Java: ✅ Buen código, patterns conocidos
Rust: ⚠️ Código correcto pero patterns menos idiomáticos
Lenguaje X: ❌ Probablemente alucinará o dará código malo
```

### Ejemplo 2: Frameworks y Librerías

**Datos de entrenamiento**:
```
React: Millones de ejemplos
Vue: Miles de ejemplos
Framework nuevo (2024): Cero ejemplos (post cutoff)
```

**Resultado**:
```
React: IA experta, conoce hooks, patterns, ecosistema
Vue: IA competente, conoce básicos y algunos patterns
Framework 2024: IA no lo conoce, inventará sintaxis
```

### Ejemplo 3: Calidad del Código

**Problema real**:
```
Datos incluyen:
✓ Código excelente de repos top
✓ Código promedio de millones de repos
✗ Código terrible de tutoriales malos
✗ Código buggeado
✗ Código deprecated

Resultado: IA puede sugerir código de cualquier calidad
```

**Por eso necesitas**:
```javascript
// Siempre revisar código generado
const generated = await ai.generateCode();

// Verificar:
✓ ¿Usa APIs actuales?
✓ ¿Sigue best practices?
✓ ¿Tiene tests?
✓ ¿Es seguro?
✓ ¿Performance OK?

// NO asumir que es perfecto
```

## Limitaciones del Entrenamiento

### 1. Cutoff Date (Fecha de Corte) 📅

**Concepto**:
```
GPT-4 (versión original):
- Entrenado hasta: Septiembre 2021
- No sabe: Nada después de sept 2021

Claude 3:
- Entrenado hasta: Agosto 2023
- No sabe: Nada después de agosto 2023
```

**Impacto**:
```
❌ Tú: "¿Cómo uso React 19 server components?"
    IA: [Si React 19 es post-cutoff, alucinará]

✅ Tú: "¿Cómo uso React 18 hooks?"
    IA: [React 18 está en training, respuesta correcta]
```

### 2. Sesgos en los Datos 🎯

**Problema**:
```
Si entrenamiento incluye:
- Código principalmente de empresas tech USA
- Documentación en inglés
- Proyectos open source (más experimentos que prod)

Resultado:
⚠️ Mejor en inglés que otros idiomas
⚠️ Favorece patterns de Silicon Valley
⚠️ Puede sugerir código experimental vs. estable
```

**Ejemplo real**:
```typescript
Tú: "Crea componente de formulario"

IA puede sugerir:
- Librería muy nueva y experimental (vio en GitHub)
En lugar de:
- React Hook Form o Formik (battle-tested)

Por qué: Proyectos experimentales son más visibles
en repos públicos que código de producción privado
```

### 3. Distribución Desigual 📊

**Qué sucede**:
```
Stack popular (MERN):
- Millones de ejemplos
- Patterns bien establecidos
→ IA es excelente

Stack menos común:
- Miles de ejemplos
- Menos documentación pública
→ IA es mediocre

Tu stack específico:
- Cero ejemplos (código privado)
→ IA debe generalizar
```

## Por Qué la IA Sabe Unas Cosas y Otras No

### Lo que Sabe Bien ✅

**1. Código y patrones comunes**:
```javascript
// IA excelente en:
- Funciones JavaScript standard
- Componentes React básicos
- Express routes
- SQL queries comunes
- Configuraciones típicas
```

**2. Documentación pública**:
```
✓ APIs de Node.js
✓ Documentación de React
✓ MDN Web Docs
✓ Tutoriales populares
✓ Stack Overflow top questions
```

**3. Conceptos fundamentales**:
```
✓ Algoritmos clásicos
✓ Patrones de diseño
✓ Principios de arquitectura
✓ Best practices establecidas
```

### Lo que NO Sabe ❌

**1. Código privado/propietario**:
```
✗ Tu arquitectura específica
✗ Tu design system interno
✗ Tus helpers y utilities custom
✗ Tus convenciones de naming
✗ Tus patterns específicos
```

**2. Información post-cutoff**:
```
✗ Features nuevos de lenguajes
✗ Versiones recientes de frameworks
✗ Librerías lanzadas recientemente
✗ Breaking changes recientes
✗ Vulnerabilidades descubiertas después
```

**3. Conocimiento específico de nicho**:
```
✗ Frameworks muy nuevos o oscuros
✗ Protocolos propietarios
✗ APIs internas de empresas
✗ Casos edge muy específicos
```

## Evolución de los Modelos

### GPT-3 (2020)
```
Training data hasta: 2019
Tamaño: 175B parámetros
Fortalezas:
- Buen lenguaje natural
- Código básico

Debilidades:
- Código complejo limitado
- Sigue mal instrucciones
- Muchas alucinaciones
```

### GPT-4 (2023)
```
Training data hasta: 2021-2022
Tamaño: Estimado 1.7T parámetros
Fortalezas:
- Razonamiento avanzado
- Código complejo
- Sigue instrucciones mejor
- Multimodal (texto + imágenes)

Debilidades:
- Aún alucina
- Costoso
- A veces verboso
```

### Claude 3 (2024)
```
Training data hasta: 2023
Características:
- Context window masivo (200K tokens)
- Excelente en análisis de código
- Menos propenso a alucinación

Fortalezas específicas:
- Leer codebases enteros
- Análisis profundo
- Respuestas concisas
```

### Especializados (Codex, CodeLlama)
```
Training data: Principalmente código
Fortalezas:
- Generación de código superior
- Autocompletado preciso
- Múltiples lenguajes

Debilidades:
- Peor en conversación general
- Limitado a código
```

## Impacto en tu Trabajo Diario

### Entiende las Fortalezas

**Para código standard**:
```typescript
✅ "Crea función para validar email con regex"
// → IA excelente, pattern muy común

✅ "Implementa binary search en TypeScript"
// → IA excelente, algoritmo clásico
```

**Para código específico**:
```typescript
⚠️ "Crea componente siguiendo NUESTRO design system"
// → Necesitas dar ejemplos o contexto

⚠️ "Implementa usando NUESTRA arquitectura CQRS custom"
// → Necesitas explicar tu arquitectura
```

### Mitiga las Debilidades

**Proporciona contexto**:
```
❌ "Refactoriza este componente"

✅ "Refactoriza este componente siguiendo este patrón:
    [pega ejemplo de tu codebase]
    Usa styled-components y nuestros design tokens
    que están en src/tokens/"
```

**Verifica información reciente**:
```
❌ Confiar ciegamente en info sobre versiones recientes

✅ Cuando IA menciona versión reciente:
   → Verifica en docs oficiales
   → Busca en changelog
   → Prueba en proyecto de test
```

### Usa Estratégicamente

**Tareas donde training ayuda**:
```
✅ Boilerplate y setup inicial
✅ Refactoring de patterns conocidos
✅ Tests de lógica común
✅ Documentación standard
✅ Conversión entre lenguajes populares
```

**Tareas donde training limita**:
```
⚠️ Código de tu dominio específico
⚠️ Integración con tus sistemas internos
⚠️ Features de últimas versiones
⚠️ Optimizaciones avanzadas
⚠️ Decisiones de arquitectura contextual
```

## El Futuro del Entrenamiento

### Tendencias Emergentes

**1. Training continuo**:
```
Modelos que se actualizan frecuentemente:
- Reducir gap de conocimiento
- Conocer features recientes
- Adaptarse a nuevas librerías
```

**2. Especialización**:
```
Modelos específicos por dominio:
- CodeLlama para código
- Copilot para GitHub
- Modelos médicos, legales, etc.
```

**3. Personalización**:
```
Modelos que aprenden de tu uso:
- Tu estilo de código
- Tus preferencias
- Tu contexto específico
```

## Conclusión Clave

El entrenamiento determina **todo lo que la IA puede y no puede hacer**:

```
Sus conocimientos ← Datos de entrenamiento
Sus sesgos ← Sesgos en los datos
Sus limitaciones ← Gaps en los datos
Sus fortalezas ← Áreas bien representadas
```

**Para trabajar efectivamente con IA**:
1. Entiende qué sabe bien (código común, público, popular)
2. Entiende qué NO sabe (tu código, post-cutoff, nicho)
3. Compensa con contexto donde sea necesario
4. Verifica siempre código crítico

**Piénsalo así**: La IA es como un developer que:
- Leyó millones de repos de GitHub
- Estudió toda la documentación pública
- Nunca olvidará nada de eso
- Pero nunca trabajó en TU proyecto específico

Tu trabajo: Darle el contexto que le falta para ser efectiva en TU código.

## Relación con Otros Conceptos

- **[LLM](./01-llm.md)**: El entrenamiento crea el LLM
- **[Modelo](./02-modelo.md)**: Cada modelo es resultado de training diferente
- **[Fine-tuning](./10-fine-tuning.md)**: Es re-entrenamiento especializado
- **[Alucinación](./09-alucinacion.md)**: Limitaciones del training causan alucinaciones
- **[Token](./03-token.md)**: El training enseña al modelo a tokenizar

---

**Hecho**: Has completado todos los conceptos fundamentales de IA para desarrollo.

[← Volver a Conceptos](../README.md#conceptos)
