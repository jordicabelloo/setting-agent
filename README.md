# setting-agent

Skill de [Claude Code](https://claude.com/claude-code) hecha por [PRYXIS](https://pryxis.es).

Le da a tu Claude Code local el contexto para **construir un Setting Agent**: un agente
de IA que responde y cualifica leads en Instagram y WhatsApp y agenda llamadas
automaticamente, las 24 horas.

Incluye la arquitectura, las APIs de Meta (ventanas de 24h, plantillas, precios), el
framework de cualificacion y conversacion, la plantilla de system prompt con guardrails
y el cumplimiento RGPD/LSSI.

## Instalacion

Clona el repo dentro de tu carpeta de skills de Claude Code:

```bash
git clone https://github.com/jordicabelloo/setting-agent \
  ~/.claude/skills/setting-agent
```

A partir de ahi, Claude Code cargara la skill cuando le pidas construir o disenar un
setting agent (o menciones "setter", "cualificar leads", "agendar llamadas").

## Uso

Pidele a Claude algo como:

> Ayudame a construir un setting agent para mi negocio de coaching en Instagram y WhatsApp.

Claude usara esta skill como contexto: seguira el workflow de construccion, aplicara los
guardrails y consultara las referencias para el detalle tecnico.

## Contenido

- `SKILL.md` -- Definicion de la skill y workflow de construccion.
- `references/architecture.md` -- Componentes, flujo y stack.
- `references/meta-apis.md` -- Instagram y WhatsApp Cloud API.
- `references/qualification-and-conversation.md` -- Cualificacion, conversacion, show-rate.
- `references/system-prompt-and-guardrails.md` -- System prompt, RAG y guardrails.
- `references/compliance.md` -- RGPD, LOPDGDD, LSSI y opt-in.

## Licencia

MIT. Uso libre. Hecho por PRYXIS.
