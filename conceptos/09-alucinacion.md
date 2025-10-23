# Alucinación

## ¿Qué es la Alucinación?

**Definición simple:** Cuando la IA genera información que es falsa, fabricada o inconsistente con la realidad, pero la presenta con total confianza.

**Analogía:** Como un compañero de equipo super confiado que inventa hechos. Dice: *"Ah sí, esa API tiene un método `.magicFix()` que resuelve todo"* - suena totalmente convincente, pero el método no existe.

**Importante**: La IA no está mintiendo intencionalmente. Está prediciendo lo que debería venir después basándose en patrones, a veces creando "hechos" que suenan correctos pero no son reales.

## Por Qué Sucede

Recuerda: La IA es un **motor de reconocimiento de patrones**, no una base de datos de hechos.

```
Tu cerebro: Busca en memoria → Recupera hecho → Responde
LLM: Ve patrón → Predice qué suena correcto → Genera respuesta

Problema: "Suena correcto" ≠ "Es correcto"
```

## Tipos de Alucinaciones en Desarrollo

### 1. APIs y Métodos Inventados 🔧

**Ejemplo real**:
```javascript
❌ IA sugiere:
fetch('api/data')
  .then(res => res.autoDeserialize()) // ← Este método NO existe
  .then(data => data.magicValidate())  // ← Este tampoco

✅ Realidad:
fetch('api/data')
  .then(res => res.json())
  .then(data => validateData(data))
```

**Por qué pasa**: La IA vio patrones de "deserializar" y "validar" en su training, e inventó métodos que "suenan" correctos.

### 2. Versiones y Features Incorrectos 📦

**Ejemplo real**:
```typescript
❌ IA afirma:
"En React 18, usa el hook useAutoMemo para optimización automática"
// useAutoMemo NO existe

✅ Realidad:
"En React 18, usa useMemo y useCallback para optimización"
```

### 3. Configuraciones Inventadas ⚙️

**Ejemplo real**:
```json
❌ IA sugiere tsconfig.json:
{
  "compilerOptions": {
    "autoFixImports": true,  // NO existe
    "smartTypeInference": "aggressive"  // NO existe
  }
}

✅ Realidad: Esas opciones no existen en TypeScript
```

### 4. Documentación Falsa 📚

**Ejemplo real**:
```
❌ IA cita:
"Según la documentación oficial de Next.js v14, usa el componente
<AutoImage> para optimización automática de imágenes"

✅ Realidad: Es <Image>, no <AutoImage>
```

### 5. Patrones y Best Practices Incorrectos 🎯

**Ejemplo real**:
```javascript
❌ IA recomienda:
"Para evitar re-renders en React, envuelve todo en useCallback"

// Código horrible con useCallback en exceso

✅ Realidad: useCallback solo cuando es necesario,
no en todas partes
```

### 6. Errores y Soluciones Inventadas 🐛

**Ejemplo real**:
```
Tú: "Tengo error: 'Cannot find module' en Node.js"

❌ IA responde:
"Ejecuta: npm fix-modules --deep-resolve"
// Comando que NO existe

✅ Solución real:
npm install o verificar import paths
```

## Alucinaciones Peligrosas en Producción

### Ejemplo 1: Seguridad 🔒

**Situación**:
```javascript
Tú: "¿Cómo valido JWT tokens en Express?"

❌ IA responde:
app.use(jwt.autoVerify({secret: process.env.SECRET}))
// jwt.autoVerify NO existe

✅ Correcto:
const jwt = require('jsonwebtoken');
app.use((req, res, next) => {
  const token = req.headers.authorization?.split(' ')[1];
  jwt.verify(token, process.env.SECRET, (err, decoded) => {
    if (err) return res.status(401).json({error: 'Invalid token'});
    req.user = decoded;
    next();
  });
});
```

**Riesgo**: Implementar código de seguridad que no funciona

