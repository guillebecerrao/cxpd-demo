# Skill: Generar Presentación HTML

## Cuándo usar este skill

Cuando el equipo necesita comunicar un artefacto estratégico a stakeholders de forma visual y ejecutiva. El LLM genera un HTML con gráficas y estilos limpios a partir de un documento `.md`.

**Activación:** El usuario dice algo como "genera el HTML del OST", "quiero presentar el roadmap", "crea la presentación del backlog".

**Importante:** El LLM siempre pregunta al usuario antes de generar, incluso si el `.md` acaba de ser editado. El usuario puede tener más cambios pendientes antes de llegar a una versión comunicable.

---

## Artefactos elegibles (lista no exhaustiva)

| Artefacto | Archivo fuente | Tipo de visualización |
|---|---|---|
| OST | `contexto/estrategia/ost.md` | Árbol jerárquico con camino elegido destacado |
| Roadmap Discovery Shape | `contexto/estrategia/roadmap-discovery-shape.md` | Timeline / tabla con estados |
| Roadmap Discovery I&V | `contexto/estrategia/roadmap-discovery-ideate-validate.md` | Timeline / tabla con estados |
| Roadmap Delivery | `contexto/estrategia/roadmap-delivery.md` | Timeline por releases |
| Backlog | `contexto/estrategia/backlog.md` | Tabla priorizada |
| Épicas | `contexto/estrategia/epicas.md` | Cards o tabla agrupada |
| Release Plan | `handoff-delivery/release-plan.md` | Timeline con PBIs por release |
| Análisis de oportunidades | `shape/analisis-oportunidades.md` | Cards o tabla con evidencia |
| Sizing y priorización | `shape/oportunidades-sizing-priorizacion.md` | Tabla con ranking y criterios |
| Cualquier otro artefacto indicado por el usuario | — | Tabla o visualización apropiada |

---

## Proceso

### Paso 0 — Chequeo de sync-log

Antes de comenzar, leer `presentaciones/_sync-log.md` y contar las entradas con **Propagado: ❌ No**.

- **0 entradas pendientes**: continuar sin comentar.
- **1-2 entradas pendientes y recientes (menos de 2 semanas)**: continuar sin comentar.
- **3+ entradas pendientes, o cualquier entrada con más de 2 semanas sin propagar**: informar al usuario:
  > "Hay [N] cambios transversales en el sync-log sin propagar a Guilles-Universe. Cuando tengas un momento, ejecuta el procedimiento de sincronización de presentaciones."

  Continuar con la generación normalmente — no bloquear el trabajo.

### Paso 1 — Confirmar con el usuario

Antes de generar, preguntar:
> "¿Confirmás que la versión actual de [archivo] está lista para presentar, o tenés cambios pendientes?"

Solo proceder si el usuario confirma.

### Paso 2 — Leer el design system

Leer los siguientes archivos para aplicar la paleta, tipografía, spacing y componentes correctos:

- `contexto/design-system/DS-input-v1/tokens.md`
- `contexto/design-system/DS-input-v1/components.md`
- `contexto/design-system/DS-input-v1/brand.md` (si el artefacto requiere lineamientos de marca)

> **Nota:** Si en el futuro esta carpeta cambia de nombre o versión, buscar el `README.md` más reciente dentro de `contexto/design-system/` para identificar la ruta correcta.

### Paso 3 — Leer la configuración de presentaciones

Leer `presentaciones/_presentaciones-config.md` y extraer:

1. **Guías visuales del artefacto:** aplicar las guías registradas para el artefacto en cuestión.
   - Si hay guías: aplicarlas estrictamente.
   - Si no hay guías: generar con criterio propio basado en el design system, y al finalizar preguntar al usuario si quiere registrar alguna preferencia. Si el usuario indica preferencias, actualizar `presentaciones/_presentaciones-config.md` antes del cierre de sesión.

2. **Documentos permanentes:** guardar la lista completa para construir el footer en el Paso 6.

3. **Estado de idiomas del artefacto:** buscar el artefacto en la tabla de documentos permanentes y leer su columna `Estado idiomas`. Si el artefacto no está registrado, asumir `single_language`.

### Paso 4 — Verificar versión existente y gestionar History

