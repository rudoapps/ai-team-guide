# Fine-tuning

## ¿Qué es el Fine-tuning?

**Definición simple:** Tomar un modelo de IA general y entrenarlo con datos específicos de tu dominio, empresa o proyecto para especializarlo.

**Analogía:** Es como contratar un **desarrollador senior general** (modelo base) y darle **3 meses de onboarding intensivo** en tu stack, tus patrones, tu código - convirtiéndolo en especialista de tu proyecto.

```
Modelo Base: "Sé JavaScript, React, Node.js en general"
Modelo Fine-tuned: "Sé específicamente cómo tu equipo estructura
                    componentes, tus naming conventions,
                    tus patterns de testing, tu arquitectura"
```

## Por Qué Hacer Fine-tuning

### Problema con Modelos Base

**Chat con GPT-4 base**:
```javascript
Tú: "Crea un componente Button siguiendo nuestras convenciones"

GPT-4: [Genera código genérico]
import React from 'react';
import styles from './Button.css';

export function Button({ label, onClick }) {
  return <button onClick={onClick}>{label}</button>;
}
```
*Funcional, pero no sigue TUS convenciones específicas*

### Con Fine-tuning

**Chat con GPT-4 fine-tuned con tu codebase**:
```typescript
Tú: "Crea un componente Button siguiendo nuestras convenciones"

GPT-4-tuned:
import { FC } from 'react';
import styled from 'styled-components';
import { ButtonProps } from '@/types/components';
import { useAnalytics } from '@/hooks';

export const Button: FC<ButtonProps> = ({
  variant = 'primary',
  size = 'md',
  label,
  onClick,
  ...props
}) => {
  const { trackClick } = useAnalytics();

  const handleClick = (e) => {
    trackClick('button', { variant, label });
    onClick?.(e);
  };

  return (
    <StyledButton
      variant={variant}
      size={size}
      onClick={handleClick}
      {...props}
    >
      {label}
    </StyledButton>
  );
};

const StyledButton = styled.button<{variant: string; size: string}>`
  // Usa tus design tokens
`;
```
*Sigue exactamente tus patrones: styled-components, analytics, props structure, naming*

## Casos de Uso en Desarrollo

### 1. Patrones de Código Específicos 🎯

**Sin fine-tuning**:
- Genera código "standard" genérico
- No conoce tus naming conventions
- Usa patterns diferentes a los tuyos

**Con fine-tuning**:
- Genera código que parece escrito por tu equipo
- Respeta tus guidelines automáticamente
- Usa tus librerías y helpers preferidos

**Ejemplo**:
```
Training data: 500 componentes de tu proyecto
Resultado: IA genera componentes indistinguibles de los reales
```

### 2. Stack Tecnológico Específico 🛠️

**Sin fine-tuning**:
```python
Tú: "Crea endpoint para crear usuario"

IA: [Genera con Express + MongoDB genérico]
```

**Con fine-tuning en tu stack**:
```python
Tú: "Crea endpoint para crear usuario"

IA: [Genera con tu stack exacto]
- FastAPI + Pydantic
- Tu estructura de validators
- Tu manera de handle errors
- Tus decorators custom
- Tu logging system
```

### 3. Design System y Componentes 🎨

**Training con tu design system**:
```
Data: Todos tus componentes + Storybook stories
Resultado: IA que genera componentes perfectamente
           integrados con tu design system
```

**Ejemplo**:
```typescript
Tú: "Crea modal de confirmación"

IA fine-tuned genera:
- Usa tus tokens de spacing
- Aplica tus animation utilities
- Estructura según tu pattern de modals
- Props tipadas según tus conventions
- Accesibilidad según tus standards
```

### 4. Testing Conventions 🧪

**Training con tus tests**:
```
Data: Todos tus archivos .test.ts
Resultado: IA que escribe tests como tu equipo
```

**Ejemplo**:
```typescript
Tú: "Escribe tests para el componente Button"

IA fine-tuned:
import { render, screen, userEvent } from '@testing-library/react';
import { Button } from './Button';

describe('Button', () => {
  it('renders with correct label', () => {
    render(<Button label="Click me" />);
    expect(screen.getByRole('button')).toHaveTextContent('Click me');
  });

  it('calls onClick handler when clicked', async () => {
    const handleClick = jest.fn();
    render(<Button label="Click" onClick={handleClick} />);

    await userEvent.click(screen.getByRole('button'));

    expect(handleClick).toHaveBeenCalledTimes(1);
  });

  it('tracks analytics on click', async () => {
    const { trackClick } = useAnalytics();
    // ... sigue tu patrón de testing de analytics
  });
});
```

## Proceso de Fine-tuning

