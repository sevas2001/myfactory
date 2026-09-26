# myfactory 🏭

Repositorio central y "fábrica" de recursos para **skills**, **agentes autónomos**, **pipelines de desarrollo** y configuraciones para **Antigravity** y asistentes de inteligencia artificial.

---

## 🎯 ¿Qué es y para qué sirve?

### ¿Qué es?
`myfactory` es un centro de comando e incubadora de herramientas donde se almacenan y versionan las habilidades especializadas (skills), agentes y flujos de trabajo que potencian el desarrollo asistido por IA, especialmente enfocado en:
- Creación de videojuegos (Game Development).
- Modelado, rigging y texturizado 3D automatizado.
- Generación y edición multimedia (imágenes, video, audio, sprites y storyboards).
- Integración de herramientas externas y motores como **Godot**, **Blender** y plataformas de IA (**Scenario**, **Krea**, **TRELLIS 2**).

### ¿Para qué sirve?
1. **Acelerar el desarrollo con IA:** En lugar de configurar o indicarle a un agente cómo realizar una tarea técnica desde cero, las *skills* le proporcionan procedimientos paso a paso, validaciones y scripts de ejecución inmediata.
2. **Centralizar y reutilizar conocimiento:** Permite mantener en un solo lugar todas las habilidades que vas creando o importando de la comunidad, listas para integrarse en cualquier proyecto futuro.
3. **Automatizar pipelines complejos sin herramientas tradicionales:** Facilitar flujos donde la IA genera arte conceptual 2D, lo transforma en modelos 3D con físicas y los programa directamente en motores como Godot, sin requerir intervención manual en software de modelado tradicional.
4. **Laboratorio de ideas y arquitectura (Incubadora):** Espacio para documentar recetas, experimentos y técnicas avanzadas antes de convertirlas formalmente en código ejecutable o skills empaquetadas.

---

## 📂 Estructura del Repositorio

| Carpeta / Archivo | Propósito y Contenido |
| :--- | :--- |
| **[`skills/`](skills/)** | Skills nativas y personalizadas del repositorio. |
| ↳ [`pixel-art-wizard`](skills/pixel-art-wizard/SKILL.md) | Generación procedural de un mago pixel art animado lanzando un hechizo en Canvas 2D (HTML autocontenido, sin librerías). Incluye [`example.html`](skills/pixel-art-wizard/example.html). |
| **[`scenario-skills/`](scenario-skills/)** | Más de 60 skills y agentes enfocados en flujos creativos con IA: generación de texturas, sprites, skyboxes, audio, videos, análisis de modelos y automatizaciones de Scenario. (*Fuente: [scenario-labs/skills](https://github.com/scenario-labs/skills)*) |
| **[`blender-game-skills/`](blender-game-skills/)** | Skills y scripts de Python para procesamiento 3D profesional: conversión de imagen a 3D, horneado de mapas de texturas (baking), rigging, exportación optimizada para motores de juegos y control de calidad. (*Fuente: [majidmanzarpour/blender-game-skills](https://github.com/majidmanzarpour/blender-game-skills)*) |
| **[`sprite-gen/`](sprite-gen/)** | Skill y suite completa para generación de sprites de videojuegos, hojas de sprites (atlases), animación cíclica, videos en bucle, cambio de paletas (palette swap) y exportación para motores usando GPT / Grok. (*Fuente: [aldegad/sprite-gen](https://github.com/aldegad/sprite-gen)*) |
| **[`ideas/`](ideas/)** | Documentación de arquitecturas, experimentos y flujos de trabajo emergentes. Incluye guías conceptuales y recetas para futuras skills. |
| ↳ [`pipeline-krea-trellis-godot.md`](ideas/pipeline-krea-trellis-godot.md) | Flujo paso a paso para crear personajes y juegos 3D en Godot a partir de ilustraciones 2D usando Krea (TRELLIS 2) y agentes LLM sin pasar por Blender. |

---

## 🛠️ ¿Cómo se usan estas Skills?

Las skills siguen el estándar de Antigravity:
1. Cada skill cuenta con un archivo principal `SKILL.md` con metadatos descriptivos (nombre y descripción) e instrucciones estructuradas para el agente.
2. Cuando el agente detecta que un problema o tarea coincide con una skill, lee el `SKILL.md` bajo demanda (revelación progresiva) y ejecuta los scripts o runbooks contenidos en la carpeta correspondiente.
3. Puedes copiar cualquiera de estas carpetas a la raíz de tus proyectos de juego o trabajo (o en `.agents/skills/`) para que el agente las aplique localmente.

---

## ➕ Cómo añadir nuevas habilidades o ideas

- **Para una nueva Skill:** Crea una carpeta dentro de `skills/<nombre-skill>/` con su respectivo archivo `SKILL.md` (con YAML frontmatter `name` y `description`) y subcarpetas como `scripts/` o `references/`.
- **Para una nueva Idea/Workflow:** Añade un nuevo archivo Markdown dentro de `ideas/` describiendo el concepto, herramientas necesarias y pasos del pipeline.
