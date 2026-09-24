# AI Skills Collection

A curated collection of modular, production-ready AI agent skills and connector integrations. Each skill is designed to extend LLM and autonomous agent capabilities with tools, structured planning workflows, API connectors, and media generation.

---

## 📦 Skills Directory

| Skill | Category | Description |
| :--- | :--- | :--- |
| [`camoufox-cli`](./camoufox-cli) | **Automation & Web** | Anti-detect browser automation CLI for stealth scraping, form interaction, and bypassing bot detection/fingerprinting. |
| [`chrome-devtools-mcp`](./chrome-devtools-mcp) | **Automation & Web** | Official Chrome DevTools MCP server & CLI for live browser inspection, performance tracing, network debugging, and puppeteer automation. |
| [`deep-research`](./deep-research) | **Research & Analysis** | Iterative multi-source deep research framework for competitive analysis, trend investigation, and reports. |
| [`planning-with-files`](./planning-with-files) | **Task Planning** | File-based planning protocol (`task_plan.md`, `progress.md`, `findings.md`) with automatic session recovery. |
| [`github`](./github) | **DevOps & Issue Tracking** | GitHub connector for repository management, PR review, issue triage, and CI workflow status. |
| [`linear`](./linear) | **Project Management** | Linear connector to manage issues, cycles, teams, engineering planning, and ticket updates. |
| [`sentry`](./sentry) | **Monitoring & Observability** | Sentry MCP connector for error triage, incident investigation, and issue resolution tracking. |
| [`notion`](./notion) | **Productivity & Docs** | Notion MCP connector for reading, creating, and updating Notion pages, blocks, and databases. |
| [`mcp-hub`](./mcp-hub) | **Integrations** | Dynamic discovery and execution proxy for user-configured Model Context Protocol (MCP) servers. |
| [`pptx-native`](./pptx-native) | **Presentation** | Native editable PowerPoint deck creation and element-level manipulation (shapes, tables, charts, text). |
| [`pptx`](./pptx) | **Presentation** | Image-backed and raster PowerPoint presentation generator using AI vision models. |
| [`remotion`](./remotion) | **Media & Video** | React-based programmatic video generation, animation, captions, audio, and rendering best practices. |
| [`video-frames`](./video-frames) | **Media & Video** | FFmpeg-based video extraction tool for grabbing still frames and short clips. |
| [`gifgrep`](./gifgrep) | **Media & Video** | Search GIF providers via CLI/TUI, download animations, and extract individual frames/sheets. |
| [`weather`](./weather) | **Utilities** | Current weather conditions and forecasts via wttr.in and Open-Meteo (no API keys required). |
| [`moclaw-help`](./moclaw-help) | **Knowledge Base** | Product reference, architecture guides, and troubleshooting documentation for MoClaw runtime. |

---

### 🌐 Google Workspace (GWS) Suite

A complete set of tools for interacting with Google Workspace services:

| Skill | Description |
| :--- | :--- |
| [`gws-shared`](./gws-shared) | Core authentication patterns, global CLI flags, and output formatters for all GWS skills. |
| [`gws-gmail`](./gws-gmail) | Send, search, read, draft, and organize emails and threads. |
| [`gws-calendar`](./gws-calendar) | Create, update, search, and manage Google Calendar events and schedules. |
| [`gws-drive`](./gws-drive) | Upload, download, search, share, and organize files and Google Drive folders. |
| [`gws-docs`](./gws-docs) | Read, write, format, and manipulate Google Docs documents. |
| [`gws-sheets`](./gws-sheets) | Read, write, formula evaluate, and structure Google Sheets spreadsheets. |
| [`gws-slides`](./gws-slides) | Inspect, create, and modify Google Slides presentations. |
| [`gws-tasks`](./gws-tasks) | Manage Google Tasks task lists, items, and due dates. |

---

## 🛠️ Skill Anatomy

Each skill directory follows a standardized schema:

```text
skill-name/
├── SKILL.md                 # Core instructions, execution rules, and trigger definitions
├── manifest.json            # Versioning, runtime group, and metadata
└── runtime-component.json   # Optional runtime configuration and component bindings
```

### `SKILL.md`
Contains YAML frontmatter that defines:
- **`name`**: Unique identifier for the skill.
- **`description`**: Semantic triggering criteria for AI models to activate the skill when needed.
- **Detailed Instructions**: Procedural steps, script paths, CLI flags, and reference guides.

---

## 🚀 Usage & Integration

Skills can be loaded into compatible agent runtime environments (such as Antigravity, OpenClaw, or custom AI agent frameworks) by pointing to the root directory or placing individual skill folders into your agent's skills path:

```bash
# Clone the repository
git clone https://github.com/ibrdot/aiskills.git

# Set your skills directory in your agent configuration
export AGENT_SKILLS_PATH="./aiskills"
```

---

## 👤 Author

- **GitHub**: [@ibrdot](https://github.com/ibrdot)
- **Contact**: `ibrdot@outlook.com`
