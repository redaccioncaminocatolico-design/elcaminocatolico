# Documento 03 — SEO Técnico
## El Camino Católico · elcaminocatolico.com

> Este documento define todas las reglas de SEO técnico del sitio.
> El agente de Antigravity debe implementar cada punto sin excepción.
> Un sitio con buen SEO técnico tiene ventaja directa en los rankings de Google.

---

## 1. Meta tags obligatorios en cada página

Cada página del sitio debe incluir estos tags en el `<head>`:

```html
<!-- SEO básico -->
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>{{ .Title }} | El Camino Católico</title>
<meta name="description" content="{{ .Params.descripcion }}">
<meta name="keywords" content="{{ .Params.keywords }}">
<meta name="author" content="El Camino Católico">
<link rel="canonical" href="{{ .Permalink }}">

<!-- Open Graph (para compartir en redes sociales) -->
<meta property="og:title" content="{{ .Title }}">
<meta property="og:description" content="{{ .Params.descripcion }}">
<meta property="og:url" content="{{ .Permalink }}">
<meta property="og:type" content="article">
<meta property="og:site_name" content="El Camino Católico">
<meta property="og:locale" content="es_AR">

<!-- Twitter Card -->
<meta name="twitter:card" content="summary">
<meta name="twitter:title" content="{{ .Title }}">
<meta name="twitter:description" content="{{ .Params.descripcion }}">

<!-- Favicon -->
<link rel="icon" type="image/png" href="/favicon.png">
```

---

## 2. Schema Markup (datos estructurados)

Cada artículo debe incluir Schema markup tipo `Article` para que Google entienda el contenido y lo muestre con rich snippets.

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "{{ .Title }}",
  "description": "{{ .Params.descripcion }}",
  "datePublished": "{{ .Date.Format "2006-01-02" }}",
  "dateModified": "{{ .Lastmod.Format "2006-01-02" }}",
  "author": {
    "@type": "Organization",
    "name": "El Camino Católico",
    "url": "https://elcaminocatolico.com"
  },
  "publisher": {
    "@type": "Organization",
    "name": "El Camino Católico",
    "url": "https://elcaminocatolico.com"
  },
  "mainEntityOfPage": {
    "@type": "WebPage",
    "@id": "{{ .Permalink }}"
  }
}
</script>
```

Para la homepage, usar Schema tipo `WebSite`:

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "WebSite",
  "name": "El Camino Católico",
  "url": "https://elcaminocatolico.com",
  "description": "Tu guía en la fe católica. Artículos, oraciones y reflexiones.",
  "inLanguage": "es"
}
</script>
```

---

## 3. Sitemap

Hugo genera el sitemap automáticamente en `https://elcaminocatolico.com/sitemap.xml`.

**Configuración en `config.toml`:**
```toml
[sitemap]
  changefreq = "weekly"
  priority = 0.5
  filename = "sitemap.xml"
```

**Prioridades por tipo de página:**
```
Homepage:            priority = 1.0
Artículos recientes: priority = 0.8
Categorías:          priority = 0.7
Artículos antiguos:  priority = 0.5
Acerca / Contacto:   priority = 0.3
```

---

## 4. Robots.txt

El agente debe crear el archivo `static/robots.txt`:

```
User-agent: *
Allow: /

Sitemap: https://elcaminocatolico.com/sitemap.xml

# Bloquear páginas irrelevantes para SEO
Disallow: /tags/
```

---

## 5. Estructura de cada artículo (reglas SEO de contenido)

### 5.1 Título (H1)
- Exactamente **uno** por página
- Debe contener la keyword principal tal como la busca la gente
- Entre 50 y 65 caracteres
- Va en el header azul de la página, nunca en el cuerpo

**Ejemplos correctos:**
```
✓ "¿Por qué se reza el Rosario? Origen, misterios y significado"
✓ "¿Qué es el pecado mortal? Diferencias con el pecado venial"
✗ "El Rosario: una bella tradición de nuestra Iglesia"  ← no tiene keyword
```

### 5.2 Meta descripción
- Entre 140 y 155 caracteres
- Debe contener la keyword principal
- Tono de invitación a hacer clic, no un resumen aburrido
- Va en el front matter del artículo como `descripcion:`

**Ejemplo:**
```
"Descubrí el origen del Rosario, qué significan sus 20 misterios y por qué 
es la oración mariana más importante del catolicismo. Guía completa."
```

### 5.3 Subtítulos H2
- Mínimo 3 H2 por artículo
- Deben contener variaciones de la keyword principal o keywords relacionadas
- Redactados como preguntas o afirmaciones claras

**Ejemplos para el artículo del Rosario:**
```
H2: ¿Qué es el Rosario y por qué se reza?
H2: Origen histórico del Rosario
H2: Los cuatro grupos de misterios del Rosario
H2: ¿Cómo rezar el Rosario correctamente?
H2: Beneficios espirituales del Rosario según los Papas
```

### 5.4 Longitud del artículo
- Mínimo: **1.200 palabras**
- Óptimo: **1.500 a 2.500 palabras**
- Artículos sobre santos o historia pueden llegar a 3.000 palabras

