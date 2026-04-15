# CLAUDE.md – Second Brain Vault

## Arbeitsverzeichnis
Claude Code laeuft aus `<dein-vault-pfad>`. Der Obsidian Vault liegt im selben Verzeichnis.
Alle Vault-Pfade sind relativ zum Vault-Root.

## Zeitzone
<deine-zeitzone> (z.B. Europe/Berlin)

**WICHTIG:** Vor jeder Tagesplan-Erstellung oder Datumsannahme das aktuelle Datum pruefen! Nie annehmen welcher Tag ist – immer verifizieren.

## Vault-Struktur
```
Dein Brain/
├── Arbeit/           Berufliches (Projekte, Meetings, Technik)
├── Haus/             Haus & Garten
├── Familie/          Schule, Kinder, Verwandte
├── Technik/          IT, Software, Hardware
├── Hobby/            Freizeit und Interessen
├── Finanzen/         Geld, Versicherungen, Rente
├── Gesundheit/       Ernaehrung, Sport, Arzt
├── _Archiv/          Abgeschlossenes
└── _Import/          Noch nicht einsortierte Notizen
```

## Konventionen

### Frontmatter
Jede Notiz soll mindestens haben:
```yaml
---
typ: [daily | projekt | recherche | uebersicht | konzept | anleitung | index]
tags: [relevante, tags]
---
```

### Quest-Frontmatter (fuer Projekte im Dashboard)
```yaml
quest_typ: hauptquest | nebenquest
quest_status: aktiv | locked | abgeschlossen
level: 0
level_max: 5
bereich: arbeit | haus | technik | familie | persoenlich
```

### Links
- `[[Dateiname]]` fuer Verlinkung (Obsidian Wikilinks)
- Cross-Folder-Links sind besonders wertvoll
- Links innerhalb desselben Ordners nur wenn inhaltlich noetig

### Sprache & Stil
- Deutsch (locker, direkt, "Moin")
- Emojis aktiv nutzen fuer Uebersichtlichkeit (✅ erledigt, ⚠️ Warnung, 🔒 locked, ⚡ aktiv, 🏆 Achievement, 💡 Idee, 🔥 dringend, 🎯 Fokus)
- Tagesberichte und Plaene mit Emojis strukturieren
- Frontmatter-Keys konsistent (typ, tags, datum, quest_typ)

### Daily Notes
- Format: `YYYY-MM-DD.md` im Vault-Root
- Frontmatter: `typ: daily, datum: YYYY-MM-DD, tags: [daily]`
- Werden durch `/today` (morgens) und `/closeday` (abends) erstellt/ergaenzt

## Quest-System (Gamification)

### 2-Slot-Modell (Arbeit + Persoenlich)
Taeglich werden zwei Quest-Slots gewaehlt:
- **Arbeit-Slot:** 1 aktives Arbeitsprojekt. Fremdbestimmt, hat immer Vorrang. Kann taeglich wechseln.
- **Persoenlich-Slot:** 1 aktiver persoenlicher Quest. Selbstbestimmt, bleibt stabil bis Level fertig. Nur in Freizeit/Restzeit.
- `/today` waehlt morgens beide Slots aus und fragt den User nach Bestaetigung.

### Regeln
1. **Max 2 aktive Dinge pro Tag** (1 Arbeit + 1 Persoenlich) – Rest ist Locked
2. **Level-Ende = Stopp-Punkt** – Speichern, Feierabend anbieten
3. **Ideen erfassen ≠ umsetzen** – Vault ist Parkplatz, nicht Startrampe
4. **Eine Sache pro Session** – nicht drei
5. **Review vor naechstem Schritt** – verstehen was da ist

### Achievement-Pflege
- Achievements werden NUR in `Brain Dashboard Quest.md` unter "### Achievements" gepflegt
- Format: `- [x] Name – Beschreibung` (erledigt) oder `- [ ] Name` (offen)
- Dashboard.md zeigt sie per Dataview TASK Query automatisch an
- Keine Duplikate! Achievements nur an einer Stelle.

### Quest-Frontmatter (PFLICHT)
Jeder Quest MUSS eine eigene .md Datei mit dem Quest-Frontmatter haben (siehe oben).
Ohne dieses Frontmatter erscheint der Quest NICHT im Dashboard!
**Regel:** Wenn du einen neuen Quest anlegst, SOFORT Frontmatter in die Datei einfuegen.

### Level-Up
- Ein Level gilt als abgeschlossen wenn der User es in /closeday bestaetigt
- Dann: Checkbox in Quest-Datei auf [x], Frontmatter `level` hochzaehlen

## Live-Tracking (nach jeder Interaktion pruefen)

**WICHTIG: Diese Pruefung ist PFLICHT nach jeder abgeschlossenen Aufgabe.**

Nach jeder abgeschlossenen Aufgabe oder Statusaenderung:
1. **Quest betroffen?** → Pruefen ob ein Level abgeschlossen wurde. Wenn ja: Checkbox abhaken + Frontmatter `level` hochzaehlen.
2. **Achievement verdient?** → Wenn ein Meilenstein erreicht wurde, in Brain Dashboard Quest.md unter Achievements einfuegen.
3. **Neue Idee?** → In Ideen.md oder als eigene Notiz erfassen.
4. **Tagesnotiz aktuell?** → Wenn relevante Arbeit erledigt wurde, in der heutigen YYYY-MM-DD.md vermerken.

Diese Pruefung soll **proaktiv** passieren. Claude fragt aktiv: "Soll ich das als erledigt markieren?"

## Burnout-Praevention
- Bei >2 aktiven Hauptquests: **Warnung ausgeben**
- Bei 3+ Themen in einer Session: **Aktiv erinnern**
- Bei langen Sessions: **Stopp-Punkt vorschlagen**

## Schluessel-Dateien
- `Brain Dashboard.md` – Hauptdashboard (Dataview-gesteuert)
- `Brain Dashboard Quest.md` – Quest-Definitionen, Level, Achievements
- `Ideen.md` – Verlinkte Ideen-Uebersicht
- `Vault-Anleitung.md` – Bedienungsanleitung
