# Nivel 2: Chat Avanzado

**Lo que aprenderás:** Técnicas avanzadas de prompting y cómo mantener conversaciones largas y efectivas con IA.

**Prerrequisito:** Haber dominado [Nivel 1: Chat Básico](./nivel-1-chat-basico.md)

---

## 🎯 Qué es Este Nivel

En el Nivel 1 aprendiste a hacer preguntas puntuales y copiar/pegar respuestas.

**El Nivel 2 es diferente:**
- Conversaciones largas donde cada mensaje construye sobre el anterior
- Mantener contexto a lo largo de múltiples interacciones
- Técnicas avanzadas que mejoran dramáticamente los resultados
- Refactorizar proyectos completos, no solo funciones aisladas

**La diferencia clave:** Ya no usas la IA para respuestas rápidas, sino como un colaborador en sesiones de trabajo largas.

---

## 🧠 Concepto Clave: Contexto Acumulado

### Nivel 1 (pregunta aislada):
```
Tú: "Crea una función de login"
IA: [genera función]
--- FIN ---
```

### Nivel 2 (conversación con contexto):
```
Tú: "Estoy construyendo una app de tareas. Necesito un sistema de autenticación."

IA: [pregunta sobre requisitos: JWT, OAuth, sesiones?]

Tú: "JWT. Backend en Python con FastAPI."

IA: [genera estructura completa]

Tú: "Ahora agrega refresh tokens"

IA: [modifica lo anterior agregando refresh tokens]

Tú: "¿Cómo manejo la expiración en el frontend?"

IA: [explica basándose en TODO el contexto anterior]
```

**La IA "recuerda" toda la conversación y adapta sus respuestas.**

---

## 💡 Técnicas Avanzadas de Prompting

### 1. Chain-of-Thought (Cadena de Pensamiento)

**Qué es:** Pedir a la IA que explique su razonamiento paso a paso antes de dar la solución.

**Cuándo usar:** Problemas complejos, debugging difícil, decisiones de arquitectura.

**Ejemplo sin CoT:**
```
¿Por qué este código es lento?
[código]
```

**Ejemplo con CoT:**
```
Analiza por qué este código es lento. Piensa paso a paso:

1. ¿Qué operaciones se ejecutan en cada iteración?
2. ¿Cuál es la complejidad temporal?
3. ¿Dónde están los bottlenecks?
4. ¿Qué optimizaciones son posibles?

Solo después de analizar, propón la solución.

[código]
```

**Resultado:** La IA analiza más profundamente y da mejores respuestas.

---

### 2. Few-Shot Prompting (Aprendizaje por Ejemplos)

**Qué es:** Dar ejemplos de lo que quieres antes de pedir la solución.

**Cuándo usar:** Cuando necesitas un formato específico, estilo de código consistente, o patrón particular.

**Ejemplo:**
```
Necesito funciones de validación siguiendo este patrón:

Ejemplo 1:
function validateEmail(email: string): ValidationResult {
  const regex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
  return {
    isValid: regex.test(email),
    error: regex.test(email) ? null : 'Email inválido'
  };
}

Ejemplo 2:
function validatePhone(phone: string): ValidationResult {
  const regex = /^\d{10}$/;
  return {
    isValid: regex.test(phone),
    error: regex.test(phone) ? null : 'Teléfono debe tener 10 dígitos'
  };
}

Ahora crea validatePassword con los mismos patrones.
Requisitos: 8+ caracteres, 1 mayúscula, 1 número, 1 símbolo.
```

**Resultado:** La IA sigue exactamente tu estructura y estilo.

---

### 3. Role Prompting (Asignar Roles)

**Qué es:** Pedir a la IA que actúe como un experto específico.

**Cuándo usar:** Code reviews, arquitectura, decisiones técnicas.

**Ejemplos:**

**Para Code Review:**
```
Actúa como un senior developer experto en [tu stack].
Revisa este código con ojo crítico:

[código]

Evalúa:
- Bugs potenciales
- Problemas de performance
- Violaciones de principios SOLID
- Security issues
- Mejores prácticas del lenguaje

Sé honesto y directo, como en un code review real.
```

**Para Arquitectura:**
```
Actúa como un arquitecto de software con 10 años de experiencia.

Necesito decidir entre:
1. Monolito modular
2. Microservicios
3. Serverless

Contexto:
- Equipo: 4 desarrolladores
- Usuarios: ~50k MAU
- Complejidad: Media
- Budget: Limitado

Analiza trade-offs y recomienda basándote en el contexto.
```

