# Agente

## ¿Qué es un Agente?

**Definición simple:** Un asistente de IA que puede ejecutar tareas por ti usando herramientas, no solo dar consejos.

**Analogía:**
- **LLM básico** = Consultor senior que da excelentes consejos
- **Agente** = Developer junior que puede implementar esas soluciones

Piensa en la diferencia entre:
- **Consultor**: "Deberías refactorizar ese componente usando composition pattern"
- **Agente**: *Refactoriza el componente, actualiza imports, ejecuta tests, y hace commit*

## Cómo Funcionan: El Ciclo ReAct

Los agentes usan un loop de **Razonar + Actuar**:

### 1. RAZONAR 🤔
```
"Para refactorizar este componente necesito:
1. Primero leer el componente actual
2. Identificar duplicación de código
3. Extraer lógica común
4. Verificar con tests"
```

### 2. ACTUAR 🔧
```
[Lee archivo src/components/Button.tsx]
```

### 3. RAZONAR 🤔
```
"Veo que el componente tiene 200 líneas.
Puedo extraer:
- Styles a styled-components
- Lógica de estado a custom hook
- Variantes a constantes"
```

### 4. ACTUAR 🔧
```
[Crea Button.styles.ts]
[Crea useButtonState.ts]
[Actualiza Button.tsx]
```

### 5. RAZONAR 🤔
```
"Cambios completados. Ahora debo verificar que funciona."
```

### 6. ACTUAR 🔧
```
[Ejecuta: npm test Button]
[Ve que todos los tests pasan]
```

### 7. COMPLETAR ✅
```
"Refactoring completado.
- Button.tsx: 200 → 80 líneas
- Tests: ✅ Todos pasando
- Listo para commit"
```

## Ejemplo Real: Feature Completo

**Tu solicitud**: "Añade un componente Toast para notificaciones"

**Proceso del Agente**:

```
1. RAZONAR: "Necesito entender la estructura del proyecto"
   ACTUAR: [Lee src/components/]

2. RAZONAR: "Veo que usan styled-components y TypeScript"
   ACTUAR: [Busca en docs: React Toast patterns]

3. RAZONAR: "Voy a crear un Toast con context para estado global"
   ACTUAR: [Crea ToastContext.tsx]

4. RAZONAR: "Ahora el componente visual"
   ACTUAR: [Crea Toast.tsx con animaciones]

5. RAZONAR: "Necesito hook para usar desde otros componentes"
   ACTUAR: [Crea useToast.ts]

6. RAZONAR: "Debo añadir tipos TypeScript"
   ACTUAR: [Crea Toast.types.ts]

7. RAZONAR: "Falta el provider en App"
   ACTUAR: [Actualiza App.tsx]

8. RAZONAR: "Ahora tests"
   ACTUAR: [Crea Toast.test.tsx]

9. RAZONAR: "Ejecuto tests para verificar"
   ACTUAR: [npm test Toast]

10. RAZONAR: "Todo funciona, documento y commiteо"
    ACTUAR: [Actualiza README con ejemplo de uso]
    ACTUAR: [git commit -m "feat: Add Toast notification system"]
```

**Tiempo ahorrado**: Lo que tomaría 2-3 horas → 10-15 minutos

## Tipos de Agentes

### Agente Conversacional 💬
**Qué hace**: Responde preguntas, explica conceptos
**Herramientas**: Principalmente búsqueda y lectura
**Ejemplo**: ChatGPT básico, Claude en web

### Agente de Código 👨‍💻
**Qué hace**: Lee, escribe, y ejecuta código
**Herramientas**: File system, terminal, git
**Ejemplo**: GitHub Copilot Workspace, Claude Code

### Agente de Testing 🧪
**Qué hace**: Ejecuta tests, encuentra bugs, valida
**Herramientas**: Test runners, debuggers, profilers
**Ejemplo**: Agentes especializados en QA

### Agente DevOps 🚀
**Qué hace**: Builds, deploys, monitorea
**Herramientas**: CI/CD, cloud platforms, logs
**Ejemplo**: Integraciones de deployment automation

## Herramientas que Usan los Agentes

### Desarrollo Frontend

**Lectura**:
```
✓ Leer componentes React/Vue/Svelte
✓ Analizar estilos CSS/SCSS/Tailwind
✓ Revisar configuración (Webpack, Vite, etc.)
✓ Ver estructura de proyecto
```

