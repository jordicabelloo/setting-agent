# Arquitectura del Setting Agent

## Componentes

1. **Canal**: Instagram y/o WhatsApp, por donde entra y sale cada mensaje.
2. **Webhook**: endpoint publico que recibe cada mensaje entrante de Meta en tiempo real.
3. **Orquestador**: logica que identifica al lead, recupera historial y estado, y llama al cerebro.
4. **Cerebro (LLM)**: modelo con function calling que entiende, decide y redacta la respuesta.
5. **Herramientas**: calendario, CRM/base de datos y aviso al closer.

## Flujo de un mensaje

1. El lead escribe por Instagram o WhatsApp.
2. Meta envia el mensaje al webhook.
3. El orquestador identifica al lead y recupera su historial y estado de cualificacion.
4. Llama al LLM con el system prompt, el historial y las herramientas disponibles.
5. El LLM decide: responde, pregunta, agenda, descalifica o escala.
6. Si toca, invoca una herramienta (reservar en el calendario, escribir en el CRM).
7. La respuesta sale al lead por el mismo canal, en segundos.

## Stack recomendado

| Pieza | Opcion recomendada | Alternativas |
|-------|--------------------|--------------|
| Canal | WhatsApp Cloud API + Instagram API | BSP (360dialog, Twilio) |
| Backend | Python o Node en un VPS propio | Serverless (con cuidado con el estado) |
| Cerebro | LLM potente con function calling | Modelo local por privacidad |
| Base de datos | PostgreSQL | SQLite para empezar |
| Calendario | Cal.com o Calendly | Google Calendar directo |

## Estado y memoria

- Guardar por lead: canal, handle/telefono, historial de mensajes, respuestas de cualificacion, puntuacion y estado (nuevo, cualificando, agendado, descartado, escalado).
- El orquestador recupera este estado en cada mensaje para que el LLM tenga contexto y no repita preguntas.
- La ventana de contexto del LLM debe incluir: system prompt, resumen del lead, historial reciente y las herramientas.

## Principio

Infraestructura propia y APIs oficiales. Las automatizaciones que scrapean o simulan
la app de Instagram/WhatsApp acaban baneando la cuenta del cliente. Todo lo que toque
Meta pasa por la puerta oficial (Graph API / Cloud API).
