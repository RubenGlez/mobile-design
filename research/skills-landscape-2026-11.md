# Análisis del ecosistema de skills de diseño (noviembre 2026)

Investigación para la versión 1.0 de `mobile-design`. Cubre los pasos 1–3 del plan: exploración, extracción de patrones y curación. La sección 6 recoge la propuesta del paso 4, que fue aprobada y está aplicada en la v1.0.0 (con modos dentro de una única skill y `DESIGN.md` opcional; ver `CHANGELOG.md`).

**Decisión de alcance tomada por el propietario:** la skill pasa a ser **puramente de diseño (UX/UI) y agnóstica de stack**. iOS y Android se mantienen como *plataformas de diseño* (HIG y Material son lenguajes de diseño, no herramientas); React Native, Expo, SwiftUI, Compose y cualquier librería salen del contenido.

---

## 1. Método

**Fuentes.** Rankings por instalaciones (skills.sh, Skillselion, ClaudeSkills.info), comparativas publicadas (Composio, Snyk, Paralect, Medium y otros), el catálogo `podo/design-agent-skills` (más de 150 skills de diseño indexadas) y búsqueda directa en GitHub. Cada candidata se clonó y se leyó en su fuente original, no a partir de resúmenes.

**Criterios de selección:** adopción (instalaciones y estrellas), especificidad (descartadas las de tipo "haz que se vea bonito"), mantenimiento reciente y aportación diferencial respecto a lo que ya tenemos.

**Analizadas en profundidad (22):**

| # | Skill | Tipo | Licencia | Adopción aprox. |
|---|---|---|---|---|
| 1 | anthropics/frontend-design | Web, dirección estética | Propietaria (solo ideas) | ~1M instalaciones |
| 2 | Leonxlnx/taste-skill | Web, constructor de sitios | MIT | ~700k instalaciones (cifra declarada) |
| 3 | nextlevelbuilder/ui-ux-pro-max | Web y app, base de datos + script | MIT | ~30k instalaciones |
| 4 | pbakaus/impeccable | Web y nativo, multi-comando | Apache-2.0 | Top 5 en las comparativas |
| 5 | vercel-labs/web-interface-guidelines | Web, reglas + auditoría | MIT | Alta |
| 6 | Nutlope/hallmark | Web, anti-slop con gates | MIT | "Supera al baseline por mucho" |
| 7 | emilkowalski/skill (18 sub-skills) | Movimiento, gestos, Apple | Ver licencia | Alta |
| 8 | jakubkrehel/make-interfaces-feel-better | Pulido de detalle | — | Media |
| 9 | kylezantos/design-motion-principles | Movimiento, auditoría | — | Media |
| 10 | garrytan/gstack design-review | Auditoría → fix → verificar | MIT | Alta |
| 11 | ceorkm/mobile-app-ui-design | **Mobile** | — | ~520★ |
| 12 | dickwu/apple-design-skill | **Mobile/Apple**, revisión HIG | Ver repo | ~3k★ |
| 13 | ehmo/platform-design-skills | **Mobile**, más de 450 reglas HIG/M3/WCAG | MIT | Media |
| 14 | wshobson/agents ui-design (mobile-ios/android) | **Mobile** | MIT | Alta |
| 15 | awesome-skills/mobile-app-design | **Mobile** | — | Baja |
| 16 | sleekdotdesign design-mobile-apps | **Mobile**, conector a una API | — | — |
| 17 | content-designer/ux-writing-skill | Microcopy | MIT | Media |
| 18 | SidKH/dark-pattern-audit | Ética y patrones engañosos | — | Media |
| 19 | Owl-Listener/designer-skills (~80 micro-skills) | Leyes UX, estados, emoción | MIT | Media |
| 20 | podo/design-agent-skills | Catálogo de punteros | — | — |
| 21 | hamen/material-3-skill | Material 3 | — | Baja |
| 22 | RubenGlez/mobile-design (la nuestra, v0.3.0) | **Mobile** | MIT | Línea base |

**Nota de licencias.** Las ideas no tienen copyright y se pueden adaptar. No se copia texto literal de ninguna fuente. En el caso de `frontend-design` (licencia propietaria) solo se toman conceptos. Las fuentes con MIT o Apache se citarán en `source-map.md`.

