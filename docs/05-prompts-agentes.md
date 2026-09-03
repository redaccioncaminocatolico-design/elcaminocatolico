# Documento 05 — Prompts para Agentes de Antigravity
## El Camino Católico · elcaminocatolico.com

> Cada sección es un prompt listo para pegar en Antigravity.
> Usarlos en el orden indicado. Cada agente construye una parte del sitio.
> Los documentos 01, 02, 03 y 04 deben estar disponibles en el contexto
> del agente antes de ejecutar cada prompt.

---

## PROMPT 1 — Crear el repositorio y estructura base de Hugo

```
Eres un agente experto en Hugo y GitHub Pages. Tu tarea es crear la 
estructura completa de un sitio Hugo para un blog llamado "El Camino Católico".

Siguiendo EXACTAMENTE el Documento 02 (Arquitectura del Sitio), debes:

1. Crear un repositorio GitHub llamado "elcaminocatolico"
2. Inicializar un proyecto Hugo con la siguiente estructura:
   - config.toml con la configuración exacta del Documento 02, sección 6
   - Carpetas: content/articulos/, layouts/_default/, layouts/, static/css/
3. Crear el archivo .github/workflows/hugo.yml con el contenido exacto 
   del Documento 02, sección 8
4. Crear el archivo static/robots.txt con el contenido del Documento 03, sección 4
5. Habilitar GitHub Pages en el repositorio para que use la rama gh-pages

No uses ningún tema externo. Los layouts serán 100% propios.
No instales dependencias npm ni otros generadores.
Confirma cuando el repositorio esté creado y GitHub Actions esté configurado.
```

---

## PROMPT 2 — Construir los layouts HTML (baseof, homepage, artículo)

```
Eres un agente experto en Hugo templates y HTML/CSS.
Tenés acceso al Documento 01 (Diseño Visual) y al Documento 02 (Arquitectura).

Tu tarea es crear los archivos de layout de Hugo, implementando EXACTAMENTE 
el diseño visual definido en el Documento 01.

Archivos a crear:

**layouts/_default/baseof.html**
- Estructura HTML completa con <head> que incluya:
  - Todos los meta tags del Documento 03, sección 1
  - Schema markup del Documento 03, sección 2
  - Preconnect y link de Google Fonts (Playfair Display + Source Serif 4)
  - Link al archivo /css/main.css
  - Código condicional de Google Analytics (Documento 03, sección 8)
  - Código condicional de AdSense (Documento 03, sección 9.1)
- Header/Nav exactamente como el Documento 01, sección 4.1
- Footer exactamente como el Documento 01, sección 4.10
- Block "main" para el contenido específico de cada página

**layouts/index.html** (homepage)
- Extiende baseof.html
- Implementa EXACTAMENTE las secciones del Documento 02, sección 4.1:
  1. Hero con frase bíblica
  2. Artículo destacado (featured: true)
  3. Grid 2 columnas de últimos 6 artículos
  4. Pills de 7 categorías
- Estilos según Documento 01, secciones 4.2, 4.3, 4.4, 4.9

**layouts/_default/single.html** (artículo individual)
- Extiende baseof.html
- Implementa EXACTAMENTE las secciones del Documento 02, sección 4.2:
  1. Breadcrumb en el header
  2. Header del artículo (fondo azul)
  3. Párrafo intro en cursiva con borde dorado
  4. Cuerpo del artículo
  5. Bloque AdSense después del 3er párrafo (Documento 03, sección 9.2)
  6. Artículos relacionados de la misma categoría
- Breadcrumb con Schema markup (Documento 03, sección 10)

**layouts/_default/list.html** (categoría / listado)
- Extiende baseof.html
- Implementa las secciones del Documento 02, sección 4.3
- Grid 2 columnas con paginación de 10 artículos

**layouts/404.html**
- Página de error según Documento 02, sección 9

Reglas absolutas de diseño (del Documento 01, sección 9):
- NO usar fuentes sans-serif en el cuerpo
- NO usar sombras decorativas tipo box-shadow
- NO usar colores fuera de la paleta
- NO centrar el texto del cuerpo del artículo
- NO agregar animaciones de scroll

Confirma cuando todos los archivos estén creados.
```

---

## PROMPT 3 — Crear el CSS completo