Antes de generar, verificar si ya existe un HTML del mismo artefacto en `presentaciones/`.

> **Identificación del artefacto:** el "mismo artefacto" se determina por el nombre-base (ej. `ost`, `como-trabajamos`), no por la fecha exacta del nombre de archivo.

**Si no existe versión previa:** continuar sin preguntar.

**Si existe una versión previa:** resolver dos preguntas en un solo mensaje al usuario:

**a) Gestión de History:**
> "Ya existe una versión de [nombre-artefacto].html en presentaciones/. ¿Querés archivarla en History (reemplazando la anterior si hubiera) o descartarla?"
- **Archivar:** mover el archivo actual a `presentaciones/History/` (sobreescribiendo si ya hay uno con el mismo nombre). Luego guardar el nuevo en `presentaciones/`.
- **Descartar:** generar el nuevo directamente en `presentaciones/` sin mover nada a History.

**b) Pausa de traducciones (solo si `estado_idiomas` es `multi_language_enabled`):**
> "Este documento tiene traducciones habilitadas. ¿Querés pausarlas durante esta iteración para trabajar más rápido? Las podés reactivar cuando consolides la nueva versión."
- Si acepta: actualizar `estado_idiomas` a `multi_language_paused` en `_presentaciones-config.md` antes de continuar. Generar en `single_language`.
- Si no: generar con `multi_language_enabled` normalmente.

**Trigger de sugerencia de traducciones (al finalizar, si aplica):**
- Si el usuario eligió **Archivar** y el `estado_idiomas` es `single_language`: al terminar de guardar el nuevo HTML, agregar al final:
  > "La versión anterior fue archivada. ¿Querés activar traducciones (ES/EN/PT) para este artefacto? Solo toma una generación y quedará habilitado para futuras iteraciones."
  - Si acepta: actualizar estado a `multi_language_enabled` en config y regenerar el HTML con traducciones.
- Si el usuario eligió **Archivar** y el `estado_idiomas` es `multi_language_paused`: al terminar, agregar:
  > "Este documento tenía traducciones pausadas. ¿Querés reactivarlas ahora que consolidaste esta versión?"
  - Si acepta: actualizar estado a `multi_language_enabled` y regenerar con traducciones.

### Paso 5 — Leer el artefacto fuente

Leer el archivo `.md` completo para entender la estructura y el contenido a visualizar.

### Paso 6 — Generar el HTML

Crear el HTML según el `estado_idiomas` determinado en el Paso 3 (o actualizado en el Paso 4):

---

#### Rama A — `single_language` o `multi_language_paused`

Generar el HTML en el idioma base del artefacto (columna `Idioma base` en config; si no está registrado, usar `es`).

El HTML incluye:
- Estilos basados en el design system (Paso 2)
- Guías visuales del artefacto (Paso 3)
- Título y fecha de generación visibles
- Visualización apropiada al tipo de artefacto
- **Navegación al home**: link fijo en la esquina superior izquierda que lleva a `home.html` (ej. "← Inicio"). Estilo sutil, siempre visible. Si no existe `home.html` en `presentaciones/`, omitir.
- Pie de página con:
  - Referencia al archivo fuente
  - Sección "Documentos relacionados" con links relativos a los documentos permanentes registrados, excluyendo el propio y excluyendo `home.html`. Si el registro está vacío, omitir esta sección.
- Hiperlinks contextuales inline (opcional): cuando el contenido haga referencia explícita a otro documento permanente registrado, insertar un hipervínculo relativo (`./nombre-archivo.html`) donde sea natural.

---

#### Rama B — `multi_language_enabled`

Generar el HTML con las tres variantes de idioma embebidas. Arquitectura: **un solo archivo HTML** con todo el contenido traducido almacenado como objetos JavaScript.

**Estructura del sistema de idiomas:**

```javascript
const translations = {
  es: {
    // todos los textos visibles en español
  },
  en: {
    // todos los textos visibles en inglés
  },
  pt: {
    // todos los textos visibles en portugués
  }
};
```