---

## 2. Línea base: `mobile-design` v0.3.0

**Fortalezas que hay que conservar.** Design read en una línea, los tres dials (variance, motion, density), un proceso con preguntas mínimas, heurísticas por categoría, la sección de confianza, emoción y recuperación, el preflight de viabilidad, el enfoque adaptativo *window-first*, localización y RTL, IDs de reglas de revisión estables, evals con 15 casos y una calibración de sesgos ("bias correction").

**Debilidades detectadas:**

1. **Acoplamiento a framework.** 236 líneas de código RN, Compose y SwiftUI repartidas en 7 referencias, y unas 100 menciones a frameworks o librerías. Además, la historia del CHANGELOG muestra que **casi todos los bugs corregidos en las versiones 0.1–0.2 eran de APIs de framework** (`returnKeyType`, `accessibilityLiveRegion`, `createStaticNavigation`, `fontFamily` en Android…). Es la parte que más rápido caduca y la que más errores produce.
2. **No hay modos de trabajo.** Crear, criticar, pulir y endurecer se tratan con el mismo flujo. Las mejores skills (impeccable, gstack, design-motion-principles) separan los modos y cada uno tiene su propio playbook.
3. **Crítica poco estructurada.** Tiene IDs de reglas y severidad P1–P3, pero le faltan: primera impresión, veredicto de especificidad ("¿esto lo podría usar cualquier otra app?"), heurísticas puntuadas, personas, carga cognitiva, cobertura declarada, candidatos descartados y un veredicto final.
4. **El anti-slop se queda en una lista de ejemplos.** Hay una sola lista de "bias correction". No calibra los looks que hoy delatan una UI generada por IA, ni el slop de movimiento, ni el de copy, ni separa lo innegociable de lo "evitable con una razón".
5. **No hay guía de UX writing.** Hay alguna línea suelta ("Pay $42.18"), pero no patrones de errores, estados vacíos, permisos ni benchmarks de longitud.
6. **El movimiento se describe en términos de implementación** (presets de Reanimated con mass/stiffness) y no en términos de diseño: frecuencia, interrumpibilidad, traspaso de velocidad, causalidad de los hápticos.
7. **Falta integración con el sistema:** widgets, Live Activities, atajos, notificaciones, launch screen. Hoy solo se mencionan.
8. **No incluye un catálogo de patrones engañosos (dark patterns)** pese a tener una sección de confianza.
9. **No hay contexto persistente de diseño** (`DESIGN.md`), algo que tienen impeccable, hallmark y ui-ux-pro-max.

---

## 3. Fichas de las skills más influyentes

Solo se detallan las que aportan algo. Las notas de todas están en el apéndice.

### impeccable (Paul Bakaus): la mejor arquitectura del grupo
- **Una skill con más de 20 subcomandos** (`shape`, `critique`, `audit`, `polish`, `bolder`, `quieter`, `distill`, `harden`, `onboard`, `clarify`, `adapt`, `animate`, `typeset`, `layout`, `colorize`, `delight`…). Cada uno tiene un playbook propio que se carga bajo demanda, y algunos tienen variante nativa (`audit.native`, `adapt.native`).
- **Modos por superficie:** *Persuade / Operate / Read / Experience*. Una app es *Operate*: "el mundo visual presta solo tipografía, paleta, densidad y **un gesto distintivo**; nunca el layout, el modelo de navegación ni los controles".
- **Craft floor**, que se carga justo antes de editar. Tiene una lista *Verify* (contraste, profundidad con offset, espaciado, estados, copy) y una lista *Refuse* (son defaults, no prohibiciones, salvo excepciones marcadas). "Light o dark se elige por la escena de uso, no por la categoría."
- **Slop test nativo:** "¿Confiaría en esta app un usuario experto de iPhone, o dudaría ante controles fuera de especificación?". En iOS lo que delata es una app "portada desde una web"; en Android, "una app de iOS con piel de Android". Incluye una tabla para **traducir idiomas de plataforma** iOS↔Android y dos principios: *reconform, don't reflow* (web→nativo) y *restructure, don't stretch* (teléfono→tablet).
- **Crítica.** Empieza por el veredicto de especificidad, puntúa las 10 heurísticas de Nielsen de 0 a 4 ("la mayoría de UIs reales sacan 20–32/40"), aplica un checklist de carga cognitiva (≤4 opciones por decisión), revisa el viaje emocional (peak-end), usa severidad P0–P3 ("¿contactaría el usuario con soporte? Entonces es ≥P1") y 5 personas, entre ellas **Casey, la usuaria móvil distraída**. Elimina por norma las frases tipo "considera explorar…".
- **Shape:** entrevista de 2–3 preguntas por ronda que **afirma la lectura más probable** en vez de preguntar en abierto. El brief resultante recoge rangos de contenido (mínimo, típico, máximo).
- "*Refinement preserves; redesign replaces*": nunca se queda a medias entre las dos.

