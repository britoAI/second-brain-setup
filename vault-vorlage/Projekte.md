---
typ: index
tags: [projekte, uebersicht, quest-mapping]
---
# Projekte & Quest-Prefixes

Diese Datei ist die zentrale Referenz fuer alle aktiven Quests/Projekte und ihre Kurz-Prefixes.
Sie wird von `/closeday` gelesen um Tasks aus Daily Notes den richtigen Quest-Dateien zuzuordnen.

## Konvention

In Daily Notes werden Tasks mit Projekt-Prefix geschrieben:
```
- [ ] MeinProjekt: Eine offene Aufgabe
- [x] Haus: Eine erledigte Aufgabe
```

`/closeday` nutzt die Tabelle unten um das Prefix auf die Quest-Datei zu mappen.

## Quest-Prefix-Mapping

| Prefix | Quest-Datei | Bereich |
|---|---|---|
| `Brain` | [[Brain Dashboard Quest]] | Persoenlich (level-basiert, kein Task-Sync) |
| *(hier deine Projekte eintragen)* | | |

## Regeln

- **Neue Projekte immer hier eintragen** wenn sie als Quest angelegt werden
- **Prefix kurz und eindeutig** (2-4 Zeichen bevorzugt)
- **Level-basierte Quests** (ohne "Offene Punkte" Sektion) mit Hinweis markieren
- **Abgeschlossene Projekte** koennen stehen bleiben mit `(abgeschlossen)` Markierung

## Wie Task-Sync funktioniert

Im Daily:
```markdown
- [x] MeinProjekt: Aufgabe erledigt
- [ ] MeinProjekt: Offene Aufgabe
```

Beim `/closeday`:
1. Claude erkennt den `MeinProjekt:` Prefix
2. Liest dieses Mapping und findet die Quest-Datei
3. Verschiebt `[x]` Tasks in die `## Erledigt` Sektion der Quest-Datei
4. Traegt `[ ]` Tasks unter `# Offene Punkte` ein (keine Duplikate)
5. Zeigt dir Vorschau und fragt vor dem Schreiben nach Bestaetigung

Wenn eine Quest-Datei keine `# Offene Punkte` Sektion hat (z.B. Brain Dashboard Quest), wird sie nicht veraendert – level-basierte Quests werden ueber das Frontmatter getrackt.
