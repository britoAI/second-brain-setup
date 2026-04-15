---
typ: anleitung
tags: [vault, workflow, obsidian, anleitung]
---
# Vault-Anleitung

## Grundprinzip

Dieser Vault ist dein Second Brain. Alles was du denkst, planst, lernst oder erlebst kann hier landen. Aber: **Erfassen heisst nicht sofort umsetzen.** Der Vault ist dein Parkplatz, nicht deine Startrampe.

---

## Ordnerstruktur

```
Dein Brain/
├── Arbeit/           Alles berufliche
├── Haus/             Alles rund ums Haus
├── Familie/          Schule, Kinder, Verwandte
├── Technik/          IT, Software, Hardware
├── Hobby/            Freizeit und Interessen
├── Finanzen/         Geld, Versicherungen, Rente
├── Gesundheit/       Ernaehrung, Sport, Arzt
├── _Archiv/          Abgeschlossenes / Veraltetes
└── _Import/          Roh-Importe (noch nicht einsortiert)
```

**Regel:** Neue Notizen gehoeren in den passenden Ordner. Im Zweifel: Root-Ebene, spaeter einsortieren.

---

## Links setzen

Obsidian-Links (`[[Dateiname]]`) sind das Herzstuck des Vaults. Sie verbinden Wissen ueber Ordnergrenzen hinweg.

### Wann verlinken?
- **Immer** wenn eine Notiz eine andere referenziert
- **Besonders wertvoll:** Links zwischen verschiedenen Ordnern
- **Weniger wertvoll:** Links innerhalb desselben Ordners

### Wie verlinken?
- `[[Dateiname]]` – einfacher Link
- `[[Dateiname|Anzeigetext]]` – Link mit anderem Anzeigetext
- `[[Dateiname#Ueberschrift]]` – Link zu einer bestimmten Ueberschrift

---

## Taeglicher Workflow

### Morgens (5 Min)
1. Oeffne Claude Code im Vault-Verzeichnis
2. Fuehre `/today` aus → bekommst priorisierten Tagesplan
3. Entscheide: Was ist heute dein **eine Sache**?

### Waehrend der Arbeit
- Neue Idee? → Schnell als Notiz erfassen, **nicht** sofort umsetzen
- Etwas gelernt? → In passenden Ordner ablegen
- Link-Gelegenheit? → `[[Verlinken]]`

### Abends (5 Min)
1. Fuehre `/closeday` aus → Tagesabschluss-Bericht
2. Wird automatisch als `YYYY-MM-DD.md` gespeichert
3. Schau dir deine Achievements an → Was hast du heute geschafft?

### Woechentlich (15 Min)
- `/weekplan` → Wochenplan basierend auf Prioritaeten
- `/drift` → Welche Themen tauchen immer wieder auf?
- `/emerge` → Werden aus kleinen Ideen groessere Projekte?

---

## Slash-Commands (Claude Code)

Starte Claude Code im Vault-Verzeichnis und nutze diese Commands:

| Command | Wann nutzen | Was es tut |
| --- | --- | --- |
| `/vault-context` | Einstieg / Ueberblick | Liest den gesamten Vault und fasst den Kontext zusammen |
| `/today` | Jeden Morgen | Priorisierter Tagesplan aus Todos und Projekten |
| `/closeday` | Jeden Abend | Tagesabschluss mit Zusammenfassung und Achievements |
| `/weekplan` | Wochenanfang | Wochenplan basierend auf Prioritaeten |
| `/ideas` | Kreativitaet | Scannt den Vault und generiert Ideen-Report |
| `/connect` | Verknuepfungen | Findet Verbindungen zwischen zwei Themen |
| `/drift` | Reflexion | Findet wiederkehrende Muster die dir nicht bewusst sind |
| `/emerge` | Strategie | Findet Ideen-Cluster die zu Projekten werden koennten |
| `/trace` | Deep Dive | Verfolgt die Entwicklung eines Themas durch den Vault |
| `/ghost` | Perspektive | Beantwortet Fragen so wie du es wuerdest |
| `/graduate` | Aufraumen | Findet halbfertige Gedanken die eine eigene Notiz verdienen |
| `/challenge` | Selbstkritik | Hinterfragt dein Denken kritisch |
| `/revise-claude-md` | Session-Ende | Aktualisiert CLAUDE.md mit Learnings aus der Session |