### Fase 1: Recolección de Datos 📊

**Para proyecto de desarrollo**:
```bash
Datos a incluir:
✓ Todo tu código fuente (src/)
✓ Tests y sus patrones
✓ Configuraciones (tsconfig, webpack, etc.)
✓ Documentación interna
✓ Pull requests y code reviews
✓ Guidelines y style guides
✓ Commits messages (para aprender tu estilo)
```

**Calidad > Cantidad**:
```
❌ 10,000 archivos mal estructurados
✅ 1,000 archivos bien seleccionados y representativos
```

### Fase 2: Preparación y Limpieza 🧹

```bash
# Eliminar datos sensibles
grep -r "API_KEY\|PASSWORD\|SECRET" src/
# → Remover o reemplazar

# Eliminar código deprecated
find src/ -name "*.old.ts"
# → No incluir en training

# Formatear consistentemente
npm run prettier
# → Código limpio para training
```

**Estructura recomendada**:
```json
[
  {
    "prompt": "Create a button component with primary variant",
    "completion": "import { FC } from 'react';\nimport styled from..."
  },
  {
    "prompt": "Write test for button click handler",
    "completion": "describe('Button', () => {\n  it('calls onClick..."
  }
]
```

### Fase 3: Training 🏋️

**Opciones**:

**OpenAI Fine-tuning**:
```bash
# Preparar dataset
openai tools fine_tunes.prepare_data -f training_data.jsonl

# Iniciar fine-tune
openai api fine_tunes.create \
  -t "training_data.jsonl" \
  -m "gpt-3.5-turbo" \
  --suffix "my-company-code"
```

**Anthropic Claude**:
```python
# Via API (contactar sales para fine-tuning)
import anthropic

client = anthropic.Client(api_key="...")
# Fine-tuning enterprise
```

**Self-hosted (LoRA)**:
```python
# Para modelos open source
from transformers import AutoModelForCausalLM
from peft import LoraConfig, get_peft_model

model = AutoModelForCausalLM.from_pretrained("codellama/CodeLlama-7b")
lora_config = LoraConfig(r=8, lora_alpha=32)
model = get_peft_model(model, lora_config)
# ... training loop
```

### Fase 4: Validación ✅

**Test suite para modelo**:
```typescript
// Validation prompts
const validationTests = [
  {
    prompt: "Create React component with styled-components",
    expectContains: ["import styled", "const Styled", "FC<"],
    expectNotContains: ["import './styles.css'"]
  },
  {
    prompt: "Write unit test for function",
    expectContains: ["describe(", "it(", "expect("],
    expectNotContains: ["test("] // tu equipo usa it(), no test()
  }
];
```

### Fase 5: Deploy y Monitoreo 🚀

```javascript
// Uso del modelo fine-tuned
const completion = await openai.createCompletion({
  model: "ft:gpt-3.5-turbo:my-company:suffix",
  prompt: "Create button component",
  max_tokens: 500
});
```

## Costes y ROI

### Inversión Inicial

**OpenAI GPT-3.5 Turbo**:
```
Training: ~$0.008 por 1K tokens
- Dataset de 100K tokens: ~$0.80
- Dataset de 1M tokens: ~$8

Uso después:
- Input: ~$0.012 por 1K tokens (vs $0.001 base)
- Output: ~$0.016 por 1K tokens (vs $0.002 base)

Coste: 12-16x más caro que modelo base
```

**OpenAI GPT-4**:
```
Training: Contactar sales (enterprise)
Uso: Significativamente más caro

Mejor para: Equipos grandes con budget
```

**Self-hosted (CodeLlama + LoRA)**:
```
Training:
- GPU time: $50-200 (según cloud provider)
- Una sola vez

Uso:
- Infraestructura propia: $100-500/mes
- 0 coste por request

Mejor para: Proyectos grandes, largo plazo
```

### ROI Esperado

**Para equipo de 5 developers**:
```
Sin fine-tuning:
- Tiempo en formatting/fixing código IA: 2h/día/persona
- 10 horas/día equipo = ~$500/día

Con fine-tuning:
- Coste mensual: ~$100-500
- Tiempo ahorrado: 50-70% en fixes
- ROI: Positivo desde semana 1
```

## Alternativas al Fine-tuning

### RAG (Retrieval-Augmented Generation)

**Qué es**:
```
En lugar de entrenar modelo, le das contexto dinámicamente:

Tú: "Create button component"

Sistema RAG:
1. Busca en tu codebase componentes similares
2. Incluye ejemplos en el prompt
3. IA genera basándose en ejemplos

Ventajas:
✓ Mucho más barato
✓ Más fácil de implementar
✓ Actualizaciones en tiempo real
✓ No requiere re-training

Desventajas:
✗ Menos "internalizado" que fine-tuning
✗ Requiere buenos embeddings
✗ Limitado por context window
```