### hallmark (Nutlope): la mejor taxonomía de reglas
- Reglas en **tres niveles**: **Floor** (nunca se dispensa: corrección, acceso, honestidad), **Reflex** (un default del modelo que se puede dispensar *por escrito, con una razón específica de este diseño*; más de 3 dispensas = estilo de la casa, que va a `design.md`) y **Finish** (detalle de oficio que se responde pero no bloquea).
- **Preguntar una sola vez:** material, audiencia, uso y tono ("elige un extremo; 'limpio y moderno' no es un tono"). Si el usuario dice "adelante", se infiere y se declaran las inferencias en una línea.
- **Inventario de material:** real / imágenes / ausente. Nunca se inventan cifras, testimonios ni logos.
- **Test del espejo:** "¿Un encargo vecino de la misma categoría obtendría exactamente esta combinación? Si es así, cambia una decisión y di cuál."
- **Firma (signature).** En pantallas de app es "el objeto por el que se conoce la herramienta (el libro mayor, la timeline, la cola), no un saludo encima de cuatro tarjetas de stats".
- **Rama de pantallas de app:** "familiaridad ganada"; color contenido (el acento marca acción primaria, selección y estado); el modal es la última opción; **cada región con datos tiene 4 estados** ("dibujar solo el estado lleno es dibujar un cuarto de la pantalla"); el movimiento es estado, nunca decoración.
- **Picks block:** un único resumen de decisiones, que funciona como ventana de redirección para el usuario y se actualiza al final con el resultado ("un pass inventado es slop en sí mismo").
- **Eval harness:** briefs con bloque `expect`, un brazo baseline sin skill, juez de visión con 6 ejes y repetición.

### apple-design-skill (dickwu): la mejor guía de revisión para mobile
- **Los 8 principios de Apple (WWDC26)** como primer filtro, con una pregunta por principio: Purpose, Agency, Responsibility, Familiarity, Flexibility, Simplicity, Craft, Delight.
- **Cinco lentes en orden, con severidad por defecto:** accesibilidad (Critical), convenciones de plataforma (High), visual y oficio (High/Med), interacción (Med) y contenido (Med).
- **Resuelve la tensión entre "nativo" y "distintivo":** los componentes familiares llevan navegación y controles; la identidad vive en color, tipo, imágenes, voz y unos pocos momentos definitorios.
- **Modo mejora:** anclar en el tema → plan de tokens (4–6 colores con nombre, cada uno con variante light/dark y cifra de contraste, más wireframe ASCII compacto y regular) → criticar el plan → arreglos concretos con números → secuencia a11y → convenciones → oficio → pulido.
- **Reglas de trabajo:** números, no adjetivos (`#999→#595959, 7.0:1`); "un límite no es un hallazgo"; no sobre-criticar; no aplanar la personalidad.

### frontend-design (Anthropic): la mejor calibración anti-slop
- **Cinco clusters** que delatan diseño generado (crema + serif + terracota, negro + verde ácido, broadsheet, kit de SaaS con tarjetas idénticas, *chrome* de plantilla: eyebrows en mayúsculas, separadores con punto medio, flechas en botones). "Las palabras del brief siempre ganan."
- **Dos pasadas:** plan compacto, revisarlo contra el brief ("¿llegaría aquí con un encargo parecido?") y luego construir.
- **Gastar la audacia en un solo sitio.** "Quítate un accesorio antes de salir."
- **Escritura:** vocabulario del usuario, no del sistema; el CTA dice qué pasa; el mismo verbo durante todo el flujo (Publicar → Publicado); los errores no piden perdón y nunca son vagos; un estado vacío es una invitación a actuar.

