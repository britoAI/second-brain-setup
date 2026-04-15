---
typ: dashboard
tags: [dashboard, gamification, uebersicht]
cssclass: dashboard
---
# Brain Dashboard

> *"Man kann nur perfekt gut werden, nicht endlos schnell."*

---

## ⚡ Aktive Quests

```dataview
TABLE WITHOUT ID
  "**" + file.link + "**" AS Quest,
  bereich AS Bereich,
  level + " / " + level_max AS Level,
  "<progress value='" + level + "' max='" + level_max + "'></progress>" AS Fortschritt
FROM ""
WHERE quest_status = "aktiv"
SORT quest_typ ASC
```

---

## 🔒 Locked Quests

```dataview
TABLE WITHOUT ID
  file.link AS Quest,
  bereich AS Bereich,
  quest_typ AS Typ,
  level_max + " Level" AS Umfang
FROM ""
WHERE quest_status = "locked"
SORT bereich ASC
```

---

## 🏆 Achievements

> Quelle: [[Brain Dashboard Quest#Achievements 🏆]] – dort pflegen, hier automatisch angezeigt

```dataviewjs
try {
  const file = dv.page("Brain Dashboard Quest");
  if (!file) { dv.paragraph("Brain Dashboard Quest nicht gefunden"); return; }
  const content = await dv.io.load(file.file.path);
  const lines = content.split('\n');
  let inAchievements = false;
  let achievements = [];
  for (const line of lines) {
    if (line.includes('### Achievements')) { inAchievements = true; continue; }
    if (inAchievements && line.startsWith('#')) break;
    if (inAchievements && line.startsWith('---')) break;
    if (inAchievements && line.match(/^- \[[xX ]\]/)) {
      const done = line.includes('[x]') || line.includes('[X]');
      const text = line.replace(/^- \[[xX ]\] /, '');
      achievements.push({done, text});
    }
  }
  if (achievements.length === 0) { dv.paragraph("Keine Achievements gefunden"); return; }
  const doneList = achievements.filter(a => a.done).map(a => `✅ ${a.text}`).join('\n');
  const todoList = achievements.filter(a => !a.done).map(a => `⬜ ${a.text}`).join('\n');
  const count = achievements.filter(a => a.done).length;
  dv.paragraph(`**${count} / ${achievements.length} Achievements**\n\n${doneList}\n\n${todoList}`);
} catch(e) { dv.paragraph("Fehler: " + e.message); }
```

---

## 📊 Letzte Aktivitaet

```dataview
TABLE WITHOUT ID
  file.link AS Datei,
  file.folder AS Ordner,
  dateformat(file.mtime, "dd.MM.yyyy HH:mm") AS Geaendert
FROM ""
WHERE file.name != "Brain Dashboard"
SORT file.mtime DESC
LIMIT 10
```

---

## 🛑 Workflow-Regeln

> **Max 2 aktive Hauptquests!** Alles andere ist 🔒 Locked.

```dataview
LIST WITHOUT ID "⚡ " + file.link
FROM ""
WHERE quest_status = "aktiv" AND quest_typ = "hauptquest"
```

| Regel | |
|---|---|
| Eine Sache pro Session | Nicht drei |
| Review vor naechstem Schritt | Verstehen was da ist |
| Level-Ende = Stopp-Option | Speichern, Feierabend |
| Ideen erfassen ≠ umsetzen | Vault ist Parkplatz |

---

## 🔗 Quick Links

- [[Brain Dashboard Quest]] – Quest-Details und Level-Uebersicht
- [[Ideen]] – Alle Ideen verlinkt
- [[Vault-Anleitung]] – Wie der Vault funktioniert