```
Eres un agente experto en CSS. Tenés acceso al Documento 01 (Diseño Visual).

Tu tarea es crear el archivo static/css/main.css con los estilos completos 
del sitio "El Camino Católico".

El CSS debe implementar EXACTAMENTE todos los valores del Documento 01:
- Variables CSS para la paleta de colores (sección 2)
- Estilos de tipografía para cada elemento (sección 3)
- Estilos de cada componente (sección 4, subsecciones 4.1 a 4.10)
- Media queries para responsive mobile (sección 6)

Reglas técnicas:
- Usar variables CSS (:root) para todos los colores de la paleta
- Un solo archivo CSS, sin imports externos
- No usar frameworks (Bootstrap, Tailwind, etc.)
- CSS organizado en secciones con comentarios
- Cada sección del CSS debe corresponder a un componente del Documento 01

Estructura del archivo:
/* === VARIABLES === */
/* === RESET Y BASE === */
/* === TIPOGRAFÍA === */
/* === HEADER / NAV === */
/* === HERO === */
/* === CARDS === */
/* === ARTÍCULO DESTACADO === */
/* === CUERPO DE ARTÍCULO === */
/* === ADSENSE === */
/* === ARTÍCULOS RELACIONADOS === */
/* === CATEGORÍAS / PILLS === */
/* === FOOTER === */
/* === RESPONSIVE === */

Confirma cuando el archivo esté creado.
```

---

## PROMPT 4 — Publicar el primer artículo de prueba

```
Eres un agente experto en Hugo y Markdown.
Tenés acceso al Documento 04 (Plantilla de Artículo).

Tu tarea es crear el primer artículo del blog en el repositorio GitHub.

El archivo a crear es: content/articulos/por-que-se-reza-el-rosario.md

El contenido completo del artículo está en la PARTE B del Documento 04.
Copiá ese contenido exactamente, incluyendo el front matter completo.

Después de crear el archivo:
1. Verificá que el front matter tiene todos los campos requeridos
2. Verificá que el slug no tiene tildes ni caracteres especiales
3. Confirmá que GitHub Actions ejecutó el build correctamente
4. Reportá la URL donde quedó publicado el artículo

Confirma cuando el artículo esté publicado.
```

---

## PROMPT 5 — Verificación SEO técnica

```
Eres un agente experto en SEO técnico. Tenés acceso al Documento 03 (SEO Técnico).

Tu tarea es verificar que el sitio publicado cumple con TODOS los puntos 
del Documento 03. Revisá:

1. Meta tags en el <head> (sección 1): verificar title, description, 
   canonical, og:tags en homepage y en el artículo del Rosario
2. Schema markup (sección 2): verificar que existe y es válido
3. Sitemap (sección 3): verificar que existe en /sitemap.xml
4. Robots.txt (sección 4): verificar que existe y tiene el contenido correcto
5. Core Web Vitals (sección 6): verificar que no hay JS innecesario, 
   que las fuentes cargan con display=swap, que el CSS es un solo archivo
6. Breadcrumbs (sección 10): verificar que aparecen en el artículo 
   con el Schema markup correcto

Para cada punto: reportar ✓ si está correcto o ✗ si hay algo que corregir.
Si encontrás errores, corregalos directamente.

Confirma cuando el sitio pase todos los puntos del checklist.
```

---

## PROMPT 6 — Crear la página de política de privacidad

```
Eres un agente experto en HTML y requisitos de Google AdSense.

Tu tarea es crear la página de política de privacidad del sitio 
"El Camino Católico" (elcaminocatolico.com).

Crear el archivo: content/privacidad.md

El contenido debe:
- Cumplir con los requisitos de Google AdSense para sitios en español
- Mencionar explícitamente el uso de cookies de Google AdSense
- Mencionar Google Analytics
- Incluir información de contacto: contacto@elcaminocatolico.com
- Estar redactado en español neutro, sin lenguaje legal innecesariamente complejo
- Tener la fecha de última actualización

El front matter del archivo:
---
title: "Política de Privacidad"
slug: "privacidad"
descripcion: "Política de privacidad de El Camino Católico."
---

Confirma cuando la página esté creada y publicada.
```

---

## Orden de ejecución recomendado

```
Paso 1 → PROMPT 1  (estructura base + GitHub Actions)
Paso 2 → PROMPT 3  (CSS completo — antes que los layouts para tenerlo listo)
Paso 3 → PROMPT 2  (layouts HTML — usan el CSS ya creado)
Paso 4 → PROMPT 4  (primer artículo — para ver el diseño con contenido real)
Paso 5 → PROMPT 5  (verificación SEO — cuando el sitio esté online)
Paso 6 → PROMPT 6  (privacidad — necesaria antes de aplicar a AdSense)
```

---

## Notas para el propietario antes de ejecutar

Antes de usar estos prompts en Antigravity:
- Tener cuenta de GitHub creada
- Tener los 5 documentos de este proyecto cargados en el contexto del agente
- Después del Paso 4, verificar visualmente que el diseño coincide con los mockups aprobados
- El dominio `elcaminocatolico.com` se conecta DESPUÉS de que el sitio esté funcionando en GitHub Pages

---

*Documento generado para uso en Google Antigravity.*
*Versión 1.0 — Aprobado por el cliente.*
