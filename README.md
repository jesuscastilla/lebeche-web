# Lebeche — Web oficial e índice de proyectos

Sitio web de la **Asociación Lebeche**, asociación cultural y vecinal de Salobreña (Granada),
y el índice de los proyectos digitales que impulsa.

> **Infraestructura:** NAS Synology con Web Station (Nginx + PHP 8 + MariaDB).
> **Dominio público:** `https://www.corrientelebeche.es/lebeche/` (ver `docs/GUIA_DOMINIO_CORRIENTELEBECHE.md`).
> **Despliegue:** Guía detallada en `docs/GUIA_NAS_SYNOLOGY_WEB_STATION.md`.

---

## La web

Web estática (HTML + CSS + JavaScript puro, sin frameworks ni CDN de scripts) con el tema visual
de la Barrioteca y la identidad de Lebeche. Secciones: asociación, programación, noticias,
aplicaciones, Barrioteca Acalencá, ubicación y contacto. Cada evento de la programación puede
añadirse al calendario del móvil/ordenador (descarga `.ics` o enlace a Google Calendar).

### Cómo editar sin saber código

La web incluye un **panel Staff** privado (en `admin/`, con usuario y contraseña) desde el que se
pueden editar de forma visual la **programación**, las **noticias**, las **apps** y el
**contacto/ubicación**. Requiere PHP (Web Station). Ver `docs/GUIA_NAS_SYNOLOGY_WEB_STATION.md`.

Los contenidos se guardan en archivos **JSON** de la carpeta `data/` (la "fuente de verdad").
Los archivos `js/*.js` son solo valores por defecto: la web carga primero el JSON y, si no está
disponible, usa esos valores.

> **Credenciales:** el archivo `admin/config.php` (usuario y hash del panel) está en `.gitignore`
> y no se sube a Git. Crea el tuyo a partir de `admin/config.example.php`.

### Estructura

```
lebeche-web/
├── index.html                     # Página principal (secciones ancla)
├── css/styles.css                 # Estilos (tema Barrioteca + identidad Lebeche)
├── js/datos.js                    # Valores por defecto (dirección, redes, contacto)
├── js/apps.js                     # Valores por defecto (aplicaciones)
├── js/noticias.js                 # Valores por defecto (noticias)
├── js/programacion.js             # Valores por defecto (programación)
├── js/main.js                     # Menú móvil, carga de datos, render, animaciones
├── data/                          # ★ Contenidos editables (JSON) — se editan desde el panel
├── admin/                         # Panel Staff (PHP): login y edición visual
├── assets/                        # Logos y favicon
└── docs/
    └── GUIA_NAS_SYNOLOGY_WEB_STATION.md   # Guía de despliegue en el NAS
```

### Ver en local

Abre `index.html` con el navegador, o lanza un servidor:

```bash
python -m http.server
```

y abre `http://localhost:8000`.

> El panel Staff (`admin/`) necesita PHP. Para probarlo en local:
> `php -S localhost:8000` desde la carpeta, y abre `http://localhost:8000/admin/`.

### Desplegar en el NAS

Consulta `docs/GUIA_NAS_SYNOLOGY_WEB_STATION.md`.

---

## Proyectos Lebeche

Aplicaciones y servicios digitales de la **Asociación Lebeche** (Salobreña, Granada).

---

## Barrioteca Acalencá

Aplicación de biblioteca vecinal autogestionada: catálogo, préstamos y devoluciones por
código de barras.

| Entrega | Tecnología | Repositorio en GitHub | Estado |
|---|---|---|---|
| Web (PWA) | React 19 + Vite + Tailwind + TypeScript | [barrioteca-web](https://github.com/jesuscastilla/barrioteca-web) | Activa |
| Backend | SLiMS 9 Bulian (PHP + MariaDB) | [barrioteca-slims](https://github.com/jesuscastilla/barrioteca-slims) | Activa |
| Android | Kotlin + Jetpack Compose (nativa) | [barrioteca-android](https://github.com/jesuscastilla/barrioteca-android) | Activa |
| iOS | Swift + WKWebView | [barrioteca-ios](https://github.com/jesuscastilla/barrioteca-ios) | Activa |

- **URL pública:** `https://www.corrientelebeche.es/barrioteca/`
- **Acceso sin app**: la web (PWA) sigue siendo la vía principal para quien no usa smartphone y para iOS.

---

## Próximamente

- **Archivo multimedia** (fotos, carteles y documentos de la asociación).
- **Tablón de anuncios** (avisos y novedades).

## Herramientas

- [HTML](https://developer.mozilla.org/es/docs/Web/HTML), [CSS](https://developer.mozilla.org/es/docs/Web/CSS) y [JavaScript](https://developer.mozilla.org/es/docs/Web/JavaScript) — web estática.
- [PHP](https://www.php.net/) — panel Staff.
- [Nginx](https://nginx.org/) — servidor web (Web Station).
- [MariaDB](https://mariadb.org/) — base de datos.
- [Cloudflare](https://www.cloudflare.com/) — DNS y HTTPS.
- [Synology Web Station](https://www.synology.com/dsm) — alojamiento.

