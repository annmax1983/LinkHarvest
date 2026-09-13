# LinkHarvest — Extractor y escáner de enlaces

[English](../README.md) | [中文](README_zh.md) | Español | [Deutsch](README_de.md) | [日本語](README_ja.md) | [Français](README_fr.md)

Una extensión ligera para el navegador que extrae todos los hipervínculos de cualquier página web, con filtrado inteligente, búsqueda y exportación a CSV.

> Basada en Chromium · Manifest V3 · Sin rastreo · Datos solo locales

---

## ¿Por qué LinkHarvest?

La mayoría de herramientas de extracción de enlaces son servicios online que requieren subir el contenido de la página. LinkHarvest se ejecuta completamente en tu navegador — tus datos nunca salen de tu dispositivo.

| Ventaja | Detalle |
|---------|--------|
| 🔍 **Escanear con un clic** | Extrae todos los enlaces de etiquetas `<a>` de la página actual |
| 📡 **Monitorización DOM en tiempo real** | MutationObserver captura enlaces añadidos dinámicamente (SPA, scroll infinito) |
| 🔎 **Filtrado inteligente** | Filtros por inclusión/exclusión de palabras clave, ordenación por columnas; filtra enlaces ancla y pseudo-enlaces JS; distingue interno/externo |
| 📋 **Copia por lotes** | Copia todos los enlaces válidos al portapapeles con un clic |
| 🖱️ **Menú contextual** | Clic derecho en cualquier página → "Extraer enlaces de la página", sin necesidad de popup |
| 🔢 **Conteo de apariciones** | Registra cuántas veces aparece cada URL en la página |
| 📥 **Exportación CSV** | Codificación UTF-8 BOM — compatible con Excel/WPS (Premium) |
| 🔒 **Datos solo locales** | Todos los datos se almacenan solo en la memoria del navegador; se borran al cerrar la página |
| 🌍 **Multi-idioma** | Soporta inglés, chino, japonés, alemán, español y francés |
| ⚡ **Ligera** | JavaScript vanilla puro, cero dependencias, paquete de menos de 100 KB |
| 🏗️ **Manifest V3** | Usa `activeTab` + `scripting` + `storage` + `contextMenus` — permisos mínimos |

---

## Gratis vs Premium

| Plan | Funcionalidades |
|------|----------|
| **Gratis** | Escanear enlaces, monitorización DOM en tiempo real, buscar y filtrar, copiar al portapapeles, exportación TXT |
| **⭐ Premium** | Exportación por lotes a CSV — descarga todos los enlaces filtrados como archivo CSV |

Todas las funcionalidades principales (escanear, filtrar, copiar) son gratuitas para siempre. La **Exportación CSV** requiere una licencia VKT Premium — una compra única que apoya el desarrollo.

- 🛒 Obtener licencia: `https://www.annmax1983.com/checkout.html?plugin=linkharvest`
- ⚙ Activarla: abre el popup de LinkHarvest → haz clic en el botón **⚙** → introduce tu clave de licencia.

> La activación de licencia es **opcional**. El nivel gratuito funciona completamente sin ella — sin cuenta, sin registro, sin clave de licencia.

---

## Vista previa

<p align="center">
  <img src="screenshot/promo.png" alt="Vista previa de LinkHarvest" width="640">
</p>

---

## Navegadores compatibles

| Navegador | Estado |
|---------|--------|
| Google Chrome | ✅ Totalmente compatible |
| Microsoft Edge | ✅ Totalmente compatible |
| Otros navegadores basados en Chromium | ✅ Debería funcionar |

---

## Instalación

1. Abre la página de extensiones de tu navegador:
   - **Chrome**: `chrome://extensions/`
   - **Edge**: `edge://extensions/`
2. Activa el **modo de desarrollador** (interruptor arriba a la derecha)
3. Haz clic en **Cargar descomprimida** y selecciona la carpeta del proyecto
4. Haz clic en el icono 🔗 de LinkHarvest en tu barra de herramientas para empezar

---

## Uso