### Emil Kowalski (apple-design, gestures): movimiento y gestos de nivel experto
- **Fluid interfaces (WWDC18):** responder en *touch-down*; seguimiento 1:1 respetando el punto de agarre; **interrumpibilidad como principio nº 1**; muelles definidos por *damping ratio + response*, no por duración; **traspaso de velocidad** al soltar; **proyección de momentum** para elegir el punto de anclaje; consistencia espacial (sale por donde entró, nace de su origen); *rubber-banding*; histéresis de ~10 pt; descartar por distancia **o** velocidad; rebote solo si el gesto tuvo inercia.
- **Valores de referencia de Apple:** reposicionar 1.0/0.4, rotación 0.8/0.4, cajón/sheet 0.8/0.3.
- **Feedback multimodal:** causalidad, armonía (todo en el mismo frame) y utilidad (reservar).
- **Reduce Motion** equivale a una alternativa suave, no a quitar el feedback. Reduce Transparency e Increase Contrast son señales independientes.
- **break-ui:** probar con datos del peor caso *plausibles* (nombres largos, de una letra, "1 miembros", 0 elementos, alemán, RTL, emoji). Nunca con basura del tipo "aaaa".

### gstack design-review: los mejores instrumentos de auditoría
- **Primera impresión:** "comunica X / noto Y / las 3 primeras cosas a las que va mi ojo (si no son las previstas, la jerarquía miente) / una palabra".
- **Trunk test:** dejado sin contexto, ¿sé qué app es, en qué pantalla estoy, cuáles son las secciones, qué opciones tengo, dónde estoy y cómo busco? 6 = PASS, 4–5 = PARTIAL, ≤3 = FAIL de impacto alto.
- **Reserva de goodwill** que se sigue a lo largo de un flujo. Empieza en 70/100. Restan la información oculta (−15), los interstitials o tours forzados (−15), castigar el formato (−10)… Suman las tareas principales obvias (+10), una recuperación elegante (+10)…
- **Dos notas:** Design A–F y AI-Slop A–F.

### Las demás, en una línea cada una
- **ui-ux-pro-max:** prioridad de categorías por impacto; disciplina de iconos (una familia, trazo uniforme, *outline* por defecto y *filled* para el estado activo); feedback de pulsación en 80–150 ms; una sola gesture primaria por región. Es la que menos supera al baseline según las comparativas.
- **taste-skill:** las *house rules* que ganan sobre todo; el catálogo de *copy tells* (palabras vetadas, frases de stock, cifras inventadas, titulares "X. Y.", marcos "no es X sino Y"), con la regla clave **"toda prohibición necesita al lado un movimiento positivo, o el modelo busca el sustituto más cercano"**.
- **web-interface-guidelines (Vercel):** loading con *show-delay* de 150–300 ms y mínimo visible de 300–500 ms; actualizaciones optimistas con rollback; "Renombrar…" con elipsis cuando abre otra entrada; no deshabilitar el submit antes de tiempo; no bloquear la escritura; skeletons que replican el contenido; ningún callejón sin salida; radios anidados concéntricos; las interacciones suben el contraste.
- **make-interfaces-feel-better:** radio concéntrico (exterior = interior + padding); alineación óptica; sombras para la elevación y bordes para la estructura; salidas más suaves que entradas; escala al pulsar de ~0,96. Su **formato de revisión** es el mejor: tabla de cobertura ("nunca insinúes que revisaste lo que no revisaste"), Before/After/Why, "considerado pero descartado" y veredicto Block / Needs changes / Approve.
- **design-motion-principles:** **frequency gate** (raro = expresivo, diario = sutil, cientos al día = nada) y **huellas de motion-slop**: indicadores que pulsan, blur en todas las entradas, stagger en todas las listas, muelles con rebote en acciones utilitarias.
- **ux-writing-skill:** fórmulas de error por tipo (inline, sistema, bloqueante, permiso); tres tipos de estado vacío; benchmarks (botones de 2–4 palabras, errores de 12–18, ≤8 palabras = 100 % de comprensión).
- **dark-pattern-audit:** 16 patrones con nombre de deceptive.design (confirmshaming, urgencia falsa, difícil de cancelar, preselección, *nagging*…), con confianza *likely* / *possible* y sin atribuir intención.
- **Owl-Listener:** de *interfaces-that-feel* sale el proceso "estado sentido → análogo físico → propiedad de comportamiento → capa (easing, retardo, tono)"; de *state-machine*, que cada estado tenga salida; además, las leyes de UX como herramientas de razonamiento con nombre.
- **ehmo/platform-design-skills:** más de 450 reglas numeradas con nivel de impacto y checklist de evaluación. Aporta contenido de integración con el sistema (widgets, Live Activities, atajos, Spotlight, interrupciones, launch screen = primera pantalla, onboarding ≤3 pantallas y saltable, no exigir cuenta si no hace falta).
- **ceorkm/mobile-app-ui-design:** las 3 preguntas iniciales; la regla peak-end (diseñar *un* pico y el final); personalización por etapa del usuario; búsqueda nunca en blanco; "etiquetas más grandes que los valores" como anti-patrón. Su capa visual (glow, inner shadows) cae en el slop.

