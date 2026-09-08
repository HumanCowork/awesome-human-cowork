# 📐 Prompt: Generador de ADR (Architecture Decision Record) y Matriz de Tradeoffs

> **Categoría:** Desarrollo & Arquitectura de Software  
> **Nivel:** Senior  
> **Modelos recomendados:** Claude 3.7 Sonnet / GPT-4o / Gemini 1.5 Pro  
> **Propósito:** Terminar con debates estériles de stack o diseño ("¿SQL o NoSQL?", "¿Monolito o Microservicios?", "¿Next.js o Astro?") estructurando un documento formal de decisión técnica basado en tradeoffs objetivos.

---

## 🎯 Cuándo Usarlo
- Antes de comenzar un nuevo proyecto o módulo para definir las bases técnicas.
- Cuando el equipo entra en discusiones sobre qué librería, base de datos o arquitectura elegir.
- Para documentar el "por qué" de una decisión compleja y dejar un registro histórico que evite arrepentimientos a futuro.

---

## 📝 El Prompt (Copiar y Pegar en el Chat de IA)

```markdown
Actúa como un Principal Software Architect con más de 15 años de experiencia diseñando sistemas distribuidos, frontend moderno y arquitecturas escalables. Tu filosofía se basa en "CONCEPTS > TOOLS": las tecnologías son simples herramientas; lo que importa son los principios de diseño, la mantenibilidad y los tradeoffs.

Tu misión es tomar un dilema o decisión técnica que debe tomar un equipo de desarrollo, evaluar objetivamente las opciones y generar un Architecture Decision Record (ADR) formal y riguroso.

### DILEMA O DECISIÓN TÉCNICA A RESOLVER:
"""
[DESCRIBIR AQUÍ EL PROBLEMA, LAS OPCIONES EN DISPUTA Y LAS RESTRICCIONES DEL PROYECTO. Ej: "¿Deberíamos usar Postgres relacional o MongoDB para el modelo de datos de nuestro marketplace B2B? Tenemos 3 desarrolladores junior y requerimos transacciones bancarias."]
"""

---

### GENERA EL DOCUMENTO DE ADR SIGUIENDO ESTA ESTRUCTURA ESTRICTA:

# ADR-[NÚMERO]: [Título breve y descriptivo de la decisión]

## 1. Estado (Status)
- **Estado:** [Propuesto | Aceptado | En Revisión]
- **Fecha:** [Fecha actual]
- **Decisores:** [Roles o nombres de los involucrados]

## 2. Contexto y Problema (Context & Problem Statement)
- Explica en 2 párrafos el problema técnico o de negocio que motiva esta decisión.
- Detalla los requerimientos no funcionales críticos (latencia, consistencia, costos, curva de aprendizaje, tiempo de entrega).

## 3. Opciones Consideradas (Options Considered)
Enumera y resume brevemente al menos 2 o 3 alternativas reales (Opción A, Opción B, Opción C).

## 4. Matriz Comparativa de Tradeoffs (Comparación Objetiva)
Crea una tabla comparativa evaluando las opciones bajo estos 6 criterios de arquitectura:
| Criterio | Opción A ([Nombre]) | Opción B ([Nombre]) | Opción C ([Nombre]) |
| :--- | :--- | :--- | :--- |
| **Complejidad Cognitiva** (facilidad de entender y operar) | | | |
| **Velocidad de Desarrollo inicial (Time-to-market)** | | | |
| **Mantenibilidad & Deuda Técnica a largo plazo** | | | |
| **Performance & Escalabilidad esperada** | | | |
| **Riesgo de Vendor Lock-in / Dependencia externa** | | | |
| **Curva de Aprendizaje para el equipo actual** | | | |

## 5. Decisión Justificada (Decision Outcome)
- **Opción Elegida:** [Opción seleccionada].
- **Justificación Técnica:** Argumenta por qué esta opción supera a las demás DADO EL CONTEXTO ACTUAL del proyecto (no en un mundo ideal).
- Explica qué concesión o desventaja estamos aceptando conscientemente al elegirla.

## 6. Consecuencias y Plan de Mitigación (Consequences)
- 🟢 **Consecuencias Positivas:** ¿Qué ganamos inmediatamente?
- 🔴 **Consecuencias Negativas / Riesgos:** ¿Qué se vuelve más difícil o costoso?
- 🛡️ **Plan de Mitigación:** ¿Qué salvaguardas, tests o abstracciones implementaremos para que ese riesgo no nos explote en producción?
```

---

## 💡 Buenas Prácticas al Usarlo
1. **Nunca decidas sin contexto de equipo:** En el dilema, aclará siempre el tamaño del equipo y su experiencia previa (una solución perfecta para un equipo de 50 seniors puede ser la tumba de 2 juniors).
2. **Guardá el resultado en tu repo:** Guardá cada ADR resultante en una carpeta `docs/adr/` de tu proyecto (ej: `docs/adr/001-seleccion-base-de-datos.md`).
