# Prompt

## ¿Qué es un Prompt?

**Definición simple:** Lo que tú le escribes a la IA para pedirle algo. Es la única manera de comunicarte con la IA sobre lo que quieres.

**Analogía:** Un prompt es como **dar instrucciones a un desarrollador junior brillante**. La calidad de tus instrucciones determina directamente la calidad del trabajo que recibes.

## Prompt Malo vs. Prompt Bueno

### Ejemplo para Desarrollo

❌ **Prompt malo:**
```
Hazme un componente
```

**Problemas**: Vago, sin contexto, sin especificaciones técnicas

✅ **Prompt bueno:**
```
**Contexto**: Estoy construyendo una app React con TypeScript

**Tarea**: Crea un componente Button reutilizable

**Requisitos**:
- Props: label, onClick, variant ("primary" | "secondary"), disabled
- Debe soportar estados: hover, active, disabled
- Usar styled-components
- Incluir tipos TypeScript
- Accesible (ARIA)

**Estilo**: Seguir convenciones de naming del proyecto
```

### Ejemplo para Diseño

❌ **Prompt malo:**
```
Dame colores para la app
```

✅ **Prompt bueno:**
```
**Contexto**: App de fintech para gestión de gastos personales

**Tarea**: Crear paleta de colores base para design system

**Requisitos**:
- Primario: Transmitir confianza y profesionalidad
- Secundario: Para acciones positivas (ahorros, ganancias)
- Error/Warning/Success: Estados del sistema
- Cumplir WCAG AA para accesibilidad
- Modo claro y oscuro

**Formato**: Variables CSS y tokens en JSON
```

## El Marco CLARO

Para recordar qué incluir en tus prompts:

**C - Contexto**: ¿Cuál es la situación técnica?
**L - Longitud**: ¿Qué tan extenso debe ser?
**A - Audiencia**: ¿Quién usará esto?
**R - Rol**: ¿Qué papel debe desempeñar la IA?
**O - Objetivo**: ¿Qué resultado específico quieres?

## Jerarquía del Prompt: De Básico a Avanzado

### Nivel 1: Solicitud Básica
```
"Crea una función que valide emails"
```

### Nivel 2: Solicitud Específica
```
"Crea una función en TypeScript que valide emails usando regex,
retorne un boolean y maneje casos edge"
```

### Nivel 3: Contexto Detallado
```
Rol: Eres un desarrollador senior de TypeScript
Tarea: Crear función de validación de email
Contexto: Para formulario de registro en app React
Requisitos:
- Regex RFC 5322 compliant
- Retornar objeto con {isValid: boolean, error?: string}
- Manejar casos: emails vacíos, formato inválido, dominios
Estilo: Functional programming, sin side effects
```

### Nivel 4: Avanzado con Ejemplos
```
Rol: Desarrollador senior de TypeScript
Tarea: Crear función de validación de email
Contexto: Formulario de registro React con validación en tiempo real

Requisitos:
- Tipo: (email: string) => ValidationResult
- Interface ValidationResult { isValid: boolean; error?: string }
- Regex RFC 5322
- Casos edge: vacío, espacios, múltiples @, dominios inválidos

Ejemplo de output esperado:
validateEmail("user@example.com")
// { isValid: true }

validateEmail("invalid.email")
// { isValid: false, error: "Formato de email inválido" }

Estilo: JSDoc completo, nombres descriptivos, pure function
```

## Plantillas para Tareas Comunes

### Para Desarrollo: Crear Componente

```
**Contexto**: [Framework/librería que usas]
**Componente**: [Nombre y propósito]
**Props necesarios**: [Lista con tipos]
**Estados**: [Estados que debe manejar]
**Estilo**: [CSS-in-JS, Tailwind, styled-components, etc.]
**Requisitos especiales**:
- [Accesibilidad, responsive, animaciones, etc.]
**Tests**: [Sí/No, qué cubrir]
```

### Para Desarrollo: Debugging

```
**Problema**: [Descripción del bug]
**Código**: [Pega el código con el error]
**Error**: [Mensaje de error exacto]
**Esperado**: [Qué debería pasar]
**Contexto técnico**:
- Stack: [Node version, framework, librerías]
- Entorno: [Desarrollo, producción, navegador]
**Ya intenté**: [Qué soluciones probaste]
```

### Para Diseño: Sistema de Componentes

```
**Componente**: [Nombre del componente]
**Contexto**: [Tipo de app/producto]
**Variantes necesarias**: [Primary, secondary, sizes, etc.]
**Estados**: [Default, hover, active, disabled, loading]
**Accesibilidad**: [Requisitos WCAG]
**Output**: [Figma structure, tokens, documentation]
```

