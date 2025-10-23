# RAG (Retrieval-Augmented Generation)

## ¿Qué es RAG?

**Definición simple:** Una técnica que permite a la IA buscar información relevante antes de responder, como usar Google antes de contestar una pregunta.

**Analogía:**
- **Sin RAG** = Estudiante haciendo un examen de memoria (solo sabe lo que memorizó)
- **Con RAG** = Estudiante haciendo un examen con libro abierto (puede consultar fuentes)

Piensa en RAG como darle a la IA acceso a una biblioteca de información específica de tu proyecto, en lugar de depender solo de su entrenamiento general.

## El Problema que Resuelve

### Sin RAG ❌

```
Tú: "¿Cómo funciona nuestro sistema de autenticación?"

IA: "Generalmente los sistemas de autenticación usan JWT o sessions.
     Puedo explicarte los conceptos generales..."

     [Responde con conocimiento genérico, no específico de TU proyecto]
```

### Con RAG ✅

```
Tú: "¿Cómo funciona nuestro sistema de autenticación?"

IA: [Busca en docs del proyecto]
    [Lee auth.ts, AUTH.md, tests]

    "Tu sistema usa JWT con refresh tokens. El flujo es:
    1. Login genera access token (15 min) y refresh token (7 días)
    2. Los tokens se firman con RS256
    3. El middleware validateAuth verifica en cada request

    Esto está implementado en src/auth/jwt.service.ts:42"
```

## ¿Cómo Funciona RAG?

### El Proceso en 4 Pasos

```
┌─────────────────────────────────────────────────┐
│ 1. PREGUNTA DEL USUARIO                         │
│    "¿Cómo funciona la cache?"                   │
└────────────┬────────────────────────────────────┘
             │
             ↓
┌─────────────────────────────────────────────────┐
│ 2. BÚSQUEDA (Retrieval)                         │
│    Sistema busca documentos relevantes:         │
│    ✓ cache.ts                                   │
│    ✓ CACHE.md                                   │
│    ✓ redis-config.ts                            │
└────────────┬────────────────────────────────────┘
             │
             ↓
┌─────────────────────────────────────────────────┐
│ 3. CONTEXTO                                     │
│    Documentos encontrados se añaden al prompt:  │
│    [contenido de cache.ts]                      │
│    [contenido de CACHE.md]                      │
│    [contenido de redis-config.ts]               │
└────────────┬────────────────────────────────────┘
             │
             ↓
┌─────────────────────────────────────────────────┐
│ 4. GENERACIÓN (Generation)                      │
│    LLM responde basándose en los documentos     │
│    encontrados + su conocimiento general        │
└─────────────────────────────────────────────────┘
```

## Componentes de un Sistema RAG

### 1. Knowledge Base (Base de Conocimiento)

**Qué es:** Donde se almacena la información que puede buscar

**Puede contener:**
```
📄 Documentación del proyecto
💻 Código fuente
📝 READMEs y guías
🐛 Issues y PRs
📊 Especificaciones
💬 Conversaciones pasadas
```

**Formatos:**
```
- Archivos de texto
- PDFs
- Markdown
- Código
- JSON/YAML
- Bases de datos
```

### 2. Embeddings (Vectorización)

**Qué son:** Convertir texto en números que representan su significado

**Ejemplo:**
```javascript
// Texto original
"función para validar email"
      ↓
// Se convierte en vector numérico
[0.2, -0.5, 0.8, 0.1, -0.3, ...]
```

**Por qué importa:**
- Permite buscar por **significado**, no solo palabras exactas
- "login de usuario" encontrará "autenticación" aunque no use esa palabra

### 3. Vector Database (Base de Datos Vectorial)

**Qué es:** Base de datos optimizada para buscar por similitud de vectores

**Populares:**
```
Pinecone    → Hosted, fácil de usar
Weaviate    → Open source, completo
Qdrant      → Rust, muy rápido
Chroma      → Python, simple
FAISS       → Meta, para investigación
```

