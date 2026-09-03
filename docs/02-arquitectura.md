# Documento 02 — Arquitectura del Sitio
## El Camino Católico · elcaminocatolico.com

> Este documento define la estructura completa del sitio: páginas, URLs,
> categorías, menú de navegación y cómo se relacionan entre sí.
> Es la referencia para el agente de Antigravity al crear la estructura de Hugo.

---

## 1. Estructura general de URLs

```
elcaminocatolico.com/                          → Homepage
elcaminocatolico.com/articulos/                → Listado de todos los artículos
elcaminocatolico.com/articulos/[slug]/         → Página individual de artículo
elcaminocatolico.com/categoria/[slug]/         → Listado por categoría
elcaminocatolico.com/santos/                   → Categoría especial: Santos
elcaminocatolico.com/acerca/                   → Página "Acerca de"
elcaminocatolico.com/contacto/                 → Página de contacto
elcaminocatolico.com/privacidad/               → Política de privacidad (requerida por AdSense)
```

### Reglas de slugs
- Siempre en minúsculas
- Sin tildes ni caracteres especiales (ñ → n, é → e, etc.)
- Palabras separadas por guión medio `-`
- Sin números al inicio
- Máximo 6 palabras en el slug

**Ejemplos correctos:**
```
/articulos/como-rezar-el-rosario/
/articulos/pecado-mortal-venial-diferencias/
/articulos/san-francisco-de-asis-vida-milagros/
/categoria/fe-y-doctrina/
/categoria/santos/
```

---

## 2. Categorías del sitio

Son las 7 categorías principales. Cada artículo pertenece a exactamente una categoría.

| Categoría           | Slug               | Descripción breve                                          |
|---------------------|--------------------|------------------------------------------------------------|
| Fe y doctrina       | `fe-y-doctrina`    | Dogmas, sacramentos, catecismo, qué cree la Iglesia        |
| Santos              | `santos`           | Vidas, milagros y legado de los santos canonizados         |
| Oraciones           | `oraciones`        | Cómo rezar, oraciones explicadas, devoción mariana         |
| Historia            | `historia`         | Historia de la Iglesia, papas, concilios, mártires         |
| Apologética         | `apologetica`      | Respuestas a dudas frecuentes, diferencias con otras fe    |
| Virgen María        | `virgen-maria`     | Apariciones, dogmas marianos, devoción a María             |
| Semana Santa        | `semana-santa`     | Liturgia, tradiciones, significado de cada día             |

---

## 3. Menú de navegación

### Menú principal (header)
```
Inicio | Fe y doctrina | Santos | Oraciones | Historia | Apologética
```

### Menú secundario (footer)
```
Acerca de | Contacto | Política de privacidad
```

### Menú móvil
El menú principal colapsa en un ícono hamburger (☰) en pantallas menores a 768px.
Al abrirlo, muestra los mismos ítems en lista vertical sobre fondo `#1B2A4A`.

---

## 4. Páginas que el agente debe construir

### 4.1 Homepage (`/`)
**Secciones en orden:**
1. Header con navegación
2. Hero con frase bíblica y descripción del sitio
3. Artículo destacado (el más reciente o marcado como featured)
4. Sección "Últimos artículos" → grid 2 columnas, máximo 6 artículos
5. Divisor
6. Sección "Explorar por categoría" → pills de las 7 categorías
7. Footer

**Datos dinámicos que Hugo debe leer:**
- Artículo con `featured: true` en su front matter → va en el destacado
- Los 6 artículos más recientes por fecha → van en el grid

---

### 4.2 Página de artículo (`/articulos/[slug]/`)
**Secciones en orden:**
1. Header con navegación + breadcrumb (Inicio › Categoría)
2. Header del artículo (fondo azul): badge de categoría + H1 + metadata
3. Cuerpo del artículo (Markdown renderizado)
   - Párrafo intro destacado (el primero va con estilo especial)
   - H2 y H3 con estilo editorial
   - Bloque de AdSense después del 3er párrafo
   - Resto del contenido
4. Sección artículos relacionados (misma categoría, 3 artículos)
5. Footer

**Front matter requerido por cada artículo:**
```yaml
---
title: "¿Por qué se reza el Rosario? Origen, misterios y significado"
slug: "por-que-se-reza-el-rosario"
date: 2025-10-01
categoria: oraciones
tags: [rosario, oracion, devocion, virgen-maria]
descripcion: "Descubrí el origen del Rosario, qué significan sus misterios y por qué es la oración más poderosa del catolicismo."
featured: false
tiempo_lectura: 8
---
```

