# Spec-Driven Development (SDD)

> Protocolo de ejecución secuencial para agentes autónomos. Desacopla la decisión arquitectónica de la escritura de código para evitar la saturación de contexto y la improvisación.

<p align="left">
  <img src="https://img.shields.io/badge/Metodolog%C3%ADa-SDD-0284C7?style=flat-square" alt="SDD" />
  <img src="https://img.shields.io/badge/Target-Antigravity%20%7C%20Cursor%20%7C%20Claude-10B981?style=flat-square" alt="Target" />
  <img src="https://img.shields.io/badge/Fases-9%20M%C3%B3dulos-38BDF8?style=flat-square" alt="Fases" />
  <img src="https://img.shields.io/badge/Comunidad-Human%20Cowork-1E293B?style=flat-square" alt="Human Cowork" />
</p>

---

## 🎯 El Problema que Resuelve

Cuando un modelo de lenguaje intenta resolver una tarea compleja de un solo disparo:
1. **Infla su contexto** leyendo archivos innecesarios antes de planificar.
2. **Alucina dependencias** porque mezcla diseño de interfaces con lógica de persistencia.
3. **Omite casos de borde** al saltar directo a escribir código sin validar requisitos.

SDD resuelve esto forzando una **máquina de estados finitos**: el agente no puede escribir una sola línea de código sin haber pasado antes por especificación y diseño técnico aprobados.

---

## 🧭 Grafo de Dependencias (DAG)

```text
┌──────────────┐     ┌──────────────┐     ┌────────────┐     ┌─────────────┐
│  sdd-explore │ ──> │  sdd-propose │ ──> │  sdd-spec  │ ──> │  sdd-tasks  │
└──────────────┘     └──────────────┘     └────────────┘     └─────────────┘
                                                 │                  │
                                                 ▼                  │
                                          ┌─────────────┐           │
                                          │  sdd-design │ ──────────┘
                                          └─────────────┘
                                                 │
                                                 ▼
┌──────────────┐     ┌──────────────┐     ┌─────────────┐
│  sdd-archive │ <── │  sdd-verify  │ <── │  sdd-apply  │
└──────────────┘     └──────────────┘     └─────────────┘
```

---

## 📦 Matriz Operativa de Fases

| Módulo | Entrada (Lee) | Salida (Produce) | Responsabilidad |
| :--- | :--- | :--- | :--- |
| **`sdd-init`** | Entorno / Git | `sdd-init/{project}` | Detecta stack técnico, dependencias y bootstrapea memoria persistente. |
| **`sdd-explore`** | Código base | `sdd/{change}/explore` | Mapea archivos y compara alternativas sin modificar código. |
| **`sdd-propose`** | Exploración | `sdd/{change}/proposal` | Documenta intención, alcance y tradeoffs arquitectónicos. |
| **`sdd-spec`** | Propuesta | `sdd/{change}/spec` | Redacta requisitos funcionales y escenarios BDD (Given/When/Then). |
| **`sdd-design`** | Propuesta | `sdd/{change}/design` | Define patrones de arquitectura, contratos de datos y diagramas. |
| **`sdd-tasks`** | Spec + Design | `sdd/{change}/tasks` | Desglosa la implementación en ítems atómicos verificables. |
| **`sdd-apply`** | Tasks + Spec | Código modificado | Implementa tareas en bloques controlados sin desviarse del diseño. |
| **`sdd-verify`** | Spec + Tasks | `verify-report` | Valida cobertura contra especificaciones (bloquea si hay regresiones). |
| **`sdd-archive`** | Todos los artefactos | `archive-report` | Sincroniza deltas con las specs maestras y archiva el cambio. |

---

## 💻 Instalación y Uso Local

### En Google Antigravity IDE:
Copiá las carpetas de esta suite en tu directorio de skills:
* **Global (todas las sesiones):** `%USERPROFILE%\.gemini\config\skills\`
* **Local (solo este repositorio):** `.agents/skills/`

### En Cursor / Claude Code:
Podés incorporar las reglas de cada módulo dentro de tu archivo `.cursorrules` o en tu system prompt como instrucciones modulares de fase.

---

> [!TIP]
> **Regla de oro de SDD:** Nunca ejecutes `sdd-apply` sin tener `sdd-spec` y `sdd-tasks` aprobados por un humano. El humano lidera la estrategia; la IA ejecuta la mecánica.
