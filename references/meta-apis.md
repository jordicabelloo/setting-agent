# APIs de Meta: Instagram y WhatsApp

## Instagram: API de mensajeria

### Requisitos
- Cuenta de Instagram profesional (empresa o creador), vinculada a una pagina y a Meta Business.
- App en Meta for Developers con permisos de mensajeria de Instagram.
- Webhook verificado para recibir mensajes entrantes.

### La ventana de 24 horas
Cuando el usuario escribe, se abre una ventana de 24h en la que puedes responder con
libertad, incluido contenido promocional. Cada mensaje del usuario reinicia el
contador. Pasadas 24h sin respuesta del usuario, no puedes enviarle mensajes libres
de forma automatica.

### La etiqueta HUMAN_AGENT (7 dias)
Amplia la ventana de respuesta de 24h a 7 dias, pero SOLO para mensajes enviados por
un agente humano real. Usarla con mensajes automaticos es una violacion de politica y
la API lo bloquea. Cualquier reactivacion fuera de la ventana la lanza un humano, no
el bot.

### Tactica clave
Dentro de las 24h, el agente trabaja a maxima velocidad con un objetivo: conseguir el
numero de WhatsApp del lead antes de que la ventana expire, para continuar sin
restricciones. WhatsApp permite reactivar con plantillas en cualquier momento;
Instagram no.

## WhatsApp: Business Platform (Cloud API)

### La ventana de servicio de 24 horas
Cuando el usuario escribe, se abre una ventana de 24h en la que los mensajes de
servicio (respuestas libres) son GRATIS. Fuera de esa ventana, para iniciar tu una
conversacion necesitas una plantilla pre-aprobada.

### Plantillas y categorias
Las plantillas se aprueban una vez (de minutos a un par de dias) y se reutilizan. La
categoria determina el precio:

| Categoria | Para que | Coste relativo |
|-----------|----------|----------------|
| Marketing | Promos, reactivacion comercial | El mas caro |
| Utility | Recordatorios, confirmaciones, seguimiento | Mucho mas barato |
| Authentication | Codigos y verificacion | Barato |

### Precios (modelo por mensaje, desde julio de 2025)
- Meta cobra **por mensaje** (antes por conversacion de 24h).
- Los mensajes de servicio dentro de la ventana de 24h son **gratis**.
- Solo pagas cuando se **entrega una plantilla**; el precio depende de categoria y pais.
- Las plantillas **utility** dentro de una ventana de servicio abierta suelen ser gratis.
- **Utility y authentication** son mucho mas baratas que **marketing** y tienen descuentos por volumen.

### Optimizacion de coste
Disenar el sistema para vivir dentro de la ventana de 24h siempre que se pueda (ahi
los mensajes son gratis) y usar plantillas utility (no marketing) para recordatorios y
confirmaciones.

### Opt-in
Meta (y la ley en la UE) exige consentimiento del usuario para recibir mensajes del
negocio. Cuando el lead escribe primero, hay base para conversar; para enviarle
plantillas de marketing mas adelante hace falta un opt-in claro y guardado.

## Referencia
Verificar siempre los detalles y precios vigentes en la documentacion oficial de Meta
for Developers (WhatsApp Business Platform e Instagram Messaging API), porque cambian.
