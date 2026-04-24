# 📋 CLAUDE CODE - QUICK REFERENCE

Spickzettel für schnelle Nachschläge.

---

## 🚀 INSTALLATION (Schnell)

### macOS / Linux
```bash
curl -fsSL https://claude.ai/install.sh | bash
claude --version  # Verify
```

### macOS (Homebrew)
```bash
brew tap anthropics/claude-code
brew install claude-code
```

### Windows (PowerShell)
```powershell
irm https://claude.ai/install.ps1 | iex
claude --version  # Verify
```

### npm (Wenn alles andere fehlschlägt)
```bash
npm install -g @anthropic-ai/claude-code
```

---

## 🔐 AUTHENTIFIZIERUNG

```bash
# OAuth (empfohlen)
claude auth login          # Browser öffnet sich
claude auth status         # Check ob authenticated

# API Key
export ANTHROPIC_API_KEY="sk-ant-..."
claude auth status

# Problem: "command not found"?
source ~/.bashrc  # oder ~/.zshrc
```

---

## 🎮 CORE USAGE PATTERNS

### Pattern 1: Interactive Mode (Standard)
```bash
cd mein_projekt
claude
# Dann: >> Deine Frage hier
# Mehrere Fragen möglich
# exit zum Beenden
```

### Pattern 2: Single Command
```bash
claude "Erkläre diesen Code"
# Sofort Antwort, dann Exit
```

### Pattern 3: Continue + Print + Exit
```bash
claude -cp "Erweitere vom letzten"
# Lädt -c (continue)
# Sendet Input
# Zeigt -p (print)
# -x (exit) automatisch
```

### Pattern 4: Specific File
```bash
claude -f datei.py "Analysiere"
# Nur diese Datei laden, nicht ganzes Projekt
```

---

## ⚡ SLASH COMMANDS (In Session)

### File Operations
```bash
/read datei.txt              # Zeige Datei
/read src/                   # Zeige Ordner
/write -a datei.txt "text"   # Anhängen
/write datei.txt "content"   # Schreiben
```

### Code Execution
```bash
/bash ls -la                 # Run bash
/bash                        # Interactive bash
/python print('hello')       # Run python
/npm install paket           # npm
/git status                  # git
```

### Project
```bash
/context                     # Zeige aktuelle context
/context add file.py         # Zu context hinzufügen
/context clear               # Context leeren
/clear                       # History löschen
/exit                        # Beenden
```

### Style
```bash
/output-style explanatory    # Mit Erklärungen
/output-style learning       # Zum Lernen
/output-style concise        # Kurz
```

---

## 🚩 CLI FLAGS

```bash
# Basic
claude                    # Interactive
claude "text"            # Single command
claude -c                # Continue last session
claude -cp "text"        # Continue + Print + Exit
claude -f file "text"    # Specific file

# Auth
claude auth login        # OAuth
claude auth status       # Check
claude auth logout       # Logout

# Config
claude config set key value  # Set config
claude config get key        # Get config
claude config list           # All settings

# Info
claude --version         # Version
claude --help            # Help
```

---

## ⚙️ CONFIGURATION

### Wichtige Settings
```bash
claude config set model claude-opus-4-1      # Modell
claude config set max_tokens 8192            # Output Limit
claude config set timeout 300                # Timeout Sekunden
claude config set auto_apply false           # Auto-Änderungen
```

### Config-Dateien
```
~/.claude/config.json         # Global
~/.claude/mcp_servers.json    # MCP Config
.claude/config.json           # Projekt-spezifisch
.claudeignore                 # Welche Dateien ignorieren
CLAUDE.md                     # Projekt-Kontext
```

### .claudeignore Muster
```
node_modules/
dist/
build/
.env
*.log
__pycache__/
.venv/
*.pyc
```

### CLAUDE.md Template
```markdown
# Mein Projekt

## Tech Stack
- Language: Python 3.9
- Framework: Django

## Rules
- Use type hints
- Write tests
- PEP 8 style

## Files
- `src/` - Source code
- `tests/` - Tests
```

---

## 🔗 MCP - External Services

```bash
# Hinzufügen
claude mcp add                    # Interactive add
claude mcp list                   # Liste alle MCPs

# Beliebte MCPs
# GitHub      - PR/Issue Management
# PostgreSQL  - Datenbank Queries
# Slack       - Message senden
# Jira        - Issue Tracking
# AWS         - Cloud Services
```

---

## 💡 PRAKTISCHE WORKFLOWS

### Workflow: Code Review
```bash
claude

>> Führe Code Review durch
>> - Security check
>> - Performance
>> - Tests

>> Refaktoriere komplexe Funktionen
>> exit
```

### Workflow: Tests generieren
```bash
claude

>> Generiere Unit Tests für src/
>> - >80% Coverage
>> - Jest Framework
>> - Mock wo nötig

>> Führe Tests aus
>> exit
```

### Workflow: Dokumentation
```bash
claude

>> Schreib README.md
>> Schreib API Docs
>> Code Comments hinzufügen
>> exit
```

