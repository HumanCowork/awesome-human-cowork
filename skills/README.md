# 🧠 Skills para Agentes de IA

> Instrucciones operativas, buenas prácticas y protocolos estandarizados para que agentes de IA (Google Antigravity IDE, Cursor, Claude, Windsurf) sigan convenciones rigurosas de desarrollo.

<div align="center">

[**🏗️ METODOLOGÍA & SPECS**](#-metodología--gobernanza-de-agentes) • [**🧠 INFRAESTRUCTURA & META-PROTOCOLOS**](#-infraestructura--meta-protocolos) • [**💻 INSTALACIÓN LOCAL**](#-cómo-usarlas-en-tu-entorno-local) • [**🤝 CONTRIBUIR**](#-querés-aportar-una-skill)

</div>

---

### 🏗️ Metodología & Gobernanza de Agentes

| Skill | Enfoque / Qué Resuelve | Trigger Semántico | Versión |
| :--- | :--- | :--- | :---: |
| 🏗️ **[sdd-framework](sdd-framework/)** | Metodología de 9 fases (Spec-Driven Development) para pensar antes de codificar | `"sdd init"`, `"sdd explore"`, `"sdd propose"` | `v1.0` |

---

### 🧠 Infraestructura & Meta-Protocolos

| Skill | Enfoque / Qué Resuelve | Trigger Semántico | Versión |
| :--- | :--- | :--- | :---: |
| 🛠️ **[skill-creator](skill-creator/)** | Meta-herramienta canónica para diseñar, estructurar y empaquetar nuevas skills | `"crear skill"`, `"new skill"`, `"documentar patrones"` | `v1.0` |
| 🧠 **[engram-protocol](engram-protocol/)** | Protocolo de memoria duradera con Engram MCP (guardado proactivo y resúmenes) | `"engram"`, `"memoria persistente"`, `"mem_save"` | `v1.0` |

---

## 💻 Cómo usarlas en tu entorno local

### En Google Antigravity IDE:
Copiá la carpeta de la skill que quieras utilizar dentro de tu directorio global de configuraciones:
```bash
# Windows
%USERPROFILE%\.gemini\config\skills\<nombre-de-la-skill>\

# macOS / Linux
~/.gemini/config/skills/<nombre-de-la-skill>/
```
O dentro de tu proyecto local en la carpeta `.agents/skills/<nombre-de-la-skill>/`.

---

## 🤝 ¿Querés aportar una skill?
Si tenés una skill que te ordena el código y querés compartirla con la comunidad, consultá la [Guía de Contribución](../CONTRIBUTING.md).
