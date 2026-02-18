# Análisis del Design System — Contpaqi (Colabora app, móvil)

**Origen:** [Figma – Colabora-app](https://www.figma.com/design/8ub6DgvpRw7Fbp1NMDNN0l/Colabora-app?node-id=1-4)  
**Alcance:** Design system para aplicaciones móviles Contpaqi (node-id 1-4).  
**Fecha de análisis:** Febrero 2025.

---

## 1. Design tokens detectados

### 1.1 Color

#### Marca (Contabilidad / no comerciales)
| Token / Uso | Valor | Notas |
|-------------|--------|--------|
| Primary | `#003A70` | PCP001, Contabilidad, no comerciales |
| Primary sombra | `#002E5A` | PCPS002L, PCP002S |
| Secondary | `#005EB8` | PCS001, Contabilidad, no comerciales |
| Secondary sombra | `#004B93` | PCSS002L |
| Matices primary | `#33618D`, `#99B0C6`, `#CCD8E2` | PCPM002L, PCP004M, disable |
| Matices secondary | `#337EC6`, `#99BFE3`, `#CCDFF1` | PCSM002L–PCSM005L |
| Inline | `#00C0F3` | PCL001L |
| Inline matices | `#CCF2FF` | PCLM005L |

#### Texto
| Token / Uso | Valor | Contexto |
|-------------|--------|----------|
| Primary text | `#101010` | Text light, Contables light |
| Secondary text | `#757575` | Text light, Comercial |
| Divider text | `#F0F0F0` | Text light, Alerts |
| White / icon on color | `#FFFFFF` | Icon, botones, surface |
| Dark grey | `#414141` | Text Light Theme |
| Black | `#000000` | Text Light Theme |
| Secondary (label) | `#35353a` | Neutral |
| Gray-900 | `#1A1F36` | Gray palette |
| Universal 50% Gray | `#797B86` | [day]/Text: `#0E0E0F` |

#### Alertas / estados semánticos
| Semántica | Base | Matices / sombras |
|-----------|------|-------------------|
| **Success** | `#3EC161` (S001L) | `#65CD81`, `#B2E6C0`, `#D8F3DF`, `#E0FBCC`, `#329A4E`, `#25743A` |
| **Danger** | `#FF6666` (D001/D001L) | `#FF5969`, `#FFDDE0`, `#CC5252` |
| **Warning** | `#FFDD66` (W001L), `#F19E0F` (500) | `#FFE485`, `#F7BE28`, `#FDF2C8` |
| **Info** | `#3D91F4` (500), `#BCC7FF` (alert) | `#DBEDFE`, `#E4E9FF`, `#F2F4FF`, `#2773E9`, `#1F5ED6` |

#### Fondos y superficies
| Uso | Valor |
|-----|--------|
| Card / [day] Card | `#FFFFFF` |
| System Background Primary | `#FFFFFF` |
| System Background Secondary | `#F2F2F7` |
| Neutral 100 | `#ececed` |

#### Otros
- **Separator:** `#3C3C43` (con transparencia).
- **System Blue (iOS):** `#007AFF`.
- **Label:** Primary `#000000`, Secondary `#3C3C43`.
- Paleta Gray: Gray10 `#FFFFFF`, Gray50 `#C2C2C2`.
- Colores de avatar/skin/hair (ej. `#C2837B`, `#AC7080`, etc.).

---

### 1.2 Tipografía

#### Fuentes
- **Karla** (principal): títulos, botones, párrafos, tooltips, placeholder.
- **SF Pro Text** (puntual): solo en `Caption2` (Default).

#### Estilos documentados en variables

| Estilo | Familia | Peso | Tamaño | Line height | Letter spacing |
|--------|---------|------|--------|-------------|----------------|
| Button | Karla | Bold (700) | 16px | 20px | 0.1 |
| Tooltips (bold) | Karla | Bold (700) | 12px | 20px | 0.1 |
| Párrafos | Karla | Regular (400) | 14px | 100* | 0.25 |
| Textos nube / Párrafos | Karla | Regular (400) | 14px | 20px | 0.25 |
| Placeholder / Sidebar | Karla | Regular (400) | 16px | 100* | 0 |
| Button mobile | Karla | Bold (700) | 14px | 100* | 0 |
| Tooltips (regular) | Karla | Regular (400) | 12px | 100* | 0 |
| H3 - Subtítulo | Karla | Bold (700) | 24px | 100* | 0 |
| Caption2 (Default) | SF Pro Text | Regular (400) | 11px | 13px | 0.066 |

\* `100` en line height probablemente indica 100% o valor relativo; en código conviene fijar px o escala (ej. 1.2–1.5).

---

### 1.3 Sombras y elevación

#### Escala numérica (dp)
- **01 dp:** 2 sombras (offset Y 1–2px, radius 1–3px).
- **02 dp:** 3 sombras (Y 1–3px, radius 1–5px).
- **04 dp:** 3 sombras (Y 1–4px, radius 4–10px).
- **08 dp mobile:** 3 sombras hacia arriba (Y -8 a -3, radius 5–14px).

#### Elevation nombrada (Light)
- **Elevation 1–4:** progresión de drop shadows (blur y spread crecientes).
- **Linea:** inner shadow `#F5F5F5`, offset (0, -1).

#### Componentes
- **Cards:** sombras con tinte primary `#003A70` (opacidades ~12–24%).
- **View:** sombras blancas (opacidades ~14–26%).
- **Sidebar:** 2 capas (offset Y 1–2, radius 2–6, spread 0–2).

Colores de sombra: `#00000026`, `#0000004D`, `#5E5E5E33`, `#5E5E5E1F`, `#5E5E5E24`, `#003A7024`, `#003A7012`, etc.

---

### 1.4 Gradientes

- **Header / Gradiente linear:** `#005EB8` → `#003A70` (secondary → primary).
- Variables de gradiente "Contabilidad" / "Icon" aparecen como **string vacío** en las definiciones; en diseño real suelen ser linear gradient con los mismos colores de marca.

---

## 2. Componentes y patrones inferidos

A partir de los tokens se infieren estos usos típicos (no se pudo inspeccionar el canvas de Figma en detalle):

- **Botones:** Karla Bold 14–16px, colores primary/secondary, elevación baja.
- **Tipografía móvil:** Button mobile 14px Bold; párrafos 14px Regular (line height 20px en “Textos nube”).
- **Cards:** fondo blanco, sombra con tinte `#003A70`.
- **Alertas:** success, danger, warning, info con base + matices + sombras definidos.
- **Navegación / header:** gradiente linear Contpaqi.
- **Iconografía:** color blanco sobre fondos primary/secondary; token "Icon" vacío sugiere heredar de “White icon”.
- **Tema claro:** Text light, Contabilidad Light, Alertas Light, Elevation Light; fondo sistema blanco/gris muy claro.

---

## 3. Inconsistencias detectadas

### 3.1 Nomenclatura y convenciones

1. **Idioma mezclado:**  
   - "Contabilidad **Light**" vs "**Alertas** Light" vs "**Alerts** Light/Dark".  
   - "Primary" vs "**Primario**" (en texto), "Secondary" vs "**Secundary**" (typo recurrente).

2. **Duplicación de conceptos:**  
   - Mismo color primary con muchos nombres: `PCP001L`, `PCP001`, `Color Contabilidad/Primary`, `Color no comerciales/Primary`, `PNCP001L`, `Contables light/Primary - light/PCPL001`, etc.  
   - Igual con secondary, texto primario y texto secundario.

3. **Jerarquías de nombres desiguales:**  
   - "Contabilidad Light/Primary/...", "Contables light/...", "No comerciales light/...", "Color no comerciales/...".  
   - Dificulta saber cuál es la fuente de verdad (Contabilidad vs Contables vs Color Contabilidad).

4. **Typos:**  
   - "Secundary" en lugar de "Secondary".  
   - "Succes" en lugar de "Success" (ej. "Alertas Light/Succes/...").

### 3.2 Tipografía

5. **Line height ambiguo:**  
   - Valores `100` (Párrafos, Placeholder, Button mobile, H3, Tooltips) sin unidad.  
   - En otros casos 20px o 13px.  
   - Riesgo de interpretar 100 como 100px en implementación.

6. **Dos familias:**  
   - Karla en casi todo y SF Pro Text solo en Caption2.  
   - Falta criterio documentado: cuándo usar SF Pro (¿solo iOS nativo?).

7. **Escala móvil vs escritorio:**  
   - Button 16px vs "button mobile" 14px está bien, pero no hay escala clara (ej. escala 1.25 o tabla de tamaños por breakpoint).

### 3.3 Color

8. **Paletas paralelas:**  
   - "Contabilidad", "Contabilidad Light", "Contables light", "No comerciales light", "Color no comerciales", "Color Contabilidad", "Alerts/Alertas Light/Dark".  
   - Muchos tokens llevan al mismo hex; aumenta mantenimiento y riesgo de desvío.

9. **Gradientes vacíos:**  
   - "Linear gradient contabilidad", "Icon Gradient Contabilidad Light", "Contabilidad Light/Gradients/..." definidos como `""`.  
   - No hay valor reutilizable en código sin acordar fórmula (p. ej. linear 180deg #005EB8 → #003A70).

10. **Token "Icon" vacío:**  
    - No queda claro si es intencional (heredar de "White icon") o pendiente de definir.

### 3.4 Sombras y elevación

11. **Dos sistemas de elevación:**  
    - "01 dp", "02 dp", "04 dp", "08 dp mobile" (colores #5E5E5E).  
    - "Elevation Light 1–4" y "Linea" (colores #000000).  
    - Cards/view con tinte primary o blanco.  
    - Falta un mapa claro: qué nivel usar en qué componente (botón, card, modal, FAB).

12. **Nombres de efecto:**  
    - "cards" vs "card" vs "view" vs "sidebar" con valores ligeramente distintos.  
    - Conviene agrupar en una escala (e.g. elevation-1 a elevation-4) y que los componentes referencien esa escala.

### 3.5 Alcance y contexto

13. **Tokens de contexto mixto:**  
    - "[day]/Text", "[day]/Card", "Label Color/Light/...", "System Background/Light/...", "Default/SystemBlue/Light".  
    - Indican tema (light/day) y posiblemente plataforma (iOS).  
    - No está explícito si son solo referencia o parte del sistema móvil Contpaqi.

14. **Colores no comerciales vs comerciales:**  
    - "Color no comerciales" y "No comerciales light" vs "Comercial/Secondary Text", "Comercial/Divider".  
    - No está documentado cuándo usar cada rama (producto, app, white-label).

---

## 4. Recomendaciones para mitigar inconsistencias

### 4.1 Estructura y nomenclatura

- **Unificar idioma:** elegir inglés o español para nombres de tokens y mantenerlo en todo el file (recomendable inglés para código y variables).
- **Corregir typos:** "Secundary" → "Secondary", "Succes" → "Success" en nombres de variables y páginas.
- **Una sola jerarquía por concepto:**  
  - Ejemplo: `brand.primary`, `brand.secondary`, `text.primary`, `text.secondary`, `surface.card`, `elevation.1`–`elevation.4`.  
  - Agrupar referencias "Contabilidad", "Contables", "No comerciales" bajo esa estructura y deprecar alias duplicados.
- **Documentar en Figma:** una página "Design tokens" con una tabla (nombre, valor, uso) y reglas de cuándo usar cada rama (Contabilidad vs no comerciales vs comercial).

### 4.2 Tipografía

- **Definir unidad de line height:** si "100" es 100%, documentarlo y en código mapear a `1` o `1.0`; si es 100px, usar `100px` y reservarlo para casos excepcionales.
- **Publicar escala tipográfica:** tabla con rol (caption, body, button, subtitle, title), familia, tamaño, line height y letter spacing para móvil (y opcionalmente escritorio).
- **Criterio SF Pro vs Karla:** documentar que SF Pro se usa solo para componentes nativos iOS (ej. Caption2) y Karla para el resto del UI Contpaqi.

### 4.3 Color

- **Reducir paletas a una base:**  
  - `brand.primary`, `brand.secondary`, y matices/sombras derivados (ej. `brand.primary.shade`, `brand.secondary.tint`).  
  - Temas "Contabilidad" / "no comerciales" como alias o modo, no como duplicados de hex.
- **Completar gradientes:** rellenar las variables de gradiente con el valor real (p. ej. `linear-gradient(180deg, #005EB8 0%, #003A70 100%)`) y un token único (ej. `gradient.brand.header`).
- **Definir token "Icon":** si es "icon on primary/secondary", fijar `#FFFFFF` y documentarlo; si hay más casos, añadir `icon.default`, `icon.muted`, etc.

### 4.4 Elevación y sombras

- **Una escala de elevación:**  
  - Definir 4–5 niveles (e.g. `elevation.0`–`elevation.4`) con valores únicos (blur, spread, opacidad).  
  - Asignar "01 dp", "02 dp", "Elevation 1–4", "card", "view", "sidebar" a esos niveles y dejar de crear sombras ad hoc con nombres de componente.
- **Documentar uso por componente:** tabla "Componente → nivel de elevación" (ej. botón: 0, card: 2, modal: 4, FAB: 4).

### 4.5 Implementación y mantenimiento

- **Exportar tokens a código:** usar Plugin (Tokens Studio o similar) o script para generar JSON/CSS/SCSS/JS desde las variables de Figma y consumir en app móvil (React Native, Flutter, etc.).
- **Design tokens en repo:** guardar la fuente de verdad en repo (JSON/YAML) y, si aplica, sincronizar con Figma en lugar de mantener dos fuentes manuales.
- **Changelog de design system:** ante cambios de color o tipografía, actualizar una sola vez la escala y reflejarlo en variables y en la doc.

---

## 5. Resumen

- **Fortalezas:** paleta de marca clara (primary/secondary Contpaqi), alertas semánticas completas, uso de variables en Figma y escalas de elevación y tipografía móvil (button, párrafos).
- **Debilidades:** nomenclatura inconsistente (idioma, typos, muchas alias para el mismo valor), line height sin unidad, gradientes y algún token vacío, y dos sistemas de elevación sin mapeo claro a componentes.

Aplicando las recomendaciones anteriores se consigue un design system más fácil de mantener, de documentar y de implementar en las aplicaciones móviles Contpaqi.
