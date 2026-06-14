# Checklist de publicacion

## Antes de publicar

- Reemplazar logo temporal en `public/logo.svg` por el logo oficial si se recibe el archivo final.
- Actualizar textos de ejemplo con informacion real de la fundacion.
- Actualizar datos de contacto en `src/data/site.json`.
- Actualizar datos de donacion en `src/data/donation.json`.
- Reemplazar imagenes de ejemplo por fotos propias o imagenes con licencia adecuada.
- Configurar endpoints reales para formularios.

## GitHub

- Crear repositorio, por ejemplo `mision-alas-para-sonar-app`.
- Subir el proyecto a la rama `main`.
- Proteger credenciales: no subir `.env`.

## Cloudflare Pages

- Project name: `mision-alas-para-sonar-app`.
- Build command: `npm run build`.
- Deploy command: `npx wrangler pages deploy dist --project-name=mision-alas-para-sonar-app`.
- Branch de produccion: `main`.

## Variables de entorno

Configurar en Cloudflare Pages:

- `PUBLIC_SITE_URL`: `https://misionalasparasonar.org`
- `PUBLIC_CONTACT_FORM_ENDPOINT`: endpoint del formulario de contacto.
- `PUBLIC_VOLUNTEER_FORM_ENDPOINT`: endpoint del formulario de voluntariado.
- `PUBLIC_DONATION_URL`: link externo de donacion, si existe.
- `PUBLIC_WHATSAPP_NUMBER`: numero en formato internacional sin `+`.
- `FORMS_TO_EMAIL`: `contacto@misionalasparasonar.org`

## Dominio y SSL

- Agregar `misionalasparasonar.org` como dominio personalizado en Cloudflare Pages.
- Apuntar DNS segun indique Cloudflare.
- Activar HTTPS automatico.
- Confirmar que `https://misionalasparasonar.org/sitemap-index.xml` responde correctamente.

## CMS

- Editar `public/admin/config.yml`.
- Confirmar que `public/admin/config.yml` apunte al repositorio real: `alasparasonar/mision-alas-para-sonar-app`.
- Configurar OAuth para Decap CMS con GitHub.
- Probar `/admin/` antes de entregar a editores.