---

## 4. Patrones transversales extraídos

### 4.1 Estructura de la skill
| Patrón | Dónde aparece | Valor |
|---|---|---|
| SKILL.md corto + referencias bajo demanda con tabla de enrutado | Casi todas las buenas | Ya lo tenemos |
| **Modos/comandos con playbook propio** | impeccable, motion-principles, gstack, hallmark | Alto |
| Fichero "floor" que se carga **justo antes de producir** | impeccable, hallmark | Alto |
| Variantes por plataforma de los playbooks | impeccable | Medio |
| Contexto persistente (`DESIGN.md` / `PRODUCT.md`) | impeccable, hallmark, ui-ux-pro-max | Alto para la adopción |
| Scripts deterministas (linters, gates) | taste, hallmark, impeccable, ui-ux-pro-max | Solo valen para web/código: no aplica a una skill agnóstica |
| Base de datos CSV + buscador | ui-ux-pro-max | Bajo (genérico, pesado) |

### 4.2 Proceso de diseño
1. **Anclar en el tema y el contexto** antes de lo visual (todas las buenas).
2. **Preguntar una vez, afirmando la lectura probable**; si no hay respuesta, inferir y declararlo.
3. **Inventario de material**: nunca inventar datos, testimonios ni cifras.
4. **Plan compacto antes de producir:** tokens, estructura, firma y movimiento.
5. **Criticar el plan** con el test del espejo o "¿mismo plan para otro producto?".
6. **Gastar la audacia en un solo sitio** y quitar un accesorio.
7. **Resumen de decisiones** visible, que se actualiza con el resultado real.

### 4.3 Reglas
- Tres niveles: **Floor / Reflex / Finish** (hallmark), con dispensa por escrito y razón específica.
- **Toda prohibición acompañada de su alternativa positiva** (taste).
- **Calibración explícita del slop actual** en lo visual, el movimiento y el copy, explicando *por qué* (los tells cambian con cada generación de modelos).
- Reglas con **números**, no adjetivos.

### 4.4 Revisión y crítica
- Orden fijo de lentes con severidad por defecto (apple-design).
- Primera impresión + especificidad *antes* de cualquier checklist (gstack, impeccable).
- Instrumentos: trunk test, goodwill, Nielsen 0–4, carga cognitiva, personas.
- Formato: cobertura declarada, Before/After/Why, descartes, veredicto, sin relleno, "un límite no es un hallazgo".

### 4.5 Verificación y evals
- "Mirar el resultado renderizado" en los tamaños reales, en lote.
- Evals con baseline sin skill; juez con ejes (Philosophy, Hierarchy, Execution, Specificity, Restraint, Variety).

---

## 5. Curación

**Rúbrica**, de 1 a 3 en cada eje: impacto en la calidad del resultado · encaje con una skill *agnóstica y mobile* · solapamiento con lo existente (invertido) · coste en contexto (invertido) · durabilidad. Entra lo que suma 11 o más sobre 15, o lo que cubre un hueco crítico.

