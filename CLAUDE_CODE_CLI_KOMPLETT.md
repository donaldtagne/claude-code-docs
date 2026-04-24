# 🤖 CLAUDE CODE CLI - KOMPLETTE DOKUMENTATION

**Die offizielle Anleitung für Anthropic's Claude Code - deinen KI-Coding-Partner im Terminal**

---

# 📋 INHALTSVERZEICHNIS

1. [Was ist Claude Code?](#was-ist-claude-code)
2. [Systemanforderungen](#systemanforderungen)
3. [Installation](#installation)
4. [Authentifizierung](#authentifizierung)
5. [Erste Schritte](#erste-schritte)
6. [Kern-Befehle](#kern-befehle)
7. [Slash-Kommandos](#slash-kommandos)
8. [CLI-Flags](#cli-flags)
9. [Konfiguration](#konfiguration)
10. [MCP - Model Context Protocol](#mcp---model-context-protocol)
11. [Hooks & Automation](#hooks--automation)
12. [Praktische Workflows](#praktische-workflows)
13. [Troubleshooting](#troubleshooting)

---

# 🎯 WAS IST CLAUDE CODE?

Claude Code ist **Anthropic's agentic coding tool** - ein KI-Partner im Terminal, der:

✅ **Deinen gesamten Codebase versteht** (nicht nur einzelne Dateien)
✅ **Natursprachliche Befehle ausführt** ("Refaktoriere diese Funktion", "Schreib Tests")
✅ **Datei liest, ändert und erstellt** (mit Bestätigung)
✅ **Bash-Kommandos ausführt** (Code testen, Git Operationen)
✅ **Multi-Datei-Reasoning** (versteht Zusammenhänge über Dateien)
✅ **Git-Workflows** (Commits, Branches, Diffs)
✅ **Im Terminal** (nicht in der Web-UI oder IDE Plugin)

## Unterschied zu Claude.ai / ChatGPT:

| Feature | Claude Code | Claude.ai | ChatGPT |
|---------|------------|----------|---------|
| **Ausführungsumgebung** | Terminal (lokal) | Web-Browser | Web-Browser |
| **Dateisystem-Zugriff** | Ja (mit Kontrolle) | Nein | Nein |
| **Code ausführen** | Ja (Bash) | Nein | Nein |
| **Kontextgröße** | Sehr groß | Groß | Groß |
| **IDE Integration** | Terminal + VS Code | Nein | Mit Plugins |
| **Kostenmodell** | API Pay-as-you-go ODER Pro/Max Abo | Pro/Max Abo | Bezahlt |

---

# 💻 SYSTEMANFORDERUNGEN

## Minimale Anforderungen:

```bash
# OS
- macOS 12+
- Ubuntu 20.04+ (oder anderes Linux)
- Windows 11 (über WSL2) ODER Windows nativer Installer

# Software
- Node.js v18.0.0 oder höher
- npm v8.0.0 oder höher
- Git v2.30.0 oder höher
- Terminal: Bash, Zsh, PowerShell, oder CMD

# Empfohlen
- RAM: 8GB+
- Freier Speicher: 2GB+
- Internet-Verbindung (ständig erforderlich)
```

## Version prüfen:

```bash
node --version       # Sollte v18+
npm --version        # Sollte v8+
git --version        # Sollte v2.30+
```

---

# 📦 INSTALLATION

## Option 1: Nativer Installer (EMPFOHLEN - Neu 2025/2026)

**Kein Node.js erforderlich!** Anthropic bietet native Installer an.

### macOS:

```bash
# Downloaden und installieren
curl -fsSL https://claude.ai/install.sh | bash

# Oder mit Homebrew
brew tap anthropics/claude-code
brew install claude-code

# Oder die neueste Version (weekly releases)
brew install claude-code@latest

# Verifizieren
claude --version
```

### Linux (Ubuntu/Debian):

```bash
curl -fsSL https://claude.ai/install.sh | bash

# Oder mit Paket-Manager
sudo apt update
sudo apt install claude-code

# Verifizieren
claude --version
```

### Linux (Fedora/RHEL):

```bash
curl -fsSL https://claude.ai/install.sh | bash

# Oder mit dnf
sudo dnf install claude-code
```

### Linux (Alpine):

```bash
curl -fsSL https://claude.ai/install.sh | bash

# Oder mit apk
apk add claude-code
```

### Windows (Native Installer):

```powershell
# Öffne PowerShell (NICHT Git Bash zuerst!)
irm https://claude.ai/install.ps1 | iex

# Dann verifizieren
claude --version
```

Alternativ mit CMD:

```cmd
# Öffne CMD
curl https://claude.ai/install.sh | bash

# Verifizieren
claude --version
```

### Windows (WSL - empfohlen für Entwickler):

```bash
# In deinem WSL Terminal (Ubuntu/Debian)
curl -fsSL https://claude.ai/install.sh | bash

claude --version
```

## Option 2: NPM Installation (Älter, aber kompatibel)

```bash
# Installation
npm install -g @anthropic-ai/claude-code

# KEIN sudo! Besser: npm permissions konfigurieren
# Falls Fehler: npm permissions konfigurieren (siehe unten)

# Verifizieren
claude --version

# Aktualisieren
npm install -g @anthropic-ai/claude-code@latest
```

## Option 3: npm Permissions Fix (Falls Fehler bei Option 2)

```bash
# Erstelle lokales npm Verzeichnis
mkdir ~/.npm-global

# Setze npm Konfiguration
npm config set prefix '~/.npm-global'

# Füge PATH hinzu (bashrc oder zshrc)
echo 'export PATH=~/.npm-global/bin:$PATH' >> ~/.bashrc
source ~/.bashrc

# Jetzt installieren
npm install -g @anthropic-ai/claude-code

# Verifizieren
claude --version
```

## Installation Verifizierung:

```bash
# Sollte Version anzeigen (z.B. "1.4.2")
claude --version

# Sollte Claude's Help anzeigen
claude --help

# PATH überprüfen
which claude

# Sollte zeigen, wo Claude installiert ist
```

---

# 🔐 AUTHENTIFIZIERUNG

Bevor du Claude Code benutzen kannst, musst du dich authentifizieren.

## Option A: OAuth (Empfohlen für Pro/Max Subscribers)

```bash
# Authentifizierung starten
claude auth login

# Ein Browser-Fenster öffnet sich automatisch
# 1. Mit deinem Anthropic-Account einloggen
# 2. Claude Code Zugriff autorisieren
# 3. Browser zeigt "Authorization successful"
# 4. Terminal sollte "Authentication successful" zeigen
```

**Vorteil:** Sicher, keine API-Keys im Terminal gespeichert.

## Option B: API Key (Pay-as-you-go Model)

### 1. API Key generieren:

```bash
# 1. Gehe zu https://console.anthropic.com/
# 2. Login oder Account erstellen
# 3. "API Keys" im Menü
# 4. "Create Key"
# 5. Copy den Key (startet mit "sk-")
```

### 2. Claude Code mit API Key authentifizieren:

**SICHER (Empfohlen):**

```bash
# Nur für diese Session
export ANTHROPIC_API_KEY="sk-ant-..."
claude

# Nach Beenden ist Key weg
```

**DAUERHAFT (Vorsicht mit Sicherheit):**

```bash
# Option A: Mit Secrets Manager (1Password, Bitwarden, etc.)
# Option B: Mit .env Datei (nur im Projekt!)

# Im Projekt-Verzeichnis:
echo "ANTHROPIC_API_KEY=sk-ant-..." > .env

# Dann:
export ANTHROPIC_API_KEY=$(cat .env | grep API | cut -d= -f2)
claude
```

**UNSICHER (NICHT EMPFOHLEN!):**

```bash
# ❌ NICHT in ~/.bashrc schreiben!
# Dies exponiert den Key zu allen Child-Prozessen
```

### 3. Authentifizierung verifizieren:

```bash
claude auth status

# Sollte anzeigen: "Authenticated as [username]"
```

## Kosten & Pricing:

**Claude Code kostet NICHT extra für:**
- Pro Subscriber ($20/Monat) - Claude Code inklusive
- Max Subscriber ($100/Monat) - Claude Code inklusive

**Kosten für API-Key Authentifizierung:**
- Pay-per-call Modell
- Abhängig von Token-Verbrauch
- Ungefähr: $0.003 pro 1K Tokens (abhängig von Modell)

**Empfehlung:**
- Anfänger: Starter Plan ($20/Monat)
- Häufige Nutzung: Pro/Max ($100/Monat)
- Sehr häufig: Max 20x ($200/Monat)

---

# 🚀 ERSTE SCHRITTE

## Schritt 1: Projekt-Verzeichnis vorbereiten

```bash
# Neues Projekt erstellen
mkdir mein_projekt
cd mein_projekt

# Oder existierendes Projekt
cd ~/existierendes_projekt

# Git initialisieren (optional aber empfohlen)
git init
git config user.name "Dein Name"
git config user.email "dein@email.com"
```

## Schritt 2: Claude starten

```bash
# Im Projekt-Verzeichnis
claude

# Es sollte einen interaktiven Prompt zeigen:
# "claude>" oder ">>>"
```

## Schritt 3: Erste Eingaben

```bash
# Beispiel 1: Claude nach Hilfe fragen
>> Was kann ich mit dir tun?

# Beispiel 2: Datei analysieren
>> Analysiere die Datei main.py

# Beispiel 3: Code generieren
>> Schreib eine Python Funktion, die...

# Beispiel 4: Beenden
>> exit
```

## Schritt 4: Mit Exit Code arbeiten

```bash
# Claude führt Code aus und zeigt Ergebnis
# Du kannst dann bestätigen oder ablehnen

# Wenn Claude Änderungen vorschlägt:
# [Claude zeigt diff]
# Do you want to apply these changes? (y/n)

# Gib 'y' für Yes oder 'n' für No ein
```

---

# 🎮 KERN-BEFEHLE

Diese Befehle funktionieren immer, ohne spezielles Setup.

## Interactive Mode (Standard)

```bash
# Startet interaktive Session
claude

# Du kannst dann tippen und mit Claude chatten
>> Meine Eingabe hier

# Mehrere Eingaben möglich, bis du exit tippst
>> exit
```

## Single Command Mode (-c)

```bash
# Sendet einen Befehl und zeigt Antwort
claude "Erkläre mir Recursion in Python"

# Datei analysieren
claude "Analysiere errors in main.py"

# Mit Pfad
cd ~/projekt && claude "Welche Tests fehlen?"
```

## Continue Mode (-c + -p)

```bash
# Resumiert letzte Session + neue Eingabe + Exit
claude -cp "Erweitere den vorherigen Code um Logging"

# Äquivalent zu:
# 1. claude -c (continue last session)
# 2. Sende neue Eingabe
# 3. Zeige Output
# 4. Exit automatisch
```

## Read File (-f)

```bash
# Liest Datei ohne ganzes Projekt
claude -f datei.py "Erkläre diese Funktion"

# Mit Mehreren Dateien
claude -f src/main.py src/utils.py "Wie hängen diese zusammen?"
```

## Version & Help

```bash
# Aktuelle Version anzeigen
claude --version

# Hilfe anzeigen
claude --help

# Detaillierte Hilfe
claude --help verbose

# Welche Befehle zur Verfügung stehen
claude commands
```

## Update Claude Code

```bash
# Mit nativen Installer (auto-update)
# Wird automatisch im Hintergrund aktualisiert

# Mit Homebrew (manuell)
brew upgrade claude-code

# Mit npm (manuell)
npm install -g @anthropic-ai/claude-code@latest

# Verifizieren
claude --version
```

---

# ⚡ SLASH-KOMMANDOS

Innerhalb einer Claude Code Session kannst du Slash-Kommandos verwenden:

## File Commands

```bash
/read datei.txt              # Datei-Inhalt zeigen
/read src/                   # Ganzen Ordner zeigen
/read *.py                   # Mehrere Dateien (glob)
/read -p                     # Nur Pfade ohne Inhalt

/write datei.txt "content"   # Datei schreiben
/write -a datei.txt "mehr"   # Anhängen
/write -e datei.txt          # Edit-Mode
```

## Code Execution

```bash
/bash "ls -la"               # Bash-Kommando ausführen
/bash                        # Interaktive Bash Session
/python "print('hello')"     # Python ausführen
/python -i script.py         # Python interaktiv

/npm install paket           # npm Befehl
/git status                  # Git Befehl
/git diff                    # Git diff anzeigen
```

## Git Commands

```bash
/git clone https://...       # Repository klonen
/git add .                   # Files stagen
/git commit "message"        # Commit mit Message
/git push                    # Zu Remote pushen
/git branch feature          # Neuen Branch
/git checkout feature        # Branch wechseln
/git merge main              # Mergen
```

## Project Context

```bash
/context                     # Zeige aktuelle Context
/context add datei.txt       # File zu Context hinzufügen
/context remove datei.txt    # File aus Context entfernen
/context clear               # Context löschen
/context set "Custom prompt" # Custom Context setzen
```

## Session Management

```bash
/clear                       # History löschen
/exit                        # Session beenden
/quit                        # Beenden (Alias)

/history                     # Zeige Session-History
/save session_name.md        # Session speichern
/load session_name.md        # Session laden
```

## Output Styles

```bash
/output-style explanatory    # Mit erklärungen
/output-style learning       # Für Lernen
/output-style concise        # Kurz und knapp
/output-style technical      # Technisch detailliert
/output-style my-style       # Benutzerdefiniert
```

## Andere

```bash
/bug                         # Bug melden
/feedback                    # Feedback geben
/help                        # Hilfe anzeigen
/settings                    # Einstellungen zeigen
```

---

# 🚩 CLI-FLAGS

Diese Flags verwendest du vom Terminal aus (nicht in der Session):

```bash
# Authentifizierung
claude auth login            # Einloggen
claude auth status           # Status prüfen
claude auth logout           # Ausloggen

# Modus
claude                       # Interaktiv (Standard)
claude "text"               # Single Command
claude -c                   # Continue (letzter Session fortsetzen)
claude -cp "text"           # Continue + Print + Exit
claude -f datei.txt "text"  # File Mode

# Ausgabe
claude -p                   # Print (zu stdout)
claude -v                   # Verbose (detailliert)
claude --debug              # Debug-Modus

# Konfiguration
claude config set key value # Einstellung ändern
claude config get key       # Einstellung lesen
claude config list          # Alle Einstellungen

# Projekt
claude --project /pfad      # Spezifisches Projekt
claude --ignore-patterns    # .claudeignore nutzen

# Performance
claude --model opus         # Modell wählen
claude --max-tokens 4000    # Max Output Tokens
claude --timeout 300        # Timeout in Sekunden

# Andere
claude --version           # Version anzeigen
claude --help              # Hilfe anzeigen
```

---

# ⚙️ KONFIGURATION

## Config-Datei Struktur

Claude Code nutzt Konfigurationsdateien an mehreren Orten:

```
~/.claude/
├── config.json            # Globale Konfiguration
├── auth.json              # Auth-Tokens (automatisch)
├── history.json           # Session-History
└── commands/              # Custom Slash-Kommandos
    ├── my-review.yaml
    └── my-test.yaml

.claude/                    # Im Projekt-Verzeichnis
├── config.json            # Projekt-spezifisch
├── commands/              # Projekt-Kommandos
├── .claudeignore          # Welche Dateien ignorieren
└── CLAUDE.md              # Projekt-Dokumentation
```

## Config.json Beispiel

```json
{
  "model": "claude-opus-4-1",
  "max_tokens": 4096,
  "temperature": 0.7,
  "timeout": 300,
  "auto_apply": false,
  "git_auto_commit": false,
  "exclude_patterns": [
    "node_modules/",
    ".git/",
    "*.log",
    "dist/",
    "build/"
  ],
  "bash_shell": "bash",
  "editor": "nano",
  "output_style": "explanatory",
  "verbose": false,
  "api_key_source": "oauth"
}
```

## .claudeignore Datei

Ähnlich wie .gitignore - welche Dateien Claude ignoriert:

```
# In der Projekt-Root als .claude/.claudeignore oder .claudeignore

# Dependencies
node_modules/
__pycache__/
.venv/
venv/

# Build/Dist
dist/
build/
.next/
out/

# Env & Secrets
.env
.env.local
*.key
*.pem
secrets/
.credentials/

# Logs & Temp
*.log
tmp/
temp/
.cache/

# IDE
.vscode/
.idea/
*.swp
*.swo

# Große Dateien
*.zip
*.tar.gz
*.iso
*.dmg

# Spezifische Dateien
config/secrets.json
database.db
```

## CLAUDE.md - Projekt-Kontext

Erstelle eine `CLAUDE.md` im Projekt für spezifische Instruktionen:

```markdown
# Mein Projekt - Claude Code Instruktionen

## Tech Stack
- Framework: Next.js 14 (App Router)
- Language: TypeScript (strict mode)
- Styling: Tailwind CSS v3.4
- Database: PostgreSQL via Prisma
- Testing: Jest

## Coding Conventions
- Use named exports, not default exports
- Prefer `interface` over `type`
- All components must be functional
- Use `async/await`, never `.then()`
- Error handling: use Result types, not try/catch

## File Structure
- `src/app/` — Next.js routes
- `src/components/` — UI components
- `src/server/` — API routes
- `src/lib/` — Utilities
- `prisma/` — Database schema

## Rules
- DO NOT modify migration files directly
- DO NOT install dependencies without approval
- Always run `npm lint` before submitting
- Keep components under 150 lines

## Common Commands
- `npm run dev` — Development Server
- `npm test` — Run Tests
- `npm lint` — Linting
- `npm build` — Production Build
- `prisma migrate dev` — Create Migration
```

## Einstellungen ändern

```bash
# Global
claude config set model claude-opus-4-1
claude config set max_tokens 8192
claude config set timeout 600

# Lokal (im Projekt)
cd mein_projekt
claude config set auto_apply true
claude config set output_style concise

# Anzeigen
claude config list
claude config get model
```

---

# 🔗 MCP - MODEL CONTEXT PROTOCOL

MCP verbindet Claude Code mit externen Services (Datenbanken, APIs, Tools, etc.).

## Was ist MCP?

MCP ermöglicht Claude Code Zugriff auf:
- ✅ Datenbanken (PostgreSQL, MySQL, SQLite)
- ✅ APIs (GitHub, Slack, Jira, etc.)
- ✅ Services (AWS, Google Cloud, etc.)
- ✅ File Systems (Remote Servers)
- ✅ Custom Tools (deine eigenen Scripts)

**300+ MCP-Integrationen verfügbar.**

## MCP Server hinzufügen

```bash
# Interaktive Hinzufügung
claude mcp add

# Automatische Liste mit populären Services
# Wähle eine oder mehrere aus

# Danach: Authentifizierung/Konfiguration folgt
```

## MCP Server manuell konfigurieren

**Datei: `~/.claude/mcp_servers.json`**

```json
{
  "servers": [
    {
      "name": "github",
      "command": "python3 -m mcp.server.github",
      "args": [],
      "env": {
        "GITHUB_TOKEN": "ghp_..."
      }
    },
    {
      "name": "postgresql",
      "command": "python3 -m mcp.server.postgres",
      "args": [
        "--connection-string",
        "postgresql://user:pass@localhost/db"
      ]
    },
    {
      "name": "slack",
      "command": "node /path/to/slack-mcp",
      "env": {
        "SLACK_BOT_TOKEN": "xoxb-..."
      }
    }
  ]
}
```

## Beliebte MCP Integrationen

### GitHub
```bash
claude mcp add github

# Erlaubt:
# - PRs lesen/erstellen
# - Issues verwalten
# - Code Reviews
# - Commits pushen
```

### PostgreSQL
```bash
claude mcp add postgresql

# Konfiguriere Verbindung:
postgresql://username:password@localhost:5432/database_name

# Erlaubt:
# - Queries ausführen
# - Schema ändern
# - Daten migrieren
```

### Slack
```bash
claude mcp add slack

# Erfordert Slack Bot Token

# Erlaubt:
# - Messages senden
# - Files hochladen
# - Channel durchsuchen
```

### Jira
```bash
claude mcp add jira

# Erfordert Jira API Token

# Erlaubt:
# - Issues erstellen/ändern
# - Status aktualisieren
# - Comments hinzufügen
```

### AWS
```bash
claude mcp add aws

# Konfiguriere AWS Credentials

# Erlaubt:
# - S3 Buckets verwalten
# - EC2 Instances starten
# - Lambda Functions aufrufen
```

## MCP im Projekt nutzen

Sobald konfiguriert, kannst du in Claude Code sagen:

```bash
claude

>> Erstelle ein Issue auf GitHub für diese TODO
# Claude nutzt automatisch GitHub MCP

>> Schreib die Migrations zu PostgreSQL
# Claude nutzt automatisch Postgres MCP

>> Sende eine Nachricht zu #development auf Slack
# Claude nutzt automatisch Slack MCP
```

---

# 🎣 HOOKS & AUTOMATION

Hooks automatisieren Aufgaben bei bestimmten Ereignissen.

## Hook-Typen

### Pre-Commit Hook

```bash
# .claude/hooks/pre-commit.sh

#!/bin/bash

# Führe Tests aus
npm test

# Linting
npm lint

# Code Format
npm run format

# Nur committen wenn alles OK
```

### Post-Commit Hook

```bash
# .claude/hooks/post-commit.sh

#!/bin/bash

# Generiere Changelog
npm run changelog

# Push automatisch
git push
```

### Pre-Push Hook

```bash
# .claude/hooks/pre-push.sh

#!/bin/bash

# Finaler Test
npm test

# Build Check
npm run build

# Type Check
npm run type-check
```

### Custom Hook

```yaml
# .claude/commands/code-review.yaml

description: >
  Security-focused code review with comprehensive checks

allowed-tools:
  - Read
  - Grep
  - Glob

model: claude-opus-4-1

body: |
  Review this code for:
  1. Security vulnerabilities
  2. Performance issues
  3. Memory leaks
  4. Unused variables
  5. Error handling gaps
  
  Format your response as:
  - **Issue**: [description]
  - **Severity**: [critical/high/medium/low]
  - **Fix**: [suggestion]
```

## Hooks aktivieren

```bash
# Stelle sicher Dateien executable sind
chmod +x .claude/hooks/*.sh

# Claude nutzt sie automatisch
claude

# Bei jedem Commit wird der Hook ausgeführt
```

---

# 📋 PRAKTISCHE WORKFLOWS

## Workflow 1: Code-Review & Refactoring

```bash
claude

>> Führe einen vollständigen Code Review meines Projekts durch
>> Zeige Design-Antipatterns
>> Refaktoriere komplexe Funktionen
>> Aktualisiere Tests

# Claude wird:
# 1. Alle Dateien analysieren
# 2. Probleme identifizieren
# 3. Refactoring vorschlagen
# 4. Diffs zeigen
# 5. Auf Bestätigung warten
```

## Workflow 2: Automatische Tests generieren

```bash
claude

>> Generiere Unit Tests für src/services/
>> Nutze Jest
>> Ziele: >80% Coverage
>> Mocking wo nötig

# Claude wird:
# 1. Service-Funktionen analysieren
# 2. Test-Cases identifizieren
# 3. Test-Dateien generieren
# 4. Mocks erstellen
# 5. Alle Tests ausführen
```

## Workflow 3: Dokumentation schreiben

```bash
claude

>> Schreib README.md für diesen Projekt
>> Schreib API Documentation in docs/api.md
>> Erstelle Deployment Guide
>> Code-Kommentare wo nötig

# Claude wird:
# 1. Projektstruktur analysieren
# 2. Dokumentation generieren
# 3. Code-Beispiele hinzufügen
# 4. Dateien erstellen
```

## Workflow 4: Bug-Fix mit Git

```bash
claude

>> Es gibt einen Bug in auth.js Zeile 45
>> Hier ist die Error Message: [...]
>> Analysiere das Problem
>> Schreib einen Fix
>> Erstelle einen Git Commit

# Claude wird:
# 1. Datei analysieren
# 2. Bug identifizieren
# 3. Fix implementieren
# 4. Tests schreiben
# 5. Git commit erstellen
```

## Workflow 5: Migrationen durchführen

```bash
claude

>> Migriere den Code von CommonJS zu ES Modules
>> Finde alle require() Statements
>> Konvertiere zu import/export
>> Aktualisiere package.json
>> Teste dass alles noch funktioniert

# Claude wird:
# 1. Alle Dateien durchsuchen
# 2. require() zu import konvertieren
# 3. Exporte aktualisieren
# 4. Tests ausführen
# 5. Potenzielle Fehler zeigen
```

## Workflow 6: Performance Optimization

```bash
claude

>> Analysiere Performance-Bottlenecks
>> Nutze diese Metriken: [...]
>> Optimiere langsame Funktionen
>> Füge Caching hinzu wo sinnvoll
>> Benchmark vorher/nachher

# Claude wird:
# 1. Code-Hotspots finden
# 2. Optimierungen vorschlagen
# 3. Changes implementieren
# 4. Tests durchführen
# 5. Performance-Report zeigen
```

---

# 🐛 TROUBLESHOOTING

## "command not found: claude"

**Problem:** Claude Code ist nicht im PATH

**Lösungen:**

```bash
# 1. Prüfe ob Installation erfolgreich war
which claude

# 2. Wenn nothing returned:
# - Terminal neustarten
# - Shell reload
source ~/.bashrc  # oder ~/.zshrc

# 3. Manuell PATH hinzufügen
echo 'export PATH=~/.npm-global/bin:$PATH' >> ~/.bashrc
source ~/.bashrc

# 4. Neu installieren
npm install -g @anthropic-ai/claude-code
```

## "EACCES: permission denied"

**Problem:** Permission-Fehler bei Installation

**Lösung:**

```bash
# ❌ NICHT sudo verwenden!
# ✅ npm Permissions konfigurieren

mkdir ~/.npm-global
npm config set prefix '~/.npm-global'
echo 'export PATH=~/.npm-global/bin:$PATH' >> ~/.bashrc
source ~/.bashrc

npm install -g @anthropic-ai/claude-code
```

## "Module not found '@anthropic-ai/sdk'"

**Problem:** Abhängigkeiten fehlen

**Lösung:**

```bash
# Cache leeren
npm cache clean --force

# Neu installieren
npm install -g @anthropic-ai/claude-code

# Oder mit Homebrew
brew install claude-code
```

## "Authentication failed"

**Problem:** API Key oder OAuth fehlgeschlagen

**Lösungen:**

```bash
# 1. Auth Status prüfen
claude auth status

# 2. Neu einloggen
claude auth logout
claude auth login

# 3. Wenn API Key:
echo $ANTHROPIC_API_KEY
# Sollte mit "sk-" starten

# 4. Key neusetzen
unset ANTHROPIC_API_KEY
export ANTHROPIC_API_KEY="sk-ant-..."
claude auth status
```

## "Request timeout"

**Problem:** Verbindung zu Claude API zu langsam

**Lösungen:**

```bash
# 1. Timeout erhöhen
claude config set timeout 600

# 2. Projekt zu groß? Context reduzieren
# - .claudeignore nutzen
# - Nur relevante Dateien laden

# 3. Netzwerk prüfen
ping api.anthropic.com

# 4. Request kleiner machen
claude -f kleine_datei.py "Analysiere dies"
```

## "Out of context"

**Problem:** Projekt zu groß für Context Window

**Lösung:**

```bash
# 1. .claudeignore erstellen/erweitern
echo "node_modules/" >> .claudeignore
echo "dist/" >> .claudeignore
echo "*.log" >> .claudeignore

# 2. Nur spezifische Dateien laden
claude -f src/main.py "Analysiere"

# 3. Projekt aufteilen
# - Arbeite in kleineren Teilen
# - Pro Funktion statt ganzes Projekt
```

## "Git conflict"

**Problem:** Git Merge-Konflikt nach Claude Changes

**Lösung:**

```bash
# 1. Konflikt manuell lösen
git status
# Zeigt conflicted files

# 2. Datei öffnen und <<<<<<, ======, >>>>>> löschen

# 3. Mergen abschließen
git add .
git commit -m "Resolve conflicts"

# 4. Claude um Hilfe bitten
claude "Löse diese Git Konflikte auf"
```

## "Connection refused"

**Problem:** Kann nicht zur Claude API verbinden

**Lösungen:**

```bash
# 1. Internet-Verbindung prüfen
ping google.com

# 2. Firewall/Proxy? VPN?
# Claude braucht Zugriff auf: api.anthropic.com

# 3. Neustart
# Terminal + Computer neustarten

# 4. Credentials reset
claude auth logout
claude auth login
```

---

# 💡 TIPPS & TRICKS

## Effektive Prompts schreiben

### ✅ GUTE Prompts:
```bash
>> Refaktoriere die calculateTotal() Funktion um:
>> - Readability zu verbessern
>> - Performance zu optimieren
>> - Error Handling hinzufügen
>> - Tests zu aktualisieren
```

### ❌ SCHLECHTE Prompts:
```bash
>> Mach das besser
>> Fix the bugs
>> Schreib Code
```

## Context sparen

```bash
# Nur eine Datei laden
claude -f src/auth.py "Erkläre die Logik"

# Statt ganzes Projekt zu laden
claude "Erkläre src/auth.py"
```

## Mehrere Sessions parallelisieren

```bash
# Terminal 1: Feature Entwicklung
terminal1> cd proj && claude

# Terminal 2: Code Review
terminal2> cd proj && claude -c

# Terminal 3: Debugging
terminal3> cd proj && claude -cp "Debug this error"
```

## Custom Slash-Kommandos erstellen

```bash
mkdir -p .claude/commands

# Datei: .claude/commands/security-audit.yaml
cat > .claude/commands/security-audit.yaml << 'EOF'
description: Comprehensive security audit
allowed-tools:
  - Read
  - Grep
model: claude-opus-4-1
body: |
  Audit this code for security:
  1. SQL Injection
  2. XSS vulnerabilities
  3. CSRF issues
  4. Auth bypasses
  5. Data exposure
EOF

# Nutzen:
claude
>> /security-audit
```

## Claude Code in CI/CD nutzen

```bash
#!/bin/bash
# In deinem CI/CD Pipeline

# Vor Commit: Code Review
ANTHROPIC_API_KEY=$API_KEY claude -p "Review this code for production readiness" > review.md

# Tests generieren falls nicht existiert
ANTHROPIC_API_KEY=$API_KEY claude -p "Generate missing tests" 

# Dokumentation aktualisieren
ANTHROPIC_API_KEY=$API_KEY claude -p "Update README and API docs"

# Commit wenn alles OK
git add .
git commit -m "Auto: Code review, tests, docs"
```

## Performance Metriken nutzen

```bash
# Messe wie lange Claude braucht
time claude "Analysiere diesen Code"

# Nutze kleinere Modelle für schnelle Tasks
claude --model claude-haiku "Erkläre kurz"
# Schneller und günstiger!

# Nutze Opus nur für komplexe Tasks
claude --model claude-opus-4-1 "Komplexe Refactorierung"
```

---

# 📚 WEITERE RESSOURCEN

## Offizielle Dokumentation

- **Claude Code Docs:** https://code.claude.com/docs
- **Anthropic Console:** https://console.anthropic.com
- **GitHub Repository:** https://github.com/anthropics/claude-code

## Community

- **Discord:** https://discord.gg/anthropic
- **GitHub Discussions:** https://github.com/anthropics/claude-code/discussions
- **Stack Overflow:** Tag `claude-ai`

## Tipps & Tricks

- **Blog:** https://blog.anthropic.com
- **Videos:** Claude Code Tutorials auf YouTube
- **Beispiele:** https://github.com/anthropics/cookbook

---

# 🎯 ZUSAMMENFASSUNG

## Die wichtigsten Befehle nochmal:

```bash
# Installation
curl -fsSL https://claude.ai/install.sh | bash  # oder Homebrew

# Authentifizierung
claude auth login                    # Mit OAuth (empfohlen)
export ANTHROPIC_API_KEY="sk-..."  # Mit API Key

# Basis-Nutzung
claude                              # Interaktiv starten
claude "Deine Frage"                # Single Command
claude -cp "text"                   # Continue + Print
claude -f datei.py "text"           # Spezifische Datei

# Konfiguration
claude config set model claude-opus-4-1
claude config set max_tokens 8192
claude mcp add                      # Externe Services

# Troubleshooting
claude --version
claude auth status
claude --help
```

---

**Claude Code ist dein Partner für schnellere, bessere Coding!** 🚀

Für aktuelle Updates: https://code.claude.com/docs
