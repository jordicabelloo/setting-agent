<p align="center">
  <img src="https://img.shields.io/badge/Claude_Code-Skill-blueviolet?style=for-the-badge&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIyNCIgaGVpZ2h0PSIyNCIgdmlld0JveD0iMCAwIDI0IDI0IiBmaWxsPSJub25lIiBzdHJva2U9IndoaXRlIiBzdHJva2Utd2lkdGg9IjIiIHN0cm9rZS1saW5lY2FwPSJyb3VuZCIgc3Ryb2tlLWxpbmVqb2luPSJyb3VuZCI+PHBhdGggZD0iTTEyIDJMNiA3djEwbDYgNSA2LTV2LTEweiIvPjwvc3ZnPg==" alt="Claude Code Skill">
  <img src="https://img.shields.io/badge/-Ventas_+_Setter-FF6B35?style=for-the-badge" alt="Ventas y Setter">
  <img src="https://img.shields.io/badge/Por-PRYXIS-2ea44f?style=for-the-badge" alt="Por PRYXIS">
  <img src="https://img.shields.io/badge/Licencia-MIT-blue?style=for-the-badge" alt="Licencia MIT">
</p>

<h1 align="center">setting-agent</h1>

<p align="center">
  <strong>Cualifica leads y reserva llamadas mientras duermes.</strong><br>
  Skill de Claude Code para construir un Setting Agent en Instagram y WhatsApp.
</p>

<p align="center">
  <a href="#el-problema">El problema</a> &bull;
  <a href="#que-construye">Que construye</a> &bull;
  <a href="#instalacion">Instalacion</a> &bull;
  <a href="#uso">Uso</a> &bull;
  <a href="#que-incluye">Que incluye</a>
</p>

---

## El problema

Un lead te escribe a las 23:47 de un domingo. Para cuando respondes, ya se ha enfriado o se ha ido a otro. No puedes estar disponible siempre, ni cualificar a cincuenta personas a la vez con el mismo criterio.

**setting-agent** le da a tu Claude Code el contexto para construir el sistema que atiende, cualifica y agenda por ti, las 24 horas.

---

## Que construye

Dile tu contexto y Claude Code construye el sistema entero:

```
       LO QUE LE DICES                     LO QUE CONSTRUYE
  ┌───────────────────────┐       ┌────────────────────────────────┐
  │                       │       │                                │
  │  Tu oferta            │       │ 1. CANALES                     │
  │  Tu cliente ideal     │       │    Instagram + WhatsApp API    │
  │  Tus canales          │       │    Ventanas 24h + plantillas   │
  │  Tu calendario        │       │                                │
  │                       │       │ 2. CUALIFICACION               │
  └───────────────────────┘       │    Preguntas BANT/CHAMP        │
                                  │    Scoring y decision          │
                                  │                                │
                                  │ 3. EL CEREBRO (LLM)            │
                                  │    System prompt + RAG         │
                             ──>  │    Guardrails + tools          │
                                  │                                │
                                  │ 4. BOOKING                     │
                                  │    Agenda real + recordatorios │
                                  │                                │
                                  │ 5. HANDOFF + CRM               │
                                  │    Resumen al closer           │
                                  │                                │
                                  │ 6. CUMPLIMIENTO                │
                                  │    RGPD / LSSI / opt-in        │
                                  │                                │
                                  └────────────────────────────────┘
```

---

## Instalacion

Clona el repo dentro de tu carpeta de skills de Claude Code:

```bash
git clone https://github.com/jordicabelloo/setting-agent \
  ~/.claude/skills/setting-agent
```

A partir de ahi, Claude Code carga la skill cuando le pidas construir un setting agent (o menciones "setter", "cualificar leads", "agendar llamadas").

---

## Uso

Pidele a Claude algo como:

> Ayudame a construir un setting agent para mi negocio de coaching en Instagram y WhatsApp.

Seguira el workflow de construccion paso a paso, aplicara los guardrails y consultara las referencias para el detalle tecnico.

---

## Que incluye

| Archivo | Que aporta |
|---------|-----------|
| `SKILL.md` | Definicion de la skill y workflow de construccion |
| `references/architecture.md` | Componentes, flujo de mensaje y stack |
| `references/meta-apis.md` | Instagram y WhatsApp Cloud API: ventanas 24h, plantillas, precios, opt-in |
| `references/qualification-and-conversation.md` | Cualificacion, conversacion, objeciones y show-rate |
| `references/system-prompt-and-guardrails.md` | System prompt, RAG y guardrails |
| `references/compliance.md` | RGPD, LOPDGDD, LSSI y opt-in |

---

<p align="center">
  Hecho por <a href="https://pryxis.es"><strong>PRYXIS</strong></a> &bull; Licencia MIT
</p>
