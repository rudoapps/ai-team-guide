# Temperatura

## ¿Qué es la Temperatura?

**Definición simple:** El "dial de creatividad" o "control de aleatoriedad" para las respuestas de IA.

**Analogía:** Como ajustar la personalidad de la IA entre dos extremos:
- **Temperatura Baja (0.1-0.3)**: El compañero metódico y predecible - siempre da la respuesta "correcta"
- **Temperatura Alta (0.7-1.0)**: El compañero creativo - te sorprende con ideas nuevas

## La Escala de Temperatura

### 0.0 - Modo Determinista 🤖
- Completamente predecible
- Misma entrada = misma salida siempre
- Elige la respuesta más probable estadísticamente

**Para desarrollo:**
- Generación de código standard
- Corrección de bugs
- Refactoring según patrones conocidos

### 0.2 - Modo Preciso 📊
- Altamente consistente
- Variaciones mínimas
- Ideal para tareas que requieren exactitud

**Para desarrollo:**
- Tests unitarios
- Documentación técnica
- Configuración de herramientas
- Code reviews

### 0.5 - Modo Equilibrado ⚖️
- Balance entre consistencia y creatividad
- Variedad razonable en respuestas
- Configuración de propósito general

**Para desarrollo:**
- Implementación de features
- Arquitectura de proyectos
- Problem solving general

### 0.8 - Modo Creativo 🎨
- Alta variedad en respuestas
- Soluciones inesperadas pero relevantes
- Bueno para exploración e innovación

**Para desarrollo:**
- Brainstorming de arquitectura
- Naming de funciones/variables
- Soluciones no convencionales
- Exploración de APIs

### 1.0 - Modo Experimental 🎲
- Máxima aleatoriedad
- Puede ser impredecible
- Usar con precaución

**Raramente útil para desarrollo profesional**

## Cuándo Usar Cada Temperatura

### Temperatura Baja (0.1-0.3) ❄️

**Tareas de Desarrollo:**
```
✅ Corregir bug específico en función
✅ Generar configuración de TypeScript
✅ Escribir SQL queries optimizadas
✅ Crear tests para cobertura
✅ Formatear código según estándar
✅ Generar tipos TypeScript desde schema
```

**Tareas de Diseño:**
```
✅ Convertir design tokens a CSS variables
✅ Generar grid system matemático
✅ Calcular ratios tipográficos
✅ Documentar componentes existentes
```

**Lo que obtienes**: Respuestas precisas, consistentes, predecibles

### Temperatura Media (0.4-0.6) 🌡️

**Tareas de Desarrollo:**
```
✅ Implementar nueva feature
✅ Refactorizar código legacy
✅ Diseñar API REST
✅ Escribir documentación técnica
✅ Code review con sugerencias
```

**Tareas de Diseño:**
```
✅ Crear variantes de componentes
✅ Proponer mejoras de UX
✅ Estructurar design system
✅ Escribir guidelines
```

**Lo que obtienes**: Profesional, fiable, con ligeras variaciones creativas

### Temperatura Alta (0.7-1.0) 🔥

**Tareas de Desarrollo:**
```
✅ Brainstorming de arquitecturas
✅ Naming creativo (funciones, variables, proyectos)
✅ Explorar soluciones no convencionales
✅ Generar ideas de features
✅ Proponer optimizaciones innovadoras
```

**Tareas de Diseño:**
```
✅ Exploración de paletas de color
✅ Naming de componentes/variables
✅ Conceptos de interacción novedosos
✅ Microinteracciones creativas
✅ Explorar tendencias de UI
```

**Lo que obtienes**: Ideas variadas, creativas, sorprendentes

## Ejemplos Reales

### Caso 1: Generación de Código

**Tarea**: "Crea función que valide formato de email"

**Temperatura Baja (0.2)**:
```typescript
function validateEmail(email: string): boolean {
  const regex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
  return regex.test(email);
}
```
*Solución estándar, probada, predecible*

**Temperatura Alta (0.8)**:
```typescript
const validateEmail = (email: string): boolean => {
  // Validación más permisiva con casos edge
  const parts = email.trim().split('@');
  if (parts.length !== 2) return false;

  const [local, domain] = parts;
  const validLocal = /^[a-zA-Z0-9._+-]+$/.test(local);
  const validDomain = /^[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/.test(domain);

  return validLocal && validDomain && local.length <= 64;
};
```
*Solución más creativa, maneja edge cases*

### Caso 2: Naming de Componentes

**Contexto**: "Necesito nombres para componente que muestra tarjeta de producto"

**Temperatura Baja (0.2)**:
```
ProductCard
```
*El nombre más obvio y estándar*

