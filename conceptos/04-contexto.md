# Contexto

## ¿Qué es el Contexto?

**Definición simple:** La información extra que le das a la IA para que entienda tu situación.

**Analogía:** Como darle a un nuevo colega la **historia completa** antes de pedirle que tome una decisión o realice una acción.

##Sin Contexto vs. Con Contexto

**Sin Contexto** (Pobre):
```
"Escribe un correo sobre la reunión."
```

**Con Contexto** (Mejor):
```
"Escribe un correo profesional a nuestro equipo de proyecto de 8 personas
explicando que la reunión de planificación Q3 del martes se pospone debido
a retrasos en la aprobación del presupuesto. El equipo incluye tanto personas
técnicas como de negocio, y necesito sonar con disculpas pero tranquilizador."
```

## Tipos de Contexto

### 1. Contexto Situacional 📍
**Qué está pasando y por qué**
- Situación actual
- Eventos recientes
- Nivel de urgencia
- Partes involucradas

### 2. Contexto de Audiencia 👥
**Quién verá o usará esto**
- Roles y niveles de experiencia
- Relación contigo (interno, cliente, ejecutivo)
- Preferencias de comunicación

### 3. Contexto de Formato 📋
**Cómo debe estructurarse**
- Tipo de documento y longitud
- Secciones requeridas
- Estilo y tono
- Método de distribución

### 4. Contexto Histórico 📚
**Qué pasó antes**
- Conversaciones previas
- Decisiones pasadas
- Lecciones aprendidas
- Patrones establecidos

### 5. Contexto Empresarial 🏢
**Tu empresa e industria**
- Cultura y valores
- Regulaciones
- Competidores
- Terminología interna

## Por Qué Importa

✅ **Con buen contexto**:
- Respuestas precisas y relevantes
- Menos ida y vuelta
- Estilo y tono apropiados
- Mejor calidad profesional

❌ **Sin contexto**:
- Respuestas genéricas
- Múltiples revisiones necesarias
- Tono inapropiado
- Resultados no útiles

## En la Práctica

### Para Desarrolladores:
```
Contexto efectivo:
"Estoy construyendo una app móvil en React Native que consume
una API REST. Necesito una función que obtenga la lista de productos.
El backend usa JWT para auth. La app debe funcionar offline
guardando en AsyncStorage."
```

### Para Diseñadores:
```
Contexto efectivo:
"Estoy diseñando un sistema de botones en Figma para una app
de fintech. Necesita cumplir con WCAG AA para accesibilidad.
La marca es moderna pero confiable. Los usuarios son
principalmente 35-55 años."
```

## La Pirámide de Contexto

**Nivel 1 - Esencial** (Siempre incluir):
- Lo que quieres lograr
- Quién es tu audiencia
- Restricciones críticas

**Nivel 2 - Importante** (Cuando sea relevante):
- Contexto situacional
- Requisitos de formato
- Tono y estilo

**Nivel 3 - Útil** (Para tareas complejas):
- Antecedentes históricos
- Ejemplos de lo que funciona
- Contexto empresarial específico

## Limitaciones de Contexto

Los modelos tienen límites (ventana de contexto):

| Modelo | Límite de Contexto |
|--------|-------------------|
| GPT-3.5 | ~12 páginas |
| GPT-4 | ~6-100 páginas |
| Claude 3 | ~150 páginas |

**Cuando el contexto se pierde**:
- Conversaciones muy largas
- Múltiples temas
- Sesiones de múltiples días

**Solución**: Resume periódicamente:
```
"Para recapitular:
- Proyecto: App de ecommerce en React Native
- Stack: Node.js + PostgreSQL
- Trabajando en: Sistema de pagos

Ahora necesito..."
```

## Conclusión Clave

El contexto es el **puente entre tu conocimiento y las capacidades de la IA**.

**Regla del Contexto**: Cuanto más importante o compleja sea la tarea, más contexto debes proporcionar.

## Relación con Otros Conceptos

- **[Prompt](./05-prompt.md)**: El contexto es parte fundamental de un buen prompt
- **[Token](./03-token.md)**: El contexto consume tokens
- **[Modelo](./02-modelo.md)**: Diferentes modelos tienen diferentes límites de contexto

---

**Siguiente**: Domina [Prompting](./05-prompt.md) para obtener mejores respuestas de IA.

[← Volver a Conceptos](../README.md#conceptos)
