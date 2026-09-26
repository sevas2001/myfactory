# Pipeline 3D sin Blender: Krea (TRELLIS 2) × LLM × Godot

Idea y flujo de trabajo para crear modelos 3D y mecánicas de juego en Godot directamente a partir de ilustraciones 2D, asistido por IA y sin requerir modelado manual en Blender.

---

## 📌 Reseña y Cita Original

> *"Opus5.5 × Krea × Godot Sin usar Blender, creación de modelos 3D a partir de ilustraciones*  
> *① Generación de ilustraciones con GPT Image*  
> *② Modelado 3D con TRELLIS 2 en «3D Objects» de Krea*  
> *③ Opus5.5 ajusta la posición del origen al pie para Godot, además de modificar el tamaño y la textura. Incluso se encargó del armado de huesos (rigging)*  
> *Codex (GPT Image), Krea y Godot se pueden integrar todos con Claude, por lo que la producción se completa solo con el chat de Claude.*  
> *Por cierto, no tenía la intención de hacer un juego de acción. Cuando envié la tercera instrucción, Claude creó un juego de acción por su cuenta [@krea_ai](https://x.com/krea_ai)"*

---

## 🔄 Desglose del Flujo (Workflow)

```
[Ilustración 2D] ──▶ [TRELLIS 2 / Krea] ──▶ [Modelo 3D (GLB)] ──▶ [Agente LLM / Scripts] ──▶ [Godot Engine]
 (GPT Image/Codex)      ("3D Objects")                             - Ajuste de pivote (al pie)  - CharacterBody3D
                                                                   - Escala y materiales        - Scripts GDScript
                                                                   - Rigging / Huesos           - Juego funcional
```

### 1. Generación de Ilustración Base (2D)
- Generación de arte conceptual con GPT Image (o similar: Midjourney, Scenario, Ideogram).
- Recomendación para 3D: personajes o props con vista frontal limpia, fondo neutral o aislado, y postura simétrica (tipo T-pose o A-pose).

### 2. Conversión 2D a 3D (TRELLIS 2 en Krea AI)
- Cargar la imagen generada en la función **«3D Objects»** de [Krea AI](https://www.krea.ai).
- Utiliza la arquitectura **TRELLIS 2** para generar mallas 3D volumétricas con texturas y geometría detallada.
- Exportación en formato estándar compatible con motores (`.glb` / `.gltf`).

### 3. Procesamiento y Rigging Asistido por el Agente (LLM)
El agente de IA (Claude / Opus / Gemini) procesa el archivo 3D mediante scripts automatizados (por ejemplo con `trimesh`, `pygltflib`, `scipy` o APIs de rigging):
- **Ajuste del punto de pivote (Origen):** Mover el origen (`(0, 0, 0)`) al punto de apoyo inferior (los pies del personaje) en lugar del centro geométrico, indispensable para el sistema de físicas y suelo de Godot.
- **Normalización de escala:** Ajustar las unidades métricas al estándar de Godot (1 unidad = 1 metro).
- **Optimización de texturas y materiales:** Corrección de propiedades PBR (albedo, roughness, metallic).
- **Armado de huesos (Rigging):** Incorporación de un esqueleto básico para habilitar animaciones futuras o deformaciones procedimentales.

### 4. Integración y Creación del Juego en Godot
- Importación directa del asset `.glb` en el proyecto de Godot.
- Creación automatizada de la escena del personaje (`CharacterBody3D`, `CollisionShape3D`, nodos de cámara).
- Generación de scripts en GDScript para:
  - Movimiento en 3D (gravedad, salto, aceleración).
  - Control de cámara en tercera persona o isométrica.
  - Mecánicas interactivas de juego.

---

## 🚀 Hoja de Ruta para convertirlo en Skill (`SKILL.md`)

Para formalizar este flujo como una **Skill** ejecutable en Antigravity:
1. **Script de ajuste de GLTF/GLB:** Crear un script en Python (`scripts/fix_origin_and_scale.py`) que tome el modelo exportado por Krea/TRELLIS y mueva automáticamente la caja delimitadora (bounding box) para que la base quede en `Y = 0`.
2. **Plantilla de escena Godot:** Generar un template `.tscn` preconfigurado con `CharacterBody3D` que cargue el `.glb`.
3. **Instrucciones en `SKILL.md`:** Runbook para guiar al agente paso a paso desde el prompt de imagen hasta la ejecución del juego en Godot.