1. **Abre la página web objetivo** y espera a que el contenido dinámico se cargue
2. **Haz clic en el icono de LinkHarvest** en la barra de herramientas de tu navegador
3. **Activa el monitor DOM** (opcional) — para páginas con scroll infinito o enlaces de carga diferida
4. **Haz clic en "Escanear enlaces de la página"** — todos los enlaces se extraen al instante
5. **Ver lista completa** — se abre una página de resultados dedicada con vista de tabla
6. **Buscar y filtrar** — usa el campo de búsqueda, filtros de inclusión/exclusión de palabras clave y ordenación por columnas para reducir los resultados
7. **Copiar enlaces** — copia los enlaces filtrados al portapapeles (gratis)
8. **Exportar TXT** — guarda las URLs filtradas como archivo de texto plano (gratis)
9. **Exportar CSV** — descarga los enlaces filtrados como archivo CSV con conteo de apariciones (Premium)

---

## Campos recopilados

| Campo | Descripción |
|-------|-------------|
| `linkText` | Texto visible del enlace (limpiado) |
| `href` | URL absoluta completa |
| `target` | `_blank` / `_self` |
| `category` | anchor / javascript / protocol / normal |
| `isInternal` | Si el enlace es del mismo origen |
| `count` | Cuántas veces aparece la URL en la página |

---

## Privacidad

- **activeTab** — Concede acceso solo cuando haces clic activamente en el icono de la extensión
- **scripting** — Se usa para inyectar el script de recopilación de enlaces en la página actual
- **storage** — Almacena temporalmente los resultados del escaneo para la página de resultados; se borra al cerrar la pestaña escaneada
- **contextMenus** — Añade un elemento de menú de clic derecho "Extraer enlaces de la página"; no lee datos por sí mismo
- **Licencia (opcional)** — Solo si activas una licencia de pago: una huella de dispositivo + metadatos del navegador se envían a `api.annmax1983.com` para activar/validar la licencia. Esto nunca incluye tus datos de escaneo, historial de navegación ni datos personales.
- Sin permiso `<all_urls>` — no accede a páginas sin tu acción
- Sin solicitudes de red externas para funcionalidades gratuitas — todo el procesamiento ocurre localmente
- Sin acceso al historial de navegación, sin rastreo de usuarios, sin subida de datos
- [Política de privacidad](privacy-policy.html)

---

## Estructura del proyecto

```
link-harvest/
├── manifest.json          # MV3 manifest
├── background/sw.js       # Service worker (enrutamiento de mensajes)
├── license.js             # Gestor de licencias (activación y validación)
├── content/collector.js   # Script de contenido (extracción de enlaces)
├── popup/
│   ├── popup.html         # Interfaz del popup (controles de escaneo + modal de licencia)
│   ├── popup.css          # Estilos
│   └── popup.js           # Lógica del popup
├── results/
│   ├── results.html       # Página de tabla de resultados completa
│   ├── results.css        # Estilos
│   └── results.js         # Lógica de tabla, búsqueda, filtrado y exportación
├── index.html             # Página de soporte (6 idiomas)
├── privacy-policy.html    # Política de privacidad
├── promo.html             # Plantilla de baldosa promocional
├── screenshot/            # Capturas de pantalla para la tienda
├── assets/                # Iconos
└── _locales/              # i18n (en/zh/ja/de/es/fr)
```

---

## Aviso de derechos de autor

Esta extensión solo lee los elementos de hipervínculo renderizados públicamente (etiquetas `<a>`) de las páginas web para comodidad del usuario. Todo el texto, las imágenes y los derechos de autor del contenido del sitio web pertenecen al editor original. Extraer enlaces no otorga a los usuarios ninguna autorización de derechos de autor sobre el contenido del sitio web.

---

## Aviso sobre el código fuente

> ⚠️ **Este repositorio no publica código fuente.** Contiene únicamente documentación de uso, notas de lanzamiento y recursos de soporte. La extensión se distribuye exclusivamente a través de Chrome Web Store. No se proporcionan paquetes de instalación sin conexión ni código fuente para usuarios finales.

---

## Licencia

Copyright © 2026 LinkHarvest. Todos los derechos reservados.
