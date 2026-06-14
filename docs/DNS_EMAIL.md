# Dominio, DNS y correo institucional

## Dominio personalizado

1. Comprar o administrar `misionalasparasonar.org`.
2. En Cloudflare Workers, abrir el proyecto y entrar a `Settings > Domains & Routes`.
3. Agregar:
   - `misionalasparasonar.org`
   - `www.misionalasparasonar.org`
4. Cloudflare indicará los registros DNS exactos.
5. Esperar propagación y verificar SSL/HTTPS.

## Registros DNS habituales

Cloudflare suele usar:

- `CNAME` para `www` apuntando al destino que indique Cloudflare.
- Registro apex gestionado por Cloudflare para el dominio raíz.

Sigue siempre el valor exacto que muestre Cloudflare.

## Correo institucional

Para usar `contacto@misionalasparasonar.org`, contratar un proveedor como Zoho Mail, Google Workspace, Microsoft 365 o similar.

El proveedor entregará registros DNS similares a:

- `MX`: recibe correos del dominio.
- `SPF`: autoriza servidores de envío. Ejemplo: `v=spf1 include:proveedor.com ~all`.
- `DKIM`: firma criptográfica para mejorar entregabilidad.
- `DMARC`: política antisuplantación. Ejemplo inicial: `v=DMARC1; p=none; rua=mailto:contacto@misionalasparasonar.org`.

No inventes valores definitivos. Copia los registros exactos del proveedor elegido.

## Formularios web

El correo institucional recibe mensajes, pero el sitio necesita un servicio para enviar formularios. Opciones:

- Formspree: fácil para sitios estáticos.
- Resend: flexible y profesional; puede requerir endpoint serverless.
- Cloudflare Workers: control total en el ecosistema Cloudflare.
- Netlify Forms: útil si se alojara en Netlify, no recomendado si el hosting será Cloudflare Workers.

Configura los endpoints en Cloudflare Workers como variables de entorno y nunca guardes claves reales en el repositorio.
