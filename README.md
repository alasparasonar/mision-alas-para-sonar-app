# Fundación Misión Alas para Soñar

Sitio institucional moderno, responsive y administrable para una fundación sin fines de lucro. Incluye páginas de inicio, quiénes somos, programas, proyectos, galería, videos, noticias, donaciones, voluntariado, contacto y transparencia.

## Stack

- Astro
- TypeScript
- Tailwind CSS
- Decap CMS en `/admin`
- Contenido en Markdown y JSON
- Cloudflare Workers con assets estáticos para hosting y despliegue automático

## Instalación local

```bash
npm install
npm run dev
```

El sitio quedará disponible en `http://localhost:4321`.

## Comandos npm

```bash
npm run dev      # desarrollo local
npm run build    # validación y build de producción
npm run preview  # previsualizar dist
```

## Variables de entorno

Copia `.env.example` a `.env` cuando necesites valores locales.

```bash
PUBLIC_SITE_URL=https://misionalasparasonar.org
PUBLIC_CONTACT_FORM_ENDPOINT=
PUBLIC_VOLUNTEER_FORM_ENDPOINT=
PUBLIC_DONATION_URL=
PUBLIC_WHATSAPP_NUMBER=593982470423
RESEND_API_KEY=
FORMS_TO_EMAIL=contacto@misionalasparasonar.org
```

No subas `.env` al repositorio.

## Cómo editar contenido

- Datos generales: `src/data/site.json`
- Quiénes somos: `src/data/about.json`
- Áreas de acción: `src/data/programs.json`
- Donaciones: `src/data/donation.json`
- Galería: `src/data/gallery.json`
- Videos: `src/data/videos.json`
- Transparencia: `src/data/transparency.json`
- Proyectos: `src/content/projects/*.md`
- Noticias: `src/content/news/*.md`

## CMS en `/admin`

El panel está en `public/admin`.

Para producción:

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
2. En Cloudflare Workers & Pages, crea una aplicación conectada al repositorio.
3. Configura:
   - Project name: `mision-alas-para-sonar-app`
   - Build command: `npm run build`
   - Deploy command: `npx wrangler deploy --assets=./dist`
   - Non-production branch deploy command: `npx wrangler versions upload --assets=./dist`
   - Path: `/`
   - Production branch: `main`
4. Agrega las variables de entorno necesarias.
5. Cada push a `main` desplegará automáticamente.

## Dominio propio

1. Compra o administra `misionalasparasonar.org`.
2. En Cloudflare Workers agrega el dominio personalizado.
3. Configura los DNS indicados por Cloudflare.
4. Activa HTTPS automático.
5. Verifica `robots.txt` y `sitemap-index.xml`.

## Correo institucional

Para `contacto@misionalasparasonar.org`, usa Zoho Mail, Google Workspace, Microsoft 365 u otro proveedor.

Configura en DNS los registros que entregue el proveedor:

- MX
- SPF
- DKIM
- DMARC

Más detalle en `docs/DNS_EMAIL.md`.

## Formularios

Los formularios están preparados para usar endpoints externos:

- `PUBLIC_CONTACT_FORM_ENDPOINT`
- `PUBLIC_VOLUNTEER_FORM_ENDPOINT`

Puedes conectarlos a Formspree, Resend con Cloudflare Workers, u otro proveedor. Sin endpoint, quedan como preparación funcional con `mailto:`.

## Mantenimiento básico

- Mantener dependencias actualizadas con cuidado.
- Ejecutar `npm run build` antes de publicar cambios grandes.
- Revisar enlaces, datos de contacto y formularios cada cierto tiempo.
- Actualizar documentos de transparencia regularmente.

## Usar Codex para futuras modificaciones

Puedes pedir cambios como:

- "Agrega una nueva sección de aliados."
- "Cambia la paleta para usar más azul institucional."
- "Conecta el formulario con Resend y Cloudflare Workers."
- "Crea una página para campañas especiales."
- "Optimiza SEO para Google Search Console."