**Escritura**:
```
✓ Crear/editar componentes
✓ Generar tests (Jest, Vitest, Playwright)
✓ Actualizar configuraciones
✓ Refactorizar código
```

**Ejecución**:
```
✓ npm install/run scripts
✓ Ejecutar tests
✓ Linting y formatting
✓ Build y preview
```

### Desarrollo Backend

**Lectura**:
```
✓ Analizar APIs (Express, Fastify, etc.)
✓ Revisar modelos de DB
✓ Entender middleware y auth
✓ Ver logs y errors
```

**Escritura**:
```
✓ Crear endpoints
✓ Definir schemas y validaciones
✓ Implementar business logic
✓ Escribir migrations
```

**Ejecución**:
```
✓ Ejecutar servidor localmente
✓ Correr tests de integración
✓ Ejecutar migrations
✓ Seed databases
```

### Design Systems

**Lectura**:
```
✓ Analizar design tokens
✓ Revisar componentes existentes
✓ Ver documentación Storybook
✓ Entender guidelines
```

**Escritura**:
```
✓ Generar tokens en múltiples formatos
✓ Crear documentación de componentes
✓ Actualizar Storybook stories
✓ Sincronizar Figma → Código
```

## Casos de Uso Reales

### 1. Migración de Proyecto

**Tarea**: "Migra el proyecto de JavaScript a TypeScript"

**El agente**:
1. Analiza estructura completa
2. Instala @types necesarios
3. Renombra .js → .ts
4. Añade tipos progresivamente
5. Ejecuta tsc para verificar
6. Corrige errores de tipos
7. Actualiza configuración
8. Commits por módulo

**Tu rol**: Supervisar y validar decisiones de tipos complejos

### 2. Bug Fixing Session

**Tarea**: "Hay 15 bugs reportados en Issues, fija los que puedas"

**El agente**:
1. Lee todos los Issues
2. Prioriza por severidad
3. Para cada bug:
   - Reproduce el error
   - Identifica causa
   - Implementa fix
   - Añade test para prevenir regresión
   - Comenta en Issue
   - Cierra Issue

**Tu rol**: Validar fixes de bugs críticos

### 3. Feature Sprint

**Tarea**: "Implementa los 5 features del sprint"

**El agente**:
1. Lee especificaciones
2. Divide en subtareas
3. Implementa cada feature:
   - Código base
   - Tests
   - Documentación
   - Validación
4. Integra todo
5. PR por feature

**Tu rol**: Code review y decisiones de UX

### 4. Refactoring Legacy

**Tarea**: "Este archivo tiene 1000 líneas, refactorízalo"

**El agente**:
1. Analiza código existente
2. Identifica responsabilidades
3. Extrae módulos lógicos
4. Separa en archivos coherentes
5. Mantiene tests pasando
6. Actualiza imports
7. Documenta cambios

**Tu rol**: Validar que lógica se mantiene

## Plataformas de Agentes Populares

### Para Desarrollo

**Claude Code** (CLI)
```
Fortalezas:
✓ Flujo completo de desarrollo
✓ Múltiples herramientas integradas
✓ Autonomía supervisada
✓ Context window gigante (200K tokens)

Uso:
$ claude-code "Añade autenticación al proyecto"
```

**Cursor** (IDE)
```
Fortalezas:
✓ Editor completo con IA
✓ Edición multi-archivo
✓ Terminal integrado
✓ Shortcuts intuitivos

Uso: Cmd+K para prompt en cualquier archivo
```

**GitHub Copilot Workspace**
```
Fortalezas:
✓ Integrado con GitHub
✓ Entiende Issues/PRs
✓ Planificación de tareas

Uso: Desde GitHub Issues
```

### Para Operaciones

**n8n + AI Agents**
```
Fortalezas:
✓ Workflows automatizados
✓ Integraciones múltiples
✓ Visual workflow builder

Uso: Automatización de procesos
```

**Zapier AI**
```
Fortalezas:
✓ Conecta apps sin código
✓ Triggers y actions
✓ Fácil de configurar

Uso: Automatizaciones simples
```

## Limitaciones de Agentes

### NO Son Perfectos ❌

```
❌ Pueden hacer suposiciones incorrectas
❌ A veces "alucinan" APIs que no existen
❌ Pueden generar código con bugs
❌ No entienden contexto de negocio sin explicación
❌ No pueden hacer juicios creativos/estratégicos
```

