# Guía de IA para el Equipo RUDO

Guía completa para desarrolladores, diseñadores y gestión sobre cómo usar IA efectivamente en el trabajo diario.

---

## 🎯 ¿Por Qué Esta Guía?

La IA es una herramienta poderosa, pero la mayoría la usa mal:
- Prompts vagos que generan código inútil
- Copy/paste sin entender qué hace el código
- Frustración cuando no funciona
- Desconocimiento de herramientas más allá de ChatGPT

**Esta guía te lleva desde cero hasta uso avanzado**, combinando teoría sólida con práctica efectiva.

---

## 📚 Estructura de la Guía

La guía está organizada en tres pilares complementarios:

### 1️⃣ **[Glosario](./glosario.md)** - Fundamentos Teóricos
Entiende **cómo funciona** la IA y **por qué** se comporta como lo hace.

**11 conceptos esenciales:**
- [01. LLM (Large Language Model)](./conceptos/01-llm.md) - El "cerebro" detrás de la IA
- [02. Modelo](./conceptos/02-modelo.md) - Elegir la herramienta correcta
- [03. Token](./conceptos/03-token.md) - Costes y límites
- [04. Contexto](./conceptos/04-contexto.md) - Información de fondo efectiva
- [05. Prompt](./conceptos/05-prompt.md) - Escribir instrucciones efectivas
- [06. Temperatura](./conceptos/06-temperatura.md) - Controlar creatividad
- [07. Herramienta](./conceptos/07-herramienta.md) - Capacidades extendidas
- [08. Agente](./conceptos/08-agente.md) - IA autónoma
- [09. Alucinación](./conceptos/09-alucinacion.md) - Detectar errores (CRÍTICO)
- [10. Fine-tuning](./conceptos/10-fine-tuning.md) - IA personalizada
- [11. Entrenamiento](./conceptos/11-entrenamiento.md) - Cómo aprende la IA

### 2️⃣ **[Guía Práctica](./guia-practica/)** - Aplicación Real
Aplica los conceptos en **tu trabajo diario** con técnicas progresivas.

**Niveles disponibles:**
- **[Nivel 1: Chat Básico](./guia-practica/nivel-1-chat-basico.md)** ✅ *Disponible*
  - Prompts efectivos
  - Ciclo: prompt → código → prueba → refina
  - Detectar errores comunes
  - Seguridad al copiar/pegar

- **[Nivel 2: Chat Avanzado](./guia-practica/nivel-2-chat-avanzado.md)** ✅ *Disponible*
  - Conversaciones largas con contexto
  - Técnicas: Chain-of-Thought, Few-Shot, Role Prompting
  - Refactoring de proyectos completos
  - Code review colaborativo

### 3️⃣ **[Cheat Sheet](./cheat-sheet.md)** - Referencia Rápida
Consulta rápida de conceptos, técnicas y mejores prácticas.

---

## 👥 Para Quién es Esta Guía

**Para todo el equipo Lãberit:**
- **Desarrolladores** (Backend, Frontend)
- **Diseñadores** (UI/UX, Design Systems, Figma)
- **Gestión** (Planificación, Documentación, Análisis)

Los principios de uso efectivo de IA aplican independientemente de tu rol.

---

## 🛠️ Herramientas Cubiertas

### Chat (Nivel 1-2)
- **ChatGPT** (OpenAI) - Propósito general
- **Claude** (Anthropic) - Análisis profundo, contexto largo
- **Gemini** (Google) - Integración Google Workspace

### Agentes y Herramientas Especializadas
- **GitHub Copilot** - Autocompletado en IDE
- **Claude Code** - Agente para desarrollo
- **Cursor** - Editor con IA integrada

---

## ⚠️ Advertencias Importantes

### Sobre Seguridad 🚨
**Nunca copies código sin revisar:**
- SQL injection
- XSS vulnerabilities
- Eval/exec de input sin sanitizar
- Credenciales hardcodeadas
- APIs inseguras

### Sobre Propiedad Intelectual ⚖️
**Ten cuidado con:**
- Código propietario en chats públicos
- Datos sensibles en prompts
- API keys en conversaciones

### Sobre Confiabilidad 🤖
**La IA no es perfecta:**
- Genera código que no compila
- Comete errores de lógica
- Inventa APIs que no existen
- Usa patrones deprecados

**Siempre verifica, siempre entiende.**

---

## 📊 Estado de la Guía

| Sección | Estado | Última Actualización |
|---------|--------|---------------------|
| Conceptos (01-11) | ✅ Completo | 2025-01 |
| Nivel 1 | ✅ Completo | 2025-01 |
| Nivel 2 | ✅ Completo | 2025-01 |
| Cheat Sheet | ✅ Completo | 2025-01 |

---

## 🚀 Empezar Ahora

### Para Principiantes Completos:
1. **[Lee Conceptos 01-05](./conceptos/01-llm.md)** (30 min)
2. **[Practica Nivel 1](./guia-practica/nivel-1-chat-basico.md)** (2-3 días)
3. **[Continúa con Nivel 2](./guia-practica/nivel-2-chat-avanzado.md)** (1 semana)

### Para Usuarios Con Experiencia:
1. **[Revisa el Cheat Sheet](./cheat-sheet.md)** (10 min)
2. **[Profundiza en Conceptos](./conceptos/)** según necesites
3. **[Técnicas Avanzadas en Nivel 2](./guia-practica/nivel-2-chat-avanzado.md)**

### Para Referencia Rápida:
→ **[Cheat Sheet](./cheat-sheet.md)** - Guarda para consulta diaria

---

## 💡 Filosofía de la Guía

### Principios:

**1. Claridad sobre cantidad**
- Directo al grano
- Sin relleno innecesario
- Ejemplos prácticos reales

**2. Teoría + Práctica**
- **Conceptos:** Entiende el "por qué"
- **Guía Práctica:** Aplica el "cómo"
- **Cheat Sheet:** Consulta rápida

**3. Progresión natural**
- De lo simple a lo complejo
- Cada nivel construye sobre el anterior
- No saltes pasos

**4. Universal pero específico**
- Principios aplicables a cualquier rol
- Ejemplos específicos para dev/design
- Adaptas a tu contexto

**5. Práctica sobre teoría**
- Enfocado en casos de uso reales
- Menos conceptos, más aplicación
- Tips del mundo real

---

## 🆘 ¿Necesitas Ayuda?

- **Vista general de conceptos:** Acude al [glosario](./glosario.md)
- **Cómo hacer algo:** Acude a [/guia-practica](./guia-practica/)
- **Referencia rápida:** Usa [Cheat Sheet](./cheat-sheet.md)
- **No funciona algo:** Vuelve al nivel anterior
- **Feedback/sugerencias:** Abre un issue

---

## 📖 Índice Completo

### Glosario
- [Glosario Completo](./glosario.md)

### Guía Práctica
- [Nivel 1: Chat Básico](./guia-practica/nivel-1-chat-basico.md)
- [Nivel 2: Chat Avanzado](./guia-practica/nivel-2-chat-avanzado.md)

### Referencia
- [Cheat Sheet](./cheat-sheet.md)

---

**¿Listo para empezar?**

→ **Principiantes:** [Conceptos: LLM](./conceptos/01-llm.md)
→ **Prácticos:** [Nivel 1: Chat Básico](./guia-practica/nivel-1-chat-basico.md)
→ **Experimentados:** [Cheat Sheet](./cheat-sheet.md)

---

*Guía creada para el equipo de Lãberit - Actualizada Enero 2025*
