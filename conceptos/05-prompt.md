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
