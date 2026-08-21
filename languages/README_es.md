# LinkHarvest

[English](../README.md) | [中文](README_zh.md) | Español | [Deutsch](README_de.md) | [日本語](README_ja.md) | [Français](README_fr.md)

Una extensión ligera del navegador que extrae todos los hipervínculos de cualquier página web, con filtros inteligentes y exportación CSV.

> Basado en Chromium · Manifest V3 · Sin rastreo · Datos solo locales

---

## Características

| Característica | Descripción |
|----------------|-------------|
| 🔍 **Escaneo con un clic** | Extrae todos los enlaces `<a>` de la página actual |
| 📡 **Monitor DOM en tiempo real** | MutationObserver captura enlaces añadidos dinámicamente (SPA, scroll infinito) |
| 🔎 **Filtro inteligente** | Filtra enlaces de anclaje y pseudo-enlaces JS; distinge internos/externos |
| 📋 **Copia por lotes** | Copia todos los enlaces válidos al portapapeles de una vez |
| 📥 **Exportación CSV** | Codificación UTF-8 BOM — compatible con Excel/WPS |
| 🔒 **Datos solo locales** | Todos los datos se almacenan en la memoria del navegador; se borran al cerrar |
| 🌍 **Multi-idioma** | Inglés, Chino, Japonés, Alemán, Español, Francés |
| ⚡ **Ligero** | JavaScript puro, sin dependencias, paquete < 40KB |
| 🏗️ **Manifest V3** | Solo `activeTab` + `scripting` — permisos mínimos |

---

## Vista previa

<p align="center">
  <img src="../screenshot/promo.png" alt="Vista previa de LinkHarvest" width="640">
</p>

---

## Navegadores compatibles

| Navegador | Estado |
|-----------|--------|
| Google Chrome | ✅ Totalmente compatible |
| Microsoft Edge | ✅ Totalmente compatible |
| Otros navegadores basados en Chromium | ✅ Debería funcionar |

---

## Instalación

1. Abra la página de extensiones de su navegador:
   - **Chrome**: `chrome://extensions/`
   - **Edge**: `edge://extensions/`
2. Active el **Modo de desarrollador** (interruptor superior derecho)
3. Haga clic en **Cargar desempaquetado** y seleccione la carpeta del proyecto
4. Haga clic en el ícono de LinkHarvest en la barra de herramientas

---

## Uso

1. **Abra la página web objetivo** y espere a que el contenido dinámico se cargue
2. **Haga clic en el ícono de LinkHarvest** en la barra de herramientas
3. **Active el monitor DOM** (opcional) — para páginas con scroll infinito o enlaces cargados diferidamente
4. **Haga clic en "Escanear enlaces"** — todos los enlaces se extraen al instante
5. **Ver lista completa** — abre una página de resultados dedicada con vista de tabla
6. **Buscar y filtrar** — use la barra de búsqueda y los filtros para reducir resultados
7. **Copiar o exportar** — copie enlaces al portapapeles o exporte como archivo CSV

> **⚠️ Aviso de exportación CSV:** Los archivos CSV exportados se guardan en el disco local de su dispositivo. Estos archivos son gestionados por usted; la extensión no controla su ciclo de vida. Por favor, elimine manualmente los archivos exportados cuando ya no sean necesarios.

---

## Campos recopilados

| Campo | Descripción |
|-------|-------------|
| `linkText` | Texto del enlace (limpiado) |
| `href` | URL absoluta completa |
| `target` | `_blank` / `_self` |
| `category` | anclaje / pseudo-enlace JS / enlace de protocolo / normal |
| `isInternal` | Si el enlace es del mismo origen |

---

## Privacidad

- Solo permisos `activeTab` + `scripting` — nada más
- `activeTab`: Otorga acceso solo cuando hace clic activamente en el ícono de la extensión
- `scripting`: Se usa para inyectar el script de recolección de enlaces en la página actual
- Sin permiso `<all_urls>` — no accede a páginas sin su acción
- Sin solicitudes de red externas — todo el procesamiento ocurre localmente
- Sin acceso al historial de navegación, sin rastreo de usuarios, sin subida de datos
- Todos los datos de escaneo se almacenan solo en la memoria del navegador y se borran al cerrar la página
- [Privacy Policy](../privacy-policy.html)