---

### 4.3 Página de categoría (`/categoria/[slug]/`)
**Secciones en orden:**
1. Header con navegación
2. Banner de categoría (fondo azul, nombre de categoría, descripción breve)
3. Grid de todos los artículos de esa categoría (2 columnas)
4. Paginación (10 artículos por página)
5. Footer

---

### 4.4 Página "Acerca de" (`/acerca/`)
**Contenido:**
- Header azul con título "Acerca de El Camino Católico"
- Texto editorial explicando el propósito del blog
- Sin sidebar, sin grid
- Footer

---

### 4.5 Página de contacto (`/contacto/`)
**Contenido:**
- Header azul con título
- Texto breve + dirección de email de contacto
- Sin formulario (para evitar spam y complejidad)
- Footer

---

### 4.6 Política de privacidad (`/privacidad/`)
**Contenido:**
- Requerida por Google AdSense para aprobación
- Texto estándar de política de privacidad adaptado al sitio
- Menciona uso de cookies de Google AdSense
- Footer

---

## 5. Estructura de archivos en Hugo

```
elcaminocatolico/
├── config.toml                  → Configuración general del sitio
├── content/
│   ├── articulos/
│   │   ├── como-rezar-el-rosario.md
│   │   ├── pecado-mortal-venial.md
│   │   └── ...
│   ├── acerca.md
│   ├── contacto.md
│   └── privacidad.md
├── layouts/
│   ├── _default/
│   │   ├── baseof.html          → Layout base (head, header, footer)
│   │   ├── single.html          → Template de artículo individual
│   │   ├── list.html            → Template de listado (categoría, todos)
│   └── index.html               → Template del homepage
├── static/
│   ├── css/
│   │   └── main.css             → Estilos globales
│   └── favicon.ico
└── themes/                      → Vacío (usamos layouts propios, sin tema externo)
```

---

## 6. Configuración base de Hugo (`config.toml`)

```toml
baseURL = "https://elcaminocatolico.com/"
languageCode = "es-AR"
title = "El Camino Católico"
description = "Tu guía en la fe católica. Artículos, oraciones y reflexiones para crecer en la fe."
paginate = 10
enableRobotsTXT = true

[params]
  author = "El Camino Católico"
  email = "contacto@elcaminocatolico.com"
  keywords = "catolicismo, fe católica, oraciones, santos, doctrina católica"
  googleAnalytics = ""   # completar cuando esté activo
  adsenseID = ""         # completar cuando esté aprobado por AdSense

[taxonomies]
  category = "categoria"
  tag = "tags"

[markup]
  [markup.goldmark]
    [markup.goldmark.renderer]
      unsafe = true   # permite HTML dentro del Markdown
```

---

## 7. Flujo de publicación de un artículo nuevo

Este es el proceso completo para agregar un artículo, sin usar la terminal:

```
1. Ir a github.com → repositorio del sitio
2. Navegar a content/articulos/
3. Clic en "Add file" → "Create new file"
4. Nombre del archivo: [slug-del-articulo].md
   Ejemplo: por-que-se-reza-el-rosario.md
5. Pegar el front matter (plantilla en Documento 03)
6. Escribir el contenido en Markdown debajo del front matter
7. Clic en "Commit changes" (botón verde)
8. GitHub Actions ejecuta Hugo automáticamente
9. En ~2 minutos el artículo está publicado en vivo
```

---

## 8. GitHub Actions — configuración necesaria

El agente debe crear el archivo `.github/workflows/hugo.yml` con este contenido:

```yaml
name: Deploy Hugo site

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
        with:
          submodules: true
          fetch-depth: 0

      - name: Setup Hugo
        uses: peaceiris/actions-hugo@v2
        with:
          hugo-version: 'latest'
          extended: true

      - name: Build
        run: hugo --minify

      - name: Deploy to GitHub Pages
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./public
```

---

## 9. Páginas de error personalizadas

El agente debe crear:
- `layouts/404.html` → página de error 404 con estilo del sitio
- Mensaje: "Esta página no existe. Volvé al inicio."
- Botón que lleva al homepage

---

*Documento generado para uso en Google Antigravity.*
*Versión 1.0 — Aprobado por el cliente.*