**Qué hace:**
```
Entrada: "cómo hacer login"
         ↓
Vector: [0.3, 0.1, -0.4, ...]
         ↓
Búsqueda de vectores similares
         ↓
Resultados:
  - auth.md (95% similar)
  - login.ts (92% similar)
  - user-flow.md (87% similar)
```

### 4. Retriever (Recuperador)

**Qué es:** El sistema que decide QUÉ documentos son relevantes

**Tipos:**

**Búsqueda Densa:**
```
Usa embeddings para encontrar similitud semántica
Mejor para: Preguntas conceptuales

Ejemplo: "¿cómo manejar errores?"
Encuentra: docs de error-handling aunque no use esas palabras exactas
```

**Búsqueda Sparse:**
```
Búsqueda tradicional por palabras clave (BM25)
Mejor para: Búsquedas exactas, nombres específicos

Ejemplo: "función validateUser"
Encuentra: exactamente donde está validateUser
```

**Híbrido:**
```
Combina ambas técnicas
Mejor para: Mayoría de casos

Usa semántica + palabras clave para mejores resultados
```

## Flujo Completo: Ejemplo Real

### Setup Inicial

```javascript
// 1. Indexar documentos
const docs = [
  "docs/auth.md",
  "src/auth/*.ts",
  "README.md"
];

// 2. Convertir a embeddings
const embeddings = await generateEmbeddings(docs);

// 3. Guardar en vector DB
await vectorDB.insert(embeddings);
```

### Pregunta del Usuario

```javascript
// Usuario pregunta
const query = "¿Cómo renovar un token expirado?";

// 1. Convertir pregunta a embedding
const queryEmbedding = await generateEmbedding(query);

// 2. Buscar documentos similares
const relevantDocs = await vectorDB.search(queryEmbedding, {
  limit: 3,
  minSimilarity: 0.7
});

// Resultados:
// [
//   { doc: "auth.md", score: 0.92 },
//   { doc: "refresh-token.ts", score: 0.88 },
//   { doc: "jwt.service.ts", score: 0.85 }
// ]

// 3. Construir prompt con contexto
const prompt = `
Basándote en esta documentación:

${relevantDocs.map(d => d.content).join('\n\n')}

Responde: ${query}
`;

// 4. LLM genera respuesta
const answer = await llm.generate(prompt);
```

## Casos de Uso

### 1. Chat con Tu Codebase

**Sin RAG:**
```
Tú: "¿Dónde se maneja el pago?"
IA: "Típicamente los pagos se manejan en un payment service..."
     [Respuesta genérica]
```

**Con RAG:**
```
Tú: "¿Dónde se maneja el pago?"
IA: [Busca en codebase]
    "Los pagos se manejan en src/services/stripe.service.ts

    El flujo es:
    1. checkoutHandler() valida el carrito
    2. createPaymentIntent() crea intención en Stripe
    3. handleWebhook() procesa confirmación

    Logs en src/services/stripe.service.ts:67"
```

### 2. Documentación Inteligente

**Problema:**
- Tienes 500 páginas de documentación
- Buscar manualmente toma mucho tiempo

**Solución RAG:**
```
Tú: "¿Cómo deployear a producción?"
IA: [Busca en docs]
    "Para deployear a producción:

    1. npm run build
    2. npm run test:e2e
    3. git tag v1.x.x
    4. git push origin v1.x.x
    5. GitHub Actions se encarga del resto

    Fuente: DEPLOYMENT.md, .github/workflows/deploy.yml"
```

### 3. Onboarding de Nuevos Developers

**Problema:**
- Nuevos desarrolladores tienen muchas preguntas
- Seniors gastan tiempo respondiendo lo mismo

**Solución RAG:**
```
Junior: "¿Cómo corro el proyecto?"
Bot RAG: [Busca en docs]
         "Setup del proyecto:

         1. npm install
         2. cp .env.example .env
         3. docker-compose up -d
         4. npm run migrate
         5. npm run dev

         Fuente: README.md sección Setup"
```

