# 🤝 Guía de Contribución a Awesome Human Cowork

¡Nos alegra un montón que quieras compartir conocimiento con la comunidad!

---

## 📌 Criterios de Aceptación
Para mantener la calidad y el valor práctico del repositorio:
1. **Testeo previo:** Los prompts, skills o scripts deben haber sido testeados en proyectos o flujos reales (evitar volcados teóricos sin validar).
2. **Sin datos sensibles:** Asegurate de no incluir API keys, tokens privados, nombres de clientes confidenciales ni datos personales.
3. **Estructura clara:** Para la organizacion de nuestros repositorios, es importante que cada aporte cuente con una breve descripción de *Qué hace*, *Cuándo usarlo* y *Cómo implementarlo*.

---

## 🛠️ Flujo de Trabajo (Git Workflow)

1. **Forkear el repositorio:** Hacé clic en el botón `Fork` arriba a la derecha.
2. **Clonar tu fork:**
   ```bash
   git clone https://github.com/TU-USUARIO/awesome-human-cowork.git
   cd awesome-human-cowork
   ```
3. **Crear una rama para tu aporte:**
   ```bash
   git checkout -b aporte/mi-prompt-o-skill
   ```
4. **Agregar tu archivo:** Ubicalo en la carpeta correspondiente (`prompts/`, `skills/`, `automatizaciones/`, etc.).
5. **Hacer commit:**
   ```bash
   git commit -m "feat(prompts): agregar prompt de discovery comercial para agencias"
   ```
6. **Subir a tu fork y abrir Pull Request:**
   ```bash
   git push origin aporte/mi-prompt-o-skill
   ```
7. En GitHub, abrí un **Pull Request** hacia la rama `main` de `HumanCowork/awesome-human-cowork`. Una vez aprobado, se procederá a subirlo al main.
