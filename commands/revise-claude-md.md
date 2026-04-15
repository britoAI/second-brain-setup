---
description: CLAUDE.md mit Learnings aus dieser Session aktualisieren
allowed-tools: Read, Edit, Glob
---

Pruefe diese Session auf Erkenntnisse fuer die Arbeit mit Claude Code in diesem Vault. Aktualisiere CLAUDE.md mit Kontext der zukuenftigen Sessions helfen wuerde.

## Schritt 1: Reflektieren

Welcher Kontext hat gefehlt der Claude effektiver gemacht haette?
- Bash-Befehle die genutzt oder entdeckt wurden
- Code-Style-Muster die befolgt wurden
- Testansaetze die funktioniert haben
- Umgebungs-/Konfigurations-Besonderheiten
- Warnungen oder Stolperfallen

## Schritt 2: CLAUDE.md Dateien finden

```bash
find . -name "CLAUDE.md" -o -name ".claude.local.md" 2>/dev/null | head -20
```

Entscheide wo jede Ergaenzung hingehoert:
- `CLAUDE.md` – Im Team geteilt (in Git eingecheckt)
- `.claude.local.md` – Nur persoenlich/lokal (gitignored)

## Schritt 3: Ergaenzungen entwerfen

**Kurz halten** – eine Zeile pro Konzept. CLAUDE.md ist Teil des Prompts, Kuerze zaehlt.

Format: `<Befehl oder Muster>` – `<kurze Beschreibung>`

Vermeiden:
- Ausfuehrliche Erklaerungen
- Offensichtliche Informationen
- Einmalige Fixes die sich nicht wiederholen

## Schritt 4: Vorgeschlagene Aenderungen zeigen

Fuer jede Ergaenzung:

```
### Update: ./CLAUDE.md

**Warum:** [einzeilige Begruendung]

\`\`\`diff
+ [die Ergaenzung – kurz halten]
\`\`\`
```

## Schritt 5: Mit Zustimmung anwenden

Frage ob der User die Aenderungen uebernehmen moechte. Nur genehmigte Dateien bearbeiten.
