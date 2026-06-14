# Fundacion Alas para Sonar

Sitio institucional moderno, responsive y administrable para una fundacion sin fines de lucro. Incluye paginas de inicio, quienes somos, programas, proyectos, galeria, videos, noticias, donaciones, voluntariado, contacto y transparencia.

## Stack

- Astro
- TypeScript
- Tailwind CSS
- Decap CMS en `/admin`
- Contenido en Markdown y JSON
- Cloudflare Workers con assets estaticos para hosting y despliegue automatico

## Instalacion local

```bash
npm install
npm run dev
```

El sitio quedara disponible en `http://localhost:4321`.

## Comandos npm

```bash
npm run dev      # desarrollo local
npm run build    # validacion y build de produccion
npm run preview  # previsualizar dist
```

## Variables de entorno

Copia `.env.example` a `.env` cuando necesites valores locales.

```bash
PUBLIC_SITE_URL=https://misionalasparasonar.org
PUBLIC_CONTACT_FORM_ENDPOINT=
PUBLIC_VOLUNTEER_FORM_ENDPOINT=
PUBLIC_DONATION_URL=
PUBLIC_WHATSAPP_NUMBER=593999999999
RESEND_API_KEY=
FORMS_TO_EMAIL=contacto@misionalasparasonar.org
```

No subas `.env` al repositorio.

## Como editar contenido

- Datos generales: `src/data/site.json`
- Quienes somos: `src/data/about.json`
- Areas de accion: `src/data/programs.json`
- Donaciones: `src/data/donation.json`
- Galeria: `src/data/gallery.json`
- Videos: `src/data/videos.json`
- Transparencia: `src/data/transparency.json`
- Proyectos: `src/content/projects/*.md`
- Noticias: `src/content/news/*.md`

## CMS en `/admin`

El panel esta en `public/admin`.

Para produccion:

1. Edita `public/admin/config.yml`.
2. Confirma que `public/admin/config.yml` apunte al repo real: `alasparasonar/mision-alas-para-sonar-app`.
3. Configura un backend OAuth para Decap CMS con GitHub.
4. Publica en Cloudflare Workers.
5. Entra a `https://misionalasparasonar.org/admin/`.

Para pruebas locales del CMS puedes usar:

```bash
npx decap-server
npm run dev
```

Luego abre `http://localhost:4321/admin/`.

## Despliegue en Cloudflare Workers

1. Sube el proyecto a GitHub.
2. En Cloudflare, crea una aplicacion conectada al repositorio.
3. Configura:
   - Project name: `mision-alas-para-sonar-app`
   - Build command: `npm run build`
   - Deploy command: `npx wrangler deploy`
   - Production branch: `main`
4. Agrega las variables de entorno necesarias.
5. Cada push a `main` desplegara automaticamente.

## Dominio propio

1. Compra o administra `misionalasparasonar.org`.
2. En Cloudflare Workers agrega el dominio personalizado.
3. Configura los DNS indicados por Cloudflare.
4. Activa HTTPS automatico.
5. Verifica `robots.txt` y `sitemap-index.xml`.

## Correo institucional

Para `contacto@misionalasparasonar.org`, usa Zoho Mail, Google Workspace, Microsoft 365 u otro proveedor.

Configura en DNS los registros que entregue el proveedor:

- MX
- SPF
- DKIM
- DMARC

Mas detalle en `docs/DNS_EMAIL.md`.

## Formularios

Los formularios estan preparados para usar endpoints externos:

- `PUBLIC_CONTACT_FORM_ENDPOINT`
- `PUBLIC_VOLUNTEER_FORM_ENDPOINT`

Puedes conectarlos a Formspree, Resend con Cloudflare Workers, u otro proveedor. Sin endpoint, quedan como preparacion funcional con `mailto:`.

## Mantenimiento basico

- Mantener dependencias actualizadas con cuidado.
- Ejecutar `npm run build` antes de publicar cambios grandes.
- Revisar enlaces, datos de contacto y formularios cada cierto tiempo.
- Actualizar documentos de transparencia regularmente.

## Usar Codex para futuras modificaciones

Puedes pedir cambios como:

- "Agrega una nueva seccion de aliados."
- "Cambia la paleta para usar mas azul institucional."
- "Conecta el formulario con Resend y Cloudflare Workers."
- "Crea una pagina para campanas especiales."
- "Optimiza SEO para Google Search Console."
