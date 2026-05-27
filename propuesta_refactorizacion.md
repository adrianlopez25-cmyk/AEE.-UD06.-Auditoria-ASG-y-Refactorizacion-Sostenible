# 3. Propuesta de Refactorización Web Sostenible

---

## Índice

1. [Análisis de la Situación Actual](#1-análisis-de-la-situación-actual)
2. [Mejoras Ambientales (A - Environmental)](#2-mejoras-ambientales-a---environmental)
3. [Mejoras Sociales (S - Social)](#3-mejoras-sociales-s---social)
4. [Mejoras de Gobernanza (G - Governance)](#4-mejoras-de-gobernanza-g---governance)
5. [Propuesta Técnica: Comparativa Código "Antes vs. Después"](#5-propuesta-técnica-comparativa-código-antes-vs-después)
6. [Plan de Validación y Herramientas](#6-plan-de-validación-y-herramientas)

---

## 1. Análisis de la Situación Actual

El sitio web actual presenta un alto nivel de obsolescencia técnica en la gestión de recursos de interfaz (frontend). Se ha detectado:
* **Exceso de peticiones redundantes:** Carga masiva de variantes tipográficas redundantes (escalas de pesos del 100 al 900 en formatos itálica y normal) de fuentes externas de Google Fonts.
* **Compatibilidad heredada innecesaria:** Inclusión de bloques CSS `@font-face` optimizados para navegadores obsoletos (ej. Firefox 27/39) y formatos antiguos (`.woff`, `.ttf`), ignorando el estándar actual.
* **Vectores de riesgo y Bloat:** Presencia de scripts desactualizados en el archivo de cabecera como `xmlrpc.php`, que ralentizan el renderizado en el dispositivo del cliente y comprometen la seguridad.

---

## 2. Mejoras Ambientales (A - Environmental)

El objetivo es reducir la huella de carbono digital del sitio disminuyendo la transferencia de datos (bytes) y los ciclos de procesamiento de CPU en el cliente y el servidor.

* **Optimización de Fuentes (Consolidación WOFF2):** Se eliminarán todas las variantes tipográficas innecesarias, manteniendo únicamente los pesos esenciales (ej. 400 y 700). Se migrará exclusivamente al formato **WOFF2**, que cuenta con un soporte global superior al 98% en navegadores modernos y ofrece una compresión hasta un 30% más eficiente que WOFF.
* **Optimización de Imágenes:** Transición obligatoria de formatos tradicionales (PNG/JPG) a formatos de última generación como **WebP** o **AVIF**.
* **Lazy Loading Nativo:** Implementación del atributo `loading="lazy"` en todas las imágenes y recursos multimedia situados fuera de la primera pantalla de visualización (*below the fold*).
* **Eliminación de Código No Utilizado (Clean Architecture):** Eliminación de las hojas de estilo inline autogeneradas por Divi que no tengan un impacto directo en el diseño actual de la página.

---

## 3. Mejoras Sociales (S - Social)

Orientado a garantizar la inclusión digital, eliminando barreras de acceso y cumpliendo las pautas de accesibilidad **WCAG 2.2**.

* **Uso de HTML5 Semántico:** Reemplazar la arquitectura basada en la división genérica (`div-in-div` o "divitis" propia de los maquetadores visuales) por etiquetas semánticas estructurales de HTML5 (`<header>`, `<nav>`, `<main>`, `<article>`, `<footer>`).
* **Inclusión de Atributos Alt:** Asegurar que todos los elementos gráficos dispongan del atributo `alt` correctamente cumplimentado para que los lectores de pantalla puedan interpretar el contenido para usuarios con discapacidad visual.
* **Navegación Accesible y Foco:** Configurar los elementos de interacción mediante atributos `aria-label` y garantizar un orden de tabulación nativo lógico (`tabindex`).
* **Mejora del Contraste:** Ajustar las paletas de colores mediante CSS para asegurar una relación de contraste mínima de 4.5:1 en textos normales y 3:1 en textos grandes, alcanzando el estándar WCAG AA.

---

## 4. Mejoras de Gobernanza (G - Governance)

Garantizar la transparencia, la privacidad de los datos del usuario y el cumplimiento legal de las normativas vigentes (RGPD / LOPDGDD).

* **Privacidad por Diseño (Self-Hosted Fonts):** Almacenar y servir las fuentes tipográficas localmente desde el propio servidor. Esto evita realizar peticiones directas a los servidores de Google antes de que el usuario otorgue su consentimiento, impidiendo que terceros capturen la dirección IP del visitante de forma no autorizada.
* **Consentimiento de Cookies Transparente:** Implementación de un Banner de Cookies (CMP) que permita revocar o aceptar los consentimientos por categorías con la misma facilidad ("Rechazar todas" en el primer nivel).
* **Eliminación de Prácticas Engañosas (Dark Patterns):** Diseño de interfaces honestas, eliminando botones de aceptación camuflados o casillas pre-marcadas.
* **Deshabilitación de Scripts Obsoletos:** Eliminación completa del enlace a `xmlrpc.php` de WordPress para cerrar un vector crítico de ataques de fuerza bruta y denegación de servicio (DDoS).

---

## 5. Propuesta Técnica: Comparativa Código "Antes vs. Después"

### Código Original (Involutivo e Ineficiente)

```html
<html lang="es-ES">
<head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <link rel="pingback" href="[https://www.mkpersons.com/dev/xmlrpc.php](https://www.mkpersons.com/dev/xmlrpc.php)" />
    
    <style id="et-divi-open-sans-inline-css">
        @font-face {
            font-family: 'Open Sans';
            font-style: italic;
            font-weight: 300;
            src: url([https://fonts.gstatic.com/s/opensans/v44/memQYaGs126MiZpBA-UFUIcVXSCEkx2cmqvXlWq8tWZ0Pw86hd0Rk5hkaVc.ttf](https://fonts.gstatic.com/s/opensans/v44/memQYaGs126MiZpBA-UFUIcVXSCEkx2cmqvXlWq8tWZ0Pw86hd0Rk5hkaVc.ttf)) format('truetype');
        }
        /* ... Cientos de líneas repetitivas para agentes de usuario antiguos como comente previamente (Firefox 27, 39, etc.) ... */
    </style>
</head>
<body>
    <div id="main-header">
        <div class="logo-container">
            <img src="logo.jpg"> </div>
        <div class="navigation-menu">
            <div class="menu-item"><a href="/inicio">Inicio</a></div>
        </div>
    </div>
</body>
</html>
Esta seria mi propuesta de la parte del codigo ya refactorizada:

<!DOCTYPE html>
<html lang="es-ES">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Plataforma Web Optimizada Sostenible</title>
    
    <style>
        @font-face {
            font-family: 'Open Sans';
            font-style: normal;
            font-weight: 400;
            font-display: swap; /* Evita el bloqueo del renderizado del texto */
            src: url('/assets/fonts/open-sans-v44-latin-regular.woff2') format('woff2');
        }
        @font-face {
            font-family: 'Open Sans';
            font-style: normal;
            font-weight: 700;
            font-display: swap;
            src: url('/assets/fonts/open-sans-v44-latin-700.woff2') format('woff2');
        }
    </style>
</head>
<body>

    <header role="banner">
        <nav aria-label="Menú de navegación principal">
            <div class="logo-container">
                <img src="/assets/images/logo.webp" 
                     alt="Logotipo oficial de la organización" 
                     width="180" 
                     height="60" 
                     loading="eager">
            </div>
            <ul class="nav-list">
                <li><a href="/inicio">Inicio</a></li>
            </ul>
        </nav>
    </header>

    <main id="main-content" role="main">
        </main>

</body>
</html>
```
<img width="1771" height="159" alt="mejora fotos" src="https://github.com/user-attachments/assets/a0e5084f-e7c9-412d-a3ec-5c6be949ca32" />

Problema principal: formato JPG sin modernizar
Los archivos call4.jpg y call2.jpg son imágenes de 1920×1080px en JPG, cargadas con lazy load correctamente, pero con dos problemas sin resolver:
html<!-- Antes -->
<img data-src="call4.jpg" ...>

<!-- Después -->
<picture>
  <source srcset="call4.avif" type="image/avif">
  <source srcset="call4.webp" type="image/webp">
  <img loading="lazy" src="call4.jpg" alt="Descripción real del equipo de trabajo">

<img width="1452" height="868" alt="adaptabilidad_web" src="https://github.com/user-attachments/assets/718875c5-ef5d-4a36-ba18-54e4cf836181" />
### Bloque 3: Privacidad y Gobernanza de Scripts (Carga de Terceros)
Antes:
<!-- Esto dispara cookies de seguimiento sin consentimiento -->
<script type='text/javascript'>
  !function(f,b,e,v...){ fbq... }
</script>

Despues:
<script type="text/plain" data-cookiecategory="marketing">
  // código del pixel aquí
</script>

Antes: El navegador ejecuta fbevents.js en el momento que carga la página. Facebook recibe la IP del visitante, su User-Agent y la URL visitada sin que haya dado ningún consentimiento. Esto es una transferencia de datos a un tercero fuera de la UE sin base legal.Después: El script tiene type="text/plain", lo que significa que el navegador lo ignora completamente. No se ejecuta, no hace peticiones, no transfiere datos. Solo cuando el CMP registra que el usuario ha aceptado la categoría "marketing", cambia el tipo a text/javascript y entonces sí se ejecuta.La diferencia ante la AEPD es total: de infracción activa a cumplimiento demostrable.

## 6. Plan de Validación y Herramientas

Para auditar y certificar el éxito del proceso de refactorización, se implementará un pipeline de pruebas automatizadas utilizando herramientas de diagnóstico estándar de la industria. Cada una de ellas validará un pilar específico de nuestra estrategia ESG:

* **Google Lighthouse / PageSpeed Insights (Métrica Ambiental y Social):** Se utilizará para medir la eficiencia bruta de la interfaz y la experiencia de usuario en dispositivos móviles y de escritorio. Tras la refactorización, el objetivo mínimo para los *Core Web Vitals* es alcanzar una puntuación **> 90** en la categoría de *Performance*. Se prestará especial atención a la reducción del *Total Blocking Time* (TBT) y del *First Contentful Paint* (FCP), métricas directamente afectadas por el antiguo bloqueo de renderizado tipográfico.
* **WAVE - Web Accessibility Evaluation Tool (Métrica Social):** Herramienta encargada de auditar de forma estricta el cumplimiento de las pautas de accesibilidad **WCAG 2.2 (Nivel AA)**. El sistema escaneará la plataforma para validar la correcta anidación semántica de las nuevas etiquetas de HTML5, la validez de los textos alternativos (`alt`), la ausencia de alertas de contraste cromático y la viabilidad de la navegación mediante teclado.
* **EcoGrader / Digital Beacon (Métrica Ambiental):** Plataformas especializadas en sostenibilidad digital que calculan la huella de carbono de los activos en la red basándose en el tamaño de la página, el procesamiento de scripts y la política de transferencia de datos. El objetivo técnico cuantitativo es situar el consumo de la plataforma en una emisión **inferior a 0.2 g de $CO_2$ por cada carga de página**, garantizando que el sitio web se clasifique dentro del rango de bajo impacto ambiental global.