### Workflow: Bug Fix mit Git
```bash
claude

>> Debugge diesen Fehler: [error]
>> Implementiere Fix
>> Schreib Test
>> Git Commit

/git status
/git add .
/git commit "Fix: error message"
>> exit
```

---

## 🎯 QUICK RECIPES

### Recipe 1: Code Review & Fix
```bash
claude -f buggy.py "Code Review & refactor"
```

### Recipe 2: Generate Documentation
```bash
claude -cp "Write README and API docs"
```

### Recipe 3: Analyze Project
```bash
claude "What does this project do? Architecture?"
```

### Recipe 4: Write Tests
```bash
claude -cp "Generate comprehensive tests for src/"
```

### Recipe 5: Migrate Code
```bash
claude "Migrate from CommonJS to ES Modules"
```

---

## 🐛 QUICK FIXES

### "command not found: claude"
```bash
source ~/.bashrc  # or ~/.zshrc
which claude      # Check PATH
npm list -g @anthropic-ai/claude-code
```

### "Authentication failed"
```bash
claude auth logout
claude auth login
# oder
export ANTHROPIC_API_KEY="sk-..."
```

### "EACCES: permission denied"
```bash
mkdir ~/.npm-global
npm config set prefix '~/.npm-global'
echo 'export PATH=~/.npm-global/bin:$PATH' >> ~/.bashrc
source ~/.bashrc
```

### "Context too large"
```bash
# Fix .claudeignore
# oder nutze: claude -f small_file.py "..."
# oder nutze: claude -c (continue, besser context)
```

### "Request timeout"
```bash
claude config set timeout 600  # 10 Minuten
# oder projekt reduzieren
```

---

## 📊 PRICING

| Plan | Kosten | Enthält |
|------|--------|---------|
| Pro | $20/Monat | Claude Code (Pro) |
| Max | $100/Monat | Claude Code (Max) |
| Max 20x | $200/Monat | Claude Code (Max) |
| API Key | Pay-per-use | Basierend auf Tokens |

**Empfehlung:** Pro ($20) für Anfänger, Max ($100) für häufige Nutzung.

---

## 🎮 MODELLE & KOSTEN

```bash
# Schnell & billig
claude config set model claude-haiku

# Balance
claude config set model claude-sonnet-4-5

# Beste (langsamer & teurer)
claude config set model claude-opus-4-1
```

---

## 📚 CHEAT SHEET - TOP 10 BEFEHLE

```bash
1. claude                      # Start interactive
2. claude "question"           # Single command
3. claude auth login           # Auth
4. /read datei.txt            # Read file
5. /bash command              # Execute bash
6. /git status                # Git status
7. claude config set key val  # Config
8. claude -c                  # Continue
9. claude -f file "q"         # File-specific
10. claude --help             # Help
```

---

## 🎓 LEARNING PATH

**Woche 1-2:** Installation, Auth, Basic Commands
```bash
claude auth login
claude "Hello Claude"
/read README.md
```

**Woche 3-4:** Slash Commands & Configuration
```bash
/bash ls -la
/git status
claude config set model
```

**Woche 5-6:** Workflows & Git Integration
```bash
claude "Code review & refactor"
/git commit "message"
```

**Woche 7-8:** MCP & Advanced
```bash
claude mcp add github
/github create-issue
```

---

## ⚡ PERFORMANCE TIPPS

```bash
# Schneller Code Review
claude --model claude-haiku "Review this"

# Bessere Analyse
claude --model claude-opus-4-1 "Complex task"

# Context sparen
echo "src/" > .claudeignore
echo "node_modules/" >> .claudeignore

# Nur Datei laden
claude -f main.py "Analyze"
```

---

## 🔐 SECURITY BEST PRACTICES

```bash
# ✅ SAFE - Für Session
export ANTHROPIC_API_KEY="sk-ant-..."
claude
unset ANTHROPIC_API_KEY

# ❌ UNSAFE - Nicht in ~/.bashrc schreiben!
# Exposes to all subprocesses

# ✅ SAFE - Secrets Manager
export ANTHROPIC_API_KEY="$(op read 'op://Private/Anthropic/key')"

# ✅ SAFE - .env (local only, nicht commiten)
# .env in .gitignore
# source .env vor claude
```

---

## 📖 OFFICIAL RESOURCES

- Docs: https://code.claude.com/docs
- GitHub: https://github.com/anthropics/claude-code
- Console: https://console.anthropic.com
- Support: https://support.claude.com

---

## 🎯 QUICK START (5 MINUTEN)

```bash
# 1. Install
curl -fsSL https://claude.ai/install.sh | bash

# 2. Auth
claude auth login

# 3. Create project
mkdir my_project && cd my_project

# 4. Start
claude

# 5. Type
>> Erkläre mir Python Decorators
>> exit

# Done! 🎉
```

---

**Gedruckt, gelaminiert, immer griffbereit!** 📱

Alle anderen 2 Dokumente (Komplett + Workbook) sind für tieferes Lernen.
