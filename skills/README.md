# 🧠 Skills para Agentes de IA

Las **Skills** son paquetes de instrucciones operativas, buenas prácticas y herramientas diseñadas para que los agentes de IA (en entornos como Google Antigravity IDE, Cursor, Claude Projects o Windsurf) sigan convenciones rigurosas de desarrollo.

---

## 📦 Skills Disponibles en la Biblioteca

* 🏗️ **[SDD Framework Suite (Spec-Driven Development)](sdd-framework/)**: Metodología completa de 9 fases para gobernar agentes de IA con especificaciones formales antes de codificar.
* 🛠️ **[Skill Creator](skill-creator/)**: Protocolo meta-estándar para diseñar, estructurar y empaquetar nuevas skills de agentes de IA con convenciones canónicas.
* 🧠 **[Engram Protocol (Persistent Memory)](engram-protocol/)**: Protocolo de memoria duradera para agentes de IA que enseña guardado proactivo (`mem_save`), convenciones de topic keys y resúmenes de sesión.

---

## 📦 Categorías de Skills

1. **Arquitectura y Clean Code:** Principios de diseño sólido, container-presentational pattern, screaming architecture.
2. **Frontend & Design Systems:** Tokens semánticos, componentes accesibles, ergonomía móvil y web.
3. **Testing y Calidad:** Patrones de testing automatizado y testing de interfaces.

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
