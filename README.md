# Second Brain Setup – Obsidian + Claude Code

Ein komplettes Setup fuer ein persoenliches "Second Brain" mit Obsidian und Claude Code als KI-Assistent.

## Was ist das?

Dieses Setup verwandelt Obsidian in ein KI-gestuetztes Wissenssystem:
- **Obsidian** = Dein Gedaechtnis (Notizen, Ideen, Projekte als .md Dateien)
- **Claude Code** = Dein Assistent (liest den Vault, plant, erinnert, verknuepft)
- **Gamification** = Brain Dashboard mit Quests, Leveln und Achievements (gegen Burnout)

---

## Voraussetzungen

1. **Obsidian** – https://obsidian.md (kostenlos)
2. **Claude Code** – Claude Pro/Max Abo

---

## Installation

### Schritt 1: Vault anlegen

Kopiere den Inhalt von `vault-vorlage/` in einen neuen Ordner (z.B. `Mein Brain/`).

Passe die Ordnerstruktur an dein Leben an. Die Standardstruktur:

```
Dein Brain/
├── Arbeit/
├── Haus/
├── Familie/
├── Technik/
├── Hobby/
├── Finanzen/
├── Gesundheit/
├── _Archiv/
└── _Import/
```

### Schritt 2: Obsidian oeffnen

1. Obsidian starten → "Ordner als Vault oeffnen" → deinen Vault-Ordner waehlen
2. Settings → Community Plugins → **Restricted Mode ausschalten**
3. Dataview ist bereits vorinstalliert und aktiviert

> **Wichtig:** DataviewJS muss aktiviert sein (Settings → Dataview → Enable JavaScript Queries). Das ist in diesem Setup bereits vorkonfiguriert.

### Schritt 3: Claude Code einrichten

```bash
# Commands (Slash-Befehle) kopieren
cp -r commands/ ~/.claude/commands/

# CLAUDE.md anpassen
# Oeffne vault-vorlage/CLAUDE.md und passe an:
# - <dein-vault-pfad> → dein tatsaechlicher Pfad
# - <deine-zeitzone> → z.B. Europe/Berlin
# - Ordnerstruktur an dein Setup anpassen
```

### Schritt 4: Memory anlegen (optional)

Erstelle unter `~/.claude/projects/<dein-vault-pfad>/memory/` eine Datei:

**user_role.md:** Beschreibe dich selbst (Beruf, Interessen, Staerken, Schwaechen). Claude nutzt das um Antworten auf dich zuzuschneiden.

### Schritt 5: Plugins installieren (optional)

```bash
# Superpowers – Brainstorming, Code Review, parallele Agenten
claude plugin install superpowers@claude-plugins-official
```

---

## Slash-Commands (13 Befehle)

### Taeglicher Workflow

| Command | Wann | Was es tut |
|---|---|---|
| `/today` | Jeden Morgen | Priorisierter Tagesplan aus dem Vault |
| `/closeday` | Jeden Abend | Tagesabschluss + Dashboard-Update |
| `/weekplan` | Wochenanfang | Wochenplan erstellen |
| `/vault-context` | Einstieg | Gesamtueberblick ueber den Vault |

### Analyse & Kreativitaet

| Command | Was es tut |
|---|---|
| `/ideas` | Ideen-Report aus Vault-Mustern (wird automatisch gespeichert) |
| `/connect` | Verbindungen zwischen zwei Themen finden |
| `/drift` | Wiederkehrende unbewusste Muster entdecken |
| `/emerge` | Ideen-Cluster finden die groesser werden |
| `/trace` | Entwicklung eines Themas verfolgen |

### Reflexion & Meta

| Command | Was es tut |
|---|---|
| `/ghost` | Fragen beantworten wie du es wuerdest |
| `/graduate` | Halbfertige Gedanken finden |
| `/challenge` | Eigenes Denken kritisch hinterfragen |
| `/revise-claude-md` | CLAUDE.md mit Session-Learnings aktualisieren |

---

## Gamification: Brain Dashboard

Das System nutzt Quests, Level und Achievements um Fortschritt sichtbar zu machen und Burnout zu verhindern.

### Quest-Frontmatter fuer Projekte:
```yaml
---
quest_typ: hauptquest | nebenquest
quest_status: aktiv | locked | abgeschlossen
level: 0
level_max: 5
bereich: arbeit | haus | technik | familie | persoenlich
---
```

### Regeln:
1. **Max 2 aktive Hauptquests gleichzeitig** (1 Arbeit + 1 Persoenlich)
2. **Level-Ende = natuerlicher Stopp-Punkt**
3. **Ideen erfassen ≠ sofort umsetzen** (Vault ist Parkplatz)
4. **Claude erinnert aktiv** wenn zu viele Themen laufen

### Dashboard

`Brain Dashboard.md` zeigt automatisch per Dataview:
- Aktive Quests mit Fortschrittsbalken
- Locked Quests
- Gesammelte Achievements
- Letzte Aktivitaet

---

## Taeglicher Workflow

**Morgens (5 Min):** `/today` → Tagesplan mit 2-Slot-Modell (1x Arbeit, 1x Persoenlich)
**Abends (5 Min):** `/closeday` → Bericht + Achievements
**Woechentlich:** `/weekplan` → Wochenplan, `/drift` → Muster erkennen

---

## Anpassen

- **Ordner:** Passe die Struktur in `CLAUDE.md` an dein Leben an
- **Quests:** Lege eigene Quests an mit dem Quest-Frontmatter
- **Commands:** Erstelle eigene Commands unter `~/.claude/commands/`

---

## Tipps

- Starte klein – nicht alles auf einmal importieren
- Erst Struktur aufbauen, dann fuellen
- Cross-Folder-Links sind wertvoller als Links im gleichen Ordner
- Jede Idee sofort erfassen, aber nicht sofort umsetzen
- `/vault-context` scannt deinen Vault. Nicht verwechseln mit dem eingebauten Claude Code Befehl `/context` (zeigt Token-Usage)

---

## Credits

Aufgebaut mit Claude Code.
Inspiriert von: Daniel Miessler (PAI), NetworkChuck.

**Hinweis:** Das mitgelieferte Dataview-Plugin kann veraltet sein. Nach dem Setup in Obsidian unter Settings → Community Plugins → Dataview → "Check for updates" aktualisieren.

## Lizenz

MIT – siehe [LICENSE](LICENSE).
