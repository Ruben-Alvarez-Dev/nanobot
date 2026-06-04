# 🐈 nanobot · Agente Multimodal Total

> **Fork de [HKUDS/nanobot](https://github.com/HKUDS/nanobot)** — Proyecto original creado por [Xubin Ren](https://github.com/re-bin).  
> Este fork extiende la plataforma hacia un agente multimodal completo con gestión de skills, búsqueda multi-registro y generación por IA.

---

<div align="center">
  <p>
    <img src="https://img.shields.io/badge/python-≥3.11-blue" alt="Python">
    <img src="https://img.shields.io/badge/license-MIT-green" alt="License">
    <a href="https://github.com/Ruben-Alvarez-Dev/nanobot"><img src="https://img.shields.io/github/stars/Ruben-Alvarez-Dev/nanobot?style=social" alt="Stars"></a>
  </p>
</div>

**nanobot** es un runtime de agente open-source ultraligero que conjuga texto, código, imágenes, voz, memoria persistente, tools, MCP, canales de chat y un ecosistema de skills expandible. Pequeño, legible, extensible. Tu stack, tus reglas.

---

## 🔥 Novedades de este fork

| Feature | Descripción |
|---------|-------------|
| **🧠 Skills Management UI** | Panel completo en WebUI para crear, editar, ver, borrar y activar/desactivar skills |
| **🔍 Multi-Registry Search** | Búsqueda simultánea en 10 registros: ClawHub, skills.sh, SkillsMP, GitHub, npm, Anthropic, addyosmani, LobeHub, OpenPackage, AutoSkills |
| **🤖 AI Skill Generation** | Describe una skill en lenguaje natural y la IA genera un SKILL.md completo siguiendo el standard agentskills.io v1 |
| **📝 SKILL.md Editor** | Editor completo con todos los campos del standard: name, description, license, allowed-tools, always, body |
| **🏷️ Badges por registro** | Cada resultado de búsqueda muestra el registro de origen con colores distintivos y link a la fuente |
| **⚡ Install inteligente** | Auto-detección del formato de slug para usar el instalador correcto (clawhub, skills.sh, GitHub, npm) |

---

## 🚀 Quick Start

```bash
git clone https://github.com/Ruben-Alvarez-Dev/nanobot.git
cd nanobot
python3 -m venv .venv && source .venv/bin/activate
pip install -e .
nanobot onboard
nanobot gateway
```

WebUI en [`http://127.0.0.1:8765`](http://127.0.0.1:8765).

---

## 🧠 Skills

nanobot implementa el standard abierto [agentskills.io](https://agentskills.io) v1. Las skills extienden al agente con instrucciones, workflows y herramientas especializadas.

### Gestión desde WebUI

**Settings → Skills** ofrece:

- **Listar + buscar** — skills builtin y workspace con badges de origen
- **Crear** — formulario completo con todos los campos SKILL.md
- **Ver/Editar** — editor markdown para workspace skills
- **Borrar** — eliminar skills del workspace
- **Toggle** — activar/desactivar sin desinstalar
- **AI Generate** — describe qué quieres y la IA te genera el SKILL.md

### 10 Registros de búsqueda

| # | Registro | Tipo | Cobertura |
|---|----------|------|-----------|
| 1 | **ClawHub** | CLI (`npx clawhub`) | 3K–13K |
| 2 | **skills.sh (Vercel)** | CLI (`npx skills`) | Universal |
| 3 | **SkillsMP** | REST API | 1.6M+ indexadas |
| 4 | **GitHub skill-md** | GitHub API | 576+ repos |
| 5 | **npm skill-md** | npm Registry | 91+ paquetes |
| 6 | **Anthropic Official** ⭐ | GitHub API | 146K★ |
| 7 | **addyosmani** ⭐ | GitHub API | 48K★ |
| 8 | **LobeHub** | CLI | 332K+ |
| 9 | **OpenPackage** | CLI | Universal |
| 10 | **AutoSkills** | CLI | Curadas |

Ver [`docs/skills.md`](docs/skills.md) para la documentación completa.

---

## ✨ Features del core

- **Chat-native**: WebUI, API, Telegram, Feishu, Slack, Discord, Teams, WhatsApp, Matrix, Email
- **Model freedom**: OpenAI, Anthropic, DeepSeek, Gemini, Ollama, vLLM, Bedrock, Azure + fallbacks
- **Tools**: filesystem, shell (sandboxed), web search/fetch, MCP, cron, image generation, subagents
- **Memory**: Dream two-phase consolidation, session persistence, context compaction
- **Deploy**: Docker, systemd, macOS LaunchAgent

---

## 🏗️ Arquitectura

Mensajes entran por canales → `MessageBus` → `AgentLoop` → `AgentRunner` (LLM + tools) → respuestas de vuelta al canal. Skills, memoria y MCP se cargan bajo demanda sin acoplar el core.

```
Channel → MessageBus → AgentLoop → AgentRunner ⇄ LLM Provider
                           ↕              ↕
                       Memory         Tools/MCP
                           ↕
                        Skills
```

---

## 📚 Docs

- [Skills Management](docs/skills.md) — nueva documentación
- [Quick Start](docs/quick-start.md)
- [Configuration](docs/configuration.md)
- [Chat Apps](docs/chat-apps.md)
- [Deployment](docs/deployment.md)
- [OpenAI-Compatible API](docs/openai-api.md)
- [Python SDK](docs/python-sdk.md)

---

## 🙏 Créditos

Este proyecto es un fork de **[HKUDS/nanobot](https://github.com/HKUDS/nanobot)**, creado y mantenido por **[Xubin Ren](https://github.com/re-bin)**. Todo el crédito del core, la arquitectura original, el diseño del agente y la inmensa mayoría del código pertenece a Xubin y a los [contributors](https://github.com/HKUDS/nanobot/graphs/contributors) del proyecto original.

Las contribuciones de este fork se centran en la capa de **gestión multimodal de skills**: UI de administración, búsqueda multi-registro, generación de skills por IA, y el sistema de instalación cross-registry.

---

## ⭐ Star History

<div align="center">
  <a href="https://star-history.com/#HKUDS/nanobot&Date">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/svg?repos=HKUDS/nanobot&type=Date&theme=dark" />
      <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/svg?repos=HKUDS/nanobot&type=Date" />
      <img alt="Star History Chart" src="https://api.star-history.com/svg?repos=HKUDS/nanobot&type=Date" style="border-radius: 15px;" />
    </picture>
  </a>
</div>

<p align="center">
  <em>🐈 nanobot · Agente Multimodal Total</em>
</p>
