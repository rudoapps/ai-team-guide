# Prompt

## La Analogía Sencilla

Un prompt es como **dar instrucciones a un empleado nuevo**. La calidad de tus instrucciones determina directamente la calidad del trabajo que recibes.

¡Piénsalo como la **única manera de comunicarte** con la IA sobre lo que quieres - así que hazlo contar!

## Lo que Hace un Buen Prompt

### El Marco CLARO

**C - Contexto**: ¿Cuál es la situación?
**L - Longitud**: ¿Qué tan larga debe ser la respuesta?
**A - Audiencia**: ¿Para quién es esto?
**R - Rol**: ¿Qué papel debe desempeñar la IA?
**O - Objetivo**: ¿Qué resultado específico quieres?

## Anatomía del Prompt: Antes y Después

### ❌ Mal Prompt
```
"Escribe un correo sobre la reunión."
```

**Problemas**: Vago, sin contexto, audiencia poco clara, sin detalles específicos

### ✅ Buen Prompt
```
**Rol**: Eres un jefe de proyecto profesional.

**Contexto**: Nuestra reunión de planificación Q3 programada para el martes a las 14:00 ha sido pospuesta debido a retrasos en la aprobación del presupuesto.

**Tarea**: Escribe un correo al equipo de 8 personas del proyecto explicando el aplazamiento.

**Audiencia**: Miembros internos del equipo (mezcla de roles técnicos y de negocio)

**Tono**: Profesional pero tranquilizador

**Longitud**: Manténlo bajo 150 palabras

**Incluir**: 
- Razón del aplazamiento
- Nueva fecha (por determinar esta semana)
- Qué debe hacer el equipo mientras tanto
- Disculpa por el aviso tardío
```

## La Jerarquía del Prompt: De Básico a Avanzado

### Nivel 1: Solicitud Básica
```
"Resume este artículo."
```

### Nivel 2: Solicitud Específica
```
"Resume este artículo en 3 puntos enfocándote en las principales implicaciones de negocio."
```

### Nivel 3: Contexto Detallado
```
Rol: Eres un analista de negocio
Tarea: Resume este artículo sobre IA en manufactura
Audiencia: Ejecutivos de alto nivel que necesitan insights rápidos
Formato: 3 puntos
Enfoque: Implicaciones de negocio y ROI potencial
Tono: Profesional y basado en datos
```

### Nivel 4: Avanzado con Ejemplos
```
Rol: Eres un analista de negocio
Tarea: Resume este artículo sobre IA en manufactura
Audiencia: Ejecutivos de alto nivel que necesitan insights rápidos

Formato: Sigue esta estructura:
• Impacto de Negocio: [implicaciones clave de negocio]
• Implicaciones Financieras: [costes, ahorros, potencial de ROI] 
• Recomendaciones Estratégicas: [qué deberíamos considerar]

Tono: Profesional y basado en datos
Longitud: Cada punto debe ser máximo 1-2 oraciones

Ejemplo de buena salida:
• Impacto de Negocio: La implementación de IA podría reducir los costes de producción en un 15-20% mientras mejora la precisión del control de calidad.
```

## Plantillas de Prompt para Tareas Comunes de Oficina

### Escritura de Correos
```
Rol: Profesional [tu puesto de trabajo]
Tarea: Escribir un correo [tipo]
Para: [destinatario y relación]
Sobre: [tema/propósito principal]
Tono: [profesional/amigable/urgente/de disculpa]
Puntos clave a incluir:
- [punto 1]
- [punto 2]
- [punto 3]
Longitud: [límite de palabras/párrafos]
```

### Análisis de Documentos
```
Rol: [rol de experto relevante]
Tarea: Analizar este [tipo de documento]
Enfoque: [aspectos específicos a analizar]
Formato de salida: [puntos/párrafos/tabla]
Audiencia: [quién leerá tu análisis]
Preguntas clave a responder:
1. [pregunta 1]
2. [pregunta 2]
3. [pregunta 3]
```

### Preparación de Reuniones
```
Rol: Facilitador de reunión
Tarea: Crear una agenda para [tipo de reunión]
Asistentes: [lista o descripción]
Duración: [límite de tiempo]
Objetivo principal: [meta primaria]
Temas clave a cubrir:
- [tema 1 con asignación de tiempo]
- [tema 2 con asignación de tiempo]
Formato: Incluir horarios y resultados esperados
```

## Técnicas Avanzadas de Prompting

### Cadena de Pensamiento
Pide a la IA que muestre su razonamiento:
```
"Antes de dar tu respuesta final, guíame paso a paso por tu proceso de pensamiento."
```

### Juego de Roles
Haz que la IA adopte una perspectiva específica:
```
"Eres un CFO escéptico revisando esta propuesta. ¿Qué preocupaciones plantearías?"
```

### Establecimiento de Restricciones
Define límites claros:
```
"Limita tu respuesta exactamente a 3 recomendaciones, cada una con una acción específica y cronograma."
```

### Prompting Multi-Paso
Divide tareas complejas en pasos:
```
"Primero, identifica los problemas principales en este documento. Luego, para cada problema, sugiere 2 soluciones. Finalmente, clasifica todas las soluciones por viabilidad."
```

## Errores Comunes de Prompting

### Error: Demasiado Vago
```
❌ "Ayúdame con este proyecto"
✅ "Revisa este plan de proyecto e identifica 3 riesgos principales con estrategias de mitigación"
```

### Error: Demasiado Complejo
```
❌ "Analiza este documento, resume los puntos clave, identifica riesgos, propón soluciones, crea un cronograma y estima costes"
```
**Solución**: Dividir en prompts separados y enfocados

## Estrategia de Prompting Iterativo

### Ronda 1: Obtener la Base
```
"Escribe un borrador de propuesta para implementar un chatbot de IA para servicio al cliente."
```

### Ronda 2: Refinar y Especificar
```
"Revisa esta propuesta para enfocarte más en ahorros de costes e incluir métricas específicas para el éxito."
```

### Ronda 3: Pulir y Perfeccionar
```
"Haz el tono más amigable para ejecutivos y añade una sección de mitigación de riesgos."
```

## Probar y Mejorar Tus Prompts

### Prueba A/B de Tus Prompts
Prueba diferentes versiones y compara resultados:

**Versión A**: "Explica este concepto de manera sencilla."
**Versión B**: "Explica este concepto como si se lo enseñaras a un colega inteligente que es nuevo en el campo."

### Mantén una Biblioteca de Prompts
Guarda tus mejores prompts para reutilizar:
- Plantillas de correo
- Marcos de análisis  
- Formatos de agenda de reunión
- Estructuras de informe

## Conclusión Clave

**Grandes prompts = Grandes resultados**

Piensa en el prompting como **dar información a un consultor**:
- Dales contexto
- Sé específico sobre lo que quieres
- Define criterios de éxito
- Proporciona ejemplos cuando sea útil

Los 30 segundos que gastes creando un buen prompt te ahorrarán 10 minutos de refinamiento de ida y vuelta.

---

**Siguiente**: Aprende sobre [Temperatura](./06-temperature.md) y cómo controlar la creatividad de la IA.