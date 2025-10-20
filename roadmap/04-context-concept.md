# Contexto en IA

## La Analogía Sencilla

Piensa en el **contexto** como la **información de fondo** que das a una IA, igual que cuando informas a un nuevo colega sobre un proyecto. Cuanta más información relevante de fondo tengan, mejor podrán ayudarte.

El contexto es como darle a alguien la **historia completa** antes de pedirle que tome una decisión o realice una acción.

## ¿Qué es el Contexto en IA?

### Definición
El contexto es toda la información que ayuda a una IA a entender:
- **Lo que estás tratando de lograr**
- **En qué situación te encuentras**
- **Qué restricciones o requisitos existen**
- **Qué estilo o enfoque prefieres**

### Contexto vs. Solo Instrucciones
**Sin Contexto** (Pobre):
```
"Escribe un correo sobre la reunión."
```

**Con Contexto** (Mejor):
```
"Escribe un correo profesional a nuestro equipo de proyecto de 8 personas explicando que la reunión de planificación Q3 del martes se pospone debido a retrasos en la aprobación del presupuesto. El equipo incluye tanto personas técnicas como de negocio, y necesito sonar con disculpas pero tranquilizador."
```

## Tipos de Contexto

### 1. Contexto Situacional 📍
**Qué está pasando y por qué**
- Situación empresarial actual
- Eventos o cambios recientes
- Nivel de urgencia
- Partes interesadas involucradas

**Ejemplo**:
```
"Nuestro principal competidor acaba de anunciar una reducción de precios, y nuestro equipo de ventas está recibiendo resistencia de los clientes. Necesito responder a este correo de cliente preguntando sobre nuestra estrategia de precios."
```

### 2. Contexto de Audiencia 👥
**Quién verá o usará esto**
- Títulos de trabajo y niveles de experiencia
- Relación contigo (equipo interno, cliente externo, ejecutivo)
- Antecedentes culturales o industriales
- Preferencias de comunicación

**Ejemplo**:
```
"Esta presentación es para ejecutivos de alto nivel que tienen 15 minutos, prefieren insights basados en datos, y necesitan elementos de acción claros que puedan aprobar inmediatamente."
```

### 3. Contexto de Formato 📋
**Cómo debe estructurarse la salida**
- Tipo de documento y longitud
- Secciones o elementos requeridos
- Requisitos de estilo y tono
- Método de distribución

**Ejemplo**:
```
"Crea un resumen ejecutivo de 2 páginas con una declaración de problema de apertura, 3 recomendaciones clave con costes, y un cronograma de decisión. Esto se imprimirá y discutirá en la reunión de junta directiva de mañana."
```

### 4. Contexto Histórico 📚
**Qué pasó antes**
- Conversaciones o decisiones previas
- Rendimiento o resultados pasados
- Lecciones aprendidas
- Patrones o preferencias establecidos

**Ejemplo**:
```
"Este es el tercer trimestre consecutivo en que hemos perdido nuestros objetivos de ventas. Las revisiones trimestrales anteriores se enfocaron en factores del mercado externo, pero esta vez el liderazgo quiere examinar nuestros procesos internos y rendimiento del equipo."
```

### 5. Contexto Empresarial 🏢
**Tu empresa y especificaciones de la industria**
- Cultura y valores de la empresa
- Regulaciones o estándares de la industria
- Panorama competitivo
- Procesos internos y terminología

**Ejemplo**:
```
"Somos una empresa B2B SaaS en el espacio de la salud, así que todas las comunicaciones deben cumplir con HIPAA. Nuestra cultura empresarial valora la transparencia y comunicación directa, y típicamente tomamos decisiones a través de construcción de consenso en lugar de directivas de arriba hacia abajo."
```

## Por qué Importa el Contexto

### 1. Precisión y Relevancia ✅
Con el contexto adecuado, la IA puede:
- Generar respuestas que se ajusten a tu situación específica
- Usar terminología y estilo apropiados
- Abordar las necesidades subyacentes reales
- Evitar sugerencias genéricas o irrelevantes

### 2. Eficiencia ⚡
Un buen contexto reduce:
- Ida y vuelta de aclaraciones
- Necesidad de múltiples revisiones
- Tiempo gastado editando salidas
- Malentendidos y errores

### 3. Calidad Profesional 💼
El contexto ayuda a la IA a producir:
- Lenguaje apropiado para la industria
- Nivel correcto de formalidad
- Ejemplos y referencias relevantes
- Estructura y flujo adecuados