**Auto-detección y switcher:**
- Al cargar el documento: detectar `navigator.language`, normalizar al código base (`es-AR` → `es`, `en-US` → `en`, `pt-BR` → `pt`). Si el idioma detectado no es `es`, `en` ni `pt`, usar `es` como fallback.
- Incluir un switcher visual `ES | EN | PT` en el header con el idioma activo destacado. El usuario puede sobreescribir la detección automática con este switcher.
- El cambio de idioma debe ser instantáneo (sin recarga de página).

**Traducciones a incluir:**
- Todo el contenido textual del artefacto
- Labels de UI (títulos de sección, encabezados de tabla, etiquetas de estado)
- Footer: "Documentos relacionados" y nombres de los documentos linkeados
- Fecha de generación: mantener en formato numérico universal (`YYYY-MM-DD`) para no necesitar traducción

**Advertencia al usuario al generar por primera vez con multi-language:**
> "HTML generado con traducciones en ES, EN y PT. Revisá los términos de dominio en las versiones en inglés y portugués — especialmente: [listar términos clave del artefacto, ej. 'Opportunity Solution Tree', 'touchpoint', 'squad', nombres propios del producto]."

---

### Paso 7 — Guardar en `presentaciones/`

Nombre del archivo según categoría del documento:

| Categoría | Formato | Ejemplo |
|---|---|---|
| **Referencia** (doc vivo, sin versión de ciclo) | `nombre.html` | `ost.html` |
| **Ciclo** (artefacto de un ciclo y sub-proceso específico) | `nombre_subproceso-cNN-YYYY.html` | `plan-discovery_shape-c01-2026.html` |
| **Cross-ciclo** (artefacto que abarca varios ciclos) | `nombre_cNN-YYYY.html` | `vision-global_c01-2026.html` |

El nombre del archivo es el mismo independientemente del estado de idiomas (el multi-language vive dentro del archivo, no en el nombre).

Si en el Paso 4 se decidió archivar, ejecutar primero el movimiento a History antes de guardar el nuevo archivo.

Después de guardar, verificar si el documento nuevo debe actualizarse en el registro de `presentaciones/_presentaciones-config.md`.

### Paso 8 — Evaluar y registrar en sync-log

Al finalizar la generación, evaluar si durante el proceso se realizó algún cambio **transversal** al patrón de presentaciones. Un cambio es transversal si afecta la arquitectura base que comparten todas las instancias del patrón:

- Nueva disposición transversal en `_presentaciones-config.md`
- Cambio en la convención de naming de archivos HTML
- Cambio en la lógica de History o versionado
- Cambio en la arquitectura de multi-idioma
- Fix a un bug en el patrón base

**No son transversales** (y no se registran):
- Guías visuales específicas de un artefacto (ej. "el OST se ve mejor con layout radial")
- Nuevos documentos permanentes en el registro
- Cambios de estado de idiomas de un artefacto

**Si hubo cambio transversal**: agregar una entrada en `presentaciones/_sync-log.md` con el formato documentado ahí. Marcar como `Propagado: ❌ No`.

**Si no hubo cambio transversal**: no hacer nada.

---

## Comportamiento especial para el OST

El HTML del OST debe renderizar el árbol **completo** (todas las ramas y nodos). No eliminar ni ocultar ninguna parte.

- Los nodos con `on_selected_path: true` en el `.md` se renderizan con **color/borde destacado** (ruta principal).
- El nodo con `selected: true` se renderiza con **resaltado especial** (nodo hoja elegido).
- El resto del árbol se renderiza en estado visual secundario (más tenue, escala de grises o color neutro).

En versiones multi-language, los labels de los nodos deben traducirse junto con el resto del contenido.

Objetivo: mostrar la decisión en contexto, evidenciando que hubo evaluación de alternativas y que la elección fue criterizada.

---

## Notas importantes

- Los HTMLs son artefactos **generados**. Nunca editarlos manualmente.
- Para actualizar un HTML, regenerarlo desde el `.md` con este skill.
- La carpeta `presentaciones/` es accesible directamente en GitLab. Stakeholders con acceso Guest pueden descargar o visualizar los HTMLs en el navegador.
- Un HTML multi-language es un solo archivo autónomo: no depende de archivos externos para las traducciones. Se puede compartir o abrir offline sin perder funcionalidad.
