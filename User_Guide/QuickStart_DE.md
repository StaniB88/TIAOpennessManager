# TIA Openness Manager - Schnellstart

## Systemvoraussetzungen

- **Betriebssystem:** Windows 10/11 (64-bit)
- **TIA Portal:** Version 15, 16, 17, 18, 19 oder 20 installiert
- **.NET Framework:** 4.8 oder höher
- **Arbeitsspeicher:** Mindestens 4 GB RAM (8 GB empfohlen)
- **Festplatte:** 500 MB für die Anwendung

## Installation

1. Entpacken Sie das TiaOpennessManager-Archiv in einen Ordner Ihrer Wahl
2. Starten Sie `TiaOpennessManager.exe`
3. Beim ersten Start wird automatisch eine 30-tägige Testlizenz aktiviert

> **Hinweis:** TIA Portal muss installiert sein, aber muss nicht geöffnet sein.

## Erster Start

### 1. Mit TIA Portal Projekt verbinden

Klicken Sie auf den **Connect**-Button in der Mitte des Projektbaum-Bereichs. Ein Dialog öffnet sich mit zwei Tabs:

**Option A: Mit laufendem TIA Portal verbinden (empfohlen)**
1. Wählen Sie den **Attach to Running** Tab (standardmäßig ausgewählt)
2. Wählen Sie Ihre laufende TIA Portal Instanz aus der Liste
3. Klicken Sie auf **Connect**

> **Tipp:** Die Attach-Funktion ist schneller, da das Projekt nicht erneut geladen werden muss.

**Option B: Projektdatei öffnen**
1. Wählen Sie den **Open Project** Tab
2. Klicken Sie auf **Browse...** und navigieren Sie zu Ihrer TIA Portal Projektdatei (`.ap15` bis `.ap20`, `.apx`)
3. Klicken Sie auf **Connect**

> **Hinweis:** Die TIA Portal Version wird automatisch aus Ihrer Projektdatei erkannt.

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

**© 2026 AnyAutomation.**
