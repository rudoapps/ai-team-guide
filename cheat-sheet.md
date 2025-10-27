# Hoja de Referencia Rápida de IA para Desarrolladores

*Guarda este documento para referencia rápida*

---

## 🧠 Conceptos Fundamentales

| Concepto | Definición | Cuándo Usar |
|----------|-----------|-------------|
| **[LLM](./conceptos/01-llm.md)** | Motor que aprendió patrones de código y texto | Entender capacidades/límites |
| **[Modelo](./conceptos/02-modelo.md)** | Implementación específica de LLM | Elegir herramienta correcta |
| **[Token](./conceptos/03-token.md)** | Unidades de texto que procesa la IA | Gestionar costes y límites |
| **[Contexto](./conceptos/04-contexto.md)** | Información de fondo que le das | Obtener mejores resultados |
| **[Prompt](./conceptos/05-prompt.md)** | Tu instrucción para la IA | Generar código/soluciones |
| **[Temperatura](./conceptos/06-temperatura.md)** | Control de creatividad (0-1) | Ajustar estilo de salida |
| **[Herramienta](./conceptos/07-herramienta.md)** | Capacidades que extienden la IA | Automatizar tareas |
| **[Agente](./conceptos/08-agente.md)** | IA que ejecuta tareas autónomamente | Tareas complejas multi-paso |
| **[Alucinación](./conceptos/09-alucinacion.md)** | IA inventa información falsa | Verificar salidas críticas |
| **[Fine-tuning](./conceptos/10-fine-tuning.md)** | Especializar IA con tus datos | IA personalizada |
| **[MCP](./conceptos/12-mcp.md)** | Protocolo para conectar IA con datos | Integrar sistemas/contexto |
| **[RAG](./conceptos/13-rag.md)** | Enriquecer respuestas con documentos | IA con datos actualizados |

---

## 🎯 Guía Rápida de Temperatura

| Tarea | Temperatura | Ejemplo |
|-------|-------------|---------|
| **Código de producción** | 0.1-0.2 ❄️ | Funciones, APIs, queries |
| **Refactoring** | 0.3-0.4 🌡️ | Optimización, arquitectura |
| **Naming** | 0.6-0.8 🔥 | Variables, funciones, componentes |
| **Documentación** | 0.4-0.5 🌡️ | READMEs, comentarios |
| **Brainstorming** | 0.7-0.9 🔥 | Ideas de features, arquitecturas |

---

## ✍️ Fórmula de Prompt para Desarrollo

**Estructura Básica:**
```
[CONTEXTO] + [TAREA ESPECÍFICA] + [RESTRICCIONES/FORMATO]
```

**Template Completo:**
```
Contexto: Estoy trabajando en [proyecto] usando [stack/tecnologías]
Tarea: [Lo que necesitas que haga]
Restricciones:
- Lenguaje/framework: [específico]
- Versión: [versión específica]
- Patrones: [arquitectura, principios]
- Sin: [librerías/patrones a evitar]
Formato de salida: [código completo, explicación, tests, etc.]
```

**Ejemplo Concreto:**
```
Contexto: App móvil en React Native con TypeScript
Tarea: Crear hook personalizado para manejar autenticación JWT
Restricciones:
- React Native 0.72
- TypeScript estricto
- Usar AsyncStorage para persistencia
- Seguir patrón de hooks de React
- Incluir manejo de errores explícito
Formato: Código completo + explicación de uso
```

---

## 🚨 Detectar Alucinaciones en Código

**Siempre verifica cuando la IA menciona:**

❌ **APIs o métodos que no conoces**
```javascript
// ❌ Esto podría no existir
import { autoOptimize } from 'react-native'
```

❌ **Configuraciones específicas sin documentar**
```yaml
# ❌ Configuración inventada
webpack:
  autoSplitChunks: magic
```

❌ **Versiones específicas de librerías**
```json
// ❌ Verifica si estas versiones existen
"react": "18.5.0",
"next": "14.8.0"
```

❌ **Comandos o flags desconocidos**
```bash
# ❌ Este flag podría no existir
npm install --smart-resolve
```

---

## 🔧 Guía de Selección de Modelo

**Para Desarrollo:**

| Necesidad | Modelo Recomendado | Por qué |
|-----------|-------------------|---------|
| **Código rápido** | GPT-3.5 Turbo | Rápido, barato, decente |
| **Código complejo** | GPT-4, Claude Opus | Razonamiento avanzado |
| **Archivos múltiples** | Claude (200K) | Contexto grande |
| **Debugging profundo** | GPT-4, Claude Opus | Análisis detallado |
| **Autocompletar en IDE** | GitHub Copilot | Especializado para código |
| **Agente autónomo** | Claude Code | Ejecuta tareas completas |

---

## ✅ Prácticas Seguras

### **Luz Verde** (Usar Libremente) 🟢
- Generar boilerplate y templates
- Explicar código existente
- Sugerir optimizaciones
- Crear tests unitarios
- Documentación y comentarios
- Brainstorming de arquitectura

### **Luz Amarilla** (Verificar Antes) 🟡
- Configuraciones de build/deploy
- Queries de base de datos
- Código de seguridad (auth, permisos)
- Integración con APIs externas
- Migraciones de datos

### **Luz Roja** (Alto Riesgo) 🔴
- Código de producción sin revisión
- Scripts de deployment
- Cambios de esquema de BD
- Configuración de seguridad
- Secrets/credentials
- Código crítico sin tests

---

## 🎭 Por Rol

