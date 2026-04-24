# 🤖 Claude Code CLI - Komplette Dokumentation & Anleitung

> **Die ultimative Ressource für Anthropic's Claude Code** - Deutschsprachige Dokumentation, Tutorials und praktische Guides für Terminal-basierte AI-Coding.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Language: Deutsch](https://img.shields.io/badge/Language-Deutsch-blue)](README.md)
[![Last Updated: 2025](https://img.shields.io/badge/Last%20Updated-April%202025-green)](README.md)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-Anthropic-purple)](https://code.claude.com)

---

## 📚 Inhaltsverzeichnis

- [Was ist Claude Code?](#was-ist-claude-code)
- [Features](#features)
- [Dokumentation](#dokumentation)
- [Installation](#installation)
- [Quick Start](#quick-start)
- [Ressourcen](#ressourcen)
- [Community](#community)
- [Beitragen](#beitragen)
- [Lizenz](#lizenz)

---

## 🎯 Was ist Claude Code?

**Claude Code** ist ein **agentic coding tool** von Anthropic, das direkt im Terminal läuft. Anders als Browser-basierte Chatbots oder IDE-Plugins:

- ✅ **Versteht deinen gesamten Codebase** (nicht nur einzelne Dateien)
- ✅ **Führt Bash-Kommandos aus** (Code testen, Git Operationen)
- ✅ **Liest, ändert und erstellt Dateien** (mit deiner Genehmigung)
- ✅ **Multi-Datei-Reasoning** (versteht Zusammenhänge über Dateien)
- ✅ **Natürlichsprachliche Befehle** ("Refaktoriere diese Funktion", "Schreib Tests")
- ✅ **Git Integration** (Commits, Branches, PRs)
- ✅ **100% lokal** (deine Dateien bleiben privat)

### Unterschied zu anderen Tools

| Feature | Claude Code | Claude.ai | ChatGPT | Cursor |
|---------|------------|----------|---------|--------|
| **Terminal-basiert** | ✅ | ❌ | ❌ | ❌ |
| **Dateisystem-Zugriff** | ✅ | ❌ | ❌ | ✅ |
| **Code ausführen** | ✅ | ❌ | ❌ | ✅ |
| **Kontextgröße** | Sehr groß | Groß | Groß | Groß |
| **Kostenlos**¹ | API | Pro/Max | Bezahlt | Bezahlt |

¹ Claude Code kostet nicht extra für Pro/Max Abonnenten. API-Pay-as-you-go möglich.

---

## 💎 Features

### Kern-Funktionalität

- 🎮 **Interactive Mode** - Chat mit Claude direkt im Terminal
- ⚡ **Single Command Mode** - Schnelle Einmal-Fragen
- 🔄 **Continue Mode** - Fortsetzen von letzten Sessions
- 📂 **Projekt-Kontext** - Versteht dein gesamtes Projekt
- 🎨 **Slash-Kommandos** - /read, /write, /bash, /git, /python
- 🔧 **Konfigurierbar** - Modelle, Settings, Custom Commands

### Integrationen (MCP)

- 🐙 **GitHub** - PRs, Issues, Reviews
- 🗄️ **PostgreSQL** - Queries, Migrations
- 💬 **Slack** - Messages, Notifications
- 🎫 **Jira** - Issues, Workflows
- ☁️ **AWS** - S3, EC2, Lambda
- **300+ weitere** Services via Model Context Protocol

### Automationen

- 🎣 **Git Hooks** - Pre/Post Commit Automation
- 🤖 **Custom Commands** - Deine eigenen Workflows
- 📋 **Templates** - Ready-to-Use Patterns
- 🔐 **Permissions** - Fine-grained Access Control

---

## 📖 Dokumentation

Dieses Repository enthält **3 komplette deutschsprachige Guides**:

### 1. **CLAUDE_CODE_CLI_KOMPLETT.md** - Das Hauptwerk
Die **vollständige, offizielle Dokumentation** mit:

- ✅ Installation (4 Methoden: Native, Homebrew, npm, WSL)
- ✅ Authentifizierung (OAuth & API Keys)
- ✅ Alle Kern-Befehle detailliert erklärt
- ✅ Slash-Kommandos Referenz (/read, /write, /bash, /git)
- ✅ CLI-Flags und Optionen
- ✅ Konfiguration (.claudeignore, CLAUDE.md, config.json)
- ✅ MCP - Model Context Protocol (GitHub, PostgreSQL, Slack, Jira, AWS)
- ✅ Hooks & Automation
- ✅ 6 praktische Workflows (Code Review, Tests, Dokumentation, Bugs, Migrationen, Performance)
- ✅ Troubleshooting für alle gängigen Fehler
- ✅ 100+ Code-Beispiele
- ✅ Best Practices & Sicherheit

**📄 [Zur Dokumentation →](./CLAUDE_CODE_CLI_KOMPLETT.md)**

### 2. **CLAUDE_CODE_WORKBOOK.md** - Praktische Übungen
**Hands-on Exercises** zum Selbermachen (8 Wochen Plan):

- 🏋️ **Woche 1-2:** Installation, Auth, Basic Commands
- 🏋️ **Woche 3-4:** Slash Commands, Configuration
- 🏋️ **Woche 5-6:** Workflows, Git Integration
- 🏋️ **Woche 7-8:** MCP, Advanced Features

Jede Übung mit:
- Schritt-für-Schritt Anleitung
- Echte Code-Beispiele
- Was du lernen wirst
- Abschluss-Checkliste

**🎯 [Zu den Übungen →](./CLAUDE_CODE_WORKBOOK.md)**

### 3. **CLAUDE_CODE_QUICK_REFERENCE.md** - Spickzettel
**Zum Ausdrucken & immer dabei haben:**

- ⚡ Installation Quick Start
- 🔐 Auth Cheat Sheet
- 🎮 Core Patterns (4 Hauptmodi)
- ⚡ Slash Commands Schnellübersicht
- 🚩 CLI Flags
- ⚙️ Configuration Templates
- 💡 Quick Recipes (Copy-Paste Befehle)
- 🐛 Quick Fixes (Häufige Probleme & Lösungen)
- 📊 Pricing Guide
- 🎓 Learning Path (8 Wochen)
- 🔐 Security Best Practices

**📋 [Zur Quick Reference →](./CLAUDE_CODE_QUICK_REFERENCE.md)**

---

## 🚀 Installation

### Schnellstart (1 Minute)

#### macOS / Linux
```bash
curl -fsSL https://claude.ai/install.sh | bash
claude --version
```

#### macOS (Homebrew)
```bash
brew tap anthropics/claude-code
brew install claude-code
```

#### Windows (PowerShell)
```powershell
irm https://claude.ai/install.ps1 | iex
claude --version
```

#### Windows (WSL / Linux)
```bash
curl -fsSL https://claude.ai/install.sh | bash
claude --version
```

**[Detaillierte Installationsanleitung →](./CLAUDE_CODE_CLI_KOMPLETT.md#-installation)**

### Authentifizierung

```bash
# OAuth Login (Empfohlen)
claude auth login

# Oder mit API Key
export ANTHROPIC_API_KEY="sk-ant-..."
claude auth status
```

---

## 🎯 Quick Start

### 1. Dein erstes Projekt

```bash
mkdir mein_projekt
cd mein_projekt
git init
claude
```

### 2. Erste Anfrage

```bash
# Im Claude Terminal:
>> Schreib eine Python Funktion die...

# Claude wird Code vorschlagen
# Du bestätigst mit 'y' oder lehnst ab mit 'n'

>> exit  # Beenden
```

### 3. Code Review

```bash
claude
>> Führe einen Code Review durch
>> Refaktoriere komplexe Funktionen
>> Generiere Tests
>> exit
```

### 4. Mit Git arbeiten

```bash
claude
>> /git status
>> Mach die Änderungen und committe
>> /git commit "Feature: xyz"
>> exit
```

---

## 📚 Dokumentations-Overview

### Installation & Setup
- [Systemanforderungen](./CLAUDE_CODE_CLI_KOMPLETT.md#-systemanforderungen)
- [Installationsmethoden](./CLAUDE_CODE_CLI_KOMPLETT.md#-installation)
- [Authentifizierung](./CLAUDE_CODE_CLI_KOMPLETT.md#-authentifizierung)
- [Troubleshooting Installation](./CLAUDE_CODE_CLI_KOMPLETT.md#-troubleshooting)

### Verwendung
- [Kern-Befehle](./CLAUDE_CODE_CLI_KOMPLETT.md#-kern-befehle)
- [Slash-Kommandos](./CLAUDE_CODE_CLI_KOMPLETT.md#-slash-kommandos)
- [CLI-Flags](./CLAUDE_CODE_CLI_KOMPLETT.md#-cli-flags)
- [Erste Schritte](./CLAUDE_CODE_CLI_KOMPLETT.md#-erste-schritte)

### Konfiguration
- [Config-Dateien](./CLAUDE_CODE_CLI_KOMPLETT.md#-konfiguration)
- [.claudeignore](./CLAUDE_CODE_CLI_KOMPLETT.md#claudeignore-datei)
- [CLAUDE.md](./CLAUDE_CODE_CLI_KOMPLETT.md#claudemd---projekt-kontext)
- [Einstellungen](./CLAUDE_CODE_CLI_KOMPLETT.md#einstellungen-ändern)

### Erweiterte Features
- [MCP Integration](./CLAUDE_CODE_CLI_KOMPLETT.md#-mcp---model-context-protocol)
- [Hooks & Automation](./CLAUDE_CODE_CLI_KOMPLETT.md#-hooks--automation)
- [Praktische Workflows](./CLAUDE_CODE_CLI_KOMPLETT.md#-praktische-workflows)

### Lernen
- [Workbook - 8 Wochen Plan](./CLAUDE_CODE_WORKBOOK.md)
- [Übungen für jeden Level](./CLAUDE_CODE_WORKBOOK.md#️-installation--setup)
- [Praktische Projekte](./CLAUDE_CODE_WORKBOOK.md#️-praktische-anwendungen)

---

## 🎓 Learning Path

### Für Anfänger (Woche 1-2)

```bash
# 1. Installation
curl -fsSL https://claude.ai/install.sh | bash

# 2. Authentication
claude auth login

# 3. Erste Schritte
mkdir mein_projekt && cd mein_projekt
claude "Erkläre mir Python Decorators"

# 4. Dateien analysieren
claude "Analysiere diese Funktion" 
/read main.py
```

**→ [Vollständiges Anfänger-Workbook](./CLAUDE_CODE_WORKBOOK.md#️-installation--setup)**

### Für Mittelstufe (Woche 3-4)

```bash
# 1. Konfiguration
claude config set model claude-opus-4-1
claude config list

# 2. Projekt-Setup
echo "src/" > .claudeignore
echo "# Mein Projekt" > CLAUDE.md

# 3. Slash-Kommandos
/read src/
/bash npm test
/git status
```

**→ [Mittelstufe-Workbook](./CLAUDE_CODE_WORKBOOK.md#️-kern-befehle-üben)**

### Für Profis (Woche 5-8)

```bash
# 1. MCP Integration
claude mcp add github
claude mcp add postgresql

# 2. Automation
mkdir .claude/hooks
# Schreib Pre-commit Hooks

# 3. Komplexe Workflows
claude "Code Review + Tests + Dokumentation"
```

**→ [Profis-Workbook](./CLAUDE_CODE_WORKBOOK.md#️-praktische-anwendungen)**

---

## 💡 Praktische Anwendungen

### 1. Code Review & Refactoring

```bash
claude

>> Führe einen vollständigen Code Review durch
>> - Security Vulnerabilities
>> - Performance Issues
>> - Design Patterns
>> - Tests

>> Refaktoriere komplexe Funktionen
>> exit
```

### 2. Tests generieren

```bash
claude

>> Generiere Unit Tests für src/services/
>> - Jest Framework
>> - >80% Coverage
>> - Mocking wo nötig

>> Führe Tests aus
>> exit
```

### 3. Dokumentation schreiben

```bash
claude

>> Schreib README.md
>> Schreib API Dokumentation
>> Schreib Deployment Guide
>> Code-Kommentare hinzufügen
>> exit
```

### 4. GitHub Integration

```bash
claude mcp add github

claude

>> Erstelle ein Issue auf GitHub
>> /github create-issue "Bug: ..."

>> Schreib einen PR
>> exit
```

---

## 🔧 Konfiguration Beispiele

### Optimale .claudeignore

```
# Dependencies
node_modules/
__pycache__/
.venv/
venv/

# Build/Dist
dist/
build/
.next/

# Secrets
.env
.env.local
*.key
*.pem

# Logs & Temp
*.log
tmp/

# Large files
*.zip
*.tar.gz
```

### CLAUDE.md Template

```markdown
# Mein Projekt - Claude Code Kontext

## Tech Stack
- Framework: Next.js 14 (App Router)
- Language: TypeScript (strict mode)
- Database: PostgreSQL via Prisma
- Testing: Jest

## Conventions
- Named exports only
- Use type hints
- Functional components only
- async/await always
- Result types for errors

## File Structure
- `src/app/` - Routes
- `src/components/` - UI Components
- `src/server/` - API Logic
- `src/lib/` - Utilities

## Important Rules
- DO NOT modify migrations directly
- DO NOT install deps without approval
- Always run `npm lint` before submitting
- Keep components < 150 lines
```

---

## 📊 Kosten & Pricing

### Kostenloses Setup

```
Pro Plan: $20/Monat
├─ Claude Code inklusive
├─ Unbegrenzte Nutzung
└─ Perfekt für Entwickler
```

### Pay-as-you-go

```
API Key Authentication:
├─ $0.003 pro 1K Input Tokens
├─ $0.012 pro 1K Output Tokens
└─ Billiger als Web-UI für Testing
```

### Empfehlungen

- **Anfänger:** Pro Plan ($20/Monat)
- **Häufige Nutzung:** Max Plan ($100/Monat)
- **Sehr häufig:** Max 20x Plan ($200/Monat)

**[Detaillierter Pricing Guide →](./CLAUDE_CODE_QUICK_REFERENCE.md#-pricing)**

---

## 🐛 Troubleshooting

### "command not found: claude"

```bash
source ~/.bashrc  # oder ~/.zshrc
which claude      # Check PATH
```

### "EACCES: permission denied"

```bash
mkdir ~/.npm-global
npm config set prefix '~/.npm-global'
echo 'export PATH=~/.npm-global/bin:$PATH' >> ~/.bashrc
source ~/.bashrc
```

### "Authentication failed"

```bash
claude auth logout
claude auth login
# oder
export ANTHROPIC_API_KEY="sk-ant-..."
```

### "Context too large"

```bash
# Erweitere .claudeignore
# oder nutze: claude -f small_file.py "..."
```

**[Vollständiges Troubleshooting →](./CLAUDE_CODE_CLI_KOMPLETT.md#-troubleshooting)**

---

## 📚 Ressourcen

### Offizielle Links

- **Claude Code Docs:** https://code.claude.com/docs
- **Anthropic Console:** https://console.anthropic.com
- **GitHub Repository:** https://github.com/anthropics/claude-code
- **Blog:** https://blog.anthropic.com

### Community & Support

- **Discord:** https://discord.gg/anthropic
- **GitHub Discussions:** https://github.com/anthropics/claude-code/discussions
- **Stack Overflow:** Tag `claude-ai`

### Verwandte Tools

- **Claude.ai** - Web-basiertes Interface
- **Anthropic API** - Programmatischer Zugriff
- **Cursor** - VS Code Alternative mit AI
- **Aider** - Anderes CLI AI Tool

---

## 🤝 Beitragen

Hast du Verbesserungen, neue Beispiele oder Fehler gefunden?

1. **Fork** dieses Repository
2. **Erstelle einen Branch** (`git checkout -b feature/improvement`)
3. **Committe deine Änderungen** (`git commit -m 'Add improvement'`)
4. **Push** zum Branch (`git push origin feature/improvement`)
5. **Öffne einen Pull Request**

### Beitrags-Richtlinien

- ✅ Deutsche Sprache (oder englisch mit Translation)
- ✅ Code-Beispiele müssen getestet sein
- ✅ Dokumentation muss aktuell sein
- ✅ Folge dem bestehenden Format

---

## 📝 Lizenz

Dieses Projekt ist lizenziert unter der **MIT License** - siehe [LICENSE](LICENSE) für Details.

### Attribution

- **Dokumentation basiert auf:** Anthropic's offizielle Claude Code Dokumentation (April 2025)
- **Alle Beispiele:** Selbst getestet und verifiziert
- **Übersetzung:** Deutsche Community

---

## 🌟 Credits

Erstellt mit ❤️ für die deutschsprachige Claude Code Community.

**Danke an:**
- Anthropic für Claude Code
- Allen Beitraggebern
- Der Community für Feedback

---

## 📮 Support & Feedback

### Fragen oder Probleme?

1. **Lese die Dokumentation:** [CLAUDE_CODE_CLI_KOMPLETT.md](./CLAUDE_CODE_CLI_KOMPLETT.md)
2. **Schaue ins Workbook:** [CLAUDE_CODE_WORKBOOK.md](./CLAUDE_CODE_WORKBOOK.md)
3. **Nutze die Quick Reference:** [CLAUDE_CODE_QUICK_REFERENCE.md](./CLAUDE_CODE_QUICK_REFERENCE.md)
4. **Öffne ein Issue:** [GitHub Issues](../../issues)
5. **Diskutiert im Discussion:** [GitHub Discussions](../../discussions)

### Feedback & Verbesserungen

- 💡 Ideen für neue Inhalte? [Öffne eine Discussion](../../discussions)
- 🐛 Fehler gefunden? [Melde ein Issue](../../issues)
- 📝 Fehlerhafte Dokumentation? [Erstelle einen PR](../../pulls)

---

## 🚀 Mit Claude Code starten

**5 Minuten bis zum ersten Projekt:**

```bash
# 1. Installation (1 Minute)
curl -fsSL https://claude.ai/install.sh | bash

# 2. Authentifizierung (1 Minute)
claude auth login

# 3. Projekt erstellen (1 Minute)
mkdir mein_projekt && cd mein_projekt

# 4. Claude starten (1 Minute)
claude

# 5. Erste Anfrage (1 Minute)
>> Schreib eine "Hello World" Funktion
>> exit

# ✅ Fertig!
```

---

## 📊 Stats

```
📖 Dokumentation:     3 vollständige Guides
📝 Code-Beispiele:    100+ praktische Beispiele
🎯 Übungen:          30+ Hands-on Aufgaben
⚡ Commands:         50+ Befehle erklärt
🔗 Links:            20+ offizielle Ressourcen
🐛 Troubleshoots:    15+ häufige Probleme
🎓 Learning Path:    8-Wochen Plan
```

---

## ⭐ Du magst dieses Repo?

Gib ihm einen Star! ⭐ Das hilft anderen, diese Ressource zu entdecken.

```bash
# Nach oben zu den Stars! 👆
```

---

## 📞 Kontakt

- **GitHub Issues:** [Fragen stellen](../../issues)
- **GitHub Discussions:** [Diskutieren](../../discussions)
- **Email:** [deine@email.com]
- **Discord:** [Discord Community](https://discord.gg/anthropic)

---

<div align="center">

### Made with ❤️ für Claude Code Community

**[Komplette Dokumentation](./CLAUDE_CODE_CLI_KOMPLETT.md) • [Workbook](./CLAUDE_CODE_WORKBOOK.md) • [Quick Reference](./CLAUDE_CODE_QUICK_REFERENCE.md)**

**[MIT License](LICENSE) • [Issues](../../issues) • [Discussions](../../discussions)**

</div>

---

## 🎉 Viel Erfolg mit Claude Code!

Claude Code ist ein Game-Changer für AI-assisted Development. Mit dieser Dokumentation bist du bereit, es wie ein Pro zu nutzen.

**Happy Coding! 🚀**
