# 💼 Prompt: Scoping Técnico y Alcance de Discovery Calls para Agencias

> **Categoría:** Negocios de Agencia & Freelance  
> **Nivel:** Intermedio / Senior  
> **Modelos recomendados:** Claude 3.7 Sonnet / GPT-4o / Gemini 3.5 Pro  
> **Propósito:** Transformar notas desordenadas o transcripciones de llamadas con clientes en un documento de alcance técnico riguroso, evitando el trabajo gratis (*scope creep*) y cotizaciones a ciegas.

---

## 🎯 Cuándo Usarlo
- Inmediatamente después de terminar una llamada de descubrimiento (*Discovery Call*) con un cliente potencial.
- Cuando el cliente te pide *"un clon de Uber/Airbnb"* o no sabe explicar técnicamente qué necesita.
- Para armar una propuesta de valor cerrado antes de cotizar un proyecto llave en mano.

---

## 📝 El Prompt (Copiar y Pegar en el Chat de IA)

```markdown
Actúa como un Lead Solutions Architect y Technical Product Manager con más de 15 años de experiencia cotizando y entregando software en agencias tecnológicas de primer nivel.

Tu objetivo es analizar las notas crudas y desordenadas de una llamada de descubrimiento con un cliente potencial, y transformarlas en un Documento de Alcance Técnico y Estratégico (Technical Scoping Brief). 

Tu enfoque debe ser DEFENSIVO con la rentabilidad de la agencia y CONSTRUCTIVO con el cliente: debemos evitar a toda costa el "scope creep" (funcionalidades agregadas fuera de presupuesto) y cotizar valor cerrado por entregables, nunca horas sueltas.

### NOTAS CRUDAS DE LA REUNIÓN:
"""
[PEGAR AQUÍ LAS NOTAS, AUDIO TRANSCRIPTO O RESUMEN DE LA REUNIÓN CON EL CLIENTE]
"""

---

### GENERA TU RESPUESTA ESTRUCTURADA EN LAS SIGUIENTES 5 SECCIONES:

#### 1. Diagnóstico del Problema Real de Negocio (Jobs to be Done)
- ¿Cuál es el dolor comercial o cuello de botella central que el cliente intenta resolver (más allá de las pantallas que cree querer)?
- ¿Quién es el usuario final y cuál es la métrica de éxito del proyecto?

#### 2. Matriz de Alcance MoSCoW (Límites Defensivos)
- 🟢 **Must Have (MVP Estricto - Sprint 1/Lanzamiento):** Únicamente las funcionalidades sin las cuales el producto no puede validar la propuesta de valor. Máximo 4-5 ítems.
- 🟡 **Should Have (Fase 2 / Post-Validación):** Características importantes que aportan valor pero que NO bloquean el lanzamiento inicial.
- 🔴 **Won't Have (Explícitamente Fuera de Alcance):** Lista taxativa de funcionalidades que NO forman parte de esta etapa (para blindar a la agencia de requerimientos imprevistos).

#### 3. Matriz de Riesgos Técnicos e Integraciones Críticas
Identifica los 3 a 5 mayores riesgos técnicos:
- Integraciones con APIs de terceros (pasarelas de pago, CRMs, servicios de mapas).
- Supuestos no validados del cliente que requieren investigación previa (*Spike* técnico).
- Riesgos de seguridad, privacidad de datos o infraestructura.

#### 4. Propuesta de Arquitectura y Stack Recomendado
- Stack sugerido (Frontend, Backend, Base de Datos, Servicios Cloud) justificando por qué es la opción más rápida, económica y mantenible para este MVP.
- ¿Se recomienda un desarrollo a medida, un backend-as-a-service (Supabase/Firebase) o una solución híbrida?

#### 5. Hoja de Ruta de Entregables en Sprints Cerrados
Desglosa el proyecto en hitos cerrados de entrega tangible (no en horas de desarrollo):
- **Sprint 0 / Setup:** Arquitectura base, diseño de datos y contratos de interfaz.
- **Sprint 1:** Flujo crítico funcional (el core del negocio operable en staging).
- **Sprint 2:** Integraciones y panel administrativo básico.
- **Sprint 3:** Hardening, tests de carga, seguridad y deploy a producción.
```

---

## 💡 Buenas Prácticas al Usarlo
1. **Pegá la transcripción en bruto:** No te gastes en emprolijar las notas; el prompt está diseñado justamente para extraer la señal del ruido.
2. **Revisá la sección "Won't Have":** Esa sección es tu escudo legal y comercial. Asegurate de incluirla tal cual en la propuesta que le envíes al cliente.
3. **No regales la arquitectura:** Podés cobrar un "Discovery Sprint" de 3 a 5 días solo para entregarle este documento al cliente antes de comprometerte al desarrollo completo.
