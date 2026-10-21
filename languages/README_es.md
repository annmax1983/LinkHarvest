# LinkHarvest — Extractor y escáner de enlaces

[English](../README.md) | [中文](README_zh.md) | Español | [Deutsch](README_de.md) | [日本語](README_ja.md) | [Français](README_fr.md)

Una extensión ligera para el navegador que extrae todos los hipervínculos de cualquier página web, con filtrado inteligente, exportación a CSV / JSON y revisión de enlaces opcional.

> Basada en Chromium · Manifest V3 · Sin rastreo · Datos solo locales

---

## ¿Por qué LinkHarvest?

La mayoría de herramientas de extracción de enlaces son servicios online que requieren subir el contenido de la página. LinkHarvest se ejecuta completamente en tu navegador — tus datos nunca salen de tu dispositivo.

| Ventaja | Detalle |
|---------|--------|
| 🔍 **Escanear con un clic** | Extrae todos los enlaces de etiquetas `<a>` de la página actual |
| 📡 **Monitorización DOM en tiempo real** | MutationObserver captura enlaces añadidos dinámicamente (SPA, scroll infinito) |
| 🔎 **Filtrado inteligente** | Filtros por inclusión/exclusión de palabras clave, ordenación por columnas; filtra enlaces ancla y pseudo-enlaces JS; distingue interno/externo |
| 💾 **Filtros guardados** | Asigna un nombre a la combinación de filtros actual y reutilízala con un clic (guardado localmente) |
| 📋 **Copia en varios formatos** | Copia los enlaces filtrados como lista de URLs, Markdown, lista HTML `<a>` o JSON Lines (gratis) |
| 🌐 **Abrir en pestañas** | Abre los enlaces filtrados en pestañas de fondo con retardo ajustable (gratis) |
| 🖱️ **Menú contextual** | Clic derecho en cualquier página → "Extraer enlaces de la página", sin necesidad de popup |
| 🔢 **Conteo de apariciones** | Registra cuántas veces aparece cada URL en la página |
| 📥 **Exportación JSON / TXT** | Archivo JSON estructurado y lista de URLs (gratis) |
| 📥 **Exportación CSV** | Codificación UTF-8 BOM — compatible con Excel/WPS (gratis) |
| 🩺 **Revisión de enlaces** | Comprueba el estado HTTP de los enlaces filtrados y marca enlaces rotos, bloqueados, redirigidos e inaccesibles; vista previa gratuita de 100 enlaces por ejecución (⭐ Premium: hasta 2.000 enlaces + informe CSV) |
| 🔒 **Datos solo locales** | Los resultados del escaneo solo viven en la memoria del navegador (se borran al cerrar la página); los filtros guardados y las preferencias de interfaz se guardan en el localStorage de este navegador y nunca se suben |
| 🌍 **Multi-idioma** | Soporta inglés, chino, japonés, alemán, español y francés |
| 🌙 **Modo oscuro** | Sigue automáticamente el tema del sistema |
| ⚡ **Ligera** | JavaScript vanilla puro, cero dependencias, paquete de menos de 100 KB |
| 🏗️ **Manifest V3** | Usa `activeTab` + `scripting` + `storage` + `contextMenus` — permisos mínimos |

---

## Gratis vs Premium

| Plan | Funcionalidades |
|------|----------|
| **Gratis** | Escanear enlaces, monitorización DOM en tiempo real, buscar y filtrar, filtros guardados, copia en varios formatos, abrir en pestañas, exportación TXT / JSON / CSV, modo oscuro, vista previa de revisión de enlaces (100 enlaces por ejecución) |
| **⭐ Premium** | Revisión de enlaces completa — hasta 2.000 enlaces por ejecución y exportación de un informe CSV con códigos de estado, destinos de redirección y tiempos de respuesta |

Todas las funcionalidades principales y la **exportación TXT / JSON / CSV** son gratuitas para siempre. La **vista previa de revisión** es gratis; la **revisión completa y el informe** requieren una licencia VKT Premium.

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
   - 💾 Guarda esa combinación de filtros como preajuste con nombre y reutilízala con un clic
   - 🌐 Abre los enlaces filtrados en pestañas de fondo con retardo ajustable
7. **Copiar o exportar** — copia enlaces como URLs, Markdown, HTML o JSON Lines (gratis), exporta TXT / JSON / CSV con conteo de apariciones (gratis)
8. **Ejecutar revisión de enlaces** — comprueba el estado HTTP de los enlaces filtrados y detecta enlaces rotos, bloqueados, redirigidos e inaccesibles; la vista previa gratuita cubre 100 enlaces por ejecución, Premium hasta 2.000 y exporta un informe CSV

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
- **Acceso opcional a sitios (revisión de enlaces)** — El navegador solicita permiso al iniciar una revisión. Las solicitudes van directamente desde tu navegador a cada URL (HTTP HEAD/GET, sin cookies); solo se guardan en memoria el código de estado, el destino de redirección y el tiempo de respuesta. No se lee ni se sube el contenido de las páginas.
- **Licencia (opcional)** — Solo si activas una licencia de pago: la clave de licencia y un identificador de instalación aleatorio + metadatos del navegador se envían a `api.annmax1983.com` para activar/validar la licencia. Esto nunca incluye tus datos de escaneo, historial de navegación ni datos personales.
- Sin acceso a todos los sitios por defecto — el acceso es opcional y solo se solicita al iniciar la revisión de enlaces
- Sin solicitudes de red externas excepto la validación opcional de la licencia y las revisiones que tú inicies
- Sin acceso al historial de navegación, sin rastreo de usuarios, sin subida de datos
- [Política de privacidad](privacy-policy.html)

---

## Aviso de derechos de autor

Esta extensión solo lee los elementos de hipervínculo renderizados públicamente (etiquetas `<a>`) de las páginas web para comodidad del usuario. Todo el texto, las imágenes y los derechos de autor del contenido del sitio web pertenecen al editor original. Extraer enlaces no otorga a los usuarios ninguna autorización de derechos de autor sobre el contenido del sitio web.

---

## Aviso sobre el código fuente

> ⚠️ **Este repositorio no publica código fuente.** Contiene únicamente documentación de uso, notas de lanzamiento y recursos de soporte. La extensión se distribuye exclusivamente a través de Chrome Web Store. No se proporcionan paquetes de instalación sin conexión ni código fuente para usuarios finales.

---

## Licencia

Copyright © 2026 LinkHarvest. Todos los derechos reservados.
