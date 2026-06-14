# Dominio, DNS y correo institucional

## Dominio personalizado

1. Comprar o administrar `misionalasparasonar.org`.
2. En Cloudflare Pages, abrir el proyecto y entrar a `Custom domains`.
3. Agregar:
   - `misionalasparasonar.org`
   - `www.misionalasparasonar.org`
4. Cloudflare indicara los registros DNS exactos.
5. Esperar propagacion y verificar SSL/HTTPS.

## Registros DNS habituales

Cloudflare Pages suele usar:

- `CNAME` para `www` apuntando al subdominio de Pages.
- Registro apex gestionado por Cloudflare para el dominio raiz.

Sigue siempre el valor exacto que muestre Cloudflare.

## Correo institucional

Para usar `contacto@misionalasparasonar.org`, contratar un proveedor como Zoho Mail, Google Workspace, Microsoft 365 o similar.

El proveedor entregara registros DNS similares a:

- `MX`: recibe correos del dominio.
- `SPF`: autoriza servidores de envio. Ejemplo: `v=spf1 include:proveedor.com ~all`.
- `DKIM`: firma criptografica para mejorar entregabilidad.
- `DMARC`: politica antisuplantacion. Ejemplo inicial: `v=DMARC1; p=none; rua=mailto:contacto@misionalasparasonar.org`.

No inventes valores definitivos. Copia los registros exactos del proveedor elegido.

## Formularios web

El correo institucional recibe mensajes, pero el sitio necesita un servicio para enviar formularios. Opciones:

- Formspree: facil para sitios estaticos.
- Resend: flexible y profesional; puede requerir endpoint serverless.
- Cloudflare Workers: control total en el ecosistema Cloudflare.
- Netlify Forms: util si se alojara en Netlify, no recomendado si el hosting sera Cloudflare Pages.

Configura los endpoints en Cloudflare Pages como variables de entorno y nunca guardes claves reales en el repositorio.
