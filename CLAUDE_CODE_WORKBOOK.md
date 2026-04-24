# 🎯 CLAUDE CODE WORKBOOK - PRAKTISCHE ÜBUNGEN

Hands-on Übungen, um Claude Code zu meistern.

---

# 1️⃣ INSTALLATION & SETUP

## Übung 1.1: Installation verifizieren

```bash
# 1. Installation überprüfen
which claude

# Sollte ausgeben: /usr/local/bin/claude oder ähnlich

# 2. Version prüfen
claude --version

# Sollte ausgeben: claude version X.Y.Z

# 3. Node.js Check (falls npm-Installation)
node --version
npm --version

# Beide sollten >= erwartete Version sein

# ✅ Erfolgreich wenn alle Checks Versionen zeigen!
```

## Übung 1.2: Authentifizierung

```bash
# 1. Authentifizieren (OAuth - empfohlen)
claude auth login

# Ein Browser-Fenster sollte sich öffnen
# - Login mit Anthropic Account
# - Autorisieren
# - Browser zeigt "Success"
# - Terminal zeigt "Authenticated"

# 2. Status prüfen
claude auth status

# Sollte anzeigen: "Authenticated as [email]"

# 3. Erfolgreicher Test
claude "Hallo! Bist du da?"

# Claude sollte antworten
```

---

# 2️⃣ ERSTE SCHRITTE

## Übung 2.1: Dein erstes Claude-Code Projekt

```bash
# 1. Neues Projekt erstellen
mkdir claude_test
cd claude_test

# 2. Git initialisieren
git init
git config user.name "Dein Name"
git config user.email "dein@email.com"

# 3. Einfache Datei erstellen
echo "# Mein erstes Claude Code Projekt" > README.md

# 4. Claude starten
claude

# 5. In Claude tippen:
>> Schreib eine Hello World Python Funktion

# 6. Claude wird Code vorschlagen
# 7. Wenn du bestätigt (y), wird Datei erstellt
# 8. Exit tippen:
>> exit
```

## Übung 2.2: Dateien analysieren

```bash
# 1. Neue Python-Datei erstellen
cat > beispiel.py << 'EOF'
def calculate_average(numbers):
    total = 0
    for n in numbers:
        total = total + n
    average = total / len(numbers)
    return average

result = calculate_average([1, 2, 3, 4, 5])
print(result)
EOF

# 2. Claude starten
claude

# 3. Datei analysieren
>> Analysiere beispiel.py
>> Erkläre was diese Funktion macht

# 4. Refactorierung fragen
>> Refaktoriere diese Funktion
>> - Nutze sum() statt Schleife
>> - Kommentiere den Code
>> - Füge Type Hints hinzu

# 5. Akzeptieren und auswerten
# y für Ja
# Dann exit
```

---

# 3️⃣ KERN-BEFEHLE ÜBEN

## Übung 3.1: Single Command Mode

```bash
# Diese Befehle funktionieren von außerhalb einer Session

# 1. Code generieren
claude "Schreib eine Funktion die Fibonacci Nummern berechnet"

# 2. Datei analysieren
cd claude_test
claude "Erkläre die Funktion in beispiel.py"

# 3. Fehler debuggen
claude "Warum gibt dieser Code einen Error? [error message here]"

# 4. Dokumentation generieren
claude "Schreib JSDoc Comments für diese JavaScript Funktion"
```

## Übung 3.2: Continue Mode

```bash
# Setze eine tiefere Konversation auf

# 1. Starte Session
claude

# 2. Erste Aufgabe
>> Erstelle eine Todo-App in Python

# 3. Verfeine/erweitere
>> Füge Database-Persistierung hinzu
>> Nutze SQLite

# 4. Tests hinzufügen
>> Schreib Unit Tests

# 5. Exit
>> exit

# 6. Später: Fortsetzen
claude -c

# Claude lädt die letzte Session
# 7. Neue Frage auf Basis des Kontexts
>> Migriere zu PostgreSQL statt SQLite

# 8. Exit wieder
>> exit
```

## Übung 3.3: Continue + Print + Exit Mode

```bash
# Für Scripts und Automatisierung

# 1. Erstelle eine kleine Aufgabe
mkdir mein_projekt
cd mein_projekt
echo "# Projekt" > README.md

# 2. Nutze -cp Flag
claude -cp "Schreib einen Development Guide"

# Das macht:
# - Lädt letzte Session (-c)
# - Sendet neue Eingabe
# - Zeigt Output (-p)
# - Exitet automatisch

# 3. Output weiterverwenden
claude -cp "Update die Version zu 2.0" > version_output.txt
```