### SON Excelentes Para ✅

```
✅ Tareas repetitivas y mecánicas
✅ Seguir patterns establecidos
✅ Procesar múltiples archivos
✅ Ejecutar flujos bien definidos
✅ Mantener consistencia
✅ Trabajar 24/7 sin cansarse
```

## Trabajando con Agentes Efectivamente

### Define Claridad

❌ **Vago**:
```
"Mejora el proyecto"
```

✅ **Específico**:
```
"Refactoriza todos los componentes en src/components/
para usar TypeScript strict mode. Mantén tests pasando."
```

### Da Contexto

❌ **Sin contexto**:
```
"Añade validación"
```

✅ **Con contexto**:
```
"Añade validación a todos los forms usando Zod.
El proyecto ya usa React Hook Form.
Sigue el patrón del LoginForm existente."
```

### Establece Límites

❌ **Sin límites**:
```
"Haz lo que creas mejor"
```

✅ **Con límites**:
```
"Refactoriza pero:
- NO cambies la API pública
- NO instales nuevas dependencias sin preguntar
- Mantén backward compatibility"
```

### Verifica Resultados

```
Siempre:
✓ Revisa código generado
✓ Ejecuta tests
✓ Valida que cumple requisitos
✓ Haz code review como con cualquier developer
```

## Flujo de Trabajo Recomendado

### Fase 1: Planificación
```
Tú: Define QUÉ quieres lograr
Agente: Propone CÓMO hacerlo
Tú: Apruebas el plan
```

### Fase 2: Ejecución
```
Agente: Implementa paso a paso
Agente: Reporta progreso
Tú: Supervisas sin interrumpir (a menos que vaya mal)
```

### Fase 3: Validación
```
Agente: Completa tarea
Tú: Revisas resultado
Tú: Pides ajustes si es necesario
```

### Fase 4: Integración
```
Tú: Validación final
Tú: Merge/Deploy
```

## Comenzando con Agentes

### Semana 1: Tareas Simples
```
- "Crea test para esta función"
- "Añade JSDoc a este archivo"
- "Formatea todo el proyecto"
- "Actualiza README con instrucciones de setup"
```

### Semana 2: Tareas Moderadas
```
- "Implementa este componente según spec"
- "Refactoriza este archivo para reducir complejidad"
- "Añade error handling a todos los endpoints"
```

### Semana 3: Flujos Completos
```
- "Implementa feature completo con tests"
- "Migra componentes a nueva versión de librería"
- "Optimiza performance de estas rutas"
```

### Mes 2: Proyectos Complejos
```
- "Restructura arquitectura del proyecto"
- "Implementa internacionalización completa"
- "Migra de REST a GraphQL"
```

## Consejos Pro

### 1. Usa Branches
```
Siempre trabaja en branch separado:
$ git checkout -b feat/agent-task

Permite rollback fácil si algo sale mal
```

### 2. Commits Pequeños
```
Pide commits incrementales:
"Commitea después de cada paso"

Fácil de revisar y revertir si necesario
```

### 3. Tests Primero
```
Asegura que tests existen y pasan:
"Antes de cambiar código, ejecuta tests actuales"

Previene romper funcionalidad existente
```

### 4. Documenta Cambios
```
Pide documentación automática:
"Actualiza CHANGELOG.md con estos cambios"
```

## Conclusión Clave

Los agentes son la **evolución de IA de asistente a ejecutor**:

- No solo **sugieren** código, lo **escriben**
- No solo **explican** bugs, los **corrigen**
- No solo **planean** features, los **implementan**

**Piénsalo así**: Un agente es como tener un junior developer muy capaz que:
- Trabaja increíblemente rápido
- Nunca se cansa
- Recuerda TODO el contexto
- Pero necesita supervisión y dirección clara

## Relación con Otros Conceptos

- **[Herramienta](./07-herramienta.md)**: Los agentes usan herramientas para ejecutar tareas
- **[LLM](./01-llm.md)**: El LLM es el "cerebro" que decide qué hacer
- **[Prompt](./05-prompt.md)**: Tus instrucciones guían al agente
- **[Contexto](./04-contexto.md)**: Más contexto = agente más efectivo

---

**Siguiente**: Aprende sobre [Alucinación](./09-alucinacion.md) y cómo detectar cuando la IA inventa información.

[← Volver a Conceptos](../README.md#conceptos)
