# fase1_analisis.md: Exploración y Deconstrucción de EcoHuerta

## 1. Mapa de Secciones e Interfaz

La interfaz de EcoHuerta guía al usuario de la información general a las acciones específicas de conversión.

| Sección | Función en la Interfaz |
| :--- | :--- |
| **Header** | Contiene el logo, la navegación principal y el control de **Modo Oscuro**. Provee acceso global y persistente. |
| **Hero** | Primera impresión. Contiene el mensaje clave y la Llamada a la Acción (CTA) principal, enfocando el valor central. |
| **Grid de Cultivos** | Muestra el contenido principal del sitio (productos/plantas) de forma visualmente organizada. |
| **Seasons** | Resalta contenido específico o promociones estacionales, destacando información relevante temporalmente. |
| **Testimonials** | Genera confianza y credibilidad mostrando la satisfacción de otros usuarios/clientes. |
| **CTA (Llamada a la Acción)** | Un bloque de diseño prominente para impulsar una acción específica de conversión. |
| **Suscripción** | Recopila correos electrónicos, convirtiendo visitantes pasivos en contactos para marketing posterior. |
| **Footer** | Contiene enlaces secundarios (legales, redes sociales) e información de contacto. |

## 2. Inventario de Tokens (@theme en Tailwind CSS)

Los tokens definidos establecen el sistema de diseño del proyecto, garantizando la **coherencia visual** y la **rapidez de desarrollo**.

### ### Análisis de Grupos de Variables

* **Colores (Color Palettes):**
    * **Propósito Semántico:** Colores tierra y verdes, asociados a la naturaleza y el crecimiento. Un color de acento brillante para los elementos interactivos (CTA).
    * **Propósito Visual:** Definen la personalidad de la marca y garantizan el contraste necesario para la legibilidad.
* **Tipografía (Fonts, Font Sizes):**
    * **Propósito Semántico:** Establece un tono moderno y accesible.
    * **Propósito Visual:** Los tamaños (ej., `text-5xl`) definen la jerarquía del contenido, haciendo que los títulos sean prominentes y el cuerpo legible.
* **Breakpoints (Screens):**
    * **Propósito Semántico/Técnico:** Establecen los puntos donde el diseño debe cambiar su *layout*.
    * **Propósito Visual:** Aseguran que la interfaz sea **responsive** y usable en cualquier dispositivo.

## 3. Utilidades Destacadas por Sección

Las utilidades contribuyen a la legibilidad, la consistencia y la accesibilidad de la interfaz.

| Sección | Utilidad Relevante | Aplicación/Función | Contribución |
| :--- | :--- | :--- | :--- |
| **Header** | `flex`, `justify-between`, `p-4`, `dark:bg-slate-800` | Manejo del *layout* para centrar el logo y navegación. Uso de *paddings* para espacio uniforme. | **Consistencia/Legibilidad:** Espaciado uniforme y fácil aplicación del cambio de color para el modo oscuro. |
| **Hero** | `text-4xl`, `md:text-6xl`, `max-w-3xl`, `mx-auto` | Tamaños de texto responsivos. Centrado horizontal del contenido. | **Accesibilidad/Legibilidad:** Clara jerarquía tipográfica. El límite de ancho (`max-w-3xl`) mejora la legibilidad en pantallas grandes. |
| **Testimonials**| `grid`, `lg:grid-cols-3`, `shadow-lg`, `rounded-xl` | Rejilla adaptable (de 1 columna a 3). Aplicación de sombra y borde redondeado a las tarjetas. | **Consistencia:** Las utilidades de sombra y borde dan un estilo uniforme a todas las tarjetas. **Legibilidad:** El *layout* de rejilla organiza el contenido eficientemente. |

## 4. Análisis del Dark Mode

El modo oscuro se implementa mediante la **estrategia de clase** de Tailwind (`.dark`), gestionada probablemente a través del estado de React (`useState`).

* **Implementación:** Requiere aplicar la clase `dark` al contenedor principal cuando se activa. El CSS utiliza prefijos (`dark:bg-color`) para las reglas que solo se aplican bajo esa clase.
* **Efectos Visuales:** Invierte la paleta: fondos claros pasan a oscuros (ej., `bg-gray-100` a `dark:bg-slate-900`) y el texto de oscuro a claro.
* **Ventajas de la Estrategia por Clase:**
    * **Control Explícito:** Permite al usuario **elegir** el modo, ignorando la preferencia del sistema operativo, ofreciendo mayor control.
    * **Fácil Integración:** Se integra de forma nativa con el sistema de utilidades de Tailwind y es simple de gestionar mediante el estado de la aplicación.

## 5. Componentes Reutilizables (@layer components)

| Componente (Ejemplo) | Ubicación de Aplicación | Coherencia Favorecida |
| :--- | :--- | :--- |
| **`.btn-primary`** | CTA del Hero, Botón de Suscripción, Botones del Footer. | Garantiza que todos los botones de acción principal (color, *padding*, *hover state*) luzcan idénticos en todo el sitio. |
| **`.card-base`** | Grid de Cultivos, Testimonials, Secciones de Seasons. | Aplica un estilo de contenedor consistente (sombra, borde redondeado, *padding* interno) a todos los bloques de contenido. |
| **`.input-text`** | Formulario de Contacto, Formulario de Suscripción. | Mantiene el mismo aspecto (borde, fuente, foco visible) en todos los campos de entrada de datos. |

## 6. Accesibilidad Visual

La accesibilidad es un pilar fundamental de la usabilidad del sitio.

| Aspecto Evaluado | Observación |
| :--- | :--- |
| **Contraste de Color** | Es necesario confirmar que la relación de contraste (texto/fondo) en ambos modos (claro y oscuro) cumpla con el estándar **WCAG 2.1 AA** (4.5:1). |
| **Jerarquía Tipográfica** | Correctamente definida por las utilidades de tamaño responsivas, estableciendo una estructura clara de títulos. |
| **Foco Visible (`Focus State`)** | Crucial para la navegación por teclado. Se requiere la aplicación consistente de utilidades como `focus:ring-2` o `focus:outline-none` en todos los elementos interactivos. |
| **Etiquetas/Atributos** | Debe verificarse el uso de etiquetas semánticas (`<header>`, `<nav>`, `<footer>`) y atributos **ARIA** (ej., `aria-label` en iconos). |

### ### Propuesta de Mejora de Accesibilidad

* **Implementar `focus:visible` globalmente:** Asegurar que todos los elementos interactivos (`<a>`, `<button>`, `<input>`) tengan un anillo de foco visible (`focus:ring-2` o similar) al ser tabulados, esencial para usuarios que navegan sin ratón.

## 7. Propuesta de Mejora Conceptual: Sección Blog/Recursos

### ### Idea: Sección Resources/Blog

* **Objetivo:** Posicionar a EcoHuerta como una autoridad en el tema. Aumentar el SEO y la permanencia del usuario en el sitio, proporcionando valor educativo.
* **Contenido:** Artículos sobre consejos de cultivo ("Cómo plantar tomates en maceta"), guías estacionales de jardinería y recetas.
* **Estructura Visual:**
    1.  **Header con Filtros:** Controles para filtrar por categoría (Vegetales, Herramientas, Recetas) utilizando *badges* definidos con `@layer components`.
    2.  **Grid de Tarjetas:** Usar la utilidad `grid-cols-3` (escritorio) para mostrar tarjetas de previsualización de artículos. Cada tarjeta (`card-base`) incluiría: imagen, título, fecha y un *badge* de categoría.
    3.  **Paginación:** Utilidades de `flex` y `justify-center` para centrar los controles de paginación.