### Ejemplo 2: Database Operations 💾

**Situación**:
```javascript
Tú: "¿Cómo hago transaction en MongoDB?"

❌ IA responde:
await db.autoTransaction(async (session) => {
  // MongoDB NO tiene autoTransaction
})

✅ Correcto:
const session = await mongoose.startSession();
session.startTransaction();
try {
  // operations
  await session.commitTransaction();
} catch (error) {
  await session.abortTransaction();
}
```

**Riesgo**: Pérdida de datos o inconsistencias

### Ejemplo 3: Performance 🚀

**Situación**:
```javascript
Tú: "¿Cómo optimizo renders en React?"

❌ IA responde:
"Usa el flag --optimize-renders en tu build"
// Este flag NO existe

✅ Correcto: useMemo, useCallback, React.memo según caso
```

**Riesgo**: Pensar que optimizaste cuando no lo hiciste

## Cómo Detectar Alucinaciones

### Señales de Alerta 🚨

**1. Demasiado específico sin fuente**:
```
❌ "El 73.4% de apps React que usan Context tienen problemas de performance"
⚠️ ¿De dónde salió ese número tan específico?
```

**2. APIs o métodos que nunca viste**:
```
❌ "Usa el método .superOptimize() de Array"
⚠️ Si programas JS hace años y nunca lo viste, probablemente no existe
```

**3. Sintaxis que "suena" demasiado conveniente**:
```
❌ "Simplemente usa: npm autofix"
⚠️ Si fuera tan fácil, ya lo habrías usado
```

**4. Información sobre versiones muy recientes**:
```
❌ "En la versión de ayer de React..."
⚠️ La IA no puede saber qué pasó ayer
```

**5. Soluciones "mágicas" sin tradeoffs**:
```
❌ "Este hook resuelve todos tus problemas de state sin ningún costo"
⚠️ En programación siempre hay tradeoffs
```

### Checklist de Verificación ✅

Antes de usar código de IA, pregúntate:

```
[ ] ¿Este API/método existe? → Busca en docs oficiales
[ ] ¿Esta sintaxis es válida? → Prueba en proyecto pequeño
[ ] ¿Esta versión tiene esta feature? → Verifica changelog
[ ] ¿Esta librería se llama así? → Busca en npm
[ ] ¿Este patrón es recomendado? → Busca en comunidad
```

## Estrategias de Verificación

### Para Código

**1. Prueba en entorno aislado**:
```bash
# Nunca pegues código directo a producción
# Crea test file primero

touch test-ai-suggestion.js
node test-ai-suggestion.js
```

**2. Consulta documentación oficial**:
```
IA dice: "Usa método X"
→ Busca en docs oficiales: [librería] + "método X"
→ Si no aparece, probablemente no existe
```

**3. Verifica en TypeScript**:
```typescript
// TypeScript te dirá si el método existe
import { someMethod } from 'library';
//       ^^^^^^^^^^
// Error: 'someMethod' does not exist in type...
```

**4. Usa linter/IDE**:
```
// Tu IDE subrayará en rojo lo que no existe
fetch.autoMagic()
//    ^^^^^^^^^^
// No property 'autoMagic' on type...
```

### Para Configuraciones

**1. Valida contra schema**:
```json
// package.json, tsconfig.json, etc. tienen schemas
// VSCode te avisará si algo no existe
```

**2. Compara con proyectos oficiales**:
```bash
# Clona ejemplo oficial
git clone https://github.com/[official-repo]
# Compara tu config con la de ellos
```

**3. Ejecuta validation**:
```bash
# Muchas herramientas tienen comando validate
npm run validate
tsc --noEmit
eslint --print-config .
```

## Usando IA de Forma Segura

### Regla de Oro

**Usa IA como asistente, NO como fuente de verdad**

```
✅ "Dame un borrador de componente Button"
   → Úsalo como punto de partida, verifica y adapta

❌ "Dame el código de autenticación y lo pego directo"
   → Peligroso para código crítico
```