---

## Session-Management

Das Setup ist **file-basiert by design**: Slash-Commands schreiben in Dateien, nicht in den Session-Speicher. Das erlaubt effiziente, kleine Sessions und verlaesslichen Uebergang zwischen ihnen.

### Grundregel

> **Neue Session pro Kontext-Wechsel – nicht pro Tag.**

Eine typische Session bleibt klein und fokussiert auf ein Thema. Mehrere Sessions pro Tag sind normal (typisch 4-5).

### Wann neue Session starten?

| Situation | Neue Session? |
|---|---|
| Morgens `/today` | ✅ Ja – sauberer Start |
| Abends `/closeday` | ✅ Ja – unabhaengig von morgens |
| Thema wechseln (Arbeit → privat) | ✅ Ja |
| Anderes Projekt (Projekt A → Projekt B) | ✅ Ja |
| Neue Idee / Recherche ohne Bezug | ✅ Ja |
| Am gleichen Thema weiterarbeiten | ❌ Nein – weiterschreiben |
| Kleiner Fix oder Rueckfrage | ❌ Nein – mittendrin reinwerfen |

**Daumenregel:** *"Hat das noch mit dem zu tun was wir vor 10 Nachrichten gemacht haben?"* – Nein → `/clear` oder neuer Chat.

### Warum das so funktioniert

`/today` schreibt den Tagesplan in die `YYYY-MM-DD.md`. `/closeday` liest diese Datei wieder ein, prueft File-Timestamps fuer Aenderungen und synct Tasks in Quest-Dateien. **Nichts davon braucht die Morgen-Session im Gedaechtnis** – alle relevanten Daten liegen auf Platte.

Dasselbe gilt fuer Arbeit an Quest-Dateien: Erledigte Punkte landen direkt in der Quest-Datei, nicht nur im Chat. Dadurch bleibt jede Session klein und `/closeday` sieht am Abend alles was wichtig war.

### Was du dafuer tun musst

**Waehrend der Arbeit in einer Session:**
- Wichtige Entscheidungen **in die passende Quest-Datei schreiben**, nicht nur diskutieren
- Neue Ideen in `Ideen.md` oder als eigene Notiz ablegen
- Tasks mit Prefix (z.B. `ProjektA:`, `ProjektB:`) markieren damit Task-Sync sie beim `/closeday` findet

Wenn ein Thema nicht in einer Datei landet, ist es beim `/closeday` verloren – auch wenn die Morning-Session noch offen ist.

### Bei Fehlern von Claude

Wenn Claude eine deutlich falsche Antwort gibt: **Session abbrechen und neu starten**. Nicht korrigieren. Der Fehler + deine Korrektur + die neue Antwort bleiben sonst fuer immer im Context und kosten bei jeder folgenden Nachricht Token.

---

## Wie Claude Code mit dem Vault arbeitet

### Komponenten
- **CLAUDE.md** – Vault-spezifische Anweisungen (Struktur, Konventionen)
- **Memory** (`~/.claude/projects/.../memory/`) – Dein Profil, Workflow-Regeln, Feedback
- **Commands** (`~/.claude/commands/`) – Die Slash-Commands
- **Plan Mode** – Fuer groessere Aenderungen: Erst planen, dann umsetzen

### Wichtige Regeln
- Claude liest den Vault, aendert aber nur nach Absprache
- Max 2 aktive Quests gleichzeitig (Claude erinnert dich!)
- Bei 3+ Themen in einer Session: Claude sagt Bescheid
- Neue Ideen → erfassen, nicht sofort umsetzen

---

## Quellen-Import

| Quelle | Methode |
|---|---|
| Google Keep | Obsidian Importer Plugin |
| OneNote | Claude Code Session starten → Automation |
| Claude.ai Chats | claude.ai → Settings → Export Data → ZIP an Claude geben |
| Freier Text | Einfach als .md in den Vault legen |

---

## Gamification: Brain Dashboard Quest

Dein Fortschritt wird als Spiel dargestellt. Siehe [[Brain Dashboard Quest]] fuer:
- Aktive Quests und Level-Fortschritt
- Achievements (gesammelte Meilensteine)
- Arbeitsprinzipien (Burnout-Bremse)

**Voraussetzung:** Dataview-Plugin in Obsidian (wird mit diesem Setup mitgeliefert).