### 4. Q&A sobre Compliance/Legal

**Problema:**
- Documentación legal extensa
- Necesitas respuestas precisas y citadas

**Solución RAG:**
```
Tú: "¿Cuánto tiempo guardamos datos de usuarios?"
IA: [Busca en políticas]
    "Según la política de retención de datos:

    - Datos activos: Mientras cuenta esté activa
    - Post-cancelación: 90 días
    - Backups: 1 año
    - Datos de menores: Eliminación inmediata tras solicitud

    Fuente: PRIVACY_POLICY.md sección 4.2, GDPR_COMPLIANCE.md"
```

## Implementación: Ejemplo Práctico

### Opción 1: Simple (Con LangChain)

```javascript
import { OpenAI } from "langchain/llms/openai";
import { RetrievalQAChain } from "langchain/chains";
import { HNSWLib } from "langchain/vectorstores/hnswlib";
import { OpenAIEmbeddings } from "langchain/embeddings/openai";

// 1. Cargar documentos
const docs = await loadDocuments("./docs");

// 2. Crear vector store
const vectorStore = await HNSWLib.fromDocuments(
  docs,
  new OpenAIEmbeddings()
);

// 3. Crear chain RAG
const chain = RetrievalQAChain.fromLLM(
  new OpenAI(),
  vectorStore.asRetriever()
);

// 4. Hacer pregunta
const answer = await chain.call({
  query: "¿Cómo funciona la autenticación?"
});
```

### Opción 2: Con Control (Custom)

```javascript
// 1. Generar embeddings
const embedModel = new OpenAIEmbeddings();

async function indexDocuments(docs) {
  const embeddings = [];

  for (const doc of docs) {
    const embedding = await embedModel.embedQuery(doc.content);
    embeddings.push({
      id: doc.id,
      content: doc.content,
      vector: embedding,
      metadata: doc.metadata
    });
  }

  await vectorDB.insert(embeddings);
}

// 2. Búsqueda
async function search(query, options = {}) {
  const queryEmbedding = await embedModel.embedQuery(query);

  const results = await vectorDB.search(queryEmbedding, {
    limit: options.limit || 5,
    minScore: options.minScore || 0.7
  });

  return results;
}

// 3. Generar respuesta
async function askQuestion(question) {
  // Buscar contexto relevante
  const context = await search(question, { limit: 3 });

  // Construir prompt
  const prompt = `
Contexto:
${context.map(c => c.content).join('\n\n')}

Pregunta: ${question}

Responde basándote en el contexto. Si la información no está en el contexto, dilo claramente.
  `;

  // Generar respuesta
  const response = await llm.generate(prompt);

  return {
    answer: response,
    sources: context.map(c => c.metadata)
  };
}
```

## Chunking: Dividir Documentos

Un documento grande debe dividirse en pedazos (chunks) más pequeños.

### Estrategias de Chunking

**Por Tamaño Fijo:**
```javascript
// Cada 500 caracteres
function chunkBySize(text, size = 500) {
  const chunks = [];
  for (let i = 0; i < text.length; i += size) {
    chunks.push(text.slice(i, i + size));
  }
  return chunks;
}

Pros: Simple, predecible
Contras: Puede cortar en mitad de oración
```

**Por Semántica:**
```javascript
// Por párrafos o secciones
function chunkBySemantic(text) {
  return text.split('\n\n').filter(p => p.trim());
}

Pros: Respeta estructura natural
Contras: Chunks de tamaño variable
```

**Con Overlap:**
```javascript
// Overlap de 50 caracteres entre chunks
function chunkWithOverlap(text, size = 500, overlap = 50) {
  const chunks = [];
  for (let i = 0; i < text.length; i += size - overlap) {
    chunks.push(text.slice(i, i + size));
  }
  return chunks;
}

Pros: Mantiene contexto entre chunks
Contras: Algo de duplicación
```

