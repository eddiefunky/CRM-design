# Instrucciones — Prototipo CRM WhatsApp (Colabora)

Documento de referencia para el prototipo móvil interactivo del CRM minimalista. Actualizado para usar el **MCP de Figma** como fuente de verdad visual.

---

## 1. Referencia visual (Figma MCP)

**Prioridad:** El estilo visual debe guiarse por **cómo se ven las pantallas reales** en Figma, no por los tokens del DS en abstracto. Usar el MCP de Figma para examinar los nodos de referencia.

### Pantallas de referencia Colabora-app

Revisar estas pantallas en Figma (vía MCP: `get_design_context` y `get_screenshot`) para extraer look & feel, headers, cards, botones, navegación y espaciado:

| Descripción | URL | Node ID |
|-------------|-----|---------|
| Referencia 1 | [Figma](https://www.figma.com/design/8ub6DgvpRw7Fbp1NMDNN0l/Colabora-app?node-id=1838-13067) | `1838:13067` |
| Referencia 2 | [Figma](https://www.figma.com/design/8ub6DgvpRw7Fbp1NMDNN0l/Colabora-app?node-id=1830-13117) | `1830:13117` |
| Referencia 3 | [Figma](https://www.figma.com/design/8ub6DgvpRw7Fbp1NMDNN0l/Colabora-app?node-id=3018-31083) | `3018:31083` |
| Referencia 4 | [Figma](https://www.figma.com/design/8ub6DgvpRw7Fbp1NMDNN0l/Colabora-app?node-id=6157-119021) | `6157:119021` |
| Referencia 5 | [Figma](https://www.figma.com/design/8ub6DgvpRw7Fbp1NMDNN0l/Colabora-app?node-id=1524-153431) | `1524:153431` |
| Referencia 6 | [Figma](https://www.figma.com/design/8ub6DgvpRw7Fbp1NMDNN0l/Colabora-app?node-id=1654-13222) | `1654:13222` |

**Hallazgos al examinar con MCP (actualizado):**

- **Headers:** Fondo **blanco** o azul **sólido** en modales. **No usar gradiente** en la barra superior.
- **Contenido:** Tarjetas blancas, bordes redondeados, sombra suave; botones azul sólido; barra inferior blanca con ítem activo en azul.
- No forzar el DS (p. ej. gradiente header) si las pantallas de referencia no lo usan.

**Design System (tokens):** [Colabora-app node-id 1-4](https://www.figma.com/design/8ub6DgvpRw7Fbp1NMDNN0l/Colabora-app?node-id=1-4) — usar como apoyo de colores y tipografía cuando no contradiga lo visto en las pantallas de referencia.

---

## 2. Producto y alcance

- **CRM minimalista** de “baja administración”, enfocado en **WhatsApp** (usuario único).
- **Sin** pantallas de inicio de sesión/registro.
- Un solo número de WhatsApp por negocio.
- Mensajería bidireccional (enviar + recibir) dentro de la app.
- Los nuevos chats entrantes **no** crean lead automático: el usuario debe tocar **“Convertir a Lead”**.
- **Inbox** organizado por **Estado**; **Pipeline** por **Etapas**.
- No incluir pantallas de permisos ni offline; sí variantes de **estado vacío**, **error** y **carga**.

---

## 3. Diseño visual y sistema

- **Look & feel:** Limpio, profesional y colaborativo. Paleta, tipografía y radios según Colabora, **validando con las pantallas de referencia vía MCP**.
- **Componentes:** Tarjetas, campos, botones y chips como en las pantallas de referencia.
- **Espaciado:** Cuadrícula y padding consistentes (ej. 16dp).
- **Iconos:** Set y estilo (grosor de trazo) según referencia.
- **Accesibilidad:** Contraste y chips con etiquetas de texto según referencia.

---

## 4. Navegación inferior (todas las pantallas)

- **Inbox** (S01)
- **Pipeline** (S04)
- **Hoy** (S05)
- **Reactivar** (S06)
- **Métricas** (S10)

**FAB “+”** abre **Agregar Lead** (S07).

---

## 5. Pantallas (IDs / nombres)

| ID | Nombre | Resumen |
|----|--------|--------|
| **S01** | Inbox de WhatsApp (Estado) | Encabezado “Inbox” + contadores. Pestañas: Nuevo / Necesita respuesta / Respondido / Convertido. Lista: contacto/teléfono, último mensaje, insignia no leído, chip de estado. Tocar fila → S02. Vacío: “No hay conversaciones aún.” |
| **S02** | Conversación de WhatsApp | Atrás → anterior. Chip de estado. Si convertido: “Ver Lead” (→ S08). Chat + compositor + Enviar. Plantillas → S09. Si no convertido: CTA “Convertir a Lead” → S03. |
| **S03** | Convertir a Lead (desde chat) | Formulario: Nombre del lead, teléfono pre-llenado, Qué necesita, Próxima acción, Fecha vencimiento (opcional), Ventana de cierre. CTA “Crear Lead” → S08. Cancelar → S02. |
| **S04** | Pipeline Kanban | Columnas: Nuevo / Calificado / Cotizado / Seguimiento / Ganado / Perdido. Tarjetas: nombre, fuente, chip vencimiento, chip ventana. Tocar tarjeta → S08. FAB “+” → S07. |
| **S05** | Hoy (Lista de atención) | Secciones: Vencido / Hoy / Próximamente. Acciones: Hecho (tachado), Posponer (selector fecha en hoja; Guardar actualiza S05), Abrir → S02 (si hay chat) o S08. |
| **S06** | Reactivar (Cola de inactividad) | Lista leads estancados + última actividad + “Elegir plantilla” → S09. Tocar lead → S08. “Editar umbrales” → S11. Vacío: “No hay leads estancados.” |
| **S07** | Agregar Lead (manual) | Campos: Nombre del lead*, Teléfono/WhatsApp, Fuente, Referido, Red social/Mensaje, Qué necesita, Próxima acción, Fecha vencimiento, Ventana de cierre. Crear Lead → S08. Cancelar → atrás. |
| **S08** | Detalle del Lead | Selector etapa (Nuevo…Ganado/Perdido), Ventana de cierre, Próxima acción + fecha, campos de info, “Abrir chat” → S02, Plantillas → S09, Guardar (toast “Guardado”), Marcar Ganado/Perdido. |
| **S09** | Plantillas | Lista de plantillas; al seleccionar se inserta en S02. Modo gestión: crear/editar. Validación: “Nombre de plantilla requerido.” Atrás → anterior. |
| **S10** | Métricas (Dashboard) | Cuadros de conteo por etapa, filas de antigüedad, indicadores semanales. CTA vacío: “Agregar lead” → S07. |
| **S11** | Ajustes de Umbrales | “Marcar lead como estancado tras [__] días” (validación: número > 0). Guardar (toast “Actualizado”). Atrás → S06. |

---

## 6. Variantes de estado

- **S01, S04, S05, S06, S07, S09, S10, S11:** Predeterminado, Vacío, Error, Carga.
- **S02, S03, S08:** Predeterminado, Error, Carga.

---

## 7. Validaciones

- **S07:** “El nombre del lead es requerido.”
- **S11:** “Ingresa un número mayor a 0.”

---

## 8. Entregable

- Pantallas en **HTML**, **sin dependencias externas**.
- **Un archivo HTML por pantalla** (S01–S11 + index).
- Estilo visual alineado con las **pantallas de referencia** revisadas vía **MCP de Figma** (headers blancos o azul sólido, sin gradiente en barra superior; tarjetas, botones y navegación como en Colabora).