---

# 4️⃣ PROJEKTKONTEXT

## Übung 4.1: .claudeignore erstellen

```bash
# 1. In deinem Projekt Root
cd mein_projekt

# 2. Erstelle .claudeignore
cat > .claudeignore << 'EOF'
# Dependencies
node_modules/
__pycache__/
.venv/
venv/

# Build
dist/
build/
.next/

# Secrets
.env
.env.local
*.key
*.pem

# Logs
*.log

# Large files
*.zip
*.tar.gz
EOF

# 3. Teste dass Dateien ignoriert werden
claude "Welche Dateien siehst du in meinem Projekt?"

# Large/sensitive Dateien sollten nicht gelistet sein
```

## Übung 4.2: CLAUDE.md schreiben

```bash
# 1. Erstelle CLAUDE.md
cat > CLAUDE.md << 'EOF'
# Mein Projekt - Kontext für Claude

## Tech Stack
- Language: Python 3.9+
- Framework: Flask
- Database: PostgreSQL
- Testing: pytest

## Code Style
- PEP 8
- Type hints überall
- Docstrings für alle Funktionen

## File Structure
- `app/` - Flask routes
- `models/` - Database models
- `tests/` - Test suite
- `config.py` - Configuration

## Important Rules
- DO NOT drop tables without approval
- DO NOT use raw SQL (use ORM)
- All functions need tests
- Commit messages must be descriptive

## Setup
- `pip install -r requirements.txt`
- `psql < schema.sql`
- `python run.py`

## Common Tasks
- Add endpoint: modify `app/routes.py` + tests
- Database change: create migration
- New model: add to `models/`, migrate, test
EOF

# 2. Claude nutzt diese Infos automatisch
claude "Erstelle einen neuen API Endpoint für User"

# Claude wird die Rules & Struktur aus CLAUDE.md nutzen!
```

---

# 5️⃣ SLASH-KOMMANDOS

## Übung 5.1: Datei-Operationen

```bash
# 1. Session starten
claude

# 2. Datei lesen
>> /read README.md

# Sollte Inhalt anzeigen

# 3. Verzeichnis lesen
>> /read src/

# Alle Dateien in src/ sollten angezeigt werden

# 4. Spezifische Dateien
>> /read src/*.py

# Nur Python Dateien

# 5. Datei schreiben
>> /write test.py

"def hello():
    return 'Hello World'
"

# Datei wird erstellt

# 6. Anhängen
>> /write -a test.py

"
hello()
"

# Text wird angehängt
```

## Übung 5.2: Code Execution

```bash
# 1. Session starten
claude

# 2. Bash Befehl
>> /bash ls -la

# Zeigt Verzeichnis

# 3. Python ausführen
>> /python print("Hello from Claude")

# 4. npm Befehl (bei JavaScript Projekt)
>> /npm install express

# 5. Git Befehl
>> /git status

# Zeigt Git Status
```

## Übung 5.3: Git Workflow

```bash
# 1. Session starten
claude

# 2. Git Operationen
>> /git add .

>> /git status

# Sollte staged Dateien zeigen

>> /git commit "Add new features"

# Commit wird erstellt

# 3. Mit Claude
>> Schreib einen aussagekräftigen Commit Message und committe
```

---

# 6️⃣ KONFIGURATION

## Übung 6.1: Einstellungen ändern

```bash
# 1. Aktuelle Einstellungen anzeigen
claude config list

# Sollte alle Einstellungen zeigen

# 2. Spezifische Einstellung
claude config get model

# Zeigt aktuelles Modell (z.B. "claude-opus-4-1")

# 3. Einstellung ändern
claude config set max_tokens 8192

# 4. Verify
claude config get max_tokens

# Sollte 8192 anzeigen

# 5. Verschiedene Modelle testen
claude config set model claude-haiku

claude "Erkläre Recursion"  # Schneller/billiger

claude config set model claude-opus-4-1

claude "Analysiere komplexe Architektur"  # Besser für komplexe
```

## Übung 6.2: Output Styles

```bash
# 1. Session starten
claude

# 2. Verschiedene Styles probieren
>> /output-style explanatory

# Mit Erklärungen

>> Erkläre mir Python Decorators

# Detaillierte Erklärung

# 3. Learning Style
>> /output-style learning

# Mit Lernzielen

>> Erkläre mir Decorators wieder

# Für Lernende optimiert

# 4. Concise
>> /output-style concise

# Kurz und knapp
```

---

# 7️⃣ PRAKTISCHE ANWENDUNGEN