### Recomendaciones

```
📝 Documentación: Por secciones/headings
💻 Código: Por funciones/clases
📊 Datos: Por registros o bloques lógicos
📄 PDFs: Por páginas o párrafos
```

## Evaluación de Calidad RAG

### Métricas Clave

**1. Retrieval Precision**
```
¿Los documentos encontrados son relevantes?

Precision = Docs relevantes encontrados / Total docs encontrados

Ideal: > 0.8
```

**2. Retrieval Recall**
```
¿Encontramos todos los documentos relevantes?

Recall = Docs relevantes encontrados / Total docs relevantes existentes

Ideal: > 0.7
```

**3. Answer Relevance**
```
¿La respuesta responde la pregunta?

Evaluación manual o con LLM evaluator

Ideal: > 90% de respuestas relevantes
```

**4. Faithfulness**
```
¿La respuesta está basada en los documentos?

Verifica que no invente información

Ideal: > 95% de fidelidad
```

### Testing

```javascript
const testCases = [
  {
    question: "¿Cómo hacer login?",
    expectedDocs: ["auth.md", "login.ts"],
    expectedAnswer: "debe mencionar JWT y el flow"
  },
  // ... más casos
];

async function evaluateRAG() {
  for (const test of testCases) {
    const result = await askQuestion(test.question);

    // Verificar documentos encontrados
    const docsMatch = test.expectedDocs.every(
      doc => result.sources.includes(doc)
    );

    // Verificar calidad de respuesta
    const answerQuality = await evaluateAnswer(
      result.answer,
      test.expectedAnswer
    );

    console.log({
      question: test.question,
      docsMatch,
      answerQuality
    });
  }
}
```

## Problemas Comunes y Soluciones

### Problema 1: Respuestas Genéricas

**Síntoma:**
```
IA responde con conocimiento general, ignorando contexto específico
```

**Causas:**
- Documentos no fueron encontrados
- Threshold de similitud muy alto
- Embeddings de baja calidad

**Solución:**
```javascript
// Bajar threshold
const results = await search(query, {
  minScore: 0.6  // antes: 0.8
});

// Aumentar número de documentos
const results = await search(query, {
  limit: 5  // antes: 2
});

// Mejorar embeddings
const embeddings = await betterEmbedModel.embedQuery(text);
```

### Problema 2: Respuestas Contradictorias

**Síntoma:**
```
IA da información que contradice la documentación
```

**Causas:**
- Documentación desactualizada en knowledge base
- Múltiples versiones del mismo documento

**Solución:**
```javascript
// Filtrar por fecha
const results = await search(query, {
  filter: {
    date: { $gte: '2024-01-01' }
  }
});

// Priorizar por versión
const results = await search(query, {
  boost: {
    version: 'latest'
  }
});
```

### Problema 3: Lentitud

**Síntoma:**
```
Búsqueda toma > 5 segundos
```

**Causas:**
- Base de datos vectorial no optimizada
- Demasiados documentos
- Embeddings grandes

**Solución:**
```javascript
// Usar índices HNSW
await vectorDB.createIndex({
  type: 'hnsw',
  m: 16,
  efConstruction: 200
});

// Filtrar antes de buscar
const results = await search(query, {
  preFilter: {
    category: 'auth'  // Solo busca en categoría relevante
  }
});

// Cache de queries comunes
const cached = await cache.get(query);
if (cached) return cached;
```

## RAG vs Fine-tuning

### Cuándo Usar RAG ✅

```
✅ Información que cambia frecuentemente
✅ Múltiples bases de conocimiento
✅ Necesitas citas/fuentes
✅ Presupuesto limitado
✅ Respuestas deben ser actualizadas
✅ Control sobre qué información se usa
```

**Ejemplo:** Chat con documentación de producto

### Cuándo Usar Fine-tuning ✅