### 5.5 Keyword density
- La keyword principal debe aparecer en:
  - El título H1 ✓
  - El primer párrafo del artículo ✓
  - Al menos 2 subtítulos H2 ✓
  - Naturalmente en el cuerpo (sin forzar)
- No repetir la keyword más de 1 vez cada 150 palabras

### 5.6 Enlace interno (interlinking)
- Cada artículo debe enlazar a **mínimo 2 artículos** del mismo sitio
- Los artículos relacionados al final del artículo cuentan
- El texto del enlace (anchor text) debe ser descriptivo, no "click aquí"

**Ejemplo correcto:**
```markdown
Podés leer más sobre [los misterios del Rosario](/articulos/misterios-del-rosario/) 
en nuestra guía completa.
```

---

## 6. Velocidad de carga (Core Web Vitals)

Hugo genera HTML estático, lo que ya es una ventaja enorme. Aun así el agente debe implementar:

### 6.1 Carga de fuentes optimizada
```html
<!-- Preconnect antes del link de Google Fonts -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<!-- Cargar fuentes con display=swap para evitar FOIT -->
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;600;700&family=Source+Serif+4:ital,wght@0,300;0,400;0,600;1,400&display=swap&display=swap" rel="stylesheet">
```

### 6.2 CSS mínimo
- Todo el CSS va en un solo archivo `main.css`
- No cargar librerías externas (Bootstrap, Tailwind, etc.)
- CSS escrito a mano, solo lo que se usa

### 6.3 Sin JavaScript innecesario
- El sitio no necesita JS para funcionar
- El único JS permitido es: Google AdSense y Google Analytics
- Nada de jQuery, nada de librerías de animación

### 6.4 Imágenes
- Formato: WebP (preferido) o JPG optimizado
- Siempre con atributo `alt` descriptivo
- Atributo `loading="lazy"` en todas las imágenes que no sean above the fold
- Tamaño máximo: 800px de ancho para imágenes de artículo

---

## 7. Google Search Console

Una vez publicado el sitio, realizar estos pasos (instrucción para el propietario):

```
1. Ir a search.google.com/search-console
2. Agregar propiedad: elcaminocatolico.com
3. Verificar con el método de archivo HTML (subir archivo a /static/)
4. Ir a Sitemaps → ingresar: sitemap.xml → Enviar
5. Esperar indexación (puede tardar 1-7 días)
```

---

## 8. Google Analytics

Agregar el tag de GA4 en el `<head>` de `baseof.html`:

```html
<!-- Google Analytics GA4 -->
{{ if .Site.Params.googleAnalytics }}
<script async src="https://www.googletagmanager.com/gtag/js?id={{ .Site.Params.googleAnalytics }}"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', '{{ .Site.Params.googleAnalytics }}');
</script>
{{ end }}
```

El ID de GA4 se completa en `config.toml` cuando esté disponible.

---

## 9. Google AdSense

El código de AdSense va en dos lugares:

### 9.1 Tag global en el `<head>`
```html
{{ if .Site.Params.adsenseID }}
<script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client={{ .Site.Params.adsenseID }}"
     crossorigin="anonymous"></script>
{{ end }}
```

### 9.2 Bloque de ad dentro del artículo
```html
<!-- Después del 3er párrafo -->
{{ if .Site.Params.adsenseID }}
<div class="ad-container">
  <p class="ad-label">Publicidad</p>
  <ins class="adsbygoogle"
       style="display:block"
       data-ad-client="{{ .Site.Params.adsenseID }}"
       data-ad-slot="XXXXXXXXXX"
       data-ad-format="auto"
       data-full-width-responsive="true"></ins>
  <script>(adsbygoogle = window.adsbygoogle || []).push({});</script>
</div>
{{ end }}
```

El `data-ad-slot` se completa cuando AdSense apruebe el sitio.

---

## 10. Breadcrumbs con Schema

Los breadcrumbs mejoran el CTR en Google y ayudan a la navegación.
Deben aparecer en páginas de artículo y de categoría, con Schema markup:

```html
<nav aria-label="breadcrumb">
  <span>Inicio</span> ›
  <span>{{ .Params.categoria }}</span>
</nav>

<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "BreadcrumbList",
  "itemListElement": [
    {
      "@type": "ListItem",
      "position": 1,
      "name": "Inicio",
      "item": "https://elcaminocatolico.com/"
    },
    {
      "@type": "ListItem",
      "position": 2,
      "name": "{{ .Params.categoria }}",
      "item": "{{ .Permalink }}"
    }
  ]
}
</script>
```

---

## 11. Checklist SEO antes de publicar cada artículo

El propietario debe verificar esto antes de hacer commit de cada artículo:

```
[ ] El slug no tiene tildes ni caracteres especiales
[ ] El título tiene entre 50 y 65 caracteres
[ ] La meta descripción tiene entre 140 y 155 caracteres
[ ] La keyword principal está en el primer párrafo
[ ] El artículo tiene mínimo 3 subtítulos H2
[ ] El artículo enlaza a mínimo 2 artículos internos
[ ] El artículo tiene mínimo 1.200 palabras
[ ] El front matter tiene todos los campos completos
[ ] La categoría es una de las 7 categorías definidas
[ ] El campo featured está en true o false
```

---

*Documento generado para uso en Google Antigravity.*
*Versión 1.0 — Aprobado por el cliente.*
