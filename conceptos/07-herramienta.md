# Herramienta

## ¿Qué es una Herramienta?

**Definición simple:** Capacidades específicas que permiten a un agente de IA interactuar con el mundo más allá de solo generar texto.

**Analogía:** Si un agente es como un **developer junior capaz**, las herramientas son como el **IDE, terminal, Git, y APIs** que usa para hacer las cosas.

Piensa en la diferencia entre:
- **IA sin herramientas**: Solo puede pensar y hablar (dar consejos)
- **IA con herramientas**: Puede leer archivos, ejecutar código, hacer commits, buscar en docs

## Herramientas vs. Solo Chat

### Sin Herramientas (Chat básico)
```
Tú: "¿Qué bug tiene mi componente Button.tsx?"
IA: "No puedo ver tu código. ¿Puedes pegarlo aquí?"
Tú: [Copias y pegas el archivo]
IA: "Veo el problema, es en línea 23..."
```

### Con Herramientas (Agente)
```
Tú: "¿Qué bug tiene mi componente Button.tsx?"
IA: [Lee el archivo directamente]
    [Analiza imports y dependencias]
    [Revisa tests relacionados]
    "Encontré 3 problemas:
     1. Línea 23: Falta manejador de undefined
     2. Línea 45: Import no usado
     3. No hay test para caso disabled + loading"
```

## Categorías de Herramientas

### 1. Herramientas de Archivos 📁

**Lectura**:
- Leer archivos del proyecto
- Buscar en codebase
- Explorar estructura de directorios
- Leer documentación

**Escritura**:
- Crear nuevos archivos
- Editar archivos existentes
- Refactorizar código
- Generar configuraciones

**Ejemplo en acción**:
```
Tú: "Crea un componente Card.tsx con props title y description"
IA: [Lee estructura de otros componentes]
    [Crea archivo en ubicación correcta]
    [Usa mismo estilo que componentes existentes]
    "✅ Creado en src/components/Card.tsx"
```

### 2. Herramientas de Ejecución ⚡

**Terminal/Shell**:
- Ejecutar comandos
- Instalar dependencias
- Correr tests
- Build y deploy

**Debugging**:
- Ejecutar código
- Ver output
- Analizar errores
- Profiling

**Ejemplo en acción**:
```
Tú: "Instala y configura Vitest"
IA: [Ejecuta: npm install -D vitest]
    [Crea vitest.config.ts]
    [Actualiza package.json scripts]
    [Crea ejemplo de test]
    [Ejecuta: npm test para verificar]
    "✅ Vitest configurado y tests pasando"
```

### 3. Herramientas de Control de Versiones 🔄

**Git operations**:
- Ver status y diffs
- Crear branches
- Hacer commits
- Push/pull
- Resolver conflictos

**Ejemplo en acción**:
```
Tú: "Commitea los cambios del componente Card"
IA: [Revisa git status]
    [Ve git diff para entender cambios]
    [Genera mensaje de commit descriptivo]
    [Hace git add y commit]
    "✅ Commit: feat: Add Card component with title and description props"
```

### 4. Herramientas de Búsqueda 🔍

**Web search**:
- Buscar documentación actualizada
- Encontrar soluciones a errores
- Verificar versiones de librerías
- Buscar ejemplos de código

**Codebase search**:
- Buscar definiciones
- Encontrar usos de funciones
- Buscar patterns similares
- Analizar dependencias

**Ejemplo en acción**:
```
Tú: "¿Cómo uso React Query v5 con TypeScript?"
IA: [Busca en docs oficiales de React Query]
    [Encuentra ejemplos actualizados]
    [Verifica sintaxis de v5 específicamente]
    "Aquí está la configuración actualizada para v5..."
```

### 5. Herramientas de Desarrollo 🛠️

**Linting/Formatting**:
- Ejecutar ESLint
- Correr Prettier
- Fix automático de issues
- Verificar tipos (TypeScript)

**Testing**:
- Ejecutar test suites
- Ver coverage
- Debug tests fallidos
- Generar nuevos tests

**Build tools**:
- Ejecutar builds
- Analizar bundle size
- Optimizar assets
- Deploy previews

**Ejemplo en acción**:
```
Tú: "Asegura que todo el código pase linting"
IA: [Ejecuta: npm run lint]
    [Ve errores]
    [Ejecuta: npm run lint --fix]
    [Corrige manualmente lo que --fix no puede]
    [Re-ejecuta lint]
    "✅ Todo el código pasa linting (37 issues corregidos)"
```

### 6. Herramientas de Integración 🔌

**APIs externas**:
- Consultar documentación de APIs
- Hacer requests de prueba
- Validar responses
- Configurar auth

**Servicios de desarrollo**:
- GitHub/GitLab
- CI/CD (Actions, CircleCI)
- Package registries (npm, Docker)
- Cloud platforms (Vercel, Netlify)

## Ejemplos Prácticos para Desarrollo

### Ejemplo 1: Debugging Completo

**Herramientas usadas**: Read files, Execute code, Search, Git

**Tarea**: "Mi app crashea al cargar, debuggéalo"

**Proceso del agente**:
1. Lee logs de error
2. Busca archivo donde ocurre
3. Analiza código relacionado
4. Busca en Stack Overflow error similar
5. Ejecuta tests para reproducir
6. Identifica causa raíz
7. Propone fix y lo implementa
8. Ejecuta tests para verificar
9. Hace commit del fix

### Ejemplo 2: Feature Completo

**Herramientas usadas**: Read, Write, Execute, Git

**Tarea**: "Añade autenticación JWT al backend"