```
✅ Comportamiento/estilo específico
✅ Dominio muy especializado
✅ Latencia crítica
✅ Información estable
✅ No necesitas citas
```

**Ejemplo:** Modelo para escribir código en estilo específico de empresa

### Usar Ambos 🎯

```
Fine-tuning: Para el estilo y comportamiento
RAG: Para información actualizada

Ejemplo: Modelo entrenado en estilo de tu empresa + RAG
        para buscar en documentación actualizada
```

## Mejores Prácticas

### 1. Estructura Tu Knowledge Base

```
/docs
  /getting-started
    - setup.md
    - quickstart.md
  /api
    - authentication.md
    - endpoints.md
  /guides
    - deployment.md
    - testing.md

Beneficio: Búsquedas más precisas con metadata de carpeta
```

### 2. Añade Metadata Rica

```javascript
{
  content: "...",
  metadata: {
    type: "documentation",
    category: "api",
    lastUpdated: "2024-01-15",
    author: "team",
    tags: ["auth", "security"],
    version: "2.0"
  }
}

Beneficio: Filtros y contexto adicional
```

### 3. Actualiza Regularmente

```javascript
// Reindexar cada noche
cron.schedule('0 2 * * *', async () => {
  const changedDocs = await getChangedDocuments();
  await reindexDocuments(changedDocs);
});

Beneficio: Knowledge base siempre actualizada
```

### 4. Monitorea Uso

```javascript
async function trackQuery(query, results) {
  await analytics.track({
    event: 'rag_query',
    query,
    resultsCount: results.length,
    topScore: results[0]?.score,
    responseTime: Date.now() - startTime
  });
}

Beneficio: Identifica queries problemáticas
```

## Herramientas y Frameworks

### Frameworks Completos

**LangChain**
```
✓ Más popular
✓ Python y JavaScript
✓ Muchas integraciones
✓ Comunidad grande
```

**LlamaIndex**
```
✓ Especializado en RAG
✓ Muy flexible
✓ Optimizado para performance
✓ Enfoque en datos
```

**Haystack**
```
✓ Production-ready
✓ Pipelines complejos
✓ Múltiples retrievers
✓ Open source
```

### Vector Databases

**Pinecone**
```
✓ Managed service
✓ Muy fácil de usar
✓ Escalable
$ Pago
```

**Weaviate**
```
✓ Open source
✓ Self-hosted o cloud
✓ Híbrido search built-in
✓ GraphQL API
```

**Qdrant**
```
✓ Muy rápido (Rust)
✓ Open source
✓ Filtros avanzados
✓ Fácil self-host
```

**Chroma**
```
✓ Súper simple
✓ Python-first
✓ Embedding store
✓ Ideal para prototipos
```

## Conclusión

RAG es **fundamental** para aplicaciones de IA prácticas:

**Sin RAG:**
- IA solo sabe lo que entrenó (limitado)
- Información desactualizada
- No puede acceder a datos privados

**Con RAG:**
- IA puede acceder a información específica
- Siempre actualizada
- Respuestas con fuentes

**Casos de uso perfectos:**
- 📚 Chat con documentación
- 💬 Customer support bots
- 🔍 Búsqueda semántica en codebase
- 📊 Q&A sobre datos internos

**Piénsalo así:** RAG convierte a la IA de "sabelotodo genérico" a "experto en TU dominio específico".

## Relación con Otros Conceptos

- **[Fine-tuning](./10-fine-tuning.md)**: Alternativa o complemento a RAG
- **[Embeddings](../glosario.md#📊-embeddings)**: Tecnología core de RAG
- **[Contexto](./04-contexto.md)**: RAG expande el contexto disponible
- **[LLM](./01-llm.md)**: RAG mejora las respuestas del LLM

---

**Siguiente**: Vuelve al [Glosario](../glosario.md) para más términos o comienza con [Nivel 1](../guia-practica/nivel-1-chat-basico.md).

[← Volver a Conceptos](../README.md#conceptos)