### 5.1 Seleccionado (y su destino)

| # | Hallazgo | Fuente | Destino propuesto |
|---|---|---|---|
| S1 | Modos de trabajo: Shape · Design · Critique · Refine (polish/bolder/quieter/distill) · Harden · Adapt | impeccable, motion-principles | `SKILL.md` + playbooks |
| S2 | Taxonomía Floor / Reflex / Finish con dispensa por escrito | hallmark | `craft-floor.md` (nuevo) |
| S3 | "La familiaridad lleva la navegación y los controles; la identidad lleva color, tipo, imagen, voz y un momento distintivo" | impeccable, apple-design, hallmark | `SKILL.md`, `visual-system.md` |
| S4 | Firma = el objeto por el que se conoce la app | hallmark | `design-process.md` |
| S5 | Preguntar una vez, afirmando la lectura; inferir y declarar | hallmark, impeccable | `design-process.md` |
| S6 | Inventario de material; nunca inventar cifras ni testimonios | hallmark, taste | `design-process.md`, Floor |
| S7 | Plan compacto + crítica del plan (test del espejo) | frontend-design, hallmark, apple-design | `design-process.md` |
| S8 | Calibración del slop mobile (visual + movimiento + copy) con el porqué y su alternativa | frontend-design, motion-principles, taste, impeccable | `craft-floor.md` |
| S9 | Slop test nativo ("¿lo aceptaría un usuario experto?") + tells "web portada" e "iOS con piel de Android" | impeccable | `platform-*.md` |
| S10 | Tabla para traducir idiomas iOS↔Android; *restructure, don't stretch*; *reconform, don't reflow* | impeccable | `adaptivity-localization.md` |
| S11 | Los 8 principios de Apple como primer filtro | apple-design, Emil | `principles.md` (nuevo) |
| S12 | Leyes UX como herramientas (Fitts, Hick, Cowan ≤4, Jakob, Doherty, Tesler, peak-end, Zeigarnik) | Owl-Listener, impeccable | `principles.md` |
| S13 | Cuatro tipos de feedback; las 4 preguntas de wayfinding; trunk test | Emil/Apple, gstack | `navigation.md`, `critique.md` |
| S14 | Crítica: primera impresión → especificidad → 5 lentes → Nielsen 0–4 → carga cognitiva → personas (incluida Casey) → goodwill → P0–P3 | impeccable, apple-design, gstack | `critique.md` (sustituye a review-rules y review-checklists) |
| S15 | Formato de informe: cobertura, Before/After/Why, descartes, verificación, veredicto, sin relleno | make-interfaces-feel-better | `critique.md` |
| S16 | Movimiento como diseño: frequency gate, interrumpibilidad, traspaso de velocidad, proyección, muelles damping/response, entrada/salida asimétricas | Emil, motion-principles, Krehel | `motion-haptics.md` (reescrito) |
| S17 | Hápticos: causalidad, armonía, utilidad | Emil/Apple | `motion-haptics.md` |
| S18 | Reduce Motion / Reduce Transparency / Increase Contrast como señales separadas | Emil/Apple | `accessibility-touch.md` |
| S19 | UX writing: fórmulas por tipo de mensaje, estados vacíos, benchmarks, mismo verbo durante el flujo, vocabulario del usuario | ux-writing, frontend-design, Vercel | `ux-writing.md` (nuevo) |
| S20 | Diseño emocional: estado sentido → propiedad → capa; un pico + el final | interfaces-that-feel, ceorkm | `design-process.md` |
| S21 | Cada región con datos tiene 4 estados; cada estado tiene salida; pensar en máquinas de estado | hallmark, state-machine, Vercel | `states-edge-cases.md` (nuevo) |
| S22 | Catálogo de contenido del peor caso *plausible* (nombres, números, plurales, tiempo, colecciones) | break-ui | `states-edge-cases.md` |
| S23 | Loading: retardo de aparición + mínimo visible; optimista con rollback; skeleton = forma real | Vercel | `states-edge-cases.md` |
| S24 | Catálogo de los 16 dark patterns + la regla de "nunca fabricar urgencia" | dark-pattern-audit | `trust-ethics.md` (nuevo) |
| S25 | Integración con el sistema (widgets, Live Activities, atajos, notificaciones, interrupciones, launch screen) | ehmo | `platform-*.md`, `screen-patterns.md` |
| S26 | Detalle de oficio: radios concéntricos, alineación óptica, sombras vs bordes, texto secundario teñido en superficies de color, trazo del icono = peso del texto, outline/filled | Krehel, Vercel, impeccable | `visual-system.md` |
| S27 | Tipografía por tamaño: tracking negativo en grande y positivo en pequeño; interlineado inverso al tamaño; escala 1,125–1,2 en apps | Emil/Apple, hallmark | `typography-color.md` |
| S28 | Light/dark según la escena de uso, no según la categoría | impeccable, gstack | `visual-system.md` |
| S29 | Contexto persistente `DESIGN.md` opcional (se lee si existe; se ofrece crearlo) | impeccable, hallmark | `SKILL.md` |
| S30 | Números, no adjetivos; "un límite no es un hallazgo"; no sobre-criticar; no aplanar la personalidad | apple-design | `critique.md` |
| S31 | Evals con baseline sin skill y ejes de juicio | hallmark | `evals/` |

