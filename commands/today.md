Erstelle einen priorisierten Tagesplan basierend auf meinem Vault.

Gehe dabei so vor:
1. Pruefe das aktuelle Datum
2. Lies meine Todo-Listen und offene Aufgaben
3. Pruefe die Projektprioritaeten und was dringend ist
4. Beruecksichtige das 2-Slot-Modell aus CLAUDE.md: 1 Arbeit-Slot + 1 Persoenlich-Slot
5. Beruecksichtige saisonale/zeitliche Faktoren

Frage den User am Anfang nach dem Energie-Check:
> "🔋 Energie heute (1-5)? 😤 Stress aktuell (1-5)? 🏃 Sport gestern/heute?"

Erstelle einen Plan mit:
- **2-Slot-Auswahl**: Vorschlag fuer Arbeit-Slot und Persoenlich-Slot, frage den User nach Bestaetigung
- **Top 3 Prioritaeten** fuer heute
- **Weitere Aufgaben** die erledigt werden koennten
- **Blockers**: Was braucht Zuarbeit oder Wartezeiten
- **Quick Wins**: Kleine Sachen die schnell gehen
- **Burnout-Check**: Kurze Einschaetzung der heutigen Last (1 Satz)

Formatiere als uebersichtliche Liste. Antworte auf Deutsch.

## Nach Bestaetigung durch den User: Automatisch speichern

1. Erstelle oder oeffne die Daily Note `YYYY-MM-DD.md` (heutiges Datum)
2. Falls die Datei noch nicht existiert, erstelle sie mit Frontmatter:
   ```yaml
   ---
   typ: daily
   datum: YYYY-MM-DD
   tags: [daily]
   ---
   ```
3. Fuege den Tagesplan am Anfang der Datei ein (nach dem Frontmatter)
4. Falls die Datei schon existiert, fuege den Plan oben ein ohne bestehenden Inhalt zu ueberschreiben
5. Speichere den Energie-Check direkt nach dem Frontmatter als eigenen Abschnitt:
   ```
   ## 🔋 Energie-Check
   🔋 Energie: X/5 | 😤 Stress: X/5 | 🏃 Sport: ja/nein
   ```

## Zeiterfassung: Startzeit eintragen

1. Pruefe die aktuelle Uhrzeit (`date +%H:%M`)
2. Oeffne `Zeiterfassung.md`
3. Fuege eine neue Zeile in die Tabelle ein mit: `| DD.MM.YYYY | HH:MM | | | |`
   (Tag + Startzeit, Stop/Pause/Dauer bleiben leer – werden von /closeday ausgefuellt)
