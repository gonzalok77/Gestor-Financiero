# Mis Finanzas — versión móvil

Panel financiero personal como PWA: se instala en la pantalla de inicio del móvil y funciona sin conexión.

## Qué incluye
- `index.html` — la app completa (gastos, ingresos, previsión, comparativa, presupuestos, hipoteca, préstamo, inversión).
- `sw.js` — service worker: caché offline, red primero para recibir actualizaciones.
- `manifest.webmanifest` + `icons/` — instalación como app.
- `xlsx.full.min.js` — SheetJS 0.18.5 local (importar/exportar Excel sin conexión).

## Datos
Todo se guarda **solo en el navegador del dispositivo** (`localStorage`, clave `pf_data_v3`). Nada se sube a ningún servidor.
- Pasar datos desde la versión de escritorio: allí **Exportar (JSON)** → aquí **Más → Importar JSON**.
- Copia de seguridad: **Más → Exportar (JSON)** abre la hoja de compartir del móvil (Archivos, Drive…).
- Borrar los datos del navegador o desinstalar la app borra los datos: exporta con regularidad.

## Publicar
Necesita servirse por HTTPS (el service worker no funciona abriendo el archivo directamente).
- **GitHub Pages**: Settings → Pages → Deploy from branch → `main` / root. En un repositorio privado requiere GitHub Pro/Team; la web publicada es pública aunque el repo sea privado.
- Alternativas gratuitas con repo privado: Cloudflare Pages o Netlify conectados al repositorio.

## Instalar en el móvil
- **iPhone (Safari)**: Compartir → Añadir a pantalla de inicio.
- **Android (Chrome)**: menú ⋮ → Instalar aplicación.

## Actualizar
Tras cambiar archivos, sube la versión de `CACHE` en `sw.js` (`finanzas-v2`, …) para forzar la recarga en los dispositivos.
