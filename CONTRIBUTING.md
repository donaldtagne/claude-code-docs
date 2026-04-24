# Beiträge zu Claude Code Dokumentation

Danke, dass du dieses Projekt unterstützen möchtest! 🙏

Dieser Guide hilft dir, effektiv zu diesem Repository beizutragen.

---

## 📋 Inhaltsverzeichnis

1. [Code of Conduct](#code-of-conduct)
2. [Bevor du anfängst](#bevor-du-anfängst)
3. [Wie man beiträgt](#wie-man-beiträgt)
4. [Style Guide](#style-guide)
5. [Commit Nachrichten](#commit-nachrichten)
6. [Pull Request Prozess](#pull-request-prozess)

---

## 📖 Code of Conduct

Dieses Projekt und alle Beteiligten unterliegen unserem [Code of Conduct](CODE_OF_CONDUCT.md).
Durch die Teilnahme erklärst du dich damit einverstanden, diesen Code zu befolgen.

---

## 🚀 Bevor du anfängst

### Was du beitragen kannst

- ✅ **Dokumentation** - Verbesserungen, Korrektionen, Erweiterungen
- ✅ **Code-Beispiele** - Neue praktische Beispiele und Rezepte
- ✅ **Übungen** - Neue Übungen für das Workbook
- ✅ **Fehler-Fixes** - Korrigiere falsche oder veraltete Infos
- ✅ **Übersetzungen** - Neue Sprachen oder Verbesserungen
- ✅ **Ressourcen** - Links zu hilfreichen Tutorials, Tools, Communities

### Was wir NICHT akzeptieren

- ❌ Werbung für externe Produkte/Services
- ❌ Plagiarismus oder copied content ohne Attribution
- ❌ Inhalte, die gegen Anthropic's Richtlinien verstoßen
- ❌ Beleidigung oder Diskriminierung

---

## 🔧 Wie man beiträgt

### 1. Fork das Repository

```bash
# Gehe zu https://github.com/[username]/claude-code-docs
# Klicke auf "Fork"
```

### 2. Clone deine Fork

```bash
git clone https://github.com/[dein-username]/claude-code-docs.git
cd claude-code-docs
git remote add upstream https://github.com/[original]/claude-code-docs.git
```

### 3. Erstelle einen Feature Branch

```bash
git checkout -b feature/beschreibung-der-änderung
# oder
git checkout -b fix/fehlerbeschreibung
```

### 4. Mache deine Änderungen

```bash
# Bearbeite Dateien
# Teste deine Änderungen
# Stelle sicher, dass alles funktioniert
```

### 5. Commit deine Änderungen

```bash
git add .
git commit -m "type: Beschreibung"
# z.B.: "docs: Fix typo in installation guide"
```

### 6. Push zu deiner Fork

```bash
git push origin feature/beschreibung-der-änderung
```

### 7. Öffne einen Pull Request

```
Title: "Short description of change"

Body:
- What: Was wurde geändert?
- Why: Warum wurde es geändert?
- How: Wie wurden die Änderungen implementiert?

Closes #[issue-number] (falls relevant)
```

---

## ✍️ Style Guide

### Markdown Formatting

```markdown
# Hauptüberschrift (H1)
## Unterüberschrift (H2)
### Subunterüberschrift (H3)

- Bullet points für Listen
- Immer mit Leerzeile davor

1. Nummerierte Listen
2. Auch mit Leerzeilen

**Fett** für Wichtiges
_Kursiv_ für Betonung
`Code` für Inline-Code
[Link Text](https://example.com) für Links
```

### Deutsch vs Englisch

- **Primär:** Deutsch (deutsche Namen, Erklärungen)
- **Code:** Englisch (Standard in Programmierung)
- **Kommentare:** Deutsch oder Englisch beide OK

```markdown
❌ False: Zeige code Beispiel
✅ True: Zeige das folgende Code-Beispiel

❌ False: "lorem ipsum dolor"
✅ True: Mit deutschen Erklärungen
```

### Code-Blöcke

```bash
# Immer Sprache angeben
# Gut dokumentiert
# Mit Kommentaren

# Bash Beispiel
mkdir projekt
cd projekt
claude auth login
```

### Struktur für Guides

```markdown
# Titel

## 📋 Inhaltsverzeichnis
- Link zu Abschnitten

## 🎯 Einführung
- Was wird gelernt?
- Warum ist das wichtig?

## 🔧 Schritt-für-Schritt
1. Schritt 1
2. Schritt 2

## 💡 Praktische Beispiele
- Echte, getestete Beispiele

## 🐛 Troubleshooting
- Häufige Fehler + Lösungen

## 📚 Weitere Ressourcen
- Links zur Vertiefung
```

---

## 📝 Commit Nachrichten

Verwende Conventional Commits Format:

```
type(scope): subject

body

footer
```

### Type
- `docs` - Dokumentation ändern
- `feat` - Neue Features/Inhalte
- `fix` - Fehler korrigieren
- `chore` - Sonstiges (Meta-Änderungen)
- `refactor` - Code/Struktur umorganisieren

### Scope
- `readme` - README.md Datei
- `guide` - Hauptguide
- `workbook` - Workbook/Übungen
- `reference` - Quick Reference
- `examples` - Code-Beispiele

### Subject
- Imperative form: "Add feature" nicht "Added feature"
- Keine Großbuchstaben am Anfang
- Kein Punkt am Ende
- Maximal 50 Zeichen

### Beispiele

```bash
git commit -m "docs(guide): Fix typo in installation section"
git commit -m "feat(workbook): Add new exercise for MCP integration"
git commit -m "fix(reference): Correct API key example"
git commit -m "docs(readme): Update resources section with new link"
```

---

## 🔄 Pull Request Prozess

### Vor dem PR

- [ ] Lokale Tests ausgeführt
- [ ] Dokumentation überprüft (Rechtschreibung, Formatierung)
- [ ] Code-Beispiele getestet
- [ ] Links überprüft (funktionieren alle?)
- [ ] Mit `git pull upstream main` aktualisiert

### PR Template

```markdown
## 📝 Beschreibung
Kurze Beschreibung der Änderungen.

## 🎯 Art der Änderung
- [ ] Dokumentation
- [ ] Code-Beispiele
- [ ] Fehlerfix
- [ ] Neue Übung
- [ ] Andere: _____

## 📋 Checkliste
- [ ] Meine Änderungen folgen dem Style Guide
- [ ] Ich habe die Dokumentation aktualisiert
- [ ] Ich habe Rechtschreibung/Grammatik überprüft
- [ ] Neue Inhalte sind getestet/verifiziert
- [ ] Keine Fehler in Links oder Code-Beispielen

## 🔗 Verwandte Issues
Closes #[issue-number]

## 📸 Screenshots (falls relevant)
Füge Screenshots für visuelle Änderungen hinzu.
```

### Review-Prozess

1. **Automatische Checks** - GitHub Actions prüfen Formatierung
2. **Maintainer Review** - Inhaltliche Überprüfung
3. **Community Feedback** - Andere können Comments hinzufügen
4. **Approval** - Mindestens 1 Approval erforderlich
5. **Merge** - PR wird gemerged

### Feedback Adressieren

```bash
# Feedback erhalten, Änderungen machen
git add .
git commit -m "fix(pr): Address reviewer feedback"
git push origin feature/branch-name

# Keine neuen PR erforderlich - wird automatisch aktualisiert!
```

---

## 🧪 Testen

### Dokumentation testen

```bash
# Prüfe Markdown-Syntax
# - Verwende einen Markdown Linter (z.B. markdownlint)

# Prüfe Links
# - Stelle sicher, dass alle Links funktionieren

# Prüfe Code-Beispiele
# - Führe alle Bash/Code-Blöcke lokal aus
# - Stelle sicher, dass Outputs stimmen
```

### Code-Beispiele testen

```bash
# Für jeden Code Block:
1. Kopiere den Code
2. Führe ihn aus
3. Prüfe, dass er funktioniert
4. Dokumentiere den erwarteten Output
```

---

## 🎓 Entwicklungs-Setup

### Tools die du brauchst

```bash
# Git
git --version

# Ein Markdown Editor (VS Code, Sublime, etc.)
code README.md

# (Optional) Markdown Linter
npm install -g markdownlint-cli
markdownlint CLAUDE_CODE_CLI_KOMPLETT.md

# (Optional) Link Checker
npm install -g broken-link-checker
blc https://github.com/[username]/repo
```

### Lokales Testen

```bash
# Repository lokalisiert ansehen
# VS Code
code .

# Öffne Markdown-Preview (Ctrl+Shift+V)
# Prüfe Formatierung und Links
```

---

## 🤝 Community Support

### Fragen stellen

- 💬 Öffne eine GitHub Discussion
- 📝 Stelle eine GitHub Issue für Fehler
- 💭 Nutze GitHub Discussions für Fragen

### Feedback geben

- ⭐ Gib dem Repo einen Star!
- 💬 Comments auf PRs/Issues
- 📢 Teile das Repo mit anderen

---

## 🎁 Rewards für Beiträge

Regelmäßige Beitragsgeber werden:
- ✨ Gelistet im CONTRIBUTORS.md
- 🏆 Erwähnt in der README
- 🎖️ Erhalten einen "Contributor" Badge (auf GitHub)

```markdown
### Contributors

<!-- If you contributed, add yourself here -->
- [Your Name](https://github.com/username) - Contribution description
```

---

## 📞 Hilfe & Support

### Du brauchst Hilfe?

1. **Lese die Docs** - [CLAUDE_CODE_CLI_KOMPLETT.md](CLAUDE_CODE_CLI_KOMPLETT.md)
2. **Schaue existierende PRs/Issues** - Wurde das schon gemacht?
3. **Öffne eine Discussion** - Stelle eine Frage
4. **Kontaktiere einen Maintainer** - DM auf GitHub/Discord

### Probleme bei der Einrichtung?

```bash
# Du kannst auch ohne lokale Einrichtung beitragen:
# 1. Öffne einen Issue mit deinem Vorschlag
# 2. Ein Maintainer kann es implementieren
# 3. Du kannst immer noch Feedback geben!
```

---

## 📜 Lizenz

Durch die Teilnahme an diesem Projekt erklärst du dich damit einverstanden, dass
deine Beiträge unter der MIT License lizenziert werden.

---

## 🙏 Danke!

Danke für deinen Beitrag zur Claude Code Community! 🌟

Deine Beiträge helfen tausenden von Entwicklern, Claude Code besser zu verstehen
und zu nutzen.

**Happy Contributing!** 🚀

---

<div align="center">

**[Code of Conduct](CODE_OF_CONDUCT.md) • [Lizenz](LICENSE) • [Issues](../../issues)**

</div>