### Para Diseño: Tokens y Variables

```
**Sistema**: [Design tokens para qué]
**Categorías**: [Color, typography, spacing, shadows, etc.]
**Requisitos**:
- Naming convention: [BEM, semantic, etc.]
- Formato output: [CSS vars, JSON, JS/TS]
- Modos: [Light/dark theme]
**Referencias**: [Links o ejemplos de tu brand]
```

## Técnicas Avanzadas

### Cadena de Pensamiento
Para problemas complejos, pide que muestre el razonamiento:
```
"Antes de dar la solución, explica paso a paso tu proceso de pensamiento
sobre cómo resolver este problema de arquitectura."
```

### Juego de Roles
Haz que adopte perspectivas específicas:
```
"Eres un code reviewer senior. Revisa este código como si fuera
un PR crítico para producción. Identifica code smells,
problemas de performance y vulnerabilidades de seguridad."
```

### Establecer Restricciones
Define límites claros:
```
"El componente debe tener máximo 100 líneas de código,
usar solo hooks estándar de React (sin custom hooks externos),
y tener 0 dependencias adicionales."
```

### Prompting Multi-Paso
Para tareas complejas:
```
"Primero, analiza la estructura actual del proyecto.
Luego, identifica los componentes que necesitan refactoring.
Después, propón una nueva arquitectura.
Finalmente, dame el plan de migración paso a paso."
```

## Errores Comunes

### Error: Demasiado Vago
```
❌ "Ayúdame con este código"
✅ "Refactoriza esta función para reducir complejidad ciclomática.
   Extrae lógica repetida a funciones helper y añade JSDoc."
```

### Error: Demasiado Complejo
```
❌ "Crea componente, añade tests, documenta, optimiza, haz responsive,
    añade animaciones, traduce a 3 idiomas"
```
**Solución**: Divide en prompts separados por tarea

### Error: Sin Stack/Contexto Técnico
```
❌ "Crea una API REST"
✅ "Crea una API REST con Express.js, TypeScript, y MongoDB.
   Endpoints: CRUD para usuarios. Auth con JWT. Validación con Zod."
```

## Estrategia Iterativa

### Ronda 1: Base
```
"Crea componente Card básico con título y descripción"
```

### Ronda 2: Refinamiento
```
"Añade prop opcional para imagen, footer con actions,
y variante con borde destacado"
```

### Ronda 3: Pulido
```
"Optimiza para performance con React.memo,
añade tests y documentación Storybook"
```

## Tips para Resultados Consistentes

### 1. Usa Formato Consistente
Mantén estructura similar en tus prompts:
```
**Contexto**: [Siempre incluye stack técnico]
**Tarea**: [Verbo de acción + output específico]
**Requisitos**: [Lista numerada o bullets]
**Estilo**: [Convenciones de código]
```

### 2. Referencias Concretas
```
❌ "Hazlo como se hace normalmente"
✅ "Sigue el patrón del componente Button existente en src/components/"
```

### 3. Especifica Versiones
```
"Usa React 18 con hooks, TypeScript 5.0, y sintaxis ESNext"
```

### 4. Ejemplo de Output
Muestra cómo quieres el resultado:
```
"Formato del output:
```typescript
interface Props {
  // Props aquí
}

export const Component: React.FC<Props> = ({ prop }) => {
  // Implementación
}
```
```

## Biblioteca de Prompts

**Mantén tus mejores prompts guardados:**
- Creación de componentes
- Patterns de testing
- Configuración de herramientas
- Debugging recurrente
- Estructuras de documentación

**Herramienta sugerida**: Archivo `prompts.md` en tu repo o snippets en tu IDE

## Conclusión Clave

**Buenos prompts = Buenos resultados**

Piensa en el prompt como **un ticket de Jira detallado**:
- Contexto del feature/bug
- Criterios de aceptación claros
- Stack técnico relevante
- Ejemplos cuando sea útil

Los 2 minutos que gastes creando un buen prompt te ahorrarán 20 minutos de refactorización.

## Relación con Otros Conceptos

- **[Contexto](./04-contexto.md)**: El contexto es componente clave del prompt
- **[Temperatura](./06-temperatura.md)**: Afecta qué tan creativas son las respuestas
- **[Token](./03-token.md)**: Prompts más largos consumen más tokens
- **[LLM](./01-llm.md)**: Los LLMs son los que procesan tus prompts

---

**Siguiente**: Aprende sobre [Temperatura](./06-temperatura.md) y cómo controlar la creatividad de la IA.

[← Volver a Conceptos](../README.md#conceptos)