## Contexto en Diferentes Interacciones de IA

### Conversaciones Cortas
**Contexto Mínimo** - Para tareas simples e independientes:
```
"Revisa este correo para gramática y claridad."
```

**Contexto Rico** - Para tareas complejas o sensibles:
```
"Revisa este correo a un cliente importante que está considerando cancelar su contrato. El tono debe permanecer profesional y confiado mientras aborda sus preocupaciones sobre nuestras interrupciones de servicio recientes."
```

### Conversaciones Largas
La IA "recuerda" partes anteriores de tu conversación, pero esta memoria tiene límites:

**Límites de Ventana de Contexto**:
- GPT-3.5: ~3 páginas de texto
- GPT-4: ~6-25 páginas de texto  
- Claude 3: ~150 páginas de texto

**Cuando el Contexto se Pierde**:
- Conversaciones muy largas
- Discusiones complejas de múltiples temas
- Sesiones que abarcan múltiples días

**Solución**: Resume periódicamente el contexto clave:
```
"Para recapitular nuestra discusión: Estamos planeando un lanzamiento de producto para Q2, dirigiéndonos a empresas de mercado medio, con enfoque en ahorro de costes. Los principales desafíos que hemos identificado son la estrategia de precios y entrenamiento del equipo de ventas. Ahora necesito ayuda con..."
```

## Proporcionar Contexto Efectivo

### La Pirámide de Contexto 🔺

**Nivel 1 - Esencial** (Siempre incluir):
- Lo que quieres lograr
- Quién es tu audiencia
- Cualquier restricción crítica

**Nivel 2 - Importante** (Incluir cuando sea relevante):
- Contexto situacional
- Requisitos de formato específicos
- Consideraciones de tono o estilo

**Nivel 3 - Útil** (Añadir para tareas complejas):
- Antecedentes históricos
- Ejemplos de lo que funciona/no funciona
- Contexto empresarial específico

## Marcos de Contexto para Tareas Comunes

### Escritura de Correos
```
Contexto a incluir:
- Relación con el destinatario
- Propósito del correo
- Nivel de urgencia
- Sensibilidades a evitar
- Acción deseada del destinatario
```

### Creación de Documentos
```
Contexto a incluir:
- Audiencia objetivo y su nivel de experiencia
- Propósito y objetivos del documento
- Duración y formato requeridos
- Dónde/cómo se utilizará
- Revisores o aprobadores
```

### Análisis de Datos
```
Contexto a incluir:
- Fuente e importancia de los datos
- Decisiones que dependen del análisis
- Audiencia para los hallazgos
- Restricciones de tiempo
```

### Resolución de Problemas
```
Contexto a incluir:
- Impacto y urgencia del problema
- Soluciones previas intentadas
- Recursos disponibles
- Criterios de éxito
- Tolerancia al riesgo
```

## Técnicas Avanzadas de Contexto

### 1. Contexto en Capas
Comienza amplio, luego ve más específico:
```
"Nuestra empresa está implementando un nuevo sistema de servicio al cliente [contexto amplio]. El equipo técnico tiene preocupaciones sobre la complejidad de integración [contexto más específico]. Necesito abordar su preocupación específica sobre el tiempo de migración de datos [contexto específico]."
```

### 2. Contexto Comparativo
Usa ejemplos para aclarar:
```
"Escribe esto como nuestro script de llamada de ganancias Q2 [ejemplo exitoso], no como la actualización de producto del trimestre pasado [ejemplo no exitoso]."
```

### 3. Contexto Negativo
Especifica qué evitar:
```
"Crea un mensaje de marketing que enfatice la innovación pero evite cualquier afirmación sobre ser 'revolucionario' o 'disruptivo' ya que nuestro equipo legal marcó esos términos."
```

## Conclusión Clave

**El contexto es el puente entre tu conocimiento y las capacidades de la IA.**

Piensa en el contexto como **informar a un consultor**:
- Dales suficiente información de fondo para entender la situación
- Explica cómo se ve el éxito
- Comparte cualquier restricción o sensibilidad
- Proporciona ejemplos cuando sea útil

**La Regla del Contexto**: Cuanto más importante o compleja sea la tarea, más contexto debes proporcionar.

Un buen contexto transforma la IA de una herramienta genérica en un asistente conocedor que entiende tus necesidades y situación específicas.

---

**Siguiente**: Domina el arte de [Prompting](./05-prompt.md) para obtener mejores respuestas de IA.