**Temperatura Alta (0.8)**:
```
ProductShowcase
ProductTile
ItemCard
ProductPreview
MerchandiseCard
ProductSnapshot
```
*Variedad de opciones creativas*

### Caso 3: Debugging

**Tarea**: "¿Por qué este código no funciona?"

**Temperatura Baja = Mejor**
- Se enfoca en el error específico
- Da solución directa y confiable
- No divaga con posibilidades

**Temperatura Alta = Puede confundir**
- Sugiere múltiples posibles causas
- Propone soluciones variadas
- Puede ser menos directo

## Cómo Controlar Temperatura

### En APIs (OpenAI, Anthropic)
```javascript
const response = await openai.chat.completions.create({
  model: "gpt-4",
  messages: [...],
  temperature: 0.2  // Ajusta aquí
});
```

### En Interfaces Web (ChatGPT, Claude)
- Busca "Configuración" o "Settings"
- Algunos tienen slider de "Creatividad"
- No todos exponen el control directo

### Via Prompting
Puedes influenciar sin control directo:
```
Baja temperatura (implícito):
"Dame LA solución más estándar y probada para..."

Alta temperatura (implícito):
"Explora 10 formas creativas diferentes de..."
```

## Estrategia por Tipo de Trabajo

### Para Backend Developers
- **Por defecto**: 0.2-0.3 (precisión)
- **Excepción**: 0.7-0.8 para arquitectura y naming

### Para Frontend Developers
- **Por defecto**: 0.3-0.5 (balance)
- **Excepción**: 0.7 para componentes innovadores

### Para Designers
- **Por defecto**: 0.5-0.7 (creatividad moderada)
- **Excepción**: 0.2 para documentación técnica

### Para DevOps
- **Por defecto**: 0.1-0.2 (máxima precisión)
- **Excepción**: Rara vez necesitas más

## Guía de Decisión Rápida

**Pregúntate**: "¿Existe UNA respuesta correcta?"

🤖 **SÍ** → Temperatura baja (0.1-0.3)
- Configuraciones
- Correcciones de bugs
- Formatos estándar
- Tests

⚖️ **DEPENDE** → Temperatura media (0.4-0.6)
- Implementaciones
- Refactoring
- Documentación

🎨 **NO** → Temperatura alta (0.7-0.9)
- Brainstorming
- Naming creativo
- Exploración de opciones

## Errores Comunes

### Error 1: Alta Temperatura para Código Crítico
```
❌ Temperatura 0.9 para generar queries SQL
✅ Temperatura 0.2 para generar queries SQL
```

### Error 2: Baja Temperatura para Creatividad
```
❌ Temperatura 0.1 para "dame 20 nombres creativos"
✅ Temperatura 0.8 para naming exploración
```

### Error 3: No Ajustar según Tarea
```
❌ Usar siempre 0.5 para todo
✅ Ajustar conscientemente según necesidad
```

## Tips Avanzados

### 1. Combina Temperaturas
```
Paso 1: Alta temperatura (0.8) - Genera 10 ideas
Paso 2: Baja temperatura (0.2) - Evalúa pros/contras
Paso 3: Media temperatura (0.5) - Implementa la elegida
```

### 2. A/B Testing
Prueba mismos prompts a diferentes temperaturas:
```typescript
// Prueba ambos y compara
const resultLow = await generate(prompt, { temperature: 0.2 });
const resultHigh = await generate(prompt, { temperature: 0.7 });
```

### 3. Temperatura por Fase del Proyecto
- **Exploración inicial**: Alta (0.7-0.8)
- **Desarrollo**: Media (0.4-0.5)
- **Testing/Deploy**: Baja (0.1-0.3)

## Conclusión Clave

La temperatura controla el **balance entre creatividad y consistencia**:

- **¿Necesitas precisión y confiabilidad?** → Baja
- **¿Necesitas balance?** → Media
- **¿Necesitas innovación y variedad?** → Alta

**Regla de oro**: Empieza en 0.5, ajusta según resultados. Para código crítico, baja a 0.2. Para exploración, sube a 0.7-0.8.

## Relación con Otros Conceptos

- **[Prompt](./05-prompt.md)**: Temperatura afecta cómo se interpreta el prompt
- **[Modelo](./02-modelo.md)**: Cada modelo responde diferente a temperatura
- **[LLM](./01-llm.md)**: La temperatura afecta el proceso de generación del LLM

---

**Siguiente**: Descubre [Herramientas](./07-herramienta.md) y las capacidades que permiten a los agentes interactuar con sistemas.

[← Volver a Conceptos](../README.md#conceptos)