## Übung 7.1: Code Review durchführen

```bash
# 1. Ein fehlerhaftes Python Script erstellen
cat > bad_code.py << 'EOF'
import random

def get_user_data(users, id):
    for u in users:
        if u['id'] == id:
            return u
            
def calculate_price(items):
    total = 0
    for item in items:
        total = total + item['price'] * item['qty']
    tax = total * 0.2
    final = total + tax
    return final
    
def save_to_db(data):
    # SQL
    query = "INSERT INTO users VALUES ('" + str(data) + "')"
    # TODO: execute(query)
EOF

# 2. Claude starten
claude

# 3. Code Review
>> Führe einen Code Review durch für bad_code.py
>> Finde Fehler, Sicherheitsprobleme und Verbesserungen

# 4. Refactorierung
>> Refaktoriere den Code:
>> - Bessere Namen
>> - Error Handling
>> - Security fixes
>> - Type hints

# 5. Akzeptieren
# y für die Änderungen

# 6. Tests
>> Schreib Unit Tests für die refakturierten Funktionen
```

## Übung 7.2: Dokumentation generieren

```bash
# 1. Ein Projekt mit Code ohne Docs
mkdir my_lib
cd my_lib

cat > math_utils.py << 'EOF'
def fibonacci(n):
    if n <= 1:
        return n
    return fibonacci(n-1) + fibonacci(n-2)

def is_prime(num):
    if num < 2:
        return False
    for i in range(2, num):
        if num % i == 0:
            return False
    return True

def gcd(a, b):
    while b:
        a, b = b, a % b
    return a
EOF

# 2. Dokumentation generieren
claude

>> Schreib eine komplette README.md für dieses Projekt
>> - Beschreibung
>> - Installation
>> - Benutzungsbeispiele
>> - API Dokumentation

# 3. Inline Docs
>> Füge docstrings und Comments hinzu zu allen Funktionen

# 4. Exit
>> exit
```

## Übung 7.3: Tests schreiben

```bash
# 1. Datei mit Funktionen (keine Tests)
cat > functions.py << 'EOF'
def add(a, b):
    return a + b

def subtract(a, b):
    return a - b

def multiply(a, b):
    return a * b

def divide(a, b):
    if b == 0:
        raise ValueError("Cannot divide by zero")
    return a / b
EOF

# 2. Claude starten
claude

# 3. Tests generieren
>> Schreib pytest Tests für alle Funktionen in functions.py
>> - Happy path
>> - Edge cases
>> - Error cases
>> - Ziel: 100% Coverage

# 4. Akzeptieren und Tests ausführen
# y

>> /bash pytest -v

# Sollte grün sein

# 5. Weitere Tests?
>> Schreib noch Integrationstests
```

## Übung 7.4: Git Workflow Automatisierung

```bash
# 1. Feature Branch erstellen & entwickeln
mkdir feature_project
cd feature_project
git init
git config user.name "You"
git config user.email "you@example.com"

echo "# Feature Project" > README.md
git add README.md
git commit -m "Initial commit"

# 2. Neue Branch
git checkout -b feature/user-auth

# 3. Claude starten
claude

# 4. Komplette Feature entwickeln
>> Implementiere User Authentication
>> - Hashing für Passwörter (bcrypt)
>> - Login-Funktion
>> - JWT Tokens
>> - Middleware
>> - Tests

# 5. Claude macht das - mit Git commits
# y bei jedem Schritt

# 6. Nach Fertigstellung
>> exit

git log --oneline
# Sollte mehrere neue Commits zeigen

git diff main..feature/user-auth
# Zeigt die Änderungen
```

---

# 8️⃣ MCP INTEGRATION

## Übung 8.1: GitHub MCP

```bash
# 1. GitHub MCP hinzufügen
claude mcp add

# Wähle GitHub aus der Liste

# Folge den Schritten:
# - GitHub Account verbinden
# - Token generieren
# - Authentifizierung bestätigen

# 2. GitHub Integration testen
claude

>> Zeige mir die offenen Issues in meinem Repo

# Sollte echte Issues zeigen (aus GitHub)

>> Erstelle ein Issue für folgende TODO: [...]

# Issue wird wirklich auf GitHub erstellt!

>> Zeige die letzten 5 Commits

# Echte Commits aus dem Repo
```

## Übung 8.2: PostgreSQL MCP

