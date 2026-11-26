# Mis Finanzas — versión móvil

Panel financiero personal como PWA: se instala en la pantalla de inicio del móvil y funciona sin conexión.

## Qué incluye
- `index.html` — la app completa (gastos, ingresos, previsión, comparativa, presupuestos, hipoteca, préstamo, inversión).
- `sw.js` — service worker: caché offline, red primero para recibir actualizaciones.
- `manifest.webmanifest` + `icons/` — instalación como app.
- `xlsx.full.min.js` — SheetJS 0.18.5 local (importar/exportar Excel sin conexión).

## Funciones móviles
- **＋ Alta rápida**: botón flotante; importe primero, recuerda la última categoría, Hoy/Ayer.
- **Deshacer**: al borrar o añadir aparece un aviso con *Deshacer* durante 5 s.
- **Selector de mes** en Resumen: ‹ › o deslizar el dedo.
- **Bloqueo con PIN** (Más → Activar bloqueo con PIN). Protección de acceso, no cifra los datos. Se vuelve a pedir tras 1 min en segundo plano. Si se olvida, hay que borrar los datos del sitio en el navegador.
- **Tema automático** según el ajuste del dispositivo (o Claro/Oscuro fijo).
- **Copias de seguridad**: aviso en Resumen si hace más de 30 días de la última; se pide al navegador almacenamiento persistente.

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