**Proceso del agente**:
1. Lee estructura actual del proyecto
2. Busca en docs de librería JWT
3. Instala dependencias necesarias
4. Crea middleware de auth
5. Actualiza routes para usar middleware
6. Crea tests de integración
7. Ejecuta tests para verificar
8. Actualiza documentación API
9. Hace commit con descripción completa

### Ejemplo 3: Refactoring Masivo

**Herramientas usadas**: Search, Read, Write, Execute

**Tarea**: "Migra todos los componentes de JavaScript a TypeScript"

**Proceso del agente**:
1. Busca todos archivos .jsx
2. Lee cada componente
3. Infiere tipos de props
4. Convierte a .tsx con tipos
5. Actualiza imports en otros archivos
6. Ejecuta type checking
7. Corrige errores de tipos
8. Ejecuta tests para verificar
9. Commits por lotes lógicos

## Ejemplo para Diseño

### Herramientas para Design Systems

**Tarea**: "Genera todos los tokens de mi design system en múltiples formatos"

**Herramientas usadas**: Read Figma, Write files, Execute transforms

**Proceso del agente**:
1. Lee tokens definidos en Figma/archivo
2. Valida estructura y consistencia
3. Genera CSS custom properties
4. Genera JSON para consumo JS
5. Genera archivos SCSS/Sass
6. Genera TypeScript types
7. Crea documentación markdown
8. Ejecuta validation tests
9. Hace commit estructurado

## Seguridad y Permisos

### Control de Acceso ⚠️

**Las herramientas necesitan permisos apropiados:**

✅ **Seguros**:
- Lectura de archivos del proyecto
- Ejecución de comandos de build/test
- Búsqueda en documentación
- Git status y diff

⚠️ **Requieren precaución**:
- Escritura de archivos
- Git commits y push
- Instalación de dependencias
- Ejecución de scripts

🚫 **Peligrosos sin supervisión**:
- Modificar archivos de configuración críticos
- Eliminar archivos/directorios
- Push a main/production
- Ejecutar comandos con sudo
- Acceso a secrets/credentials

### Mejores Prácticas

```
✅ Revisar cambios antes de commit
✅ Usar branches para cambios experimentales
✅ Validar dependencias antes de instalar
✅ Revisar comandos antes de ejecución crítica
✅ Limitar acceso a archivos sensibles

❌ Dar acceso root/admin sin límites
❌ Permitir push directo a main
❌ Ejecutar scripts sin revisar
❌ Compartir credentials en prompts
```

## Herramientas Populares en Práctica

### GitHub Copilot
**Herramientas**:
- Autocompletar código en tiempo real
- Sugerir funciones completas
- Generar tests

**Limitación**: Solo sugiere, no ejecuta

### Claude Code
**Herramientas**:
- Leer/escribir archivos
- Ejecutar terminal
- Hacer git operations
- Buscar en web y codebase

**Fortaleza**: Flujo completo autónomo

### Cursor
**Herramientas**:
- Autocompletar con contexto del proyecto
- Editar múltiples archivos
- Ejecutar comandos
- Terminal integrado

**Fortaleza**: IDE completo + IA

## Eligiendo Herramientas

### Para Proyectos Pequeños
```
Mínimo necesario:
- Read/Write archivos
- Ejecutar tests básicos
- Buscar en docs
```

### Para Proyecos Medianos
```
Añadir:
- Git operations completas
- Linting/Formatting automation
- Test execution y coverage
- Build y validation
```

### Para Proyectos Enterprise
```
Añadir:
- CI/CD integration
- Multi-repo operations
- Deployment automation
- Monitoring y logs
```

## Limitaciones de Herramientas

### Lo que NO pueden hacer ❌
- Tomar decisiones de negocio
- Entender contexto humano complejo
- Creatividad genuina (solo patterns)
- Reemplazar code reviews humanos
- Garantizar código perfecto

### En lo que sobresalen ✅
- Ejecución consistente de tareas
- Velocidad en operaciones repetitivas
- Trabajo cross-file sin cansarse
- Disponibilidad 24/7
- Recordar TODO el contexto del proyecto

## Comenzando con Herramientas

### Paso 1: Herramientas de Solo Lectura
```
Seguras para empezar:
- Leer archivos
- Ver git status/diff
- Buscar en codebase
- Ejecutar tests (solo lectura)
```

### Paso 2: Herramientas de Escritura Supervisada
```
Con revisión:
- Crear archivos nuevos
- Editar código existente
- Instalar dependencias
- Commits en branches
```

### Paso 3: Herramientas Avanzadas
```
Con experiencia:
- Refactoring masivo
- Deploys automatizados
- Multi-repo operations
- Integration workflows
```

## Conclusión Clave

Las herramientas transforman la IA de **consultor pasivo** a **compañero de desarrollo activo**:

- Puede no solo sugerir, sino **implementar**
- Trabaja en **múltiples archivos simultáneamente**
- Ejecuta **flujos completos** (code → test → commit)
- Mantiene **consistencia** en todo el proyecto

**Piensa en herramientas como el upgrade de IA de "copiloto que sugiere" a "pair programmer que ejecuta".**

## Relación con Otros Conceptos

- **[Agente](./08-agente.md)**: Los agentes usan herramientas para ejecutar tareas
- **[LLM](./01-llm.md)**: El LLM decide QUÉ herramientas usar y CUÁNDO
- **[Prompt](./05-prompt.md)**: El prompt puede indicar qué herramientas prefieres

---

**Siguiente**: Descubre [Agentes](./08-agente.md) y cómo usan herramientas para completar tareas complejas.

[← Volver a Conceptos](../README.md#conceptos)