### Few-shot Prompting

**Qué es**:
```typescript
Tú: `
Aquí están 3 ejemplos de nuestros componentes:

EJEMPLO 1:
${componentExample1}

EJEMPLO 2:
${componentExample2}

EJEMPLO 3:
${componentExample3}

Ahora crea un componente Button similar:
`

Ventajas:
✓ Gratis
✓ Inmediato
✓ Flexible

Desventajas:
✗ Consume muchos tokens
✗ No escala bien
✗ Limitado a pocos ejemplos
```

### Comparación

| Método | Coste | Setup | Calidad | Mejor Para |
|--------|-------|-------|---------|------------|
| Fine-tuning | Alto | Complejo | Máxima | Enterprise, largo plazo |
| RAG | Medio | Moderado | Alta | Equipos medianos |
| Few-shot | Bajo | Simple | Media | Proyectos pequeños |

## Cuándo SI Hacer Fine-tuning

✅ **Vale la pena si**:
```
✓ Equipo de 5+ developers
✓ Codebase grande (50K+ líneas)
✓ Patrones muy específicos
✓ Alto volumen de uso diario
✓ ROI claro (tiempo ahorrado > coste)
✓ Budget para experimento
```

## Cuándo NO Hacer Fine-tuning

❌ **No vale la pena si**:
```
✗ Equipo pequeño (1-3 personas)
✗ Proyecto corto o temporal
✗ Codebase pequeño o genérico
✗ Bajo uso de IA
✗ Sin budget para experimentos
✗ RAG/Few-shot suficiente
```

## Mejores Prácticas

### 1. Empieza con RAG

```
Orden recomendado:
1. Prueba few-shot prompting (gratis)
2. Implementa RAG si necesitas más (barato)
3. Solo entonces considera fine-tuning (caro)
```

### 2. Itera Incremental

```
No fine-tunees todo de una:

Iteración 1: Solo componentes React
Iteración 2: Añade hooks y utils
Iteración 3: Añade tests
Iteración 4: Añade configuraciones
```

### 3. Mantén Versionado

```
my-model-v1 → Componentes básicos
my-model-v2 → + Hooks y context
my-model-v3 → + Testing patterns
my-model-v4 → + Full stack

Permite rollback si algo falla
```

### 4. Documenta Todo

```markdown
# Model: my-company-fe-v2

## Training Data
- 500 React components (src/components/)
- 200 custom hooks (src/hooks/)
- 300 tests (*.test.tsx)

## Known Good At
- Creating components with our patterns
- Writing tests with Testing Library
- Using our design tokens

## Known Limitations
- Backend code (not trained)
- Legacy components (excluded)
- CSS-in-JS (we use styled-components only)

## Cost
- Training: $15
- Usage: ~$0.016/1K output tokens

## Metrics
- Pass rate on validation: 94%
- Time saved: ~30% vs base model
```

## Herramientas y Platforms

### OpenAI Platform
```bash
# CLI oficial
pip install openai

# Web dashboard
https://platform.openai.com/finetune
```

### Hugging Face
```python
# Para modelos open source
from transformers import Trainer, TrainingArguments
# ... extensive ecosystem
```

### LangChain + Custom
```python
# Para implementar RAG o fine-tuning custom
from langchain import LLM, PromptTemplate
# ... flexible framework
```

## Conclusión Clave

Fine-tuning es **especialización mediante entrenamiento**:

- Transforma modelo general → experto en TU código
- Costoso pero potente para equipos grandes
- Para la mayoría, RAG es suficiente y más práctico

**Regla práctica**:
```
Equipo pequeño → Few-shot prompting
Equipo mediano → RAG
Equipo grande + presupuesto → Fine-tuning
```

**Recuerda**: Fine-tuning no es magia. Necesitas:
1. Datos de calidad
2. Casos de uso claros
3. Métricas de éxito
4. Presupuesto adecuado

## Relación con Otros Conceptos

- **[LLM](./01-llm.md)**: Fine-tuning crea versión especializada de un LLM
- **[Entrenamiento](./11-entrenamiento.md)**: Fine-tuning es re-entrenamiento parcial
- **[Modelo](./02-modelo.md)**: Creas un nuevo modelo derivado del base
- **[Agente](./08-agente.md)**: Agentes fine-tuned son más efectivos en tu dominio

---

**Siguiente**: Aprende sobre [Entrenamiento](./11-entrenamiento.md) y cómo los modelos aprenden.

[← Volver a Conceptos](../README.md#conceptos)
