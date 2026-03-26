# TIA Openness Manager - Schnellstart

## Systemvoraussetzungen

- **Betriebssystem:** Windows 10/11 (64-bit)
- **TIA Portal:** Version 15 bis 21 installiert
- **TIA Portal Openness:** Ihr Windows-Benutzer muss Mitglied der Gruppe **"Siemens TIA Openness"** sein (siehe Einrichtung unten)
- **Arbeitsspeicher:** Mindestens 4 GB RAM (8 GB empfohlen)
- **Festplatte:** 500 MB für die Anwendung

## Installation

1. Entpacken Sie das TiaOpennessManager-Archiv in einen Ordner Ihrer Wahl
2. Starten Sie `TiaOpennessManager.V3.exe`
3. Beim ersten Start können Sie eine 30-tägige Testversion mit allen Funktionen starten

> **Hinweis:** TIA Portal muss installiert sein, aber muss nicht geöffnet sein.

### Windows-Benutzer zur Gruppe "Siemens TIA Openness" hinzufügen

TIA Portal erfordert, dass Ihr Windows-Benutzer Mitglied der Gruppe "Siemens TIA Openness" ist. Ohne diese Berechtigung wird die Verbindung verweigert.

1. Drücken Sie `Win + R`, geben Sie `lusrmgr.msc` ein, drücken Sie Enter
2. Klicken Sie links auf **Gruppen**
3. Doppelklicken Sie auf **"Siemens TIA Openness"**
4. Prüfen Sie, ob Ihr Benutzer aufgelistet ist. Falls nicht, klicken Sie auf **Hinzufügen**, geben Sie Ihren Benutzernamen ein, klicken Sie auf **Namen überprüfen** → **OK**
5. Klicken Sie auf **Übernehmen** → **OK**
6. **Melden Sie sich ab und wieder an**, damit die Änderung wirksam wird

> **Windows 11 Home:** `lusrmgr.msc` ist nicht verfügbar. Verwenden Sie stattdessen eine Eingabeaufforderung als Administrator:
> ```
> net localgroup "Siemens TIA Openness" %USERNAME% /add
> ```

## Erster Start

### 1. Mit TIA Portal Projekt verbinden

Es gibt zwei Möglichkeiten, sich zu verbinden:

**Option A: Projektdatei öffnen**
1. Wählen Sie **File → Connect**
2. Wechseln Sie im Connect-Dialog zum Tab **Open Project**
3. Klicken Sie auf **Browse** und wählen Sie Ihre `.ap15`/`.ap16`/`.ap17`/`.ap18`/`.ap19`/`.ap20`/`.ap21` Projektdatei
4. Die Verbindung startet automatisch

**Option B: Mit laufendem TIA Portal verbinden**
1. Öffnen Sie Ihr Projekt in TIA Portal
2. Wählen Sie **File → Connect**
3. Wechseln Sie im Connect-Dialog zum Tab **Attach to Running**
4. Klicken Sie auf **Refresh List**, wählen Sie die laufende Instanz, klicken Sie auf **Connect**

> **Tipp:** Das Verbinden ist schneller, da das Projekt nicht erneut geladen werden muss.

### 2. Export-Verzeichnis festlegen

1. Wechseln Sie zum **Import/Export** Tab
2. Klicken Sie auf **...** neben dem Feld "Right directory"
3. Wählen Sie einen Ordner aus, in dem die XML-Dateien gespeichert werden sollen

> **Tipp:** Verwenden Sie einen Git-Repository-Ordner für automatische Versionskontrolle.

## Erste Export-Operation

### Alle Blöcke exportieren

1. Im **Import/Export** Tab sehen Sie links den Projektbaum mit allen PLCs
2. Klappen Sie die PLC auf und navigieren Sie zu **Blocks**
3. Klicken Sie auf **Export All**
4. Die Blöcke werden als XML-Dateien in das gewählte Verzeichnis exportiert

### Einzelne Blöcke exportieren

1. Setzen Sie ein Häkchen bei den gewünschten Blöcken
2. Klicken Sie auf **Export Selected**

## Erste Import-Operation

### Blöcke aus XML importieren

1. Im rechten Bereich sehen Sie die XML-Dateien im Working Directory
2. Setzen Sie ein Häkchen bei den Dateien, die Sie importieren möchten
3. Klicken Sie auf **Import Selected**

> **Wichtig:** Der Import überschreibt bestehende Blöcke mit gleichem Namen!

## Nächste Schritte

- Lesen Sie das vollständige **Benutzerhandbuch** für alle Features
- Erkunden Sie die **Preview Diff** Funktion zum Vergleichen von Änderungen
- Nutzen Sie **Find Unused Blocks** um ungenutzte Bausteine zu finden
- Richten Sie **Protected Items** ein, um wichtige Blöcke vor Überschreiben zu schützen

---

## Haftungsausschluss

Die Software wird „as is" geliefert. Der Anbieter übernimmt keine Haftung für Schäden. Der Anwender trägt die volle Verantwortung für die Prüfung aller Inhalte. Siehe EULA auf https://www.tiaopenessmanager.ch

---

**Support:** Bei Fragen wenden Sie sich an den Support oder konsultieren Sie das ausführliche Benutzerhandbuch.

**© 2025-2026 AnyAutomation.**
