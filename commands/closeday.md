Erstelle einen Tagesabschluss-Bericht.

Gehe dabei so vor:
1. Pruefe welche Dateien heute bearbeitet wurden (Timestamps)
2. Vergleiche mit dem Tagesplan falls vorhanden
3. Identifiziere was erledigt wurde und was offen blieb
4. Pruefe ob neue Achievements freigeschaltet wurden

Frage den User nach dem Abend-Energie-Check:
> "🔋 Energie jetzt (1-5)? 😤 Stress am Ende des Tages (1-5)? 🏃 Sport heute?"

Erstelle einen Bericht mit:
- **Energie-Check Abend**: 🔋 X/5 | 😤 X/5 | 🏃 ja/nein
- **Erledigt**: Was wurde heute geschafft
- **Neue Ideen**: Was kam heute auf, das festgehalten werden sollte
- **Offen geblieben**: Was muss morgen weitergehen
- **Gelernt**: Neue Erkenntnisse oder Entscheidungen
- **Morgen wichtig**: Top 3 fuer den naechsten Tag
- **Achievements**: Neue Meilensteine die heute erreicht wurden
- **Burnout-Check**: Kurze Einschaetzung (1 Satz) wie der Tag war

**Warnlogik:** Wenn 🔋 ≤ 2 oder 😤 ≥ 4: Aktiv darauf hinweisen und fragen ob morgen bewusst reduziert werden soll.

Nach der Bestaetigung durch den User:
1. Speichere den Bericht als Daily Note (YYYY-MM-DD.md im Vault-Root). Falls die Datei existiert, haenge den Bericht unten an (bestehenden Inhalt nicht ueberschreiben!)
2. Aktualisiere die Brain Dashboard Quest.md:
   - Neue Achievements unter "### Achievements" als `- [x] ⭐ **Name** – Beschreibung` einfuegen
   - Quest-Level in den Frontmatter-Feldern der betroffenen Quest-Dateien hochzaehlen wenn ein Level abgeschlossen wurde

## Task-Sync: Offene Punkte in Quest-Dateien uebertragen

Nach dem Speichern der Daily Note: Tasks aus der Daily Note mit den Quest-Dateien synchronisieren, damit offene Punkte nicht in alten Daily Notes verloren gehen.

### Prefix → Quest-Datei Mapping

**Lies die Datei `Projekte.md` im Vault-Root** – dort steht die aktuelle Mapping-Tabelle von Prefixes auf Quest-Dateien. Diese Datei ist die Single Source of Truth.

Wenn `Projekte.md` nicht existiert: Dem User mitteilen dass Task-Sync uebersprungen wird und vorschlagen die Datei anzulegen.

### Sync-Schritte

1. **Task-Extraktion:** Alle Checkboxen aus der heutigen Daily Note lesen (`- [ ]` und `- [x]`)
2. **Prefix-Erkennung:** Fuer jede Task den Prefix pruefen (`ProjektA:`, `ProjektB:`, etc.)
3. **Unklare Tasks sammeln:** Tasks ohne erkennbaren Prefix oder ohne Mapping → dem User zeigen und nachfragen
4. **Fuer jede erkannte Task:**
   - Quest-Datei oeffnen
   - Pruefen ob "# Offene Punkte" Sektion existiert (falls nicht: ueberspringen, kein Sync fuer level-basierte Quests!)
   - Pruefen ob "## Erledigt" Sektion existiert (falls nicht: anlegen am Ende der Datei)

5. **Erledigte Tasks `- [x]`:**
   - In "Offene Punkte" suchen (Text-Match, Fuzzy OK)
   - Falls gefunden: Aus "Offene Punkte" entfernen
   - In "## Erledigt" am Anfang einfuegen mit Format: `- [x] YYYY-MM-DD: <Task-Text>`

6. **Offene Tasks `- [ ]`:**
   - In "Offene Punkte" suchen
   - Falls bereits vorhanden: Nichts tun (Duplikat vermeiden)
   - Falls neu: Am Ende der passenden Kategorie oder Sektion einfuegen

### Dialog vor dem Schreiben

Zeige dem User eine Vorschau und warte auf Bestaetigung:

```
📋 Task-Sync Vorschau:

Projekt-A-Quest.md:
  ✅ Erledigt → Erledigt-Sektion:
     - Erste Teilaufgabe abgeschlossen
     - Review mit Stakeholder gemacht
  📝 Offene Punkte → neu hinzufuegen:
     - Naechsten Meilenstein vorbereiten

Projekt-B-Quest.md:
  📝 Offene Punkte → neu hinzufuegen:
     - Umsetzung starten

❓ Unklar (bitte zuordnen):
  - "Notebook aufraeumen" → welche Quest?

Synchronisieren? [ja/nein]
```

**WICHTIG:** Nur nach Bestaetigung schreiben. Nie ohne Rueckfrage Quest-Dateien modifizieren!

### Edge Cases

- **Quest-Datei existiert nicht:** Warnen, User fragen ob neue Datei erstellt werden soll oder Sync fuer diesen Prefix uebersprungen werden soll
- **Kein Prefix in Task:** Task wird nicht automatisch gesynct, bleibt nur in Daily Note
- **Brain Dashboard Quest.md:** Hat keine "Offene Punkte" Sektion, bleibt level-basiert – Task-Sync ueberspringen
- **Fuzzy-Match unsicher:** Bei unklarer Zuordnung nachfragen statt raten

## Zeiterfassung: Stoppzeit eintragen

1. Pruefe die aktuelle Uhrzeit (`date +%H:%M`)
2. Oeffne `Zeiterfassung.md`
3. Finde die heutige Zeile (heutiges Datum in der Tag-Spalte)
4. Fuege die Stoppzeit ein
5. Frage den User nach der Pausenzeit (Standard: 0:30)
6. Berechne die Dauer exakt im Dezimalformat: (Stop - Start - Pause) in Stunden mit Dezimalstellen
   Beispiele: 7h 45min = 7,75 | 8h 15min = 8,25 | 7h 30min = 7,5 | 8h = 8,0
   NICHT runden – exakte Dezimalzahl eintragen

Antworte auf Deutsch.
