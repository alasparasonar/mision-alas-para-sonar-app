# Checklist de publicación

## Antes de publicar

- Reemplazar logo temporal en `public/logo.svg` por el logo oficial si se recibe el archivo final.
- Actualizar textos de ejemplo con información real de la fundación.
- Actualizar datos de contacto en `src/data/site.json`.
- Actualizar datos de donación en `src/data/donation.json`.
- Reemplazar imágenes de ejemplo por fotos propias o imágenes con licencia adecuada.
- Configurar endpoints reales para formularios.

## GitHub

- Crear repositorio, por ejemplo `mision-alas-para-sonar-app`.
- Subir el proyecto a la rama `main`.
- Proteger credenciales: no subir `.env`.

## Cloudflare Workers

- Project name: `mision-alas-para-sonar-app`.
- Build command: `npm run build`.
- Deploy command: `npx wrangler deploy --assets=./dist`.
- Non-production branch deploy command: `npx wrangler versions upload --assets=./dist`.
- Path: `/`.
- Branch de producción: `main`.

## Variables de entorno

Configurar en Cloudflare Workers:

- `PUBLIC_SITE_URL`: `https://misionalasparasonar.org`
- `PUBLIC_CONTACT_FORM_ENDPOINT`: endpoint del formulario de contacto.
- `PUBLIC_VOLUNTEER_FORM_ENDPOINT`: endpoint del formulario de voluntariado.
- `PUBLIC_DONATION_URL`: link externo de donación, si existe.
- `PUBLIC_WHATSAPP_NUMBER`: número en formato internacional sin `+`.
- `FORMS_TO_EMAIL`: `contacto@misionalasparasonar.org`

## Dominio y SSL

- Agregar `misionalasparasonar.org` como dominio personalizado en Cloudflare Workers.
- Apuntar DNS según indique Cloudflare.
- Activar HTTPS automático.
- Confirmar que `https://misionalasparasonar.org/sitemap-index.xml` responde correctamente.

## CMS

- Editar `public/admin/config.yml`.
- Confirmar que `public/admin/config.yml` apunte al repositorio real: `alasparasonar/mision-alas-para-sonar-app`.
- Configurar OAuth para Decap CMS con GitHub.
- Probar `/admin/` antes de entregar a editores.