**Para Diseño (Figma):**
```
Actúa como un design system architect.

Revisa mi estructura de componentes en Figma:
[describe estructura]

Evalúa:
- Naming conventions
- Jerarquía de componentes
- Escalabilidad
- Mantenibilidad

Dame feedback como si fuera un design review.
```

---

### 4. Prompting Iterativo Avanzado

**Qué es:** Refinar en múltiples pasadas, cada vez más específico.

**Ejemplo de sesión real:**

**Iteración 1 (exploración):**
```
Necesito implementar un sistema de permisos para una app.
¿Qué enfoques existen?
```

**Iteración 2 (decisión):**
```
RBAC (Role-Based Access Control) suena bien.
Explica cómo implementarlo en [tu stack].
```

**Iteración 3 (implementación):**
```
Genera la estructura de código para RBAC.
Roles: admin, editor, viewer
Recursos: posts, comments, users
```

**Iteración 4 (refinamiento):**
```
Agrega permisos granulares:
- editor puede editar solo sus propios posts
- admin puede editar todos
```

**Iteración 5 (edge cases):**
```
¿Cómo manejo permisos heredados?
Ejemplo: un usuario es editor de proyecto A pero viewer de proyecto B.
```

**Resultado:** Sistema completo, pensado a fondo, con edge cases cubiertos.

---

### 5. Contrast Prompting (Comparación Explícita)

**Qué es:** Pedir comparaciones directas entre opciones.

**Cuándo usar:** Decisiones técnicas, evaluación de trade-offs.

**Ejemplo:**
```
Compara estas 3 formas de manejar estado en React:

1. useState + Context
2. Redux Toolkit
3. Zustand

Para cada una dame:
- Ventajas
- Desventajas
- Cuándo usarla
- Cuándo NO usarla
- Ejemplo de código mínimo

Contexto: App mediana, 5 desarrolladores, estado moderadamente complejo.
```

**Resultado:** Análisis objetivo que te ayuda a decidir.

---

## 🔄 Manteniendo Contexto en Conversaciones Largas

### Técnica: Context Anchoring (Anclaje de Contexto)

Cada ciertos mensajes, recuerda a la IA el contexto global:

```
Recordatorio del contexto:
- Proyecto: App de ecommerce en React Native
- Backend: Node.js + PostgreSQL
- Estamos implementando: Sistema de pagos
- Ya tenemos: Auth, products catalog

Ahora, siguiendo este contexto: [tu pregunta]
```

**Por qué funciona:** Los LLMs tienen memoria limitada. Refrescar el contexto mejora las respuestas.

---

### Técnica: Checkpoint Summaries

En conversaciones muy largas, pide resúmenes periódicos:

```
Hemos discutido mucho. Resume:
1. Decisiones tomadas
2. Código generado (archivos/funciones)
3. Próximos pasos pendientes
```

**Beneficio:** Mantiene todo organizado y detecta inconsistencias.

---

## 🏗️ Casos de Uso Avanzados

### 1. Refactoring de Proyecto Completo

**Setup inicial:**
```
Voy a compartir la estructura de un proyecto que necesita refactoring.

Proyecto: [nombre]
Stack: [tecnologías]
Problema: [qué está mal]
Objetivo: [qué quieres lograr]

Iremos paso a paso. Primero, analiza la estructura actual.

[pega estructura de archivos]
```

**Conversación iterativa:**
```
Tú: [compartes archivo 1]
IA: [analiza, sugiere cambios]

Tú: [compartes archivo 2]
IA: [analiza en contexto del archivo 1]

Tú: "¿Cómo afecta esto al archivo 1?"
IA: [explica conexiones]

Tú: "Refactoriza ambos manteniendo consistencia"
IA: [genera código consistente entre archivos]
```

---

### 2. Debugging Complejo Multi-Capa

**Estructura de la conversación:**

```
Paso 1: Presentar el problema
"Tengo un bug que solo ocurre en producción, no en desarrollo.
Síntomas: [describe]
Stack trace: [pega]
No es obvio dónde está el problema."

Paso 2: Análisis colaborativo
IA: "¿Qué diferencias hay entre dev y prod?"
Tú: [explicas]
IA: "Revisa [X, Y, Z]"

Paso 3: Hipótesis
Tú: "Revisé X y Y, todo bien. Pero Z tiene [esto]"
IA: "Eso podría ser. Prueba [experimento]"

Paso 4: Iteración
Tú: "Probé, ahora el error es [nuevo error]"
IA: "Progreso. Ahora sabemos que [análisis]"

Paso 5: Solución
Tú: "Encontré que [causa raíz]"
IA: "Exacto. Para prevenir esto en el futuro: [mejoras]"
```

**Clave:** La conversación larga permite explorar hipótesis paso a paso.

