# Censo Materno — sitio web

Landing de una sola página (HTML estático, ES/EN). No requiere build ni dependencias.

## Publicar en GitHub Pages
1. Sube el contenido de esta carpeta a la raíz del repositorio (`index.html`, `.nojekyll`, `README.md`).
2. En el repositorio: **Settings → Pages → Build and deployment**.
3. Source: **Deploy from a branch** → Branch: `main` / carpeta `/ (root)` → **Save**.
4. En 1–2 minutos queda en `https://<usuario>.github.io/<repo>/` (o `https://<usuario>.github.io/` si el repo se llama `<usuario>.github.io`).

## Compra (checkout)
- `checkoutUrl` (en `window.CENSO_SITE`, `index.html`) → `checkout.html` ("Comprar Censo" / "Compra ahora").
- `checkout.html` llama a las Cloud Functions `createPayPalOrder` y `capturePayPalOrder` (proyecto `censo-materno`, `us-central1`), redirige a PayPal y, al volver, muestra `licenseId` + `licenseKey` al comprador.
- `window.CENSO_CHECKOUT.sandbox` (en `checkout.html`) muestra el aviso de "Modo de prueba"; ponlo en `false` al pasar a producción.

## Pendiente de configurar
- `trialUrl` → hoy `FIREBASE_TRIAL_URL_PENDING` ("Pruébalo gratis"). Mientras termine en `_PENDING`, el botón no navega y avisa en la consola.

## Notas
- Nunca pongas secretos de PayPal ni claves privadas en este archivo; viven en Firebase (Secret Manager).
- La configuración web de Firebase (`firebaseConfig`) es pública por diseño, pero conviene restringir la API key por dominio en Google Cloud y proteger todo con reglas de seguridad / App Check.
