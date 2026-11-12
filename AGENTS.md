# AGENTS.md · Guía del Repositorio Único (Páginas Eva · UEM)

## 1. Propósito del proyecto
Este repositorio (`evajimenezgarcia.github.io`) centraliza en un único sitio de GitHub Pages todos los informes web y subpáginas de **Eva** (`EvaJimenezGarcia`), de la **Facultad de Ciencias Jurídicas, Educación y Humanidades** de la **Universidad Europea de Madrid (UEM)**.

- **URL raíz:** `https://evajimenezgarcia.github.io/`
- **URL de cualquier subpágina:** `https://evajimenezgarcia.github.io/<ruta-de-carpetas>/`

> **Regla de oro:** El contenido académico, las cifras estadísticas, los textos analíticos y las referencias bibliográficas (APA) son responsabilidad de la autora y **no deben alterarse nunca**, salvo petición expresa. Toda intervención de diseño o maquetación debe limitarse estrictamente a la presentación visual, legibilidad, accesibilidad y coherencia estética.

---

## 2. Estructura de carpetas y publicación de subpáginas

```text
evajimenezgarcia.github.io/
├── .nojekyll               # Desactiva Jekyll en GitHub Pages
├── .gitignore              # Mantiene _borradores/ y respaldos fuera de Git
├── AGENTS.md               # Esta guía
├── index.html              # Portada / directorio principal del sitio
├── assets/
│   └── uem.css             # Hoja de estilos oficial compartida (única fuente de verdad)
├── _borradores/            # (Solo local) Documentos de trabajo, copias previas o notas
└── <area>/<subpagina>/     # Cada página vive en su propia carpeta con un index.html
    └── index.html
```

### Reglas al crear una nueva página o subpágina anidada
1. **Nombre de carpeta en `kebab-case`:** siempre en **minúsculas**, sin tildes, sin espacios y con guiones (ej. `publicaciones/2027/`, `ciie-ue/programa/`, `filiacion/`). GitHub Pages distingue mayúsculas de minúsculas.
2. **Archivo de entrada `index.html`:** cada página va dentro de su carpeta como `index.html` para tener URLs limpias sin `.html`.
3. **Ruta relativa al CSS compartido (`assets/uem.css`):** calcular el número de `../` según el nivel de profundidad para que funcione tanto en GitHub Pages como al abrir el archivo en local:
   - Nivel 1 (`filiacion/index.html`): `<link rel="stylesheet" href="../assets/uem.css">`
   - Nivel 2 (`publicaciones/2026/index.html`): `<link rel="stylesheet" href="../../assets/uem.css">`
   - Nivel 3 (`ciie-ue/ediciones/2026/index.html`): `<link rel="stylesheet" href="../../../assets/uem.css">`
4. **Recursos propios de una página:** si una página usa imágenes o datos propios, guardarlos dentro de su misma carpeta (ej. `area/pagina/imagenes/`) con rutas relativas simples (`imagenes/grafico.png`).
5. **Carpetas intermedias:** si se crea una subpágina anidada nueva (ej. `ciie-ue/2026/`), crear o actualizar el `index.html` de la carpeta padre (`ciie-ue/index.html`) si procede para evitar errores 404 al acortar la URL.
6. **Portada raíz (`index.html`):** añadir o actualizar el enlace en `index.html` solo si la autora desea que la página aparezca listada en el directorio principal.

---

## 3. Sistema de Diseño UEM (`assets/uem.css`)

Todas las páginas institucionales comparten **`assets/uem.css`**. No duplicar hojas de estilo dentro de las subcarpetas.

- **Tipografía:** `'Poppins', 'Segoe UI', Arial, sans-serif`. Cuerpo base a `16px`, interlineado `1.65`, tamaño mínimo absoluto `13px`.
- **Longitud de línea:** Textos de lectura corrida y conclusiones limitados a `72ch–75ch`.
- **Formato numérico:** Norma ortotipográfica del español (**coma decimal**: `34,9 %`, `47,8 %` y espacio antes del `%`). En KPIs (`.tile .n` / `.kpi-card .number`), `<span class="u">%</span>` o `<span class="unit">%</span>` va siempre dentro del elemento del número.
- **Paleta y contraste (WCAG AA):**
  - **Antracita (`#1E1E1E`):** cabeceras, cierres metodológicos, pestañas activas y texto principal.
  - **Rojo UEM (`#FF3228` / `#C81910` con texto blanco):** acento ($\le 10\%$) para el cuadrado del logo, cifra clave principal, serie destacada (`.bar.top`) y borde izquierdo del *callout*.
  - **Azul Real (`#2D41B4`):** series comparativas y enlaces.
  - **Cuartiles (`Q1–Q4` / `C1–C4`):** gama secuencial azul (`--color-q1` a `--color-q4`) y `--color-q-none` (`#E2E2E2`).
  - **Insignias (`.pill`, `.table-badge`):** texto antracita sobre fondo tintado suave con borde sutil.
- **Contenedores y accesibilidad:** usar `.section-open` para secciones agrupadoras (evitar «cajas dentro de cajas»), mostrar valores visibles en gráficos de barras apiladas, evitar scroll horizontal en `.uem-table`, y usar `<details class="foot">` plegado para el cierre metodológico.

---

## 4. Flujo de publicación
1. Crear o editar la carpeta correspondiente y revisar visualmente en escritorio (`1200px`) y móvil (`375px`).
2. Comprobar que todas las rutas a `assets/uem.css` y recursos locales cargan correctamente.
3. Hacer `git add`, `git commit` con mensaje claro en español y `git push origin main`.
