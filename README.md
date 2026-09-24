<div align="center">

# 🧠 AI Agent Skills Suite

### *Production-ready skills, stealth browser automation, deep research workflows, Google Workspace suite & Chrome DevTools engine.*

<br/>

[![GitHub Stars](https://img.shields.io/github/stars/ibrdot/ai-agent-skills?style=for-the-badge&color=ffd700&logo=github)](https://github.com/ibrdot/ai-agent-skills/stargazers)
[![Repo Size](https://img.shields.io/github/repo-size/ibrdot/ai-agent-skills?style=for-the-badge&color=4169e1&logo=files)](https://github.com/ibrdot/ai-agent-skills)
[![License: MIT](https://img.shields.io/badge/License-MIT-success?style=for-the-badge&color=2ea44f)](LICENSE)
[![Dual Mode](https://img.shields.io/badge/Mode-CLI%20%2B%20MCP-blueviolet?style=for-the-badge&logo=fastapi)](https://github.com/ibrdot/ai-agent-skills)
[![Compatibility](https://img.shields.io/badge/Compatible%20With-Antigravity%20|%20Claude%20|%20Cursor-orange?style=for-the-badge&logo=openai)](https://github.com/ibrdot/ai-agent-skills)

<br/>

[✨ Features](#-key-highlights) • [📦 Skills Catalog](#-skills-catalog) • [🌐 Google Workspace](#-google-workspace-gws-suite) • [🔍 Chrome DevTools](#-chrome-devtools-for-agents-dual-mode) • [🚀 Quick Start](#-quick-start--installation)

---

</div>

## 🌟 Key Highlights

> [!TIP]
> **Zero Configuration Required**: All skills work directly via your agent's terminal execution (**Standalone CLI & Script Mode**) with no extra server setup required, or seamlessly as **MCP Servers** when configured.

- 🛡️ **Anti-Detect Browser Automation** (`camoufox-cli`): Built-in C++ fingerprint spoofing to bypass Cloudflare, bot protections, and captchas.
- 🔍 **Live Chrome DevTools Engine** (`chrome-devtools`): Full Puppeteer automation, live console traces, network interception, and Core Web Vitals profiling.
- 🧠 **Manus-Style Working Memory** (`planning-with-files`): File-backed persistent planning (`task_plan.md`, `progress.md`, `findings.md`) with automatic session restoration.
- 🔬 **Recursive Deep Research** (`deep-research`): Multi-source intelligence gathering, competitive analysis, and automated report synthesis.
- 🎬 **Programmatic Video & Motion** (`remotion`, `video-frames`): React-based video generation, automated subtitling, and FFmpeg frame extraction.
- 📊 **Enterprise Presentation Engine** (`pptx-native`, `pptx`): Native element-level editable PowerPoint authoring and AI vision slide generator.
- ☁️ **Full Google Workspace Suite** (`gws-*`): End-to-end management for Gmail, Drive, Docs, Sheets, Calendar, Slides, and Tasks.

---

## 🏛️ Architecture Overview

```mermaid
flowchart TD
    subgraph AgentRuntime["🤖 AI Agent Runtime (Antigravity / Claude / Cursor / CLI)"]
        direction TB
        Agent["AI Assistant Core"] --> Router["Skill & Intent Router"]
    end

    Router --> WebAuto["🌐 Web & Automation"]
    Router --> PlanMem["🧠 Memory & Research"]
    Router --> GWS["☁️ Google Workspace Suite"]
    Router --> MediaDev["🎬 Media & Presentation"]
    Router --> OpsDev["🛠️ DevOps & Observability"]

    subgraph WebAuto["Automation & Scraping"]
        camoufox["camoufox-cli (Anti-Detect)"]
        devtools["chrome-devtools (Puppeteer & Traces)"]
    end

    subgraph PlanMem["Planning & Intelligence"]
        planning["planning-with-files (Manus Protocol)"]
        research["deep-research (Iterative Synthesis)"]
    end

    subgraph GWS["Google Workspace"]
        gws["Gmail • Drive • Docs • Sheets • Calendar • Slides • Tasks"]
    end

    subgraph MediaDev["Media Generation"]
        remotion["remotion (React Video)"]
        pptx["pptx-native (OfficeCLI)"]
        frames["video-frames & gifgrep"]
    end

    subgraph OpsDev["DevOps & MCP"]
        github["github • linear • sentry • notion"]
        mcphub["mcp-hub (Dynamic Proxy)"]
    end
```

---

## 📦 Skills Catalog

| Skill | Category | Capabilities & Trigger Context | Mode |
| :--- | :--- | :--- | :---: |
| [`camoufox-cli`](./camoufox-cli) | **Web & Stealth** | Anti-detect Firefox browser automation, bypassing Cloudflare/Bot detection, DOM snapshotting. | `CLI` |
| [`chrome-devtools`](./chrome-devtools) | **Web & DevTools** | Live Chrome automation, performance tracing, network interception, heap inspection, and debugging. | `CLI + MCP` |
| [`deep-research`](./deep-research) | **Research** | Iterative multi-source deep research, competitive intelligence, and structured research reports. | `Skill` |
| [`planning-with-files`](./planning-with-files) | **Task Planning** | Manus-style file-based planning (`task_plan.md`, `progress.md`) with automatic session recovery. | `Skill` |
| [`github`](./github) | **DevOps** | Repository management, PR review workflows, issue triage, and CI failure debugging. | `Connector` |
| [`linear`](./linear) | **Project Mgmt** | Issue tracking, cycles, team boards, roadmaps, and automated ticket synchronization. | `Connector` |
| [`sentry`](./sentry) | **Observability** | Exception investigation, crash triage, issue resolution tracking, and incident summaries. | `MCP` |
| [`notion`](./notion) | **Productivity** | Read, create, and update Notion workspace pages, nested blocks, notes, and databases. | `MCP` |
| [`mcp-hub`](./mcp-hub) | **Integrations** | Dynamic discovery and execution proxy for user-configured remote MCP servers. | `MCP` |
| [`pptx-native`](./pptx-native) | **Presentation** | Native editable PowerPoint deck creation via OfficeCLI (shapes, text, animations, tables). | `Skill` |
| [`pptx`](./pptx) | **Presentation** | AI image-backed raster slide deck generator using vision models packaged to PPTX. | `Skill` |
| [`remotion`](./remotion) | **Media & Video** | React-based programmatic video generation, transitions, dynamic captions, and motion graphics. | `Skill` |
| [`video-frames`](./video-frames) | **Media & Video** | FFmpeg-based still frame extraction, scene detection, and short clip clipping. | `CLI` |
| [`gifgrep`](./gifgrep) | **Media & Video** | Search GIF providers via CLI/TUI, download animations, and extract frame sequences. | `CLI` |
| [`weather`](./weather) | **Utilities** | Current weather conditions and multi-day forecasts via wttr.in and Open-Meteo. | `CLI` |
| [`moclaw-help`](./moclaw-help) | **Knowledge Base** | In-depth MoClaw product documentation, troubleshooting manuals, and runtime reference. | `Docs` |

---

## 🌐 Google Workspace (GWS) Suite

Comprehensive enterprise integration tools covering the entire Google productivity ecosystem:

<div align="center">

| Service | Skill | Key Capabilities |
| :---: | :--- | :--- |
| ✉️ | [`gws-gmail`](./gws-gmail) | Send, search, parse attachments, read email threads, and manage drafts. |
| 📅 | [`gws-calendar`](./gws-calendar) | Create events, check calendar availability, reschedule, and manage invites. |
| 📁 | [`gws-drive`](./gws-drive) | File upload/download, shared drive management, folder structures, and permissions. |
| 📝 | [`gws-docs`](./gws-docs) | Read, write, format markdown to Google Docs, and modify document trees. |
| 📊 | [`gws-sheets`](./gws-sheets) | Read/write cell ranges, formula calculation, data extraction, and sheet formatting. |
| 📽️ | [`gws-slides`](./gws-slides) | Generate, restyle, inspect, and update presentation slide decks. |
| ✅ | [`gws-tasks`](./gws-tasks) | Manage task lists, set deadlines, mark items completed, and track progress. |
| 🔑 | [`gws-shared`](./gws-shared) | Unified OAuth patterns, authentication tokens, global CLI flags, and output formats. |

</div>

---

## 🔍 Chrome DevTools for Agents (Dual-Mode)

The [`chrome-devtools`](./chrome-devtools) suite provides deep browser instrumentation for AI agents.

```
                           ┌──► Standalone CLI Mode (Terminal / Zero Setup)
[ Chrome DevTools Suite ] ─┤
                           └──► MCP Server Mode (Tool-calling in Claude / Cursor)
```

### 🌟 Key Capabilities
- **Automated Puppeteer Control**: Seamlessly open URLs, click, input text, select options, and await DOM readiness.
- **Console & Network Traces**: Real-time console logs with source-mapped stack traces; network payload inspection and request blocking.
- **Core Web Vitals & Tracing**: Record live performance traces, measuring **LCP**, **CLS**, and **INP** with Google CrUX field data integration.
- **V8 Heap Snapshots & Leak Detection**: Compare memory snapshots to isolate detached DOM nodes and memory leaks.

### 🧩 7 Built-In DevTools Specialist Skills

```
chrome-devtools/skills/
├── a11y-debugging/          # WCAG compliance, ARIA diagnostics, contrast audits
├── chrome-devtools/         # Conversational MCP server interface
├── chrome-devtools-cli/     # Terminal-first browser control workflows
├── cookie-debugging/        # Cookie lifecycle, SameSite/Secure flag validation
├── debug-optimize-lcp/      # Largest Contentful Paint diagnostics & fixes
├── memory-leak-debugging/   # V8 heap diffing and detached element cleanup
└── troubleshooting/         # Automated recovery patterns for agent-browser sessions
```

### 💻 Quick Usage

#### 1. CLI Mode (Without MCP)
```bash
# Open URL and inspect elements
npx chrome-devtools-mcp open https://example.com

# Capture interactive snapshot with element IDs (@e1, @e2)
npx chrome-devtools-mcp snapshot -i
```

#### 2. MCP Server Configuration (Optional)
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

---

## 🚀 Quick Start & Installation

### 1. Clone the Repository
```bash
git clone https://github.com/ibrdot/ai-agent-skills.git
cd ai-agent-skills
```

### 2. Configure with Your Favorite Agent

#### Antigravity / OpenClaw / Custom Agents
Point your agent environment to the cloned repository path:
```bash
export AGENT_SKILLS_PATH="/path/to/ai-agent-skills"
```

#### Claude Desktop / Cursor / Copilot
Simply register any MCP skill (e.g. `chrome-devtools`, `sentry`, `notion`) into your `claude_desktop_config.json` or `mcp.json`.

---

## 🛠️ Anatomy of a Skill

Each skill adheres to an open, standardized modular structure:

```text
skill-name/
├── SKILL.md                 # YAML frontmatter + model instructions & triggers
├── manifest.json            # Versioning, runtime group, and tool definitions
├── runtime-component.json   # Optional container runtime bindings
├── scripts/                 # Standalone automation scripts (Python, Bash, PowerShell)
└── references/              # Detailed guides, recipes, and API specifications
```

---

## 👤 Author & Support

<div align="center">

**Crafted by [@ibrdot](https://github.com/ibrdot)**  
*Building cutting-edge tools for autonomous AI agents and developer workflows.*

[![GitHub](https://img.shields.io/badge/GitHub-ibrdot-181717?style=for-the-badge&logo=github)](https://github.com/ibrdot)
[![Email](https://img.shields.io/badge/Email-ibrdot@outlook.com-0078D4?style=for-the-badge&logo=microsoftoutlook)](mailto:ibrdot@outlook.com)

⭐ **If you find this suite useful, please give it a Star on GitHub!**

</div>
