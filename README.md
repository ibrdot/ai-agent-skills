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

## 🔍 Chrome DevTools for Agents (`chrome-devtools-mcp`)

The repository includes the full **Chrome DevTools MCP server, CLI, and specialized debugging skills** (`./chrome-devtools-mcp`). It equips AI agents with direct, programmatic control over live Google Chrome browser sessions with industrial-grade inspection tooling.

### 🌟 Key Capabilities & Features

- **Automated Browser Control**: Full Puppeteer-backed automation enabling agents to navigate, type, click, fill inputs, capture screenshots, and await page mutations with deterministic reliability.
- **Deep Console & Network Diagnostics**:
  - Live console message capture with automatic source-mapped stack traces for instant root-cause identification.
  - Granular HTTP/WebSocket request inspection, request blocking, latency simulation, and payload verification.
- **Performance Profiling & Core Web Vitals**:
  - Record performance traces using Chrome DevTools' native tracing engine.
  - Automatically analyze Largest Contentful Paint (LCP), Cumulative Layout Shift (CLS), and Interaction to Next Paint (INP).
  - Integration with the Chrome User Experience Report (CrUX) for comparing field data with lab metrics.
- **Memory Leak & Heap Analysis**:
  - Capture and compare V8 Heap snapshots directly from running sessions.
  - Pinpoint memory leaks, detached DOM trees, and uncollected closures.
- **DOM & Accessibility (A11y)**:
  - Accessibility tree traversal, color contrast checks, and ARIA attribute validation.
  - Semantic DOM tree snapshotting with actionable element reference handles (`@e1`, `@e2`).

### 🧩 Included DevTools Specialist Skills

Located under [`chrome-devtools-mcp/skills`](./chrome-devtools-mcp/skills):

| Specialist Skill | Focus Area |
| :--- | :--- |
| [`a11y-debugging`](./chrome-devtools-mcp/skills/a11y-debugging) | Automated accessibility audits, WCAG checks, and ARIA diagnostics. |
| [`chrome-devtools`](./chrome-devtools-mcp/skills/chrome-devtools) | Model Context Protocol integration for conversational browser interaction. |
| [`chrome-devtools-cli`](./chrome-devtools-mcp/skills/chrome-devtools-cli) | Terminal-first browser control workflows without protocol overhead. |
| [`cookie-debugging`](./chrome-devtools-mcp/skills/cookie-debugging) | Cookie lifecycle inspection, SameSite/Secure flag validation, and session auth debugging. |
| [`debug-optimize-lcp`](./chrome-devtools-mcp/skills/debug-optimize-lcp) | Automated analysis and step-by-step optimization strategies for Largest Contentful Paint. |
| [`memory-leak-debugging`](./chrome-devtools-mcp/skills/memory-leak-debugging) | Heap snapshot comparison and detached DOM node leak remediation. |
| [`troubleshooting`](./chrome-devtools-mcp/skills/troubleshooting) | Diagnostic guides and automated recovery patterns for agent-browser sessions. |

### ⚙️ Quick MCP Setup

Add the server to your agent's MCP configuration (`mcp.json` or editor settings):

```json
{
  "mcpServers": {
    "chrome-devtools": {
      "command": "npx",
      "args": ["-y", "chrome-devtools-mcp@latest"]
    }
  }
}
```

*For lightweight/headless tasks only, pass `--slim` and `--headless`:*
```json
{
  "mcpServers": {
    "chrome-devtools": {
      "command": "npx",
      "args": ["-y", "chrome-devtools-mcp@latest", "--slim", "--headless"]
    }
  }
}
```

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