```bash
# 1. PostgreSQL MCP hinzufügen
claude mcp add

# Wähle PostgreSQL

# Konfiguriere die Verbindung:
# postgresql://user:password@localhost:5432/database

# 2. Datenbank-Operationen
claude

>> Zeige mir das Schema der users Tabelle

# Echtes Schema von der DB

>> Schreib eine Migration um ein "bio" Feld hinzuzufügen

# Claude wird die Migration schreiben

>> Führe die Migration aus

# Führt sie tatsächlich aus (mit Bestätigung)

>> Wie viele User haben sich registriert?

# Echte Zahlen aus der DB
```

---

# 9️⃣ AUTOMATION

## Übung 9.1: Einfaches Hook Script

```bash
# 1. Hook Verzeichnis
mkdir -p .claude/hooks

# 2. Pre-commit Hook
cat > .claude/hooks/pre-commit.sh << 'EOF'
#!/bin/bash

echo "Running tests before commit..."
npm test

if [ $? -ne 0 ]; then
  echo "Tests failed! Commit aborted."
  exit 1
fi

echo "Running linter..."
npm lint

if [ $? -ne 0 ]; then
  echo "Linting failed! Commit aborted."
  exit 1
fi

echo "All checks passed!"
exit 0
EOF

# 3. Executable machen
chmod +x .claude/hooks/pre-commit.sh

# 4. Claude nutzt das automatisch:
claude

>> Committe diese Änderungen

# Hook wird vor Commit ausgeführt!
```

## Übung 9.2: Custom Kommandos

```bash
# 1. Custom Kommando-Datei
mkdir -p .claude/commands

cat > .claude/commands/audit.yaml << 'EOF'
description: Umfassender Security Audit
allowed-tools:
  - Read
  - Grep
  - Bash

model: claude-opus-4-1

body: |
  Führe ein Security Audit durch:
  
  1. Finde alle Authentifizierungs-Funktionen
  2. Prüfe auf:
     - SQL Injection vulnerabilities
     - XSS Risiken
     - CSRF Protection
     - Password Security
     - Session Management
  
  3. Generiere einen Report mit:
     - Gefundene Issues
     - Severity Level
     - Fixes
EOF

# 2. Nutzen
claude

>> /audit

# Wird Custom Kommando ausgeführt!
```

---

# 🔟 TROUBLESHOOTING ÜBUNGEN

## Übung 10.1: Connection Issues

```bash
# 1. Teste Basis-Konnektivität
ping api.anthropic.com

# 2. Verifiziere Auth
claude auth status

# 3. Wenn Fehler - Neu-Login
claude auth logout
claude auth login

# 4. Test mit einfacher Frage
claude "Test: Antworte mit deiner Modell-Version"
```

## Übung 10.2: Context Overflow Handling

```bash
# 1. Großes Projekt testen
cd ~/large_project

# 2. Versuche vollen Scan
claude "Analysiere diesen gesamten Projekt" 

# Könnte Context Fehler zeigen

# 3. Fix mit .claudeignore
echo "node_modules/" >> .claudeignore
echo "dist/" >> .claudeignore
echo "*.log" >> .claudeignore

# 4. Retry
claude "Analysiere diesen Projekt jetzt"

# Sollte schneller gehen!

# 5. Noch besser: Spezifische Analyse
claude -f src/main.py "Analysiere nur diese Datei"
```

---

# ✅ ABSCHLUSS-CHECKLISTE

Wenn du alle Übungen gemacht hast, kannst du:

- [ ] Claude Code installieren und authentifizieren
- [ ] Interactive Mode nutzen
- [ ] Single Command Mode nutzen
- [ ] Continue Mode nutzen
- [ ] .claudeignore und CLAUDE.md erstellen
- [ ] Slash-Kommandos nutzen (/read, /bash, /git)
- [ ] Konfiguration ändern
- [ ] Code Review durchführen
- [ ] Tests generieren
- [ ] Dokumentation schreiben
- [ ] Git Workflows automatisieren
- [ ] MCP Integrationen nutzen
- [ ] Hooks schreiben
- [ ] Custom Kommandos erstellen
- [ ] Troubleshooting-Probleme lösen

**Wenn alle ✅, bist du Claude Code Master!** 🚀

---

# 🎓 NÄCHSTE SCHRITTE

1. **Dein eigenes Projekt starten** - Nutze Claude Code täglich
2. **MCP für deine Stack nutzen** - GitHub, Datenbanken, APIs
3. **Automation bauen** - Hooks und Custom Commands
4. **Team Prozesse** - Claude Code in CI/CD
5. **Experimente** - Neue Modelle testen, Custom Workflows
6. **Dokumentation teilen** - CLAUDE.md perfektionieren

**Die beste Lernmethode: Learning by doing!** 💪