---

### 3. Diseño de Arquitectura Completa

**Sesión ejemplo:**

```
Inicio:
"Voy a diseñar la arquitectura de una app de [descripción].
Actúa como arquitecto de software. Iremos definiendo componentes paso a paso."

Definición de requisitos:
IA: "¿Cuáles son los requisitos funcionales principales?"
Tú: [listas requisitos]
IA: "¿Requisitos no funcionales? (performance, scale, etc)"
Tú: [defines]

Propuesta inicial:
IA: [propone arquitectura high-level]
Tú: "Me gusta, pero tengo dudas sobre [componente X]"

Refinamiento:
IA: [explica X, propone alternativas]
Tú: "Vamos con opción 2. ¿Cómo se integra con [componente Y]?"
IA: [detalla integración]

Iteración por capa:
Tú: "Detalla la capa de datos"
IA: [genera esquema de BD, repositories, etc]
Tú: "Ahora la capa de negocio"
IA: [genera services, casos de uso]

Resultado final:
Tú: "Resume toda la arquitectura con diagrama y justificaciones"
IA: [genera documentación completa]
```

---

### 4. Code Review de Pull Request Completo

```
Setup:
"Actúa como senior developer. Voy a compartir un PR para review.

PR: [título y descripción]
Archivos modificados: [lista]
Tests: [incluidos/no incluidos]

Revisaremos archivo por archivo."

Por cada archivo:
Tú: [pega código del archivo]
IA: [revisa y comenta]

Consolidación:
Tú: "Dame feedback general del PR completo"
IA: [resume issues, sugiere mejoras globales]

Iteración:
Tú: "Apliqué tus sugerencias en archivo X. ¿Mejor ahora?"
IA: [re-evalúa en contexto]
```

---

## 🎨 Para Diseñadores: Casos Avanzados

### 1. Evolución de Design System

```
Contexto inicial:
"Tengo un design system básico en Figma.
Necesito escalarlo para soportar múltiples plataformas y temas.

Actual: [describe estructura]
Objetivo: [describe meta]

Trabajemos paso a paso."

Iteración:
IA: "Empecemos por tokens. ¿Cómo están estructurados actualmente?"
Tú: [explicas]
IA: [sugiere mejoras]
Tú: "Apliqué cambios. Ahora, ¿cómo afecta esto a los componentes?"
IA: [explica cascada de cambios]

Resultado: Sistema completo, escalable, bien documentado.
```

### 2. Audit de Accesibilidad

```
"Actúa como experto en accesibilidad (WCAG 2.1 AA).

Voy a compartir diseños de [proyecto].
Revisa conformidad con estándares.

Por cada pantalla:
- Issues de contraste
- Jerarquía visual
- Touch targets
- Focus states
- Screen reader compatibility"

[Compartes pantalla por pantalla]
[IA revisa cada una en contexto del flujo completo]
```

---

## 🚨 Errores Comunes en Nivel 2

### ❌ Error 1: No Establecer Contexto al Inicio

**Mal:**
```
Cómo hago X?
```

**Bien:**
```
Contexto: Estoy trabajando en [proyecto] usando [stack].
Ya tengo implementado [A, B, C].
Ahora necesito [X].

¿Cómo lo implemento manteniendo consistencia con lo existente?
```

---

### ❌ Error 2: Cambiar de Tema Abruptamente

**Mal:**
```
[Conversación sobre autenticación]
Tú: "Perfecto, ya funciona el login"
Tú: "Ahora cómo hago un diseño responsive?"  ⚠️ Sin contexto
```

**Bien:**
```
[Conversación sobre autenticación]
Tú: "Perfecto, ya funciona el login"
Tú: "Cambio de tema: Necesito hacer responsive la UI del login.
Framework: React Native. ¿Mejores prácticas?"
```

---

### ❌ Error 3: Asumir que la IA Recuerda Todo Perfectamente

**Problema:** En conversaciones muy largas (50+ mensajes), la IA puede "olvidar" mensajes antiguos.

**Solución:** Refresca contexto clave periódicamente:
```
Para refrescar contexto:
- Proyecto: [nombre]
- Stack: [tecnologías]
- Trabajando en: [feature actual]
- Decisiones previas: [lista]

Continuando: [tu pregunta]
```

---

### ❌ Error 4: No Validar Consistencia

**Problema:** En conversaciones largas, la IA puede contradecirse.

**Solución:** Valida explícitamente:
```
"En el mensaje anterior sugeriste usar Redis para cache.
Ahora sugieres Memcached.
¿Cuál es mejor para nuestro caso específico y por qué?"
```

---

## 💪 Técnicas Pro