### Permisos NO solicitados

| Permiso | Motivo por el cual no se solicita |
|---------|-----------------------------------|
| `<all_urls>` | No accede a páginas sin la acción del usuario |
| `storage` (persistente) | No guarda datos en almacenamiento persistente local |
| `notifications` | No envía notificaciones del sistema |
| `cookies` | No lee ni modifica cookies |
| `webRequest` | No intercepta ni monitorea solicitudes de red |

### Datos NO recopilados

- ❌ Contraseñas, contenido de formularios
- ❌ Cookies, LocalStorage, IndexedDB, datos de SessionStorage
- ❌ Caché del navegador, historial de navegación
- ❌ Credenciales de usuario, información de inicio de sesión
- ❌ Texto del cuerpo de la página, imágenes, videos u otros contenidos multimedia
- ❌ Datos de scripts de terceros, información de seguimiento publicitario
- ❌ Identificadores de dispositivo, direcciones IP, datos de comportamiento del usuario

### Derechos del usuario (GDPR/CCPA)

- **Derecho a detener:** Puede cerrar la extensión o detener el escaneo en cualquier momento
- **Derecho a eliminar:** Todos los datos en memoria se borran automáticamente al cerrar la página o el navegador; también puede eliminar manualmente los archivos CSV exportados localmente
- **Derecho de acceso:** Esta extensión no almacena ningún dato personal identificable del usuario
- **Derecho a la portabilidad de datos:** La función de exportación CSV permite la exportación de datos
- **Derecho a exclusión voluntaria:** Esta extensión no involucra ningún seguimiento de datos ni perfilado

---

---

## Aviso de código fuente

> ⚠️ **Este repositorio no publica el código fuente.** Contiene únicamente documentación de uso, notas de versión y recursos de soporte. La extensión se distribuye exclusivamente a través de Chrome Web Store. No se proporcionan paquetes de instalación sin conexión ni código fuente para usuarios finales.


## Aviso de derechos de autor

Esta extensión solo lee los elementos de hipervínculo renderizados públicamente (`<a>`) de las páginas web para conveniencia del usuario. Todos los derechos de autor del texto, imágenes y contenido del sitio web pertenecen al editor original. La extracción de enlaces no otorga a los usuarios ningún derecho de autor sobre el contenido del sitio web. Los usuarios deben cumplir con las leyes locales de propiedad intelectual al utilizar los enlaces extraídos.

### Restricciones de uso

Los usuarios NO deben usar esta extensión para:

- Realizar rastreo masivo de alta frecuencia que viole los términos de servicio del sitio web objetivo
- Realizar descargas masivas de recursos en violación de las leyes de propiedad intelectual
- Llevar a cabo la reproducción o distribución no autorizada a gran escala de contenido protegido por derechos de autor
- Violar los protocolos `robots.txt` o los acuerdos de usuario del sitio web objetivo

Se recomienda a los usuarios revisar el archivo `robots.txt` y los términos de servicio del sitio web objetivo antes de extraer enlaces masivamente. Toda responsabilidad por el uso indebido recae en el usuario.

---

## Licencia

Copyright © 2026 LinkHarvest. Todos los derechos reservados.

Este proyecto está licenciado bajo la [Licencia MIT](../LICENSE). Usted es libre de usar, modificar y distribuir este software de acuerdo con los términos de la licencia.

---

## Notas de auditoría

Para los revisores de tiendas de aplicaciones, esta extensión declara lo siguiente:

| Elemento | Detalles |
|----------|----------|
| Permisos solicitados | Solo `activeTab`, `scripting` |
| Uso de `activeTab` | Acceso temporal a la pestaña actual cuando el usuario hace clic en el ícono de la extensión |
| Uso de `scripting` | Inyección del script de recolección de enlaces al escanear por acción del usuario |
| Solicitudes de red | Ninguna — todo el procesamiento es local |
| Almacenamiento de datos | Solo memoria de sesión del navegador (`chrome.storage.session`) |
| Servicios de terceros | Ninguno |
| Rastreo de usuarios | Ninguno |