### **Desarrolladores iOS/Android**
- **Prompt tipo**: "Crea en [Swift/Kotlin]..."
- **Temperatura por defecto**: 0.2-0.3
- **Verificar siempre**: APIs del sistema, permisos, ciclo de vida

### **Desarrolladores Frontend**
- **Prompt tipo**: "Componente React/Vue en TypeScript..."
- **Temperatura por defecto**: 0.3-0.4
- **Verificar siempre**: Hooks, renders, performance

### **Desarrolladores Backend**
- **Prompt tipo**: "API endpoint en [framework]..."
- **Temperatura por defecto**: 0.2-0.3
- **Verificar siempre**: SQL injection, auth, validación

### **Diseñadores (Figma)**
- **Prompt tipo**: "Sistema de componentes con..."
- **Temperatura por defecto**: 0.5-0.6
- **Verificar siempre**: Accesibilidad, consistencia, tokens

### **DevOps**
- **Prompt tipo**: "Script para automatizar..."
- **Temperatura por defecto**: 0.1-0.2
- **Verificar siempre**: Comandos destructivos, permisos, rollback

---

## 🆘 Solución Rápida de Problemas

**"El código no compila"**
→ Verifica versiones de lenguaje/framework en el prompt

**"API no existe"**
→ IA inventó método. Consulta documentación oficial

**"Funciona pero muy lento"**
→ Pide optimización: "Optimiza esto con complejidad O(n log n)"

**"Código inseguro"**
→ Rechaza y pide: "Reescribe esto sin vulnerabilidades SQL/XSS"

**"Respuesta muy genérica"**
→ Añade más contexto: stack, versiones, patrones usados

**"Se contradice en conversación larga"**
→ Resume contexto: "Recordatorio: proyecto X, stack Y, trabajando en Z"

---

## 📊 Comparación Rápida de Modelos

| Modelo | Velocidad | Coste | Calidad Código | Contexto | Mejor Para |
|--------|-----------|-------|----------------|----------|------------|
| **GPT-4** | ⚡⚡ | 💰💰💰 | ⭐⭐⭐⭐⭐ | 128K | Código complejo |
| **GPT-3.5** | ⚡⚡⚡⚡ | 💰 | ⭐⭐⭐ | 16K | Boilerplate rápido |
| **Claude Opus** | ⚡⚡ | 💰💰💰 | ⭐⭐⭐⭐⭐ | 200K | Refactoring grande |
| **Claude Sonnet** | ⚡⚡⚡ | 💰💰 | ⭐⭐⭐⭐ | 200K | Balance |
| **Copilot** | ⚡⚡⚡⚡⚡ | 💰💰 | ⭐⭐⭐ | Archivo | Autocompletar |
| **Claude Code** | ⚡⚡ | 💰💰💰 | ⭐⭐⭐⭐ | Proyecto | Agente autónomo |

---

## 🎓 Ejemplos Prácticos Rápidos

### Ejemplo 1: Generar Función

**Prompt:**
```
Crea una función en TypeScript que valide emails.
- Usa regex moderno
- Retorna objeto con { valid: boolean, error?: string }
- Incluye tests con Jest
```

### Ejemplo 2: Debugging

**Prompt:**
```
Este código da error "Cannot read property 'map' of undefined":

[pega código]

Contexto: React 18, datos vienen de API async
¿Cuál es el problema y cómo lo soluciono?
```

### Ejemplo 3: Refactoring

**Prompt:**
```
Refactoriza esta clase siguiendo principios SOLID:

[pega código]

Stack: TypeScript, Node.js
Mantén: misma funcionalidad, tests deben pasar
Objetivo: más testeable y mantenible
```

### Ejemplo 4: Optimización

**Prompt:**
```
Este código es lento con 10k items:

[pega código]

Optimízalo manteniendo funcionalidad.
Explica complejidad antes y después.
```

---

## 💡 Tips Pro

1. **Versiones importan**: Siempre especifica versiones exactas
2. **Itera gradualmente**: No pidas todo a la vez
3. **Copy-paste con cerebro**: Lee y entiende antes de usar
4. **Tests primero**: Pide tests junto con el código
5. **Documentación oficial**: Verifica APIs en docs oficiales
6. **Contexto acumulativo**: Construye sobre respuestas previas
7. **Prompt library**: Guarda tus mejores prompts
8. **Temperatura baja**: Para código de producción (0.1-0.3)

---

## 📞 Obtener Más Ayuda

1. **Conceptos**: Consulta [/conceptos](./conceptos/) para entender a fondo

---

## 🚀 Workflows Comunes

### Crear Feature Nueva
```
1. "Diseña arquitectura para [feature]"
2. "Genera estructura de archivos y tipos"
3. "Implementa [componente/módulo 1]"
4. "Crea tests para [componente 1]"
5. "Repite 3-4 para cada componente"
6. "Crea documentación y ejemplos de uso"
```

### Debugging
```
1. "Analiza este error: [stack trace]"
2. "¿Qué causa este comportamiento?"
3. "Propón 3 soluciones con pros/contras"
4. "Implementa solución [elegida]"
5. "Crea test para prevenir regresión"
```

### Code Review
```
1. "Actúa como senior developer"
2. "Revisa este código: [código]"
3. "Evalúa: bugs, performance, seguridad, SOLID"
4. "Sugiere mejoras específicas"
5. "Prioriza por impacto"
```

---

*Mantén esta hoja a mano - ¡domina estos conceptos y serás un power user de IA!*

[← Volver al Inicio](./README.md)