### 5.2 Descartado (y por qué)

| Hallazgo | Fuente | Motivo |
|---|---|---|
| Scripts y linters (sloplint, detector, gate hooks) | hallmark, taste, impeccable | Inspeccionan CSS o DOM. Contradicen la decisión agnóstica y añaden dependencias. Su *idea* (los gates) se conserva en el Floor. |
| Base de datos CSV de estilos, paletas y fuentes + buscador | ui-ux-pro-max | Lleva a resultados genéricos (según las comparativas, apenas supera al baseline), tiene un coste de mantenimiento alto y es web-céntrica. |
| Reparto de temas aleatorios y log de rotación | hallmark | Pensado para landings. En apps, la identidad viene del producto y no se reparte al azar. |
| Reglas de landing (hero, fold, secciones por pantalla, fotos de stock) | taste, hallmark, gstack | Son de modo *Persuade*. La skill es de apps (*Operate*). Como mucho, una nota para las pantallas de marketing dentro de la app (paywall, onboarding). |
| HIG completo copiado (123 páginas) | apple-design-skill | Peso enorme y caducidad. Lo sustituye el enlace a la fuente con la instrucción "verifica antes de citar". |
| Más de 450 reglas con código SwiftUI/Compose | ehmo | Acoplamiento a framework. Solo se extrae el contenido de diseño. |
| Personas por nombre de diseñador (Emil / Jakub / Jhey) | motion-principles | Atribuir criterios a personas reales es frágil. Se conserva la idea de *ponderar por contexto* sin nombres. |
| Valores CSS exactos (blur 4 px, `scale(0.96)` obligatorio, *font smoothing*) | Krehel, Vercel | Son de implementación web. Se traducen a principios (presión sutil y proporcional) sin valores de librería. |
| Recomendaciones de dogma ("nunca hamburguesa", "Inter prohibida") | ehmo, gstack | Absolutos sin contexto. Se reformulan como Reflex con razón. |
| Glow, inner shadows, glassmorphism como "polish" | ceorkm | Son precisamente los tells del slop. |
| Mensaje inicial "I'm ready…" sin hacer nada | Emil | Fricción gratuita. |
| Telemetría, preámbulos y *question tuning* | gstack | Infraestructura propia de su ecosistema. |
| Conector a una API de pago | sleek | No es una guía de diseño. |

---

## 6. Propuesta para el paso 4: `mobile-design` v1.0.0 (agnóstica)

**Es un cambio incompatible:** deja de dar código de implementación. Por eso sube a 1.0.0.

### 6.1 Rol y promesa
"Diseñador de producto mobile sénior. Produce decisiones de diseño (flujos, estructura, especificaciones, sistemas y críticas) en unidades y roles neutrales (pt/dp, roles de color, estados), válidas para cualquier stack. Si el usuario está implementando, traduce el vocabulario a su stack, pero sin prescribir librerías ni APIs."

### 6.2 Mapa de ficheros

