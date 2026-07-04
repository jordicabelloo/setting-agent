---
name: setting-agent
description: Usar cuando el usuario quiere construir, disenar o implementar un agente "setter" de IA que responde y cualifica leads en Instagram o WhatsApp y agenda llamadas automaticamente. Dispara con "setting agent", "setter IA", "cualificar leads", "agendar llamadas automatico", "bot de leads en Instagram/WhatsApp", "appointment setter", "reservar llamadas 24/7".
---

# Setting Agent (agente de cualificacion y reserva de llamadas)

## Overview

Esta skill le da a Claude el contexto para construir un Setting Agent: un agente de
IA que atiende cada lead al instante en Instagram y WhatsApp, lo cualifica con
criterio, agenda la llamada en un calendario y le pasa al closer un lead caliente
con contexto. No es un chatbot de arbol: es un agente que entiende, decide y actua
dentro de limites claros.

## When to Use

- El usuario quiere montar un agente que responda y cualifique leads en DMs (Instagram/WhatsApp).
- El usuario quiere automatizar la reserva de llamadas de venta (appointment setting).
- El usuario habla de "setter", "cualificar leads", "speed to lead", "reservar demos/llamadas".
- El usuario quiere reducir el tiempo de respuesta a leads a segundos, 24/7.

## Prerequisites

- Cuenta de Instagram profesional vinculada a Meta Business, y WhatsApp Business Platform (Cloud API) o un BSP (360dialog, Twilio).
- Un LLM con function calling (tool use).
- Un backend (Python o Node) con un webhook publico para recibir mensajes de Meta.
- Una base de datos (PostgreSQL recomendado) y un calendario con API (Cal.com, Calendly o Google Calendar).
- Conocimiento del RGPD/LSSI si se opera en la UE (ver `references/compliance.md`).

## Build Workflow

Construir el agente en este orden. No saltarse la cualificacion ni los guardrails.

### 1. Definir la oferta y la logica de cualificacion

- Documentar la oferta real (que vende, precio, cliente ideal) como fuente para el RAG.
- Definir 4-6 preguntas de cualificacion adaptadas a la oferta (framework BANT/CHAMP). Ver `references/qualification-and-conversation.md`.
- Definir el criterio de decision: quien encaja (agendar), quien es dudoso (repreguntar), quien no (descalificar con elegancia).

### 2. Disenar la conversacion

- Escribir la apertura, el ritmo (un mensaje = una idea), el manejo de objeciones y la transicion a la llamada. Ver `references/qualification-and-conversation.md`.
- Regla: velocidad primero (responder en segundos), tono humano, nunca muro de texto ni menus de botones.

### 3. Conectar los canales (APIs oficiales)

- Instagram: API de mensajeria, ventana de 24h, etiqueta HUMAN_AGENT. Objetivo tactico: llevar el lead a WhatsApp antes de que expire la ventana.
- WhatsApp: Cloud API, ventana de servicio de 24h, plantillas (categoria utility para recordatorios), opt-in. Detalles y precios en `references/meta-apis.md`.
- Verificar el webhook y procesar cada mensaje entrante en tiempo real.

### 4. Construir el cerebro (LLM)

- Escribir el system prompt (rol, objetivo, reglas duras, flujo, escalado). Plantilla en `references/system-prompt-and-guardrails.md`.
- Conectar RAG con los documentos de la oferta para que el agente NO se invente precios ni promesas.
- Definir guardrails y las herramientas (function calling): consultar oferta, ver huecos, agendar, guardar lead, escalar a humano.

### 5. Booking y reduccion de no-shows

- Integrar el calendario para leer huecos reales y escribir la cita.
- Montar la secuencia de recordatorios (confirmacion inmediata, 24h antes, 2h antes) con plantillas utility. Sube el show-rate; ver `references/qualification-and-conversation.md`.

### 6. Handoff al closer y CRM

- Al agendar, pasar al closer un resumen (quien, que le duele, urgencia, presupuesto, historial).
- Escribir cada lead y su estado en el CRM/DB. En cuanto hay interes real, escalar a un humano.

### 7. Cumplimiento y lanzamiento

- Aplicar opt-in y aviso de privacidad (`references/compliance.md`).
- Probar con casos reales y casos raros antes del go-live. No lanzar a leads reales sin pruebas.

## Architecture (resumen)

```
Lead (Instagram / WhatsApp)
  -> Webhook (recibe cada mensaje de Meta)
  -> Orquestador (identifica lead, recupera historial y estado)
  -> Cerebro LLM (system prompt + RAG de la oferta + herramientas)
       decide: responder / preguntar / agendar / descalificar / escalar
  -> Herramientas: calendario, CRM/DB, aviso al closer
  -> Respuesta al lead por el mismo canal, en segundos
```

Detalle completo en `references/architecture.md`.

## Guardrails (no negociables)

- Nunca dar un precio o dato que no este en la base de conocimiento (RAG).
- Nunca prometer un resultado concreto ("ganaras X").
- Nunca presionar ni agendar a quien no encaja: destroza el show-rate.
- Escalar a un humano ante peticion explicita, queja o caso sensible.
- No sonar a bot: mensajes cortos, una pregunta cada vez.

## Resources

- `references/architecture.md` -- Componentes, flujo de mensaje y stack recomendado.
- `references/meta-apis.md` -- Instagram API y WhatsApp Cloud API: ventanas 24h, HUMAN_AGENT, plantillas, categorias, precios (jul-2025), opt-in.
- `references/qualification-and-conversation.md` -- Framework de cualificacion, preguntas, diseno de conversacion, objeciones, booking y show-rate.
- `references/system-prompt-and-guardrails.md` -- Plantilla de system prompt, RAG, guardrails y herramientas (function calling).
- `references/compliance.md` -- RGPD, LOPDGDD, LSSI y opt-in para la UE.

## Key Principles

1. El setter no vende: consigue la llamada con la persona correcta y la prepara. Se mide en llamadas cualificadas que ademas asisten.
2. Velocidad y relevancia ganan: responder en segundos con criterio bate al mejor producto que responde tarde.
3. Conocimiento conectado (RAG) y limites claros (guardrails) no son opcionales: sin ellos el agente inventa y quema leads.
4. APIs oficiales de Meta siempre. Nada de automatizaciones que simulan la app: banean la cuenta del cliente.
