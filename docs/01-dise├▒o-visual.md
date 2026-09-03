# Documento 01 — Diseño Visual
## El Camino Católico · elcaminocatolico.com

> Este documento define la identidad visual completa del sitio.
> Es la referencia para el agente de Antigravity al construir cualquier página.

---

## 1. Concepto visual

**Palabra clave:** Sobriedad con calidez.

El sitio debe sentirse como una publicación editorial seria pero accesible.
No es una iglesia fría ni un blog colorido. Es una guía confiable.
La jerarquía visual la construye la tipografía, no los efectos decorativos.

**Lo que NO debe aparecer nunca:**
- Gradientes decorativos
- Sombras exageradas en cards
- Animaciones innecesarias al hacer scroll
- Colores llamativos fuera de la paleta definida
- Tipografías sans-serif en el cuerpo del texto

---

## 2. Paleta de colores

| Nombre        | Hex       | Uso principal                                      |
|---------------|-----------|----------------------------------------------------|
| Azul noche    | `#1B2A4A` | Header, footer, fondos de sección destacada, títulos |
| Dorado suave  | `#C8A96E` | Acento, links, bordes decorativos, badges, logo     |
| Crema         | `#F7F4EE` | Fondo general de página                            |
| Gris texto    | `#3D3D3A` | Cuerpo de texto principal                          |
| Blanco        | `#FFFFFF` | Fondo de cards y artículos                         |
| Borde suave   | `#DDD8CE` | Bordes de cards y divisores                        |
| Texto muted   | `#888780` | Fechas, tiempos de lectura, metadata               |
| Azul claro    | `#7A8FA8` | Links secundarios, breadcrumbs en header oscuro    |
| Crema oscura  | `#B8B0A0` | Texto secundario sobre fondo azul                  |

### Reglas de combinación
- Texto sobre `#1B2A4A` → siempre `#F7F4EE` o `#C8A96E`
- Texto sobre `#F7F4EE` → siempre `#3D3D3A` o `#1B2A4A`
- Nunca usar el dorado `#C8A96E` como fondo de texto oscuro
- El azul noche `#1B2A4A` es el color de identidad: header, footer, badges

---

## 3. Tipografía

### Fuentes a importar (Google Fonts)
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;600;700&family=Source+Serif+4:ital,wght@0,300;0,400;0,600;1,400&display=swap" rel="stylesheet">
```

### Roles tipográficos

| Elemento                  | Fuente            | Peso | Tamaño (desktop) | Tamaño (móvil) |
|---------------------------|-------------------|------|-------------------|----------------|
| Logo / nombre del sitio   | Playfair Display  | 700  | 20px              | 17px           |
| Títulos de artículo (H1)  | Playfair Display  | 700  | 32px              | 24px           |
| Subtítulos de sección (H2)| Playfair Display  | 600  | 22px              | 18px           |
| H3 dentro del artículo    | Playfair Display  | 600  | 18px              | 16px           |
| Cuerpo del artículo       | Source Serif 4    | 400  | 16px              | 15px           |
| Párrafo intro / destacado | Source Serif 4    | 400  | 16px italic       | 15px italic    |
| Metadata (fecha, tiempo)  | Source Serif 4    | 300  | 12px              | 11px           |
| Navegación                | Source Serif 4    | 300  | 12px              | —              |
| Categorías / badges       | Source Serif 4    | 600  | 10px uppercase    | 10px uppercase |

### Reglas tipográficas
- Line-height del cuerpo: `1.85`
- Ancho máximo del cuerpo del artículo: `640px` (centrado)
- Nunca usar sans-serif en el cuerpo de texto
- Letter-spacing en badges y eyebrows: `0.10em`
- Los títulos H1 de artículo van siempre sobre fondo `#1B2A4A`

---

## 4. Componentes del sitio

### 4.1 Header / Navegación
```
Fondo:          #1B2A4A
Logo:           Playfair Display 700, color #C8A96E, con prefijo "✝ "
Links nav:      Source Serif 4 300, color #D4C9B8, 12px, letter-spacing 0.04em
Hover links:    color #C8A96E
Alto:           ~50px
```

Ítems del menú principal:
- Fe y doctrina
- Santos
- Oraciones
- Historia de la Iglesia
- Apologética

### 4.2 Hero del homepage
```
Fondo:          #1B2A4A
Borde inferior: 3px solid #C8A96E
Eyebrow:        "Yo soy el camino, la verdad y la vida — Jn 14,6"
                Source Serif 4 300, #C8A96E, 11px, uppercase, letter-spacing 0.14em
Título H1:      Playfair Display 700, #F7F4EE, 34px
Subtítulo:      Source Serif 4 300, #B8B0A0, 15px, max-width 460px centrado
Padding:        48px 24px 40px
```

### 4.3 Cards de artículos (grid)
```
Fondo:          #FFFFFF
Borde:          0.5px solid #DDD8CE
Border-radius:  8px
Hover borde:    #C8A96E
Imagen/thumb:   Fondo #1B2A4A, símbolo ✝ en #C8A96E como placeholder
Categoría:      10px, uppercase, #C8A96E, letter-spacing 0.10em
Título:         Playfair Display 600, #1B2A4A, 14px
Excerpt:        Source Serif 4 300, #888780, 11px
Grid:           2 columnas en desktop, 1 columna en móvil
Gap:            14px
```

