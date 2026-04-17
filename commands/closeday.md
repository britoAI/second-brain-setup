Erstelle einen Tagesabschluss-Bericht.

Gehe dabei so vor:
1. Pruefe welche Dateien heute bearbeitet wurden (Timestamps)
2. Vergleiche mit dem Tagesplan falls vorhanden
3. Identifiziere was erledigt wurde und was offen blieb
4. **Quest-Level-Review (PFLICHT, bevor Bericht geschrieben wird)** – siehe Abschnitt unten
5. Pruefe ob neue Achievements freigeschaltet wurden

## Quest-Level-Review

Vor dem Bericht aktiv pruefen, ob User-Arbeit einen Level-Abschluss bedeutet. Nicht passiv warten – Timestamps allein reichen nicht, weil vieles ausserhalb des Vaults passiert (externe Dokumente, Termine vor Ort etc.).

**Schritte:**
1. Brain Dashboard Quest.md vollstaendig lesen
2. Aus `Projekte.md` die **Sub-Projekt-Aliase** lesen (Tabelle am Ende) – das sind Begriffe, die auf Parent-Quests triggern, auch wenn kein Prefix genutzt wird
3. Sammle alle aktiven Quests (`quest_status: aktiv`) mit aktuellem Level
4. Fuer JEDE aktive Quest: User-Args + Daily-Note-Inhalt gegen Level-Beschreibungen abgleichen. Sub-Projekt-Namen in Level-Texten sind starke Trigger (z.B. wenn ein Unterprojekt-Kuerzel im Level-Text steht und in User-Args vorkommt = Treffer)
5. Bei thematischem Treffer proaktiv vorschlagen – **inklusive aktuellem Quest-Stand**, damit User Drift zwischen Quest-Datei und Realitaet sofort sieht:

```
🎯 Quest-Level-Check: ProjektA – Teilgebiet

Aktueller Stand laut Brain Dashboard Quest.md (level: 2, level_max: 5):
  [x] Level 1: Grundstruktur fertig
  [x] Level 2: Erstes Derivat reviewt
  [ ] Level 3: Template verbessern
  [ ] Level 4: Zweites Derivat fertigstellen
  [ ] Level 5: Alle Derivate abgenommen

Heutige Arbeit: "Zweites Derivat auf V1.3 mit neuer Vorlage + Erfahrung aus Derivat 1"
→ Passt auf Level 4. Level 3 (Template) ggf. auch schon erledigt?

Aktueller Stand korrekt? Oder ist Quest-Datei nicht auf dem Laufenden?
Welcher Level ist heute erreicht? [z.B. 2→4 / nur 3 / nur 4 / keiner]
```

6. Auch Level-Spruenge ueber mehrere Stufen moeglich (z.B. 2 → 4). Der Quest-File-Stand kann veraltet sein – User darf den aktuellen Stand korrigieren, nicht nur den Tages-Fortschritt.
7. Bestaetigter Level-Abschluss = Achievement-Kandidat
8. Keine Quest-Datei ohne explizite User-Bestaetigung modifizieren

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