### Framework de Confianza

**Alta confianza** (usar con supervisión mínima):
```
✓ Boilerplate y setup inicial
✓ Conversión de formatos obvios
✓ Refactoring de nombres
✓ Documentación y comments
✓ Tests de casos simples
```

**Media confianza** (revisar antes de usar):
```
⚠ Implementación de features
⚠ Lógica de negocio
⚠ Configuraciones complejas
⚠ Integración de librerías
```

**Baja confianza** (verificar exhaustivamente):
```
🚫 Código de seguridad (auth, permissions)
🚫 Operaciones de database críticas
🚫 Configuración de deploy
🚫 Código que maneja dinero/datos sensibles
🚫 Performance optimizations críticas
```

## Casos de Uso Seguros

### Donde la Alucinación es Menos Problema

**1. Exploración y aprendizaje**:
```
"Explícame el concepto de closures en JavaScript"
→ Aunque tenga imprecisiones menores, ayuda a entender
```

**2. Brainstorming**:
```
"Dame 10 ideas de nombres para esta función"
→ No importa si inventa palabras, busco inspiración
```

**3. Boilerplate**:
```
"Genera estructura básica de Express app"
→ Es punto de partida, no código final
```

**4. Documentación**:
```
"Escribe JSDoc para esta función"
→ Fácil de revisar y corregir
```

## Técnicas Avanzadas de Mitigación

### 1. Pide Fuentes

```
❌ "¿Cómo uso esta API?"
✅ "¿Cómo uso esta API? Proporciona link a documentación oficial"
```

### 2. Verifica Paso a Paso

```
✅ "Primero dame el nombre exacto del método"
✅ "Ahora dame link a docs oficiales"
✅ "Ahora muéstrame ejemplo de uso"
```

### 3. Usa Constraints

```
✅ "Genera código solo usando APIs estándar de JavaScript,
    sin librerías externas ni métodos no documentados"
```

### 4. Pide Alternativas

```
✅ "Dame 3 formas diferentes de hacer esto,
    con pros y contras de cada una"

Si todas usan mismo método "mágico" → sospecha
```

## Herramientas de Verificación

### Automáticas

```bash
# TypeScript type checking
npm run type-check

# Linting
npm run lint

# Tests
npm test

# Build (detecta muchos errores)
npm run build
```

### Manuales

```
✓ Google: "[método] [librería] documentation"
✓ GitHub: Busca en issues/código fuente
✓ Stack Overflow: Busca el método/patrón
✓ Can I Use: Para features de browser
✓ npm: Verifica nombres exactos de packages
```

## Conclusión Clave

La alucinación es una **característica inherente** de cómo funciona la IA:

- **NO es un bug** - es parte del modelo de predicción
- **NO desaparecerá** - siempre existirá el riesgo
- **PUEDES mitigarlo** - con verificación y buenas prácticas

**Filosofía**: "Trust but verify"
```
1. Usa IA para acelerar desarrollo
2. Pero SIEMPRE verifica código crítico
3. Prueba antes de mergear
4. Documenta lo que funciona
```

**Remember**: La IA es una herramienta increíblemente útil, pero tú eres el developer. La responsabilidad final es tuya.

## Relación con Otros Conceptos

- **[LLM](./01-llm.md)**: Las alucinaciones son inherentes a cómo funcionan los LLMs
- **[Temperatura](./06-temperatura.md)**: Temperatura alta aumenta riesgo de alucinación
- **[Agente](./08-agente.md)**: Los agentes pueden alucinar al usar herramientas
- **[Entrenamiento](./11-entrenamiento.md)**: La calidad del training afecta las alucinaciones

---

**Siguiente**: Aprende sobre [Fine-tuning](./10-fine-tuning.md) y cómo especializar modelos de IA.

[← Volver a Conceptos](../README.md#conceptos)