| Fichero | Acción | Contenido |
|---|---|---|
| `SKILL.md` | Reescribir | Rol; modos; bucle operativo; postura de plataforma (S3); dials; resumen del Floor; enrutado; contrato de salida; `DESIGN.md` opcional |
| `references/design-process.md` | Reescribir | Contexto, design read + tesis, preguntar una vez, inventario de material, heurísticas por categoría, plan compacto, test del espejo, firma, diseño emocional, dials |
| `references/principles.md` | **Nuevo** | 8 principios de Apple como filtro; leyes UX como herramientas; 4 tipos de feedback; wayfinding |
| `references/craft-floor.md` | **Nuevo** | Floor / Reflex / Finish; calibración del slop mobile (visual, movimiento y copy) con alternativas |
| `references/critique.md` | **Nuevo** (sustituye a `review-rules.md` y `review-checklists.md`) | Flujo de crítica, instrumentos, severidad, formato de informe, reglas MD-### conservadas |
| `references/screen-patterns.md` | Actualizar | Firma por tipo de pantalla, búsqueda, seguimiento de estado, ajustes, paywall/onboarding |
| `references/states-edge-cases.md` | **Nuevo** (absorbe `feasibility-risk.md`) | Los 4 estados, máquinas de estado, catálogo del peor caso, loading/optimista, offline, permisos, interrupciones |
| `references/navigation.md` | Reescribir agnóstico | Wayfinding, selección de patrón, tabs = secciones, modalidad como último recurso, back, restauración de estado, deep links como requisito de diseño |
| `references/forms.md` | Reescribir agnóstico | Intenciones de entrada (teclado, autofill, OTP) descritas sin props, capas de validación, envío, checkout y auth |
| `references/ux-writing.md` | **Nuevo** | Voz y tono, fórmulas, estados vacíos, benchmarks, *copy tells* |
| `references/visual-system.md` | Actualizar | Detalle de oficio (S26), light/dark por escena, iconos, radios, superficies |
| `references/typography-color.md` | Reescribir agnóstico | Escalas, tracking e interlineado, roles, contraste (APCA como complemento), escalado de texto |
| `references/motion-haptics.md` | Reescribir | Propósito, frequency gate, fluidez, muelles en damping/response, gestos, hápticos, slop de movimiento |
| `references/accessibility-touch.md` | Reescribir agnóstico | Objetivos táctiles, affordance, pulgar, gestos, lector de pantalla (conceptos), preferencias del sistema |
| `references/adaptivity-localization.md` | Actualizar | + traducción de idiomas, *restructure / reconform* |
| `references/platform-ios.md` / `platform-android.md` | Reescribir agnóstico | Slop test, convenciones, integración con el sistema, QA |
| `references/trust-ethics.md` | **Nuevo** | Momentos de confianza (de design-process), 16 dark patterns y su alternativa honesta, permisos y privacidad |
| `references/source-map.md` | Actualizar | HIG, M3, WCAG/APCA, NN/g, deceptive.design + atribución de las skills fuente; sin RN/Expo |
| `references/react-native-implementation.md` | **Eliminar** | — |
| `references/feasibility-risk.md` | Fusionar | → `states-edge-cases.md` |
| `evals/cases.md` | Reescribir | Casos agnósticos + nuevos (especificidad, trunk test, microcopy, rechazo de dark pattern, frecuencia de movimiento, peor caso, traducción de plataforma, brief escaso) + protocolo con baseline |
| `README.md`, `CHANGELOG.md`, `metadata.version` | Actualizar | 1.0.0 |

### 6.3 Riesgos
- **Pérdida de usuarios que querían código RN.** Se mitiga porque la skill sigue activándose en tareas de implementación y aporta las especificaciones. El README lo explicará.
- **Que crezca de más.** Presupuesto: `SKILL.md` ≤ 180 líneas; ninguna referencia por encima de ~220; cada tarea carga 2–4 ficheros.
- **Caducidad de la plataforma** (Liquid Glass, M3 Expressive). La regla "verifica en la fuente antes de citar" se mantiene.

---

## Apéndice: notas de lectura

Las notas brutas de cada skill (valores, citas parafraseadas, estructura) se usaron como base de este informe y no se versionan, por el volumen que tienen. Para re-auditar una fuente, el comando de clonación aparece en la tabla de la sección 1 (`github.com/<owner>/<repo>`).
