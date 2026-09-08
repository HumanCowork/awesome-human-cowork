# 🤖 Protocolo Operativo para Agentes de IA (`AGENTS.md`)

> **Human Cowork** — Hub Tecnológico Colaborativo  
> Este documento define las reglas de ejecución autónoma, seguridad defensiva, introspección dinámica y calidad de integración para cualquier agente de Inteligencia Artificial (Google Antigravity IDE, Cursor, Windsurf, Claude Code, GitHub Copilot, etc.) que opere en este repositorio.

---

## 🧭 Principio Rector: Introspección Dinámica > Suposiciones Fijas

> [!IMPORTANT]
> **REGLA CERO:** Ningún agente de IA debe asumir estructuras de directorios, nombres de carpetas ni esquemas de tablas codificados de forma rígida (*hardcoded*).  
> Este repositorio es un ecosistema vivo y modular: la cantidad de categorías puede escalar de 3 a 200 directorios, y las columnas de los catálogos pueden evolucionar con el tiempo.  
> **Todo agente tiene el mandato estricto de inspeccionar el estado actual del repositorio en tiempo de ejecución antes de proponer, crear o mergear cambios.**

---

## 🔀 Selector de Rol (Role Dispatcher)

Al iniciar una sesión de trabajo en este repositorio, identificá tu contexto operativo:

| Rol Operativo | Contexto de Ejecución | Protocolo Obligatorio |
| :--- | :--- | :--- |
| 🛡️ **Maintainer / Admin Agent** | Tenés credenciales de escritura y aprobación de PRs en la organización `HumanCowork`. | **Aplicar [Sección 1: Protocolo de Maintainers](#-sección-1-protocolo-para-agentes-maintainers--admins)** |
| 🤝 **Community Member Agent** | Operás desde un fork personal o rama comunitaria para enviar aportes. | **Aplicar [Sección 2: Protocolo para la Comunidad](#-sección-2-protocolo-para-agentes-de-la-comunidad-forks)** |

---

## 🛡️ Sección 1: Protocolo para Agentes Maintainers / Admins

Como agente con privilegios administrativos, tu prioridad es la **integridad de la infraestructura, la seguridad y la consistencia del catálogo**.

### 1.1 Auditoría Pre-Merge (`Files changed`)
Antes de aprobar o fusionar cualquier Pull Request, inspeccioná de forma exhaustiva la lista de archivos modificados:

1. **Barrera de Seguridad CI/CD:**
   > [!CAUTION]
   > Si un PR proveniente de un fork o de un colaborador externo modifica cualquier archivo dentro de `.github/workflows/`, **DETENÉ EL MERGE EN SECO**.
   > Las automatizaciones con secretos (como `notify-discord.yml`) solo pueden ser modificadas por administradores humanos explícitamente.
2. **Inspección de Contenido Malicioso:**
   - Verificá que no existan scripts ofuscados, ejecutables binarios sospechosos ni URLs externas a servidores desconocidos.
   - Si se aportan scripts de automatización o flujos, verificá que no capturen ni transmitan credenciales sin consentimiento.
3. **Coherencia con el Árbol del Repositorio:**
   - Leé el `README.md` raíz para identificar qué categorías o dominios existen oficialmente.
   - Si el PR introduce una **nueva categoría raíz**, debe justificar la creación en la descripción del PR y registrar dicha sección en la tabla general del `README.md`.

---

### 1.2 Invariante de Sincronización Dinámica de Catálogos (Tablas)

> [!WARNING]
> **REGLA INVARIANTE:** Ningún recurso nuevo (skill, prompt, flujo, plantilla o documentación) puede quedar "huérfano" en el filesystem. Al incorporarse, **debe quedar reflejado en la tabla del catálogo correspondiente**.

Dado que las columnas de las tablas pueden cambiar en el tiempo, **no asumas qué columnas existen**. Aplicá este procedimiento de adaptación dinámica:

#### 📋 Algoritmo de Adaptación Dinámica de Tablas:
1. **Identificar el Directorio Destino:**  
   Revisá en qué directorio se guardó el recurso (ej. `<directorio_padre>/<subcarpeta>/`).
2. **Localizar el Catálogo Activo:**  
   Buscá el archivo `README.md` dentro de `<directorio_padre>/` (o en la raíz si aplica).
3. **Inspeccionar la Cabecera de la Tabla:**  
   Leé la fila de títulos de la tabla en cuestión:  
   `| Columna A | Columna B | Columna C | ... |`  
   Identificá qué representa cada columna según su nombre (ej. *Recurso*, *Descripción / Enfoque*, *Modelos Recomendados*, *Triggers*, *Versión*, *Tags*, etc.).
4. **Respetar la Alineación Existente:**  
   Observá la fila divisoria (ej. `| :--- | :--- | :---: |`) para mantener la coherencia visual.
5. **Generar la Fila Coherente:**  
   Construí la nueva fila mapeando la información del recurso a las columnas **descubiertas en tiempo real**. Si un dato opcional no aplica, colocá `-` o dejá el campo limpio según el patrón de la tabla.
6. **Verificar si el PR ya lo incluyó:**  
   - Si el autor del PR ya agregó la fila en la tabla respetando el formato actual: ✅ Validar y aprobar.
   - Si el autor lo olvidó: ⚠️ El agente admin debe incorporar la actualización de la tabla como parte del merge o en un commit posterior inmediato.

---

### 1.3 Formato del PR y Compatibilidad con Webhooks (Discord)

El repositorio cuenta con una GitHub Action (`notify-discord.yml`) que notifica automáticamente a la comunidad de Discord cada vez que un PR se fusiona a `main`.

Para evitar fallos en la integración (`HTTP 400 Bad Request` en Discord):
1. **Límite de Longitud del PR Body:**  
   El cuerpo de la descripción del PR no debe exceder los **2.000 caracteres**. (Discord rechaza embeds que superen los 4.096 caracteres combinados).
2. **Prohibido Volcar Bloques de Código Crudos:**  
   > [!IMPORTANT]
   > La descripción del PR debe contener explicaciones, viñetas y enlaces, **nunca bloques gigantes de código con triple backticks (```)**. El código pertenece a los archivos del repositorio, no al resumen del PR.
3. **Uso de la Plantilla Oficial:**  
   Asegurate de que el PR responda a las secciones definidas en `.github/PULL_REQUEST_TEMPLATE.md`.

---

### 1.4 Estrategia de Merge
- **Método Obligatorio:** `Squash and merge`.  
  Mantiene el historial de `main` lineal, atómico y legible.
- **Formato del Commit Mensaje (Conventional Commits):**
  - `feat(<dominio>): agregar <nombre-recurso> por @<autor> (#<pr>)`
  - *Ejemplo:* `feat(skills): agregar auditor-code-review-senior por @juanperez (#8)`
- **Prohibido:** Crear *Merge Commits* recursivos con ramas intermedias o commits sin contexto.

---

## 🤝 Sección 2: Protocolo para Agentes de la Comunidad (Forks)

Si sos un agente que asiste a un miembro de la comunidad para contribuir un nuevo recurso, seguí este protocolo para que el aporte sea aceptado sin fricción:

### 2.1 Descubrimiento de Destino
1. **Inspeccioná el repositorio remoto (`upstream`):**  
   Antes de crear carpetas al azar, leé el `README.md` principal para conocer qué colecciones existen (ej. `skills/`, `prompts/`, `automatizaciones/`, etc.).
2. **Inspeccioná un Recurso Existente como Ejemplo:**  
   Abrí un archivo existente dentro de la carpeta destino para emular su estilo, nomenclatura (`kebab-case`), frontmatter (si aplica) y nivel de detalle.
3. **Autocontenido y Atómico:**  
   Cada recurso debe ser modular y no depender de rutas locales absolutas de tu máquina.

---

### 2.2 Flujo de Git & Branching
1. **Fork del Repositorio:**  
   Trabajá siempre en tu propio fork (`gh repo fork HumanCowork/awesome-human-cowork`).
2. **Rama Atómica:**  
   Creá una rama descriptiva para tu cambio:  
   `git checkout -b feat/<nombre-recurso>`
3. **Alcance Exclusivo:**  
   Solo modificá los archivos pertinentes a tu recurso.  
   > [!CAUTION]
   > **NUNCA** toques `.github/workflows/` ni reconfigures scripts de integración continua. Hacerlo provocará el rechazo inmediato del PR.

---

### 2.3 Auto-Catalogación Proactiva (Recomendado ⭐)
Para facilitar el merge por parte de los administradores:
1. Abrí el `README.md` de la carpeta donde estás agregando tu recurso.
2. Analizá las columnas de la tabla del catálogo activo.
3. Agregá una fila con tu recurso enlazado, respetando estrictamente las columnas actuales.

---

### 2.4 Llenado Riguroso de la Plantilla de PR
Al ejecutar `gh pr create` o abrir el Pull Request vía web, utilizá la plantilla ubicada en `.github/PULL_REQUEST_TEMPLATE.md`:

```markdown
## 📌 Resumen del Cambio
[Explicación concisa en 2 o 3 párrafos de qué problema resuelve este recurso y qué valor aporta]

### 📦 Módulos / Archivos incluidos:
- `ruta/al/archivo-o-carpeta/` — [Breve descripción]

### 🎯 ¿Cómo se prueba o utiliza?
- [Pasos simples para que el revisor o cualquier miembro de la comunidad lo ejecute]
```

**Reglas de oro para la descripción:**
- ✅ Usá viñetas, negritas y enlaces relativos.
- ❌ **NO incluyas bloques de código crudo** de decenas de líneas en la descripción (rompe la notificación de Discord).
- ✅ Mantené el texto claro, profesional y por debajo de 2.000 caracteres.

---

## 📐 Referencia Rápida: Algoritmo de Detección de Esquemas para LLMs

Cuando tengas que parsear o agregar una fila a una tabla Markdown desconocida, ejecutá esta lógica mental:

```text
1. target_table = extraer_bloque_tabla(readme_path, seccion_relevante)
2. header_line  = primera_linea_que_empieza_con("|")
3. separator    = segunda_linea_que_empieza_con("|")
4. columns      = [col.strip() for col in header_line.split("|")[1:-1]]

5. nueva_fila   = []
6. for col in columns:
       val = extraer_metadata(recurso, col_name=col)
       nueva_fila.append(formatear_para_markdown(val))

7. fila_markdown = "| " + " | ".join(nueva_fila) + " |"
8. insertar_fila(target_table, fila_markdown)
```

---

## 💡 Enfoque Human Cowork
En **Human Cowork** valoramos los **conceptos claros por sobre el código improvisado**.  
Si una skill, prompt o automatización no cuenta con contexto, límites claros o pruebas reproducibles, no está lista para ser incorporada. Diseñá pensando en que otros miembros y agentes puedan aprender y construir sobre tus cimientos.