### 1. Rubber Duck Debugging Avanzado

Explica tu problema en detalle a la IA como si fuera un patito de goma:

```
"Déjame explicarte este problema paso a paso.
No respondas hasta que termine de explicar.

1. Tengo [situación]
2. Esperaba [resultado X]
3. Pero obtengo [resultado Y]
4. Ya probé [A, B, C]
5. Mi hipótesis es [H]
6. Pero no tiene sentido porque [razón]

Ahora sí, ¿qué opinas?"
```

**Por qué funciona:** El acto de explicar a fondo a menudo revela el problema. La IA suma una perspectiva adicional.

---

### 2. Socratic Method (Método Socrático)

En lugar de pedir respuestas, pide preguntas:

```
"Necesito implementar [feature].
Antes de darme soluciones, hazme las preguntas que necesitas
para entender completamente el problema y dar la mejor solución."
```

**Resultado:** La IA te guía a pensar en aspectos que quizás olvidaste.

---

### 3. Devil's Advocate (Abogado del Diablo)

```
"Propuse esta arquitectura: [describe]

Actúa como abogado del diablo.
Ataca mi propuesta. Encuentra todos los problemas posibles.
Sé brutalmente honesto."
```

**Beneficio:** Descubres debilidades antes de implementar.

---

### 4. Reverse Engineering de Conceptos

```
"No me digas cómo implementar [X].
Primero, explica:

1. ¿Qué problema resuelve X?
2. ¿Qué alternativas existen?
3. ¿Por qué X es mejor (o no) que las alternativas?
4. ¿Qué trade-offs tiene X?

Solo después de esto, muestra implementación."
```

**Resultado:** Entiendes el "por qué", no solo el "cómo".

---

## ✅ Resumen: Dominas Nivel 2 Cuando...

### Entiendes:

- ✅ Cómo mantener contexto en conversaciones largas
- ✅ Cuándo usar cada técnica avanzada (CoT, few-shot, role prompting)
- ✅ Cómo estructurar sesiones de trabajo largas con IA
- ✅ Limitaciones de memoria y cómo trabajar con ellas

### Puedes:

- ✅ Refactorizar proyectos completos conversando con IA
- ✅ Debuggear problemas complejos multi-capa
- ✅ Diseñar arquitecturas completas colaborativamente
- ✅ Hacer code reviews completos con contexto
- ✅ Iterar sobre diseños complejos (design systems, flows)
- ✅ Mantener consistencia en conversaciones largas

### Evitas:

- ✅ Perder contexto en conversaciones largas
- ✅ Contradicciones de la IA sin detectar
- ✅ Prompts genéricos cuando necesitas especificidad
- ✅ Aceptar primeras respuestas sin iterar

---

## 📊 Limitaciones de Este Nivel

### Lo que PUEDES hacer:

- ✅ Conversaciones largas y complejas
- ✅ Trabajo en múltiples archivos (compartidos manualmente)
- ✅ Refactoring completo de proyectos
- ✅ Diseño de arquitecturas
- ✅ Debugging avanzado

### Lo que NO puedes hacer (todavía):

- ❌ IA que autocomplete mientras escribes código
- ❌ IA que lea archivos directamente de tu proyecto
- ❌ Integración en tu editor sin copiar/pegar
- ❌ Ejecutar código automáticamente
- ❌ IA que navegue tu codebase autónomamente

**Para eso necesitas:** Nivel 3: IA en tu Editor *(próximamente)*

---

## 🆘 Problemas Comunes

**"La IA se contradice en conversaciones largas"**
→ Refresca contexto periódicamente. Señala contradicciones explícitamente.

**"Pierde el hilo de la conversación"**
→ Usa "checkpoint summaries": pide que resuma lo discutido hasta ahora.

**"Las respuestas son cada vez más genéricas"**
→ Estás siendo menos específico. Vuelve a dar contexto detallado.

**"No sé cuándo usar qué técnica"**
→
- Chain-of-thought: Problemas complejos
- Few-shot: Necesitas formato específico
- Role prompting: Code review, arquitectura
- Iteración: Siempre que algo no esté perfecto

---

## 🎯 Próximo Paso

**Cuando domines este nivel**, el siguiente paso será:

→ **Nivel 3: IA en tu Editor** *(próximamente)*

Aprenderás:
- Autocompletado inteligente mientras codeas
- GitHub Copilot, Cursor, Codeium
- Adiós al copy/paste constante
- Shortcuts y flujo de trabajo optimizado

---

[← Anterior: Nivel 1](./nivel-1-chat-basico.md) | [Volver a Inicio](../README.md) | [Conceptos](../README.md#conceptos)