### 4.4 Artículo destacado (featured)
```
Layout:         Horizontal (imagen izquierda + texto derecha)
Imagen:         120px ancho, fondo #1B2A4A
Badge:          Fondo #1B2A4A, texto #C8A96E, 9px uppercase
Título:         Playfair Display 700, #1B2A4A, 16px
Metadata:       Source Serif 4 300, #AAAAAA, 11px
```

### 4.5 Header de página de artículo
```
Fondo:          #1B2A4A
Borde inferior: 3px solid #C8A96E
Badge categoría: borde 1px #C8A96E, texto #C8A96E, 10px uppercase
Título H1:      Playfair Display 700, #F7F4EE, 26-32px
Metadata:       Source Serif 4 300, #7A8FA8, 12px
Padding:        36px 32px 32px
```

### 4.6 Cuerpo del artículo
```
Fondo página:       #F7F4EE
Fondo cuerpo:       transparente (sin card wrapper)
Max-width texto:    580px, centrado
Padding:            32px 32px 24px

Párrafo intro:      Source Serif 4 400 italic, 16px, border-left 3px #C8A96E, padding-left 16px
H2 dentro artículo: Playfair Display 600, #1B2A4A, 20px, margin-top 28px
Párrafos:           Source Serif 4 400, #3D3D3A, 15px, line-height 1.85

Bloque de cita:     Fondo #FFFFFF, border-left 3px #1B2A4A, border-radius 0 6px 6px 0
                    Texto: Playfair Display 600, #1B2A4A, 14px
                    Fuente de cita: Source Serif 4 300, #888780, 11px
```

### 4.7 Bloque de AdSense
```
Posición:       Después del 3er párrafo del artículo (mitad del contenido)
Contenedor:     Fondo #FFFFFF, borde 0.5px #DDD8CE, border-radius 6px
                Margin: 20px 0, padding 14px
Label:          "Publicidad", 10px, #BBBBBB, uppercase, letter-spacing 0.08em
Tamaño del ad:  Responsive (auto), preferentemente 728x90 desktop / 320x50 móvil
```

### 4.8 Artículos relacionados (al final)
```
Fondo:          #1B2A4A
Título sección: Playfair Display 600, #C8A96E, 15px
Ítems:          Punto dorado + texto #B8C8D8, 13px, Source Serif 4 300
Separador:      0.5px solid #2A3F62
Padding:        20px 24px
```

### 4.9 Pills de categorías (homepage)
```
Fondo:          #FFFFFF
Borde:          0.5px solid #C8A96E
Border-radius:  20px (pill completa)
Padding:        6px 14px
Texto:          Source Serif 4 400, #1B2A4A, 12px
Hover fondo:    #1B2A4A
Hover texto:    #C8A96E
```

### 4.10 Footer
```
Fondo:          #1B2A4A
Texto:          Source Serif 4 300, #6A7A96, 11px
Nombre sitio:   color #C8A96E
Padding:        20px 24px
Contenido:      Copyright + nombre + dominio
```

---

## 5. Layout general

### Homepage
```
[Header/Nav]
[Hero — azul con frase bíblica y título]
[Artículo destacado]
[Grid de últimos artículos — 2 columnas]
[Divisor]
[Pills de categorías]
[Footer]
```

### Página de artículo
```
[Header/Nav con breadcrumb]
[Header del artículo — azul con título]
[Cuerpo del artículo]
  → párrafo intro en cursiva
  → H2 + párrafos
  → [AdSense a mitad del artículo]
  → resto del artículo
[Artículos relacionados — fondo azul]
[Footer]
```

### Página de categoría
```
[Header/Nav]
[Banner de categoría — azul, nombre de categoría]
[Grid de artículos — 2 columnas, todos de esa categoría]
[Paginación]
[Footer]
```

---

## 6. Responsive (móvil)

- Grid de artículos: 2 col → 1 col en pantallas < 480px
- Menú de navegación: colapsa en hamburger en móvil
- Artículo destacado: cambia de horizontal a vertical en móvil
- Padding general en móvil: 16px (en lugar de 24-32px)
- Título H1 del artículo: 24px en móvil (vs 32px desktop)

---

## 7. SEO técnico — reglas visuales

- Cada artículo tiene exactamente **un H1** (el título principal)
- Los H2 estructuran el contenido del artículo (subtemas)
- Las imágenes siempre llevan atributo `alt` descriptivo
- El logo siempre enlaza al homepage
- Los breadcrumbs están visibles en páginas de artículo y categoría

---

## 8. Íconos y símbolos

- Símbolo de la cruz `✝` como elemento gráfico de identidad
- Se usa en: logo, placeholders de imágenes, separadores decorativos
- No se usan íconos de redes sociales en el diseño principal
- No se usan emojis en ninguna parte del sitio

---

## 9. Lo que NUNCA debe hacer el agente

- No usar fuentes sans-serif en cuerpo de texto (ni Arial, ni Roboto, ni Inter)
- No usar sombras de cards tipo `box-shadow: 0 4px 20px rgba(0,0,0,0.1)`
- No usar colores fuera de la paleta definida en la sección 2
- No centrar el texto del cuerpo del artículo (va alineado a la izquierda)
- No agregar animaciones de scroll (fade-in, slide-up, etc.)
- No usar border-radius mayor a 12px en cards
- No agregar banners de cookies, popups ni overlays de ningún tipo
- No usar imágenes de stock genéricas — usar el placeholder ✝ sobre fondo azul

---

*Documento generado para uso en Google Antigravity.*
*Versión 1.0 — Aprobado por el cliente.*
