# TIA Openness Manager - Benutzerhandbuch

**Version:** 3.0
**Stand:** Februar 2026

---

## Inhaltsverzeichnis

0. [Willkommen-Tab](#0-willkommen-tab)
1. [Einführung](#1-einführung)
2. [Installation & Systemvoraussetzungen](#2-installation--systemvoraussetzungen)
3. [Benutzeroberfläche](#3-benutzeroberfläche)
4. [Projekt-Management](#4-projekt-management)
5. [Import/Export Tab](#5-importexport-tab)
6. [Project Tab](#6-project-tab)
7. [Protected Items Tab](#7-protected-items-tab)
8. [Passwort-Tresor (Vault Tab)](#8-passwort-tresor-vault-tab)
9. [MCP Tab (KI-Integration)](#9-mcp-tab-ki-integration)
9a. [KI-Chat](#9a-ki-chat)
9b. [OPC UA Tab](#9b-opc-ua-tab)
9c. [SCL Unit Testing (Enterprise)](#9c-scl-unit-testing-enterprise)
9c. [AI Canvas](#9c-ai-canvas)
10. [Projektbibliothek-Verwaltung](#10-projektbibliothek-verwaltung)
11. [Hardware Tab](#11-hardware-tab)
12. [Find Unused Blocks](#12-find-unused-blocks)
13. [Einstellungen](#13-einstellungen)
14. [Lizenzierung](#14-lizenzierung)
14a. [Git-Client](#14a-git-client)
15. [Fehlerbehebung & FAQ](#15-fehlerbehebung--faq)

---

## 0. Willkommen-Tab

### Was ist der Willkommen-Tab?

Der Willkommen-Tab ist das Erste, was Sie beim Start des TIA Openness Managers sehen. Er bündelt an einem Ort den Einstieg in eine neue Sitzung, eine kompakte Einführung in die wichtigsten Konzepte der Anwendung und den schnellen Wiedereinstieg in ein zuletzt genutztes Projekt. Der Tab ist nicht-modal — Sie können ihn parallel zu Ihrer Arbeit offen lassen oder schließen und später über das Hilfe-Menü wieder öffnen.

### Wann er sich öffnet

- **Beim ersten Start** öffnet sich der Willkommen-Tab automatisch.
- **Bei jedem weiteren Start** öffnet er sich so lange, bis Sie unten auf der Seite *„Willkommen-Seite beim Start anzeigen"* abwählen.
- **Jederzeit** können Sie ihn über **Hilfe → Willkommen-Guide** erneut öffnen. Ein erneutes Öffnen auf diesem Weg aktiviert die Startup-Einstellung nicht wieder.

### Schnellzugriff-Aktionen

Die linke Spalte bietet sieben Abkürzungen für die häufigsten ersten Schritte:

- **Mit TIA Portal verbinden…** — auf eine laufende TIA-Portal-Instanz aufsetzen.
- **TIA-Projekt öffnen…** — eine `.ap1x`- / `.ap2x`-Projektdatei von der Platte wählen.
- **Export-Ordner auswählen…** — den Ordner festlegen, in den exportierte Blöcke geschrieben werden.
- **Git-Repository klonen…** — ein Repository direkt in der Anwendung klonen.
- **Neue SCL-Datei…** — einen leeren SCL-Editor-Tab öffnen.
- **SCL Unit Testing…** — den SCL-Unit-Testing-Arbeitsbereich öffnen.
- **KI-Assistent konfigurieren…** — die KI-Chat-Einstellungen öffnen, um einen API-Schlüssel zu hinterlegen oder sich anzumelden.

### „Erste Schritte"-Anleitung

In der Mitte des Tabs finden Sie die interaktive **Erste Schritte**-Karte mit vier Schritten. Die Schritte haken sich automatisch ab, während Sie mit der Anwendung arbeiten:

1. **Mit TIA Portal verbinden** — wird abgehakt, sobald die Verbindung erfolgreich steht.
2. **Project Explorer kennenlernen** — erklärt die Checkboxen pro Zeile, den Unterschied zwischen *Export Selected* und *Export All*, die Protection-Spalte, an Import-/Export-Ordner gebundene Protection-Profile sowie Drag-&-Drop-Import. Ein Inline-Button öffnet den Protection-Profile-Speichern-Dialog; der Schritt wird abgeschlossen, sobald Sie ein Profil speichern (egal ob über diesen Button oder über Ihren normalen Project-Explorer-Ablauf).
3. **Ersten Baustein exportieren** — wird abgehakt, sobald ein Block-Export erfolgreich durchläuft.
4. **Nächsten Schritt wählen** — vier Buttons (Git, KI-Chat, SCL Unit Testing, OPC UA) öffnen den jeweiligen Tab und schließen diesen Schritt ab.

Oben auf der Karte zeigt ein Fortschrittsbalken, wie viele Schritte bereits abgeschlossen sind. Unten auf der Karte setzt der Link **Anleitungs-Fortschritt zurücksetzen** alle vier Haken zurück, wenn Sie die Anleitung noch einmal durchlaufen wollen.

### Feature-Karten

Fünf Karten rechts im Tab beschreiben die Hauptbereiche der Anwendung. Ein Klick auf eine Karte öffnet den passenden Bereich:

- **KI-Chat** — öffnet den KI-Chat-Arbeitsbereich und den Einstellungsdialog.
- **Git-Versionsverwaltung** — öffnet den Git-Arbeitsbereich.
- **SCL Unit Testing** — öffnet den SCL-Unit-Testing-Arbeitsbereich.
- **OPC-UA-Browser** — öffnet den OPC-UA-Arbeitsbereich.
- **Was ist neu in 3.x** — öffnet das mitgelieferte `CHANGELOG` mit den letzten nutzer-sichtbaren Änderungen.

### Zuletzt geöffnete Projekte

Die Liste **Zuletzt** zeigt bis zu fünf zuletzt geöffnete TIA-Projekte. Ein Klick auf einen Eintrag verbindet Sie direkt wieder damit. Bei mehr als fünf öffnet der Link **Mehr…** den vollständigen Connect-Dialog. Ist die Liste leer, bietet ein einzelner Inline-Link an, eine Verbindung zu starten.

### Willkommen-Tab ausblenden

Entfernen Sie unten im Tab den Haken bei **Willkommen-Seite beim Start anzeigen**. Die Anwendung öffnet den Willkommen-Tab beim Start dann nicht mehr automatisch. Über **Hilfe → Willkommen-Guide** können Sie ihn jederzeit wieder aufrufen.

---

## 1. Einführung

### Was ist der TIA Openness Manager?

Der TIA Openness Manager ist eine Desktop-Anwendung, die die Siemens TIA Portal Openness API nutzt, um SPS-Programmbausteine zu exportieren, importieren und zu verwalten. Er bietet eine benutzerfreundliche Alternative zu manuellen Export/Import-Operationen direkt im TIA Portal.

### Hauptanwendungsfälle

- **Versionskontrolle** - Exportieren Sie Blöcke als XML für Git/SVN
- **Projekt-Migration** - Übertragen Sie Blöcke zwischen Projekten
- **Backup** - Erstellen Sie regelmäßige Sicherungen Ihrer Programmbausteine
- **Code-Review** - Vergleichen Sie Änderungen mit der Preview Diff Funktion
- **Aufräumen** - Finden und entfernen Sie ungenutzte Blöcke

---

## 2. Installation & Systemvoraussetzungen

### Systemvoraussetzungen

| Komponente | Anforderung |
|------------|-------------|
| Betriebssystem | Windows 10/11 (64-bit) |
| TIA Portal | V15, V16, V17, V18, V19, V20 oder V21 |
| TIA Portal Openness | Windows-Benutzer muss in der Gruppe "Siemens TIA Openness" sein |
| .NET | .NET 10 Runtime (im Installer enthalten) |
| RAM | Mindestens 4 GB (8 GB empfohlen) |
| Festplatte | 500 MB |

### Installation

1. Laden Sie das TiaOpennessManager-Archiv herunter
2. Entpacken Sie das Archiv in einen Ordner Ihrer Wahl (z.B. `C:/Tools/TiaOpennessManager`)
3. Starten Sie `TiaOpennessManager.V3.exe`

> **Hinweis:** Es ist keine separate Installation erforderlich. Die Anwendung ist portable und enthält alle notwendigen Laufzeitumgebungen. TIA Portal muss auf dem System installiert sein.

### TIA Portal Openness einrichten

Ihr Windows-Benutzer muss Mitglied der Gruppe **"Siemens TIA Openness"** sein. Ohne diese Berechtigung verweigert TIA Portal die Verbindung.

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

### Anwendung starten

Pro Windows-Sitzung läuft nur eine Instanz des TIA Openness Managers. Wenn Sie eine Datei oder einen Ordner aus dem Windows Explorer öffnen, während die Anwendung bereits läuft, wird das vorhandene Fenster aktiviert und das Element dort geöffnet, statt eine zweite Kopie zu starten. Ein erneuter Doppelklick auf das Anwendungssymbol oder ein erneutes Ausführen der Exe holt ebenfalls nur das laufende Fenster nach vorn.

Wenn ein anderes Programm den Namen belegt hat, den die Anwendung intern verwendet, verweigert sie den Start und zeigt eine Warnung. Schließen Sie das andere Programm (oder melden Sie sich ab und wieder an) und versuchen Sie es erneut.

---

## 3. Benutzeroberfläche

### Hauptfenster-Übersicht

Die Anwendung ist in mehrere Bereiche unterteilt:

```
┌─────────────────────────────────────────────────────────────┐
│  Titelleiste                            [_] [□] [X]         │
├─────────────────────────────────────────────────────────────┤
│  Menü: File | Project | View | Help                         │
├─────────────────────────────────────────────────────────────┤
│  Toolbar: [Archive] [Disconnect] [Rescan] [Save]    TIA:V20 │
├─────────────────────────────────────────────────────────────┤
│  Schutzprofile: [Name] [Save] | [Profiles ▼] [Apply]        │
├─────────────────────────────────────────────────────────────┤
│  Baumsteuerung: [F-Signatur] [Safety Printout]               │
├─────────────┬───────────────────────────────────────────────┤
│             │  [Project] [Import/Export] [Find Unused]       │
│  Projekt-   │  [MCP] [Hardware]                              │
│  Baum       ├───────────────────────────────────────────────┤
│             │                                               │
│  (Links)    │              Tab-Inhalt                       │
│             │                                               │
├─────────────┴───────────────────────────────────────────────┤
│  Unteres Panel: [Log Output] [Terminal] [Compare]            │
├─────────────────────────────────────────────────────────────┤
│  Statusleiste: ● Verbunden | Statusnachricht | MCP: ● Aktiv  │
└─────────────────────────────────────────────────────────────┘
```

### Linker Bereich - Projektbaum

- Zeigt die Struktur des geöffneten TIA Portal Projekts
- Hierarchie: Projekt → Hardware → Source → PLC → Blocks/Datatypes/Tags
- Checkboxen ermöglichen Mehrfachauswahl für Export

### Rechter Bereich - Tabs

- **Project** - Code-Editor für ausgewählte Blöcke
- **Import/Export** - Haupt-Arbeitsbereich für Datei-Operationen
- **Find Unused** - Dead-Code-Erkennung und Aufräumen
- **MCP** - KI-Integrations-Status und Server-Steuerung
- **Hardware** - Geräteliste mit PROFINET-Namen und IP-Konfiguration

### Menüleiste

| Menü | Wichtige Einträge |
|------|-------------------|
| File | Connect, Browse Folder, Archive Project, Disconnect, Exit |
| Project | Rescan PLC, Save, Compile, Safety Login/Logoff |
| View | Settings, Terminal, Import/Export Settings, Protection Profiles Folder |
| Help | Documentation, Release Notes, Problem melden, About |

### Symbolleiste

| Button | Funktion |
|--------|----------|
| Archive | Erstellt ein komprimiertes Archiv des Projekts |
| Disconnect | Trennt die Verbindung zu TIA Portal |
| Rescan | Scannt die PLC nach Änderungen |
| Save | Speichert das TIA Portal Projekt |
| Compile | Kompiliert das Projekt |
| Safety Login | Meldet sich mit Safety-Anmeldedaten an |
| Safety Logoff | Meldet sich von Safety ab |

Die TIA Portal Version (z.B. V20) wird auf der rechten Seite der Symbolleiste angezeigt.

### Unteres Panel

Das untere Panel enthält drei Tabs:
- **Log Output** - Anwendungs-Logmeldungen mit farbcodierter Schwere
- **Terminal** - Integriertes Terminal für Kommandozeilen-Operationen
- **Compare** - Nebeneinander-Bausteinvergleich

Das Panel kann mit den Steuerelementen in der oberen rechten Ecke eingeklappt, erweitert oder maximiert werden.

---

## 4. Projekt-Management

### Mit TIA Portal verbinden

Klicken Sie auf **Connect** im File-Menü, um den Connect-Dialog zu öffnen.

Der Connect-Dialog hat zwei Tabs:

#### Tab 1: Mit laufender Instanz verbinden

1. Öffnen Sie zuerst Ihr Projekt in TIA Portal
2. Klicken Sie auf **Connect**, um den Connect-Dialog zu öffnen
3. Wechseln Sie zum Tab **Attach to Running**
4. Klicken Sie auf **Refresh List**, um laufende TIA Portal Instanzen zu finden
5. Wählen Sie die gewünschte Instanz aus
6. Klicken Sie auf **Connect**

**Vorteile des Attach Mode:**
- Schnellere Verbindung (kein Projekt-Laden)
- Sie können gleichzeitig in TIA Portal arbeiten
- Änderungen sind sofort sichtbar

#### Tab 2: Projektdatei öffnen

1. Klicken Sie auf **Connect**, um den Connect-Dialog zu öffnen
2. Wechseln Sie zum Tab **Open Project**
3. Klicken Sie auf **Browse** und navigieren Sie zur Projektdatei (`.ap15` bis `.ap21`)
4. Wählen Sie die Datei aus - die Verbindung startet automatisch

Dies startet TIA Portal im Hintergrund (Headless Mode) ohne sichtbare Benutzeroberfläche. Dies ist schneller für reine Export/Import-Operationen.

**Letzte Projekte:** Der Dialog merkt sich Ihr zuletzt geöffnetes Projekt für schnellen Zugriff.

**Hinweis:** Bei großen Bulk-Operationen (25+ Dateien) nutzt die Anwendung automatisch ExclusiveAccess für bessere Stabilität.

### Projekt archivieren

Erstellt ein komprimiertes Archiv (.zap-Datei) des aktuellen Projekts:

1. Klicken Sie auf **Archive Project** in der Toolbar
2. Wählen Sie einen Zielordner
3. Das Projekt wird mit allen zugehörigen Dateien archiviert

**Hinweis:** Das Projekt muss vor dem Archivieren gespeichert werden.

### Safety Printout

Generiert einen Safety-Dokumentations-Ausdruck für F-Blöcke:

1. Stellen Sie sicher, dass Sie mit Safety-Anmeldedaten eingeloggt sind (klicken Sie zuerst **Safety Login**)
2. Klicken Sie auf **Safety Printout** im Tree Controls Bereich
3. Wählen Sie einen Zielordner
4. Ein PDF wird mit allen sicherheitsrelevanten Dokumentationen generiert

**Hinweis:** Diese Funktion erfordert einen aktiven Safety-Login und ist nur für Projekte mit F-Blöcken verfügbar.

### Verbindung trennen

Klicken Sie auf **Disconnect** in der Toolbar oder wählen Sie **File → Disconnect**, um die Verbindung zu trennen. Im Headless Mode wird TIA Portal beendet.

---

## 5. Import/Export Tab

Der Import/Export Tab ist das Herzstück der Anwendung.

### Layout

```
┌──────────────────┬──────────────────┬───────────────────────┐
│   TIA Projekt    │    Aktionen      │   Working Directory   │
│   (Links)        │    (Mitte)       │   (Rechts)            │
├──────────────────┼──────────────────┼───────────────────────┤
│ □ Blocks         │ Export Selected→ │ [Refresh] [Pfad: ...] │
│   □ Main [OB1]   │ Export All →     │ □ Main.xml            │
│   □ Motor [FB1]  │                  │ □ Motor.xml           │
│   □ Calc [FC1]   │ ← Import Selected│ □ Calc.xml            │
│ □ Datatypes      │ ← Import All     │                       │
│ □ Tags           │                  │                       │
└──────────────────┴──────────────────┴───────────────────────┘
```

### Right Directory (Export-/Import-Verzeichnis)

Das Right Directory ist der Ordner auf Ihrem Dateisystem, in dem exportierte XML-Dateien gespeichert werden und aus dem Dateien importiert werden.

**Festlegen:**
1. Klicken Sie auf **...** neben dem Feld "Right directory"
2. Wählen Sie einen Ordner aus
3. Der Ordner wird mit dem Profil gespeichert und bei jedem Start geladen

**Tipp:** Verwenden Sie einen Git-Repository-Ordner für automatische Versionskontrolle.

> **Hinweis:** Das "Working Directory" in den Einstellungen bezieht sich auf die "Find Unused Blocks" Funktion und ist ein separater Ordner.

### Export-Operationen

#### Export Selected
1. Setzen Sie Häkchen bei den gewünschten Blöcken im linken Baum
2. Klicken Sie auf **Export Selected**
3. Die ausgewählten Blöcke werden als XML exportiert

#### Export All
1. Klicken Sie auf **Export All**
2. ALLE Blöcke, Datentypen und Tag-Tabellen werden exportiert

### Import-Operationen

#### Import Selected
1. Setzen Sie Häkchen bei den gewünschten XML-Dateien im rechten Baum
2. Klicken Sie auf **Import Selected**
3. Die ausgewählten Dateien werden importiert

#### Import All
1. Klicken Sie auf **Import All**
2. ALLE XML-Dateien im Working Directory werden importiert

**Wichtig:** Der Import überschreibt bestehende Blöcke mit gleichem Namen!

### Import/Export Optionen

Die Toolbar über dem rechten Baum bietet Optionen zur Anpassung des Import- und Exportverhaltens:

**Import-Optionen:**

| Option | Beschreibung |
|--------|--------------|
| Ignore Structural Changes | Ignoriert Strukturänderungen beim Import |
| Ignore Missing References | Setzt Import fort, auch wenn referenzierte Objekte fehlen |

**Export-Optionen:**

| Option | Beschreibung |
|--------|--------------|
| Export With Defaults | Inkludiert Standardwerte in der exportierten XML |
| Export With Read Only | Markiert exportierte Blöcke als schreibgeschützt |
| Geschützte Dateien exportieren | Wenn deaktiviert, werden als geschützt markierte Elemente nicht exportiert. Die Ordnerstruktur bleibt erhalten. |

Diese Optionen helfen bei häufigen Import-Problemen und passen das Export-Verhalten für Versionskontrolle an.

**S7DCL Export-Optionen (nur TIA Portal V20+):**

Die S7DCL (SIMATIC 7 Declaration Language) Export-Funktion bietet zusätzliche textbasierte Exporte neben den Standard-XML- und Quellcode-Dateien.

| Option | Beschreibung | Export-Ergebnis |
|--------|--------------|-----------------|
| SCL + S7DCL | SCL-Blöcke zusätzlich als S7DCL-Format exportieren | `.xml` + `.scl` + `.s7dcl` |
| AWL + S7DCL | AWL/STL-Blöcke zusätzlich als S7DCL-Format exportieren | `.xml` + `.awl` + `.s7dcl` |
| LAD/FBD + S7DCL | LAD/FBD/GRAPH-Blöcke zusätzlich als S7DCL-Format exportieren | `.xml` + `.s7dcl` |

**Warum S7DCL Export verwenden?**
- **Bessere Lesbarkeit:** Textbasiertes Format ideal für Code-Review
- **Versionskontrolle:** Perfekt für Diff-Vergleiche in Git/SVN
- **Mehrfachformat:** Behalte sowohl Standardformate ALS AUCH S7DCL für maximale Kompatibilität
- **Grafische Sprachen:** Ermöglicht Textexport für LAD/FBD-Blöcke (normalerweise nur XML)

**Wichtige Hinweise:**
- S7DCL-Dateien (`.s7dcl`) sind **nur Export** - sie **können NICHT** in TIA Portal re-importiert werden
- Die Checkboxen aktivieren **zusätzliche** Exporte, keine Ersetzungen - du erhältst immer die Standardformate
- Für LAD/FBD-Blöcke bietet S7DCL eine Textdarstellung, die sonst nicht existieren würde
- S7DCL Export erfordert TIA Portal V20 oder höher

**Zugriff auf S7DCL-Einstellungen:**
Wählen Sie **View → Import/Export Settings** aus der Menüleiste.

### Preview Diff

Die Preview Diff Funktion zeigt Unterschiede zwischen dem TIA Portal Projekt und dem Working Directory:

1. Klicken Sie auf **Preview Diff**
2. Die SPS wird zuerst kompiliert, damit auch noch nicht gespeicherte Änderungen erfasst werden, dann vergleicht die Anwendung TIA-Portal-Fingerprints und Datei-Hashes gegen den gespeicherten Stand vom letzten Export
3. Das Compare-Panel öffnet sich mit einer Zusammenfassungszeile (`X geändert · Y hinzugefügt · Z geschützt · N unverändert`) und einer Zeile pro Block-Unterschied:
   - **Geändert** - Block-Inhalt in TIA oder Source-Datei unterscheidet sich
   - **Neu in TIA** - Block existiert nur im Projekt
   - **Gelöscht** - Block existiert nur im Working Directory
4. Haken Sie die Checkbox neben jedem Block an, den Sie in die PLC zurückschreiben möchten (Geändert und Hinzugefügt sind vorausgewählt, geschützte Blöcke sind deaktiviert)
5. Klicken Sie auf **Importieren**, um die gewählten Dateien zu re-importieren

Preview Diff erkennt sowohl XML-seitige Änderungen (Block-Interface-Bearbeitungen in TIA) als auch Source-Datei-Änderungen (SCL, AWL, DB auf der Platte). Der Re-Import läuft in einer einzelnen Transaktion — wenn ein Block fehlschlägt, werden alle Änderungen zurückgerollt, und das Projekt bleibt im ursprünglichen Zustand. Nicht angehakte Zeilen und geschützte Blöcke werden nicht angefasst.

**Erste Nutzung:** Preview Diff funktioniert auf einem frischen Working Directory auch dann, wenn Sie Export All noch nie ausgeführt haben. Beim ersten Klick baut die Anwendung still eine Baseline auf, indem sie die SPS temporär exportiert, die temporären Dateien mit den bereits auf der Platte vorhandenen vergleicht und die Baseline (`.fingerprint-cache.json`) speichert — danach läuft jeder Folge-Vergleich über den schnellen Pfad. Der erste Durchlauf dauert länger als Folge-Durchläufe.

**Linke und rechte Dateiliste:** Das Compare-Panel zeigt links eine Dateiliste für die TIA-Seite und rechts eine passende Dateiliste für die Disk-Seite. Geänderte Blöcke erscheinen in beiden Listen; Blöcke, die nur in TIA existieren (oder noch kompiliert werden müssen), erscheinen nur links, Blöcke, die nur auf der Platte existieren, nur rechts. Beide Listen haben einen eigenen Ein-/Ausblenden-Toggle in der Compare-Toolbar — Sie können sich wahlweise auf eine Seite konzentrieren oder beide nebeneinander anzeigen lassen.

**Farbbalken am Zeilenrand:** Jede Zeile in beiden Dateilisten trägt am rechten Rand einen schmalen farbigen Balken, der den Änderungstyp ohne Textabgleich signalisiert: Grün für Hinzugefügt, Rot für Gelöscht, Orange für Geändert, Gelb für Inkonsistent (muss kompiliert werden), Blau für Blöcke, die nur in TIA existieren. Unveränderte Zeilen zeigen keinen Balken.

### Ad-hoc Compare (Drag and Drop)

Für schnelle Side-by-Side-Überprüfungen ohne Projektweiten Scan ziehen Sie Items direkt in das Compare-Panel:

1. Ziehen Sie einen oder mehrere Blöcke aus dem TIA-Projektbaum und lassen Sie sie über dem Compare-Panel fallen
2. Die SPS wird kompiliert, die Blöcke werden mit Ihren aktuellen Import/Export-Einstellungen exportiert (dieselben Strip-Regeln wie beim normalen "Export Selected"), und jede exportierte Datei wird zu einer eigenen Zeile in der Dateiliste links — ein SCL-Block erzeugt sowohl eine `.xml`- als auch eine `.scl`-Zeile, ein InstanceDB erzeugt `.xml` und `.db`
3. Klicken Sie auf die Zeile mit dem Format, das Sie links sehen möchten
4. Ziehen Sie die Datei, gegen die Sie vergleichen möchten, auf die rechte Seite des Diff-Editors (oder ziehen Sie zwei Dateien direkt, um sie ohne TIA-Export gegeneinander zu vergleichen)
5. Der Diff-Viewer zeigt die Unterschiede Zeile für Zeile

**Hinweise:**

- Die TIA-Seite wird kompiliert und genau gleich gestrippt wie bei einem normalen Export — der Vergleich erfolgt also Apfel gegen Apfel gegen eine Datei, die früher ins Working Directory exportiert wurde.
- Die rechte Seite bleibt leer, bis Sie dort eine Datei ablegen — ein TIA-Block kann so gegen mehrere Kandidat-Dateien geprüft werden, ohne neu zu exportieren.
- Der Splitter der Dateiliste ist zwischen 180 und 500 Pixeln resizebar und merkt sich die von Ihnen gewählte Breite.

Für den projektweiten Vergleich mit selektivem Re-Import zurück in die SPS verwenden Sie stattdessen **Preview Diff** (Hash-basiert, produziert Modified / Only in TIA / Only on Disk-Kategorien und einen Sync-Mode Import-Button).

### Diff-Editor Toolbar

Die Toolbar des Diff-Editors enthält folgende Bedienelemente:

- **Änderungsnavigation** — Buttons Erste / Vorherige / Nächste / Letzte Änderung plus ein `1/N`-Zähler springen durch alle Hunks der aktuellen Datei.
- **Kontextzeilen** — `+=` und `-=` erhöhen oder verringern die Anzahl der unveränderten Zeilen um jede Änderung (Standard 3, Minimum 4). Die Bereiche zwischen Hunks werden hinter einer `@@ -a,b +c,d @@`-Kopfzeile eingeklappt.
- **Ganze Datei zeigen** — Jede Zeile der Datei sichtbar, keine Kontext-Faltung mehr.
- **Syntax-Highlighting** — Ein/Aus (SCL, AWL, DB, XML und weitere Sprachen werden anhand der Dateiendung erkannt).
- **Zeilenumbruch** — Lange Zeilen in der Unified-Ansicht umbrechen.
- **Whitespace ignorieren** — Reine Leerzeichen-Unterschiede als unverändert behandeln.
- **Verborgene Zeichen** — Leerzeichen, Tabs und Zeilenende-Marker sichtbar machen.
- **Nebeneinander / Vereinheitlicht** — Layout umschalten.

Links daneben finden Sie die TIA-spezifischen Aktionen:

- **Bearbeiten** — Beide Seiten zum direkten Bearbeiten entsperren. Beim Aktivieren wechselt die Ansicht automatisch auf Side-by-Side und klappt die ganze Datei auf, damit Kontext-Faltung den Edit nicht zerreisst. Änderungen werden pro Seite getrackt.
- **Links speichern / Rechts speichern** — Die editierte Seite zurück zur Quelle schreiben (Datei auf der Platte oder Baustein in TIA).
- **Verwerfen** — Ungespeicherte Bearbeitungen verwerfen.
- **Alle nach rechts** / **Tauschen** / **Alle nach links** — Eine Seite mit der anderen überschreiben oder die Seiten tauschen.
- **Leeren** — Aktuellen Vergleich schliessen.

### HMI Export/Import

Für Projekte mit HMI-Geräten (WinCC Unified, Comfort Panels, etc.):

**Export HMI Selected:**
1. Wählen Sie HMI-Elemente im linken Baum aus (unter dem HMI-Geräteknoten)
2. Klicken Sie auf **Export HMI Selected**
3. Ausgewählte Bildschirme, Vorlagen, Variablen, Skripte werden exportiert

**Export HMI All:**
1. Klicken Sie auf **Export HMI All**
2. Alle HMI-Elemente von allen HMI-Geräten werden exportiert

**Unterstützte HMI-Elemente:**
- Bildschirme und Popups
- Bildschirmvorlagen
- HMI-Variablentabellen
- VB-Skripte
- Verbindungen
- Textlisten
- Grafiklisten

#### WinCC Unified Screen Export/Import

WinCC Unified Screens werden als JSON-Dateien exportiert (nicht XML wie bei Classic HMI). Der Export umfasst alle Bildschirmelemente mit ihren Eigenschaften, Positionen, Farben, Schriften, Texten, Kompositionen (z.B. ListBox-Einträge), Dynamisierungen und Ereignissen.

- **Export Selected:** Bildschirme im HMI-Baum auswählen, Export HMI Selected klicken
- **Export All:** Export HMI All klicken — exportiert automatisch alle Screens unter Beibehaltung der Ordnerstruktur (z.B. `Screens/Device PopUp/DCM.json`)
- **Import:** JSON-Dateien im Dateibaum auswählen, Import HMI Selected klicken. Bestehende Screens mit gleichem Namen werden gelöscht und neu erstellt.

> **Hinweis:** Bei WinCC Unified Screens werden nach dem Import alle Elemente in **Layer 0** platziert. Die Siemens TIA Portal Openness API bietet keine Möglichkeit, Layer-Zuordnungen zu lesen oder zu schreiben. Positionen und alle anderen Eigenschaften bleiben korrekt erhalten.

### Hardware-Export

Hardware-Konfiguration als AML/XML exportieren:

1. Erweitern Sie den **Hardware**-Knoten im Projektbaum
2. Wählen Sie Geräte oder Module zum Export
3. Klicken Sie auf **Export Selected**

**Hinweis:** Der Hardware-Export erstellt AutomationML (.aml) Dateien, die reimportiert oder für Dokumentation verwendet werden können.

---

## 6. Project Tab

### Code-Anzeige

Wenn Sie einen Block im Projektbaum auswählen, wird sein Quellcode im Code-Editor angezeigt.

**Unterstützte Sprachen:**
- SCL (Structured Control Language)
- STL (Statement List)
- LAD/FBD (als XML-Darstellung)

### Block-Details Panel

Neben dem Code werden Metadaten angezeigt:
- **Block-Typ:** OB, FB, FC, DB
- **Nummer:** z.B. OB1, FB10
- **Sprache:** SCL, STL, LAD, FBD, GRAPH
- **Autor:** Falls verfügbar
- **Letzte Änderung:** Zeitstempel

### Inline-Chat (Strg+I)

Der Inline-Chat ermöglicht es, der KI direkt im Code-Editor Fragen zu stellen oder Codeänderungen anzufordern — ohne zur KI-Chat-Seitenleiste wechseln zu müssen.

**Verwendung:**

1. Öffnen Sie den **Project**-Tab mit einem ausgewählten Block (oder leerem Editor)
2. Markieren Sie optional den Code, den Sie ändern oder über den Sie fragen möchten
3. Drücken Sie **Strg+I** — ein kleines Chat-Eingabefeld erscheint oben im Editor
4. Geben Sie Ihre Frage oder Anweisung ein (z.B. „Fehlerbehandlung hinzufügen", „Was macht dieser Abschnitt?")
5. Drücken Sie **Enter** zum Senden

**Umgang mit KI-Antworten:**

- Die KI streamt ihre Antwort direkt im Inline-Chat-Widget
- Wenn die KI eine Codeänderung vorschlägt, erscheinen **Übernehmen/Ablehnen**-Schaltflächen:
  - Drücken Sie **Tab** oder klicken Sie auf **Übernehmen**, um die Änderung anzuwenden
  - Drücken Sie **Escape** oder klicken Sie auf **Ablehnen**, um sie zu verwerfen
- Drücken Sie **Escape** jederzeit, um den Inline-Chat zu schließen

> **Tipp:** Der Inline-Chat funktioniert auch ohne geladenen Block — nützlich für allgemeine SCL-Fragen.

### Suche im Projektbaum

Nutzen Sie das Suchfeld über dem Projektbaum, um Blöcke schnell zu finden:
- Suche nach Name
- Suche nach Nummer
- Groß-/Kleinschreibung wird ignoriert

---

## 7. Protected Items Tab

### Konzept

Das Schutz-System verhindert, dass wichtige Blöcke versehentlich überschrieben werden.

### Blöcke schützen

1. Wechseln Sie zum **Protected Items** Tab
2. Navigieren Sie zum gewünschten Block
3. Setzen Sie ein Häkchen beim Block

Geschützte Blöcke werden:
- Beim Import übersprungen
- Beim Export übersprungen (wenn "Geschützte Dateien exportieren" in den Import/Export-Einstellungen deaktiviert ist)
- Mit einem grünen Schild-Symbol markiert
- In der Schutzliste angezeigt

> **Tipp:** Auch wenn geschützte Blöcke vom Export ausgeschlossen sind, bleibt die Ordnerstruktur immer erhalten.

### Profile

Profile speichern Ihre Schutz-Konfiguration:

**Profil speichern:**
1. Konfigurieren Sie Ihre geschützten Blöcke
2. Klicken Sie auf **Save Profile**
3. Geben Sie einen Namen ein

**Profil laden:**
1. Klicken Sie auf **Load Profile**
2. Wählen Sie ein gespeichertes Profil

---

## 8. Passwort-Tresor (Vault Tab)

### Übersicht

Der Passwort-Tresor speichert TIA Portal Know-How-Schutz-Passwörter sicher. Er verwendet AES-256-GCM-Verschlüsselung mit einem Master-Passwort zum Schutz aller Einträge. Der Tresor ermöglicht Massen-Schutz- und Entschutz-Operationen auf zugeordneten Blöcken.

### Tresor erstellen

1. Wechseln Sie zum Tab **Vault**
2. Klicken Sie auf **Neuer Tresor**
3. Wählen Sie einen Speicherort und Dateinamen (`.vault`-Erweiterung)
4. Geben Sie ein Master-Passwort ein

> **Wichtig:** Merken Sie sich Ihr Master-Passwort. Es kann nicht wiederhergestellt werden.

### Bestehenden Tresor öffnen

1. Klicken Sie auf **Tresor öffnen**
2. Wählen Sie eine `.vault`-Datei
3. Klicken Sie auf **Entsperren** und geben Sie Ihr Master-Passwort ein

### Einträge verwalten

**Eintrag hinzufügen:**
1. Klicken Sie auf **Eintrag hinzufügen**
2. Geben Sie einen Namen ein (z.B. "Produktions-SPS-Passwort")
3. Geben Sie das Know-How-Schutz-Passwort ein

**Eintrag bearbeiten:**
- Rechtsklick auf einen Eintrag und **Bearbeiten** wählen

**Eintrag entfernen:**
- Rechtsklick auf einen Eintrag und **Entfernen** wählen

### Passwörter Blöcken zuordnen

**Über Kontextmenü (einzelner Block):**
1. Rechtsklicken Sie im **Projektbaum** auf einen Block oder Ordner
2. Wählen Sie **Tresor-Passwort zuordnen**
3. Wählen Sie einen Tresoreintrag aus der Dropdown-Liste
4. Das Passwort ist nun mit diesem Blockpfad verknüpft

**Über Tresor-Toggle (Massen-Zuordnung):**
1. Aktivieren Sie die Tresor-Toggles (Schlüssel-Symbole erscheinen neben jedem Block im Baum)
2. Aktivieren Sie den Tresor-Toggle für die gewünschten Blöcke
3. Wählen Sie einen Tresoreintrag wenn aufgefordert
4. Markierte Blöcke werden diesem Tresoreintrag zugeordnet

### Massen-Schutz/Entschutz

1. Ordnen Sie Tresor-Passwörter über die Tresor-Toggle-Checkboxen oder das Kontextmenü zu
2. Rechtsklick und **Massen-Schutz (Tresor)** oder **Massen-Entschutz (Tresor)** wählen
3. Alle Blöcke mit zugeordneten Tresor-Passwörtern werden in einem Vorgang geschützt oder entschützt

> **Hinweis:** Geschützte Blöcke bleiben ihrem Tresoreintrag zugeordnet, auch wenn Sie den Tresor-Toggle deaktivieren. Um einen geschützten Block aus dem Tresor zu entfernen, müssen Sie ihn zuerst entschützen.

### Crash-Recovery

Falls die Anwendung abstürzt, während Blöcke ungeschützt sind:
1. Beim nächsten Projektöffnen erscheint ein Wiederherstellungsdialog
2. Er listet Blöcke auf, die ungeschützt geblieben sind
3. Klicken Sie **Ja**, um sie automatisch wieder zu schützen

### Tresor sperren

- Klicken Sie **Sperren**, um den Tresor zu sperren
- Klicken Sie **Tresor schliessen**, um den Tresor vollständig zu entladen
- Klicken Sie **Passwort ändern**, um das Master-Passwort zu ändern

### Tresor als CSV exportieren

Die CSV-Export-Funktion ermöglicht es Ihnen, eine Sicherung aller Tresor-Einträge im Textformat zu erstellen:

**Exportieren:**
1. Öffnen und entsperren Sie Ihren Tresor
2. Klicken Sie auf **CSV exportieren** in der Symbolleiste
3. Wählen Sie einen Zielordner für die Sicherungsdatei
4. Eine CSV-Datei wird mit allen Tresor-Einträgen erstellt

**CSV-Format:**
- Metadaten-Header mit Tresor-Informationen (App-Version, Tresor-Pfad, Export-Datum, Anzahl der Einträge)
- Spaltenkopfzeilen: Name, Password, Paths, ProtectedPaths
- UTF-8 Kodierung mit BOM (für Excel-Kompatibilität)
- RFC 4180 kompatible CSV-Formatierung

**Sicherheitshinweis:**
Die CSV-Datei enthält Passwörter im Klartext für Sicherungszwecke. Speichern Sie die exportierte CSV-Datei sicher, genau wie Sie die Tresordatei selbst schützen würden. Löschen Sie die CSV-Datei nach der Verifikation der Sicherung.

**Verfügbarkeit des Exports:**
- Der Export-CSV-Button ist nur aktiv, wenn der Tresor entsperrt ist
- Sperren Sie den Tresor danach, um unbeabsichtigte Exporte zu verhindern

---

## 9. MCP Tab (KI-Integration)

### Was ist MCP?

Das Model Context Protocol (MCP) ermöglicht KI-Assistenten, auf Ihr TIA Portal Projekt zuzugreifen.

### MCP Server Status

Der Tab zeigt:
- **Server Status:** Running / Stopped
- **Verbundene Clients:** Anzahl aktiver Verbindungen
- **Verfügbare Tools:** Liste der MCP-Funktionen

### Verwendung mit KI-Assistenten

1. Starten Sie den MCP Server im TIA Openness Manager
2. Konfigurieren Sie Ihren KI-Assistenten mit der MCP-Server-Adresse
3. Der KI-Assistent kann nun:
   - Projektstruktur abfragen
   - Block-Code lesen
   - Analysen durchführen

---

## 9a. KI-Chat

Das integrierte KI-Chat-Panel bietet eine Konversationsoberfläche zu einem KI-Assistenten, der Ihr Projekt und Ihre Umgebung kennt. Konfigurieren Sie es über **View → AI Chat Settings**.

### Chat-Anbieter

Wählen Sie pro Agent einen Anbieter im Provider-Dropdown. Jeder Anbieter verwendet seinen eigenen API-Schlüssel, den Sie einmalig in den Einstellungen hinterlegen.

| Anbieter | API-Schlüssel beziehen |
|----------|------------------------|
| xAI (Grok) | <https://console.x.ai/> |
| Groq | <https://console.groq.com/keys> |
| Cerebras | <https://cloud.cerebras.ai/> |
| DeepSeek | <https://platform.deepseek.com/api_keys> |
| Perplexity | <https://www.perplexity.ai/settings/api> |
| Together AI | <https://api.together.ai/settings/api-keys> |
| Hugging Face | <https://huggingface.co/settings/tokens> |
| Z.AI | <https://z.ai/manage-apikey/apikey-list> |
| MiniMax | <https://www.minimax.io/platform/user-center/basic-information/interface-key> |
| Fireworks AI | <https://fireworks.ai/account/api-keys> |
| Moonshot AI | <https://platform.moonshot.ai/console/api-keys> |
| Vercel AI Gateway | <https://vercel.com/dashboard/ai-gateway/api-keys> |
| SGLang (self-hosted) | Kein API-Schlüssel standardmäßig erforderlich — richten Sie den Endpunkt auf Ihren SGLang-Server aus (z.B. `http://localhost:30000/v1`) |
| vLLM (self-hosted) | Kein API-Schlüssel standardmäßig erforderlich — richten Sie den Endpunkt auf Ihren vLLM-Server aus (z.B. `http://localhost:8000/v1`) |
| Qwen | <https://home.qwencloud.com/api-keys> |
| Alibaba Model Studio | <https://home.qwencloud.com/api-keys> |
| Baidu Qianfan | <https://qianfan.baidubce.com/> |
| Volcano Engine (Doubao) | <https://console.volcengine.com/ark> |
| BytePlus (Doubao Global) | <https://console.byteplus.com/ark> |
| Arcee AI | <https://app.arcee.ai/> |
| Kimi Coding | <https://platform.moonshot.cn/console/api-keys> |

**Cloudflare AI Gateway** funktioniert anders als die oben genannten Provider: Es ist ein Proxy, der Chat-Anfragen über Ihr eigenes Cloudflare-Konto leitet. Wählen Sie es im Provider-Dropdown, tragen Sie dann Ihre **Konto-ID**, **Gateway-ID** ein und wählen Sie einen **Backend-Provider** (OpenAI, Anthropic, Groq, Mistral, Google oder Workers AI). Cloudflare-Caching, Analytics und Rate-Limits greifen vor dem gewählten Backend-LLM. Einstieg: <https://dash.cloudflare.com/?to=/:account/ai/ai-gateway>.

**Regions-Option für Qwen, Z.AI, MiniMax und Moonshot** — Wenn einer dieser vier Provider gewählt ist, erscheint im Einstellungsdialog zusätzlich ein **Region**-Picker. Wählen Sie **Global** für den internationalen Endpunkt oder **China** für den chinesischen Endpunkt; Qwen und Z.AI bieten zusätzlich **Global (Coding-Plan)** und **China (Coding-Plan)** für die separaten Coding-Abo-Endpunkte. Auf **Auto** bleibt der jeweilige Provider-Standard aktiv.

Zusätzlich verfügbar: Anthropic, OpenAI, Google Gemini, Mistral, OpenRouter, GitHub Copilot, Azure OpenAI, Google Vertex, AWS Bedrock, Ollama (lokal), LM Studio (lokal), **Google Antigravity** (Anmeldung mit Ihrem Google-Konto — gleicher Flow wie Gemini CLI — um Claude Opus/Sonnet, Gemini 3 Pro/Flash und GPT-OSS 120B in der Antigravity-Sandbox zu nutzen).

### Kontext-Ordner

Registrieren Sie Ordner auf Ihrem Dateisystem, die der KI zum Durchsuchen freigegeben sind. Nach der Registrierung kann die KI die Tools `fs_read_file`, `fs_list_directory` und `fs_search_files` verwenden, um diese Ordner in Ihrem Auftrag zu untersuchen.

**Einrichtung:**
1. Öffnen Sie **View → AI Chat Settings**
2. Navigieren Sie zum Abschnitt **Context Folders**
3. Klicken Sie auf **Ordner hinzufügen** und wählen Sie ein Verzeichnis (z.B. Ihr Export-Working-Directory oder ein Git-Repository)
4. Die KI kann Dateien in diesem Ordner während Chat-Sitzungen lesen und durchsuchen

### Anweisungsdateien

Anweisungsdateien sind Markdown-Dateien (`.md`), deren Inhalt automatisch zu Beginn jeder Konversation in den System-Prompt der KI eingefügt wird. Verwenden Sie sie, um der KI feste Anweisungen, Projektkonventionen oder Kontext mitzugeben, den sie immer kennen soll.

**Einrichtung:**
1. Öffnen Sie **View → AI Chat Settings**
2. Navigieren Sie zum Abschnitt **Instruction Files**
3. Klicken Sie auf **Datei hinzufügen** und wählen Sie eine `.md`-Datei
4. Der Dateiinhalt wird bei jeder neuen Chat-Sitzung dem System-Prompt vorangestellt

### Git-Integration

Der KI-Chat ist git-fähig. Wenn ein Git-Repository in einem Ihrer konfigurierten Kontext-Ordner (oder im aktuellen Arbeitsverzeichnis) erkannt wird, kann die KI:

- Den aktuellen Branch und Repository-Status anzeigen
- Staged und unstaged Änderungen anzeigen
- Dateien stagen
- Commits erstellen (unter Verwendung der aktiven Commit-Vorlage, falls konfiguriert)
- Änderungen pushen und pullen

**Schreibende Operationen** (Stagen, Commit, Push, Pull) erfordern eine ausdrückliche Benutzerbestätigung, bevor sie ausgeführt werden.

### Commit-Vorlagen

Definieren Sie Commit-Message-Vorlagen, an die sich die KI beim Erstellen von Commit-Nachrichten hält. Die aktive Vorlage wird verwendet, wenn die KI einen Commit erstellt.

**Einrichtung:**
1. Öffnen Sie **View → AI Chat Settings**
2. Navigieren Sie zum Abschnitt **Commit Templates**
3. Klicken Sie auf **Vorlage hinzufügen**, vergeben Sie einen Namen und schreiben Sie den Vorlagentext
4. Wählen Sie mit dem Radio-Button neben einer Vorlage diese als aktiv aus
5. Die KI hält sich bei allen Commits in der Chat-Sitzung an dieses Format

**Beispielvorlage:**
```
<typ>: <kurze Beschreibung>

<optionaler Textkörper>
```

### Skills

Skills sind Markdown-Dateien, die als Befehle in der `/`-Befehlspalette der Chat-Eingabe erscheinen. Sie ermöglichen die Definition wiederverwendbarer Prompts oder Anweisungen, die Sie beim Namen aufrufen können.

**Speicherort:** `%LocalAppData%\TiaOpennessManager\skills\`

#### Eingebaute Skills

Vier Standard-Skills werden mitgeliefert und beim ersten Start automatisch bereitgestellt:

| Skill | Icon | Beschreibung |
|-------|------|--------------|
| Explore Project | 🧭 | Analysiert das verbundene TIA Portal-Projekt und erstellt eine Kontextdatei |
| Explain Block | 💡 | Liest den Quellcode eines Bausteins und erklärt seine Logik |
| Generate SCL | ⌨️ | Generiert SCL-Code nach Siemens-Programmierstandards |
| Compare Blocks | 🔄 | Vergleicht Bausteinversionen zwischen Projekt und Exportordner |

Eingebaute Skills können bearbeitet werden. Um sie auf den Originalinhalt zurückzusetzen, klicken Sie auf **Skills-Ordner öffnen**, löschen Sie die geänderten Dateien und klicken Sie auf den **Neu laden**-Button (↻) — die Standards werden automatisch neu bereitgestellt.

#### Eigene Skills erstellen

Um einen neuen Skill zu erstellen, legen Sie eine `.md`-Datei im Skills-Ordner ab. Der einfachste Skill ist eine reine Textdatei:

```markdown
Bitte analysiere das aktuelle SPS-Programm und schlage Verbesserungen vor.
```

Für mehr Kontrolle fügen Sie YAML-Frontmatter oben ein, um Name, Beschreibung und Icon festzulegen:

```markdown
---
name: Export-Zusammenfassung
description: Den letzten Exportvorgang zusammenfassen
icon: 📊
---

Bitte fassen Sie die Bausteine zusammen, die beim letzten Export ausgegeben wurden, einschliesslich der Anzahl nach Typ.
```

Alle Frontmatter-Felder sind optional. Wenn kein `name` angegeben ist, wird der Dateiname verwendet. Wenn kein `icon` angegeben ist, wird ein Standard-Icon (📄) angezeigt.

Nach dem Hinzufügen oder Bearbeiten von Skill-Dateien klicken Sie auf den **Neu laden**-Button (↻) im Skills-Palette-Header, um die Liste zu aktualisieren.

**Frontmatter-Felder:**

| Feld | Pflicht | Beschreibung |
|------|---------|--------------|
| `name` | Nein | Anzeigename (Standard: Dateiname ohne Erweiterung) |
| `description` | Nein | Kurzbeschreibung in der Befehlspalette |
| `icon` | Nein | Emoji-Icon neben dem Skill-Namen (Standard: 📄) |
| `action` | Nein | Kommagetrennte Aktions-IDs für automatisches Verhalten (siehe unten) |
| `save-path` | Nein | Dateipfad zum Speichern der KI-Antwort (mit `save-response`-Aktion) |

#### Variablenersetzung

Skill-Inhalte unterstützen Variablen, die zur Laufzeit mit Projektinformationen ersetzt werden:

| Variable | Ersetzt durch |
|----------|---------------|
| `{ProjectName}` | Name des verbundenen TIA Portal-Projekts |
| `{ProjectDir}` | Verzeichnispfad des TIA Portal-Projekts |
| `{PlcName}` | Name der ersten SPS im Projekt |
| `{TiaVersion}` | Verbundene TIA Portal-Version (z.B. "V20") |
| `{Date}` | Aktuelles Datum im Format `yyyy-MM-dd` |
| `{ContextDir}` | Pfad zum Kontextdateien-Verzeichnis |

#### Aktions-Skills

Skills können ein `action`-Feld im Frontmatter enthalten, um automatisches Verhalten bei der Ausführung auszulösen:

| Aktion | Verhalten |
|--------|-----------|
| `auto-send` | Sendet den Prompt automatisch, ohne dass der Benutzer Enter drücken muss |
| `save-response` | Speichert die KI-Antwort in der durch `save-path` angegebenen Datei |
| `explore-project` | Kombiniert auto-send + save-response und speichert die Antwort als KI-Kontextdatei des Projekts (erfordert ein verbundenes TIA Portal-Projekt) |

Mehrere Aktionen können mit Kommas kombiniert werden: `action: auto-send, save-response`

**Beispiel eines Aktions-Skills:**
```markdown
---
name: Projekt dokumentieren
description: Projektdokumentation generieren und speichern
action: auto-send, save-response
save-path: {ProjectDir}\Projektdokumentation.md
---

Erstellen Sie eine vollständige Dokumentation für das TIA Portal-Projekt {ProjectName}.
```

#### Verwendung

1. Geben Sie in der Chat-Eingabe `/` ein
2. Die Befehlspalette listet alle verfügbaren Skills auf (eingebaute und eigene)
3. Wählen Sie einen Skill, um seinen Inhalt als Prompt einzufügen
4. Bei Aktions-Skills mit `auto-send` wird der Prompt automatisch gesendet

### Agent-Konfigurationen

Agenten definieren eine Persona für die KI, einschliesslich eines benutzerdefinierten System-Prompts und eines bestimmten Satzes erlaubter Tools. Wechseln Sie Agenten, um das KI-Verhalten für verschiedene Aufgaben anzupassen.

**Speicherort:** `%LocalAppData%\TiaOpennessManager\agents\`

**Format:** Jede `.json`-Datei definiert einen Agenten. Drei eingebaute Agenten werden bereitgestellt:

| Agent | Zweck |
|-------|-------|
| General Assistant | Allgemeine Chat-Funktion mit vollem Tool-Zugriff |
| Git Assistant | Fokussiert auf Git-Operationen; Datei-Tools eingeschränkt |
| SCL Expert | Spezialisiert auf das Schreiben und Prüfen von SCL/SPS-Code |

**Agenten wechseln:**
Verwenden Sie das Agenten-Dropdown in der KI-Chat-Kopfzeile, um den aktiven Agenten auszuwählen. Die Änderung tritt mit der nächsten gesendeten Nachricht in Kraft.

**Eigenen Agenten erstellen:**
Legen Sie eine `.json`-Datei in `%LocalAppData%\TiaOpennessManager\agents\` ab mit folgender Struktur:

```json
{
  "name": "Mein Benutzerdefinierter Agent",
  "description": "Eine kurze Beschreibung, die im Dropdown angezeigt wird",
  "systemPrompt": "Sie sind Experte für ...",
  "allowedTools": ["fs_read_file", "fs_list_directory", "git_status"]
}
```

**Responses API für Reasoning-Modelle (Azure):** Wenn Ihr Azure-Deployment ein Reasoning-Modell wie `o1`, `o3` oder `gpt-5` hostet, aktivieren Sie die Option „Responses API verwenden (für Reasoning-Modelle)" im Azure-Abschnitt des Agenten. Damit wird die Anfrage über den Azure-Responses-Endpoint geleitet, was nötig ist, damit `reasoning_effort` wirksam wird. Für Standard-Deployments (ohne Reasoning) lassen Sie die Option deaktiviert.

### Dateianhänge

Ziehen Sie Dateien direkt in den KI-Chat, um sie an Ihre Nachricht anzuhängen. Die KI kann den Inhalt angehängter Dateien sehen und entsprechend antworten.

**Unterstützte Dateitypen:**

| Kategorie | Erweiterungen |
|-----------|--------------|
| Bilder | `.png`, `.jpg`, `.jpeg`, `.bmp`, `.gif`, `.webp` |
| Text | `.cs`, `.xml`, `.json`, `.txt`, `.md`, `.yaml`, `.yml`, `.csv`, `.log`, `.scl`, `.cfg` |

**So hängen Sie Dateien an:**
1. Ziehen Sie eine oder mehrere Dateien aus dem Datei-Explorer auf den Chat-Bereich
2. Ein Drop-Overlay erscheint und bestätigt das Ziel
3. Bilder werden als Vorschau im Eingabebereich angezeigt; Textdateien als Chips
4. Klicken Sie auf **X** an einem Anhang, um ihn vor dem Senden zu entfernen
5. Senden Sie Ihre Nachricht wie gewohnt; Anhänge werden automatisch einbezogen

Bilder werden automatisch auf maximal 1024px (längste Seite) skaliert, um innerhalb der API-Limits zu bleiben.

### Zwischenablage einfügen

Fügen Sie einen Screenshot direkt aus der Zwischenablage in den Chat ein.

**So fügen Sie ein:**
1. Erstellen Sie einen Screenshot (z.B. Win+Umschalt+S)
2. Klicken Sie in das Chat-Eingabefeld
3. Drücken Sie **Strg+V** — wenn die Zwischenablage ein Bild enthält, wird es automatisch angehängt
4. Alternativ klicken Sie auf das **Büroklammer**-Symbol und wählen Sie **Aus Zwischenablage einfügen**

Wenn die Zwischenablage Text (kein Bild) enthält, erfolgt das normale Text-Einfügen.

### Chat-Sitzungen

Konversationen werden automatisch als Sitzungen gespeichert. Sie können neue Chats erstellen, zwischen Sitzungen wechseln und frühere Gespräche fortsetzen.

**Kopfzeilen-Buttons:**
- **+** (Neuer Chat) — Erstellt eine neue leere Sitzung und wechselt dorthin
- **Uhr** (Verlauf) — Blendet das Sitzungs-Panel ein/aus

**Sitzungsliste:**
- Klicken Sie auf eine Sitzung, um deren Nachrichten zu laden und das Gespräch fortzusetzen
- Sitzungstitel werden automatisch aus der ersten Nachricht generiert (bearbeitbar per Doppelklick)
- Bewegen Sie die Maus über eine Sitzung, um die Archiv- und Lösch-Buttons zu sehen

**Archiv:**
- Klicken Sie auf das Archiv-Symbol einer Sitzung, um sie in den eingeklappten Bereich "Archiviert" zu verschieben
- Archivierte Sitzungen können wiederhergestellt oder dauerhaft gelöscht werden
- Der Archiv-Bereich zeigt einen Zähler und lässt sich per Klick aufklappen

Sitzungen werden als JSON-Dateien in `%LocalAppData%\TiaOpennessManager\ChatSessions\` gespeichert.

### Agenten-Gedächtnis

Der KI-Agent kann Informationen über Chat-Sitzungen hinweg speichern und abrufen. Jeder Agent hat seinen eigenen privaten Gedächtnisspeicher, der zwischen Gesprächen erhalten bleibt, mit Scope-Isolierung zur Steuerung der Sichtbarkeit.

**Funktionsweise:**
- Der Agent speichert während einer Konversation automatisch wichtige Fakten, Entscheidungen und Präferenzen (Auto-Gedächtnis)
- Zu Beginn jeder Sitzung werden semantisch relevante Erinnerungen automatisch in den Kontext des Agenten eingefügt
- Subagenten-Ergebnisse werden automatisch als Erinnerungen für zukünftige Referenz gespeichert
- Sie können den Agenten auch ausdrücklich bitten, bestimmte Informationen zu merken, zu aktualisieren oder zu vergessen

**Gedächtnis-Scopes:**

| Scope | Beschreibung |
|-------|--------------|
| **Lokal** (Standard) | Nur dieser Agent sieht seine Erinnerungen |
| **Projekt** | Erinnerungen an ein bestimmtes Projekt gebunden (geteilt mit Agenten gleichen Scopes) |
| **Benutzer** | Globale Erinnerungen, sichtbar für alle Agenten |

Konfigurieren Sie den Gedächtnis-Scope in der Konfigurationsdatei jedes Agenten.

**Verfügbare Gedächtnis-Tools:**

| Tool | Beschreibung |
|------|--------------|
| `memory_store` | Einen Fakt, eine Entscheidung oder Präferenz für spätere Abfrage speichern |
| `memory_search` | Gespeicherte Erinnerungen per Stichwort oder semantischer Ähnlichkeit suchen |
| `memory_list` | Alle für den aktuellen Agenten gespeicherten Erinnerungen auflisten |
| `memory_update` | Den Inhalt einer bestehenden Erinnerung aktualisieren |
| `memory_delete` | Eine bestimmte Erinnerung löschen |

**Memory-Snapshots (Team-Initialisierung):**

Sie können Agenten mit geteiltem Wissen vorbefüllen, indem Sie eine JSON-Datei namens `{agent-id}.memories.json` im Agenten-Verzeichnis (`%LocalAppData%/TiaOpennessManager/agents/`) ablegen. Die Datei wird beim ersten Einsatz des Agenten automatisch importiert:

```json
[
  { "content": "Projekt nutzt ExclusiveAccess für Massenimporte", "tags": "project,import" },
  { "content": "PLC_1 läuft mit Firmware V4.5", "tags": "plc,hardware" }
]
```

Wenn die Snapshot-Datei aktualisiert wird, wird die neue Version beim nächsten Agentenstart automatisch importiert.

**Gedächtnis-Einstellungen:**

Öffnen Sie **View → AI Chat Settings** und navigieren Sie zum Abschnitt **Memory** für den ausgewählten Agenten:

- **Erinnerungen anzeigen** — Alle gespeicherten Erinnerungen des aktuellen Agenten durchsuchen
- **Erinnerungen löschen** — Einzelne Einträge entfernen oder alle Erinnerungen löschen
- **Exportieren (JSON)** — Alle Erinnerungen zur Sicherung in eine JSON-Datei exportieren
- **Importieren** — Erinnerungen aus einer zuvor exportierten JSON-Datei wiederherstellen
- **Alte Erinnerungen aufräumen** — Erinnerungen älter als ein konfigurierbares Alter entfernen

**Embedding-Anbieter (semantische Suche):**

Jeder Agent kann mit einem Embedding-Anbieter für semantische Gedächtnissuche konfiguriert werden. Wenn konfiguriert, findet der Agent Erinnerungen nach Bedeutung statt Schlüsselwortübereinstimmung:

| Anbieter | Einrichtung |
|----------|-------------|
| OpenAI | API-Schlüssel erforderlich |
| Google | API-Schlüssel erforderlich |
| Ollama | Lokale Ollama-Instanz |
| LM Studio | Lokale LM Studio-Instanz |

Wenn kein Embedding-Anbieter konfiguriert ist, wechselt der Agent automatisch zur schlüsselwortbasierten Suche.

### Subagenten-Steuerung

Der KI-Agent kann Teilaufgaben an unabhängige Subagenten delegieren und diese während einer Konversation verwalten. Dies ermöglicht dem Agenten, parallele oder langwierige Aufgaben auszuführen, ohne den Hauptdialog zu blockieren.

**Verfügbare Subagenten-Tools:**

| Tool | Beschreibung |
|------|--------------|
| `run_subagent` | Eine Teilaufgabe an einen neuen Agenten delegieren (blockierend oder nicht-blockierend) |
| `manage_subagents list` | Alle aktuell laufenden Subagenten und ihren Status anzeigen |
| `manage_subagents kill` | Einen laufenden Subagenten beenden |
| `manage_subagents steer` | Einen laufenden Subagenten mit neuen Anweisungen umlenken |

**Wichtige Verhaltensweisen:**
- Bis zu 5 Subagenten können gleichzeitig laufen
- Nicht-blockierende Subagenten laufen im Hintergrund; der Hauptagent kann weiterarbeiten und Ergebnisse später prüfen
- Blockierende Subagenten pausieren den Hauptagenten, bis die Teilaufgabe abgeschlossen ist
- Der Hauptagent kann einen laufenden Subagenten mit neuen Anweisungen umlenken

**Beispiel-Anwendungsfälle:**
- Mehrere SPS-Bausteine parallel analysieren
- Einen langen Exportvorgang im Hintergrund ausführen, während Fragen beantwortet werden
- Dokumentationserstellung an einen Subagenten delegieren, während Code überprüft wird

**Genehmigungs-Anfragen von Sub-Agenten.** Wenn ein Sub-Agent deine Erlaubnis braucht, um ein Tool auszuführen (z. B. eine OPC-UA-Verbindung aufzubauen oder einen Git-Branch zu pushen), erscheint die Anfrage jetzt direkt im Hauptchat — du musst das Sub-Agent-Panel nicht aufklappen, um sie zu finden. Jede Anfrage zeigt klar, welcher Sub-Agent sie ausgelöst hat. Nach deiner Entscheidung zeigt die Anfrage einen von drei Status: grüner Haken ("Erlaubt"), rotes X ("Abgelehnt" — du hast aktiv abgelehnt) oder oranger Hinweis ("Unterbrochen" — die App wurde geschlossen oder der Aufruf abgebrochen, bevor du entscheiden konntest). Tool-Argumente mit Namen wie `password`, `api_key` oder `token` werden als `[redacted]` angezeigt, damit sie nicht in der Chat-Historie auf der Platte landen.

### Hooks

Hooks sind ereignisgesteuerte Abfangmechanismen, die vor oder nach KI-Tool-Aufrufen ausgefuehrt werden. Sie ermoeglichen benutzerdefinierte Validierung, Formatierung, Protokollierung oder Steuerung der Tool-Ausfuehrung.

**Eingebaute Hooks** (immer aktiv):
- **Safety-Bestaetigung** — Blockiert automatisch die KI-Modifikation von Safety-Bausteinen (F_-Prefix)
- **Kompilierung nach Import** — Erinnert die KI nach dem Import an die Kompilierung
- **Audit-Log** — Protokolliert alle TIA Portal Tool-Operationen

**Benutzerdefinierte Hooks:**

Eigene Hooks koennen in `ai_chat_settings.json` unter dem `Hooks`-Array hinzugefuegt werden:

```json
{
  "Hooks": [
    {
      "Event": "PreToolUse",
      "Matcher": "tia_delete_*",
      "Type": "command",
      "Command": "node validate-delete.js",
      "TimeoutSeconds": 30,
      "IsBackground": false,
      "Enabled": true
    },
    {
      "Event": "PostToolUse",
      "Matcher": "tia_export_*",
      "Type": "http",
      "Url": "http://localhost:8080/hooks/post-export",
      "TimeoutSeconds": 10,
      "IsBackground": true,
      "Enabled": true
    }
  ]
}
```

| Feld | Beschreibung |
|------|-------------|
| `Event` | Zeitpunkt: `PreToolUse`, `PostToolUse`, `Stop`, `UserPromptSubmit` |
| `Matcher` | Tool-Namensmuster (z.B. `tia_*`, `tia_delete_*\|tia_import_*`, `Bash(git *)`) |
| `Type` | `command` (Shell) oder `http` (POST-Callback) |
| `Command` | Shell-Befehl (empfaengt JSON auf stdin, gibt JSON auf stdout zurueck) |
| `Url` | HTTP-Endpunkt fuer `http`-Typ-Hooks |
| `TimeoutSeconds` | Maximale Ausfuehrungszeit (Standard 60s) |
| `IsBackground` | Bei `true` wird fire-and-forget ausgefuehrt (nur PostToolUse) |
| `Enabled` | Auf `false` setzen um zu deaktivieren ohne zu loeschen |

**Shell-Hook-Protokoll:** Der Hook empfaengt ein JSON-Objekt auf stdin mit `tool_name`, `tool_input`, `tool_output`, `session_id` und `agent_id`. Er sollte JSON auf stdout zurueckgeben mit `decision` (`allow`/`deny`/`ask`), optionalem `reason`, `additionalContext` oder `updatedInput`. Exit-Code 2 blockiert die Ausfuehrung.

### Befehlswarteschlange

Sie koennen Nachrichten eingeben und senden waehrend der KI-Agent aktiv arbeitet. Waehrend des Streamings eingegebene Nachrichten werden in eine Prioritaetswarteschlange gestellt und nach jedem abgeschlossenen Turn automatisch verarbeitet.

**Senden waehrend der Agent arbeitet:** Geben Sie einfach Ihre Nachricht ein und druecken Sie Enter waehrend der Agent streamt. Die Nachricht wird als "in Warteschlange" angezeigt und das Eingabefeld wird geleert, damit Sie weitertippen koennen. Ein kleiner Indikator neben dem Eingabebereich zeigt an, wie viele Nachrichten warten (z.B. "2 Nachrichten in Warteschlange").

**Prioritaetsstufen:**

| Prioritaet | Verwendung | Verhalten |
|------------|-----------|----------|
| Naechstes | User-Nachrichten (Standard) | Verarbeitung nach aktuellem Turn |
| Spaeter | Agenten-Benachrichtigungen | Verarbeitung nach User-Nachrichten |

**Warteschlangen-Steuerung:**

- **ESC waehrend Streaming:** Bricht die aktuelle KI-Antwort ab und leert alle wartenden Nachrichten
- **Pfeil-nach-oben bei leerem Eingabefeld:** Holt alle wartenden Nachrichten zurueck ins Eingabefeld, damit Sie sie bearbeiten oder verwerfen koennen. Bereits eingegebener Text bleibt stehen — die Warteschlangen-Nachrichten werden dahinter angehaengt.
- **Stop-Button im Leerlauf mit wartenden Nachrichten:** Gleich wie Pfeil-nach-oben — holt die Warteschlange ins Eingabefeld zurueck.

**Warteschlangen-Anzeige:** Der Text neben dem Eingabefeld zeigt, wie viele Nachrichten warten und was der Assistent gerade tut — zum Beispiel "2 in Warteschlange — tia_import laeuft", "1 in Warteschlange — Sub-Agent scl-expert laeuft" oder "3 in Warteschlange — ESC entfernt letzte", wenn der Assistent im Leerlauf ist.

**Sub-Agent-Genehmigungen:** Wenn ein Sub-Agent ein Tool ausfuehren moechte, das eine Genehmigung benoetigt, erscheinen die Allow/Deny-Buttons im Haupt-Chat und sind mit "ueber Sub-Agent X" gekennzeichnet, damit erkennbar ist, von welchem Agenten die Anfrage stammt.

**Sub-Agent in den Hintergrund verschieben:** Wenn ein blockierender Sub-Agent den Haupt-Assistenten wartet laesst, druecken Sie **Strg+B**. Der Sub-Agent wird losgeloest und laeuft im Hintergrund weiter, waehrend der Haupt-Assistent frei ist, auf neue Nachrichten zu antworten. Am Sub-Agent-Block erscheint ein kleines "(Hintergrund)"-Kennzeichen. Sobald der Sub-Agent im Hintergrund fertig ist, erscheint sein Ergebnis als Benachrichtigung im Chat, und der Haupt-Assistent setzt dort an. Wenn mehrere Sub-Agenten gleichzeitig blockieren, schickt Strg+B alle auf einmal in den Hintergrund.

**Warteschlangen-Verarbeitung:** Nach jedem abgeschlossenen KI-Turn prueft das System automatisch die Warteschlange und verarbeitet die naechste Nachricht. Bei mehreren wartenden Nachrichten werden diese einzeln in Prioritaetsreihenfolge verarbeitet (hoehere Prioritaet zuerst, FIFO innerhalb gleicher Prioritaet).

---

### Multi-Session

Fuehren Sie mehrere KI-Chat-Sessions gleichzeitig aus. Jede Session hat einen eigenen Konversationskontext, Canvas-State und Modell-Override.

**Agent-Sidebar:** Klicken Sie auf das Sidebar-Toggle-Icon (PanelLeftOpen/PanelLeftClose) im Chat-Header, um die Agent-Sidebar ein-/auszublenden. Sie gleitet als Overlay von links heraus, ohne den Chat-Inhalt zu verschieben. Sie zeigt alle Sessions gruppiert nach Status:

- **In Bearbeitung** — Sessions, in denen die KI aktiv streamt oder mit denen interagiert wurde
- **Abgeschlossen** — Sessions, die erfolgreich oder mit Fehlern beendet wurden

**Sessions erstellen:** Klicken Sie auf den **+**-Button im Sidebar-Header, um eine neue Session zu erstellen. Die Sidebar oeffnet sich automatisch bei der zweiten Session.

**Sessions wechseln:** Klicken Sie auf eine Session in der Sidebar, um zu ihr zu wechseln. Chat-Kontext, Canvas und Modell-Override wechseln zur gewaehlten Session.

**Sessions schliessen:** Klicken Sie auf den **X**-Button eines Session-Eintrags. Bei laufenden Sessions erscheint ein Bestaetigungsdialog. Das Schliessen bricht aktives Streaming ab, beendet Subagenten und bereinigt den Session-Kontext.

**Ungelesene-Badges:** Wenn eine andere Session eine Nachricht empfaengt waehrend Sie eine andere Session betrachten, erscheint ein Ungelesen-Badge mit kurzer Blink-Animation auf dem Session-Eintrag.

**Sessions umbenennen:** Doppelklicken Sie auf einen Session-Namen zum Bearbeiten. Druecken Sie Enter oder klicken Sie ausserhalb zum Speichern.

**Canvas pro Session:** Jede Session verwaltet ihren eigenen Canvas-State. Beim Wechsel wird das WebView zurueckgesetzt und der Canvas-Inhalt der Ziel-Session automatisch wiedergegeben.

**Live-Modellwechsel:** Verwenden Sie den Modell-Picker-Button im Chat-Header, um das KI-Modell nur fuer die aktuelle Session zu wechseln. Andere Sessions und die globale Einstellung sind nicht betroffen.

---

## 9b. OPC UA Tab

Der OPC UA Tab bietet einen eingebauten OPC UA Client, um direkt aus dem TIA Openness Manager heraus eine Verbindung zu SPSen und anderen OPC UA Servern herzustellen, den Adressraum zu durchsuchen und Variablen zu überwachen. Öffnen Sie ihn über die ActivityBar in der linken Seitenleiste (drittes Symbol von oben).

### Übersicht

OPC UA (Open Platform Communications Unified Architecture) ist ein industrieller Kommunikationsstandard, der von Siemens S7-1500 und S7-1200 SPSen ab Firmware 4.1 unterstützt wird. Der Tab ermöglicht das Lesen und Schreiben von Live-PLC-Werten, das Abonnieren von Änderungen für Echtzeit-Überwachung sowie den Export von Beobachtungstabellen-Daten für die Analyse.

### Verbindung zu einem OPC UA Server herstellen

#### Manuelle Verbindung

1. Klicken Sie auf das **OPC UA**-Symbol in der ActivityBar (linke Seitenleiste, drittes von oben)
2. Geben Sie die **Endpunkt-URL** in das Verbindungsfeld ein (z.B. `opc.tcp://192.168.0.1:4840`)
3. Wählen Sie den **Authentifizierungsmodus**:
   - **Anonym** - Keine Anmeldedaten erforderlich (wenn der Server dies erlaubt)
   - **Benutzername/Passwort** - Geben Sie die auf der SPS konfigurierten OPC UA Anmeldedaten ein
   - **Zertifikat** - Wählen Sie ein Client-Zertifikat für sichere Authentifizierung
4. Klicken Sie auf **Verbinden**

Der Status-Indikator im Tab-Header wird grün, wenn die Verbindung hergestellt ist.

#### Automatische Erkennung aus TIA-Projekt

Wenn ein TIA Portal-Projekt geöffnet ist, kann der TIA Openness Manager automatisch in dem Projekt konfigurierte OPC UA Endpunkte erkennen:

1. Klicken Sie auf **Auto-Discover** im Verbindungsbereich
2. Die Anwendung liest die Netzwerkkonfiguration aus dem verbundenen TIA-Projekt
3. Erkannte PLC-Endpunkte werden in einem Dropdown aufgelistet
4. Wählen Sie den gewünschten Endpunkt und klicken Sie auf **Verbinden**

Dadurch entfällt die manuelle Eingabe von IP-Adressen und Port-Nummern.

### Adressraum durchsuchen

Der linke Bereich des OPC UA Tabs zeigt eine Baumansicht des Server-Adressraums:

- Der Stamm zeigt die Knoten der obersten Ebene des Servers
- Erweitern Sie einen Knoten, um seine Kinder anzuzeigen
- PLC-Variablen, Datenbausteine und Tag-Gruppen erscheinen als Knoten
- Symbole zeigen die Knotenklasse an: Objekt, Variable, Methode, Ansicht

**Knoten suchen:**
Verwenden Sie das Suchfeld über dem Baum, um Knoten nach Namen zu filtern. Der Baum klappt zusammen und zeigt nur übereinstimmende Knoten und ihre übergeordneten Elemente an.

### Knoteninformationen

Ein im Adressraum ausgewählter Knoten füllt das **Knoteninformationen**-Panel auf der rechten Seite mit allen OPC UA-Attributen dieses Knotens: Node Id, Browse Name, Display Name, Node Class, Description, Write Mask und User Write Mask. Bei Variablen kommen Data Type, Value Rank, Array Dimensions, Access Level, User Access Level, Minimum Sampling Interval, Historizing, aktueller Value, Status Code sowie Source- und Server-Timestamp dazu. Alle Zellen lassen sich mit Strg+C kopieren.

### Referenzen

Neben den Knoteninformationen zeigt das **Referenzen**-Panel jede eingehende und ausgehende Referenz des ausgewählten Knotens:

| Spalte | Beschreibung |
|--------|--------------|
| Richtung | In (invers) oder Out (vorwärts) |
| Referenztyp | Aufgelöster Name des Referenztyps (z. B. `HasComponent`, `Organizes`, `HasTypeDefinition`) |
| Browse-Name | Browse-Name des Zielknotens |
| Knotenklasse | Knotenklasse des Zielknotens |
| Ziel-Knoten-ID | Vollständige Node Id des referenzierten Knotens |

### Ereignisprotokoll

Das **Ereignisprotokoll** liegt als Tab neben der Beobachtungstabelle am unteren Rand des OPC-UA-Arbeitsbereichs und empfängt Live-Ereignismeldungen von einem serverseitigen Notifier-Objekt.

| Toolbar-Element | Zweck |
|-----------------|-------|
| Notifier-Knoten | Node Id des OPC-UA-Objekts, das Ereignisse meldet. Standard ist `i=2253` (Server). Während aktiver Subscription gesperrt. |
| Schweregrad | Zwei Zahleneingaben (0–1000), die einkommende Ereignisse nach Schweregrad einschränken. Ereignisse außerhalb des Bereichs werden vor der Anzeige verworfen. |
| Ereignisse abonnieren | Startet die Subscription gegen den konfigurierten Notifier. |
| Ereignis-Abonnement stoppen | Bricht die aktive Subscription ab. |
| CSV exportieren | Speichert die sichtbaren Ereignisse als CSV. Zellen, die mit `=`, `+`, `-`, `@`, Tabulator oder Wagenrücklauf beginnen, werden mit einem führenden Apostroph quotiert, um Tabellenkalkulations-Formel-Injektionen zu entschärfen. |
| Ereignisprotokoll leeren | Leert die Tabelle, ohne die aktive Subscription zu beenden. |

Die Tabelle hält die letzten 5000 Ereignisse mit dem neuesten oben. Server-gelieferte Felder werden auf 8 KB pro Zelle begrenzt, um den Speicher zu schützen; bei Ereignisfluten werden zusätzliche Ereignisse stillschweigend verworfen, und einmal pro Sekunde wird eine Debug-Log-Zeile mit der Anzahl der verworfenen Ereignisse geschrieben.

### Verlaufsdiagramm (History Chart)

Das **Verlaufsdiagramm** liegt als dritter Tab neben Beobachtungstabelle und Ereignisprotokoll am unteren Rand des OPC-UA-Arbeitsbereichs. Es lädt die historischen Rohwerte eines Variablenknotens über einen Zeitbereich und stellt sie in einem Streudiagramm mit Datum/Uhrzeit-X-Achse dar.

| Bedienelement | Zweck |
|---------------|-------|
| Quelle | Schreibgeschützte Anzeige, folgt automatisch dem aktuell im Adressraum ausgewählten Variablenknoten. |
| Start | Beginn des Zeitbereichs (UTC). Standard: vor einer Stunde. |
| Ende | Ende des Zeitbereichs (UTC). Standard: jetzt. |
| 1h / 6h / 24h / 7T | Schnellauswahl: setzt Ende auf jetzt und Start auf jetzt minus das gewählte Intervall. |
| Verlauf lesen | Holt die historischen Rohwerte für den Quellknoten zwischen Start und Ende. Während eines laufenden Lesevorgangs deaktiviert. |
| CSV exportieren | Speichert die geladenen Werte als CSV (Source Timestamp / Server Timestamp / Value / Status Code). Der Schutz gegen Formel-Injektion ist identisch mit dem Ereignisprotokoll-Export. |
| Diagramm leeren | Löscht das Diagramm und gibt den Speicher frei. |

Nicht-numerische Werte, Werte mit `Bad`-Status sowie Samples mit ungültigen Zeitstempeln werden im Diagramm ausgelassen, bleiben aber im CSV-Export enthalten. Ein Lesevorgang ist auf 100.000 Werte pro Anfrage und 1.000.000 Werte gesamt begrenzt; liefert der Server mehr, zeigt das Diagramm das, was hineinpasst, und eine Warnung wird protokolliert. Das Diagramm wird automatisch beim Protokollwechsel oder bei der Trennung geleert — beim Navigieren im Adressraum bleibt der Inhalt jedoch erhalten, damit geladene Daten nicht durch einen Knotenwechsel verloren gehen.

Die Variable muss am Server `Historizing = true` haben und die Sitzung muss HistoryRead-Zugriff besitzen. Siemens S7-1500-CPUs aktivieren Historizing nicht automatisch — die meisten Variablen müssen in der PLC-Konfiguration explizit für den Verlaufszugriff markiert werden.

### Methodenaufruf-Dialog

Rechtsklick auf einen **Methodenknoten** im Adressraum-Browser und **Methode aufrufen...** wählen öffnet einen modalen Dialog, der einen OPC-UA-Methodenaufruf von Anfang bis Ende durchführt.

Der Dialog lädt zunächst die Liste der Eingabe- und Ausgabeargumente vom Server und rendert je ein Eingabefeld pro Input:

| Argumentform | Eingabefeld |
|--------------|-------------|
| Skalar (boolean, Integer, Float, String, DateTime) | Einzelnes Textfeld mit dem erwarteten Datentyp als Platzhalter |
| Array | Liste von Einzelwertzeilen mit **+ Zeile** / **− Zeile** zum Anpassen der Arraylänge |

Jede Karte zeigt Name, Datentyp und Beschreibung des Arguments (falls vom Server geliefert). Nach dem Befüllen der Eingaben **Aufrufen** klicken — der Dialog ruft den Server auf, begrenzt übergroße Payloads und füllt den Ausgabebereich mit den zurückgegebenen Werten und einer Statuszeile. Dialog schließen bricht einen noch laufenden Aufruf ab.

Methodenaufrufe schreiben auf die PLC — vor dem Aufruf an einer laufenden Maschine die Wirkung der Methode verstehen.

### Matrix bearbeiten-Dialog

Rechtsklick auf einen **Variablenknoten**, dessen Wert eine zweidimensionale Matrix ist (zum Beispiel eine `Double[3,4]`-Sollwert-Tabelle oder ein Kalibriergitter), im Adressraum-Browser und **Matrix bearbeiten...** wählen öffnet einen tabellenartigen Editor. Der Menüeintrag erscheint nur, wenn die selektierte Variable tatsächlich Matrix-Form am Server hat.

Der Dialog lädt den aktuellen Wert und rendert jede Zelle als bearbeitbares Textfeld mit Zeilenüberschriften (`R0`, `R1`, ...) und Spaltenüberschriften (`C0`, `C1`, ...). Zellen einzeln bearbeiten — geänderte Zellen werden als geändert markiert. **Speichern** schreibt die gesamte Matrix zurück zum Server (nur tatsächlich geänderte Zellen werden neu geparst; unveränderte Zellen bleiben erhalten) oder **Neu laden** verwirft die Bearbeitung und holt eine frische Kopie vom Server.

Wenn der Server die Variable als schreibgeschützt deklariert (kein Schreibzugriff für Ihre Sitzung), zeigt der Dialog ein **Nur lesen**-Etikett und der Speichern-Button bleibt deaktiviert. Matrizen mit mehr als zwei Dimensionen sind nicht bearbeitbar — der Dialog meldet "Rang nicht unterstützt" statt die Daten still zu flatten. Ungültige Zellwerte (zum Beispiel Text in einer numerischen Matrix) werden beim Speichern markiert; Zelle korrigieren und erneut versuchen.

### Zertifikatsverwaltung

Im Einstellungen-Flyout (Zahnradsymbol neben der Endpunkt-URL in der Verbindungsleiste) öffnet der Button **Zertifikatsverwaltung...** einen Dialog, der die OPC UA Zertifikate dieses Clients auflistet und verwaltet. Der Dialog zeigt drei Tabs:

| Tab | Inhalt | Aktionen |
|-----|--------|----------|
| Eigenes Zertifikat | Ihr Client-Zertifikat — das, welches die SPS beim Verbindungsaufbau sieht | Neu erstellen (erzeugt ein frisches Schlüsselpaar; beendet alle aktiven OPC UA Sessions), Entfernen |
| Vertrauenswürdig | Server-Zertifikate, denen dieser Client vertraut | Ablehnen (verschiebt in den Tab „Abgelehnt"), Entfernen |
| Abgelehnt | Server-Zertifikate, die dieser Client abgelehnt hat oder die bei ausgeschaltetem Auto-Accept empfangen wurden | Vertrauen (verschiebt in den Tab „Vertrauenswürdig"), Entfernen |

Jede Zeile zeigt Betreff, Aussteller (bei Server-Zertifikaten), Fingerabdruck, „Gültig ab" und „Gültig bis". Zeile auswählen und die Aktionsbuttons des jeweiligen Tabs verwenden.

Direkt darüber sitzt der Schalter **Serverzertifikate automatisch akzeptieren**:

- **An (Default)** — Jedes neue Server-Zertifikat wird beim ersten Verbindungsaufbau automatisch vertraut. Schnellster, bequemster Pfad; entspricht dem bisherigen Verhalten.
- **Aus** — Neue Server-Zertifikate landen statt im vertrauenswürdigen im abgelehnten Store. Der Dialog muss geöffnet und „Vertrauen" geklickt werden, bevor der nächste Verbindungsaufbau erfolgreich ist. Dieser Modus eignet sich in Netzen, in denen jede SPS explizit freigegeben werden soll.

### Verbindungsstatus-Indikatoren (S7 Nativ)

Beim nativen S7-Comm+-Zugriff auf eine S7-1200 oder S7-1500 zeigt der PLC-Online-Tab drei Live-Indikatoren, die unmittelbar auf das reagieren, was die SPS macht:

- **Tab-Header-Punkt** — ein kleiner farbiger Kreis vor dem Tab-Titel. Hover zeigt einen Tooltip mit der Bedeutung:
  - **Grau** — noch nicht verbunden
  - **Grün** — online, CPU läuft
  - **Gelb** — online, aber CPU nicht in RUN (Stop, Anlauf, Hold, ...), oder die App stellt die Verbindung gerade wieder her
  - **Rot** — SPS nicht erreichbar
- **Wiederverbindungs-Banner** — ein gelber Streifen unter der Verbindungsleiste erscheint mit der Meldung "Wiederverbinde…" solange die App versucht, eine unterbrochene Verbindung wiederherzustellen. Er verschwindet automatisch, sobald die SPS wieder da ist.
- **Ausgegraute Werte** — wird die SPS unerreichbar, werden die Werte in der Beobachtungstabelle auf halbe Deckkraft gedimmt und auf `???` umgestellt, damit klar ist, dass sie nicht mehr aktuell sind. Sobald die SPS zurück ist, ersetzen frische Live-Werte die Platzhalter automatisch. Kein Neustart, kein manuelles Wiederverbinden nötig.

### Beobachtungstabelle (Watch Table)

Die Beobachtungstabelle auf der rechten Seite zeigt Variablen, die Sie zur Überwachung ausgewählt haben.

#### Variablen hinzufügen

- **Doppelklicken** Sie auf einen Variablenknoten im Adressraum-Baum, um ihn zur Beobachtungstabelle hinzuzufügen
- **Klicken Sie auf die +-Schaltfläche** neben einem Knoten, um ihn hinzuzufügen, ohne die Navigation zu verlassen
- Ziehen Sie einen Knoten aus dem Baum und legen Sie ihn in der Beobachtungstabelle ab

Jede Zeile der Beobachtungstabelle zeigt:

| Spalte | Beschreibung |
|--------|--------------|
| Name | Anzeigename der Variable |
| Knoten-ID | OPC UA Knoten-ID (z.B. `ns=3;s="Datenbaustein1"."Drehzahl"`) |
| Datentyp | OPC UA Datentyp (z.B. Int16, Float, Bool) |
| Wert | Aktueller Wert |
| Status | OPC UA Statuscode (Good, Bad, Uncertain) |
| Zeitstempel | Server-Zeitstempel des letzten Wertes |

#### Werte lesen

- Klicken Sie auf **Alle lesen**, um alle Werte in der Beobachtungstabelle mit einer einzelnen Serveranfrage zu aktualisieren
- Klicken Sie auf die **Lesen**-Schaltfläche einer einzelnen Zeile, um nur diese Variable zu aktualisieren

#### Werte schreiben

1. Doppelklicken Sie auf die **Wert**-Zelle einer Zeile in der Beobachtungstabelle
2. Geben Sie den neuen Wert ein
3. Drücken Sie **Enter** oder klicken Sie außerhalb der Zelle zur Bestätigung
4. Der Wert wird sofort in die SPS geschrieben

> **Hinweis:** Schreiboperationen setzen voraus, dass der OPC UA Benutzer Schreibrechte auf der SPS konfiguriert hat.

### Live-Überwachung (Abonnements)

Abonnements ermöglichen es dem OPC UA Server, Wertänderungen automatisch an den TIA Openness Manager zu übertragen, ohne wiederholtes Abfragen.

#### Abonnement starten

1. Stellen Sie das **Abonnement-Intervall** (in Millisekunden) über das Intervallfeld ein — z.B. `500` für Updates alle 500 ms
2. Klicken Sie auf **Abonnieren**, um die Überwachung aller Variablen in der Beobachtungstabelle zu starten
3. Werte aktualisieren sich automatisch, wenn Änderungen auf der SPS auftreten
4. Ein pulsierender Indikator zeigt an, dass ein Abonnement aktiv ist

#### Abonnement stoppen

Klicken Sie auf **Abonnement beenden**, um den Empfang von Updates zu stoppen. Die Werte in der Beobachtungstabelle bleiben auf den zuletzt empfangenen Werten.

#### Variablen-spezifische Abonnements

Um nur bestimmte Variablen zu abonnieren:
1. Wählen Sie die gewünschten Zeilen aus (Strg gedrückt halten für Mehrfachauswahl)
2. Rechtsklick und **Auswahl abonnieren** wählen

### Beobachtungstabellen-Konfigurationen speichern und laden

Beobachtungstabellen-Konfigurationen (die Liste der überwachten Variablen und die Endpunkt-URL) können gespeichert und wiederhergestellt werden:

**Speichern:**
1. Klicken Sie auf **Beobachtungstabelle speichern** (Disketten-Symbol)
2. Wählen Sie einen Dateinamen und Speicherort
3. Die Konfiguration wird als `.opcua-watch` JSON-Datei gespeichert

**Laden:**
1. Klicken Sie auf **Beobachtungstabelle laden** (Ordner-Symbol)
2. Wählen Sie eine zuvor gespeicherte `.opcua-watch`-Datei
3. Die Variablen werden wiederhergestellt; klicken Sie auf **Verbinden** und dann **Alle lesen** oder **Abonnieren**, um die Überwachung fortzusetzen

### Den gesamten Arbeitsbereich speichern und wiederherstellen

Der gesamte OPC UA-Arbeitsbereich — Panel-Layout (welche Tabs aktiv sind), offene Verbindungen (ohne Passwörter) und die Beobachtungstabelle — wird zusätzlich automatisch gespeichert und beim nächsten App-Start wiederhergestellt. Es ist keine Einrichtung nötig; einfach die App schliessen und wieder öffnen.

Jeder geöffnete Verbindungstab bekommt jetzt seinen eigenen gespeicherten Zustand — Beobachtungsliste, Abonnements, Ereignisfilter und Verlaufsbereich — nicht mehr nur der gerade aktive Tab. Beim erneuten Öffnen der App oder beim Laden einer Workspace-Datei kehrt jeder Tab mit genau den Variablen, Alarmen und dem Zeitbereich zurück, mit denen Sie ihn verlassen haben.

Für benannte Snapshots, die Sie an Kollegen weitergeben oder für eine bestimmte Inbetriebnahme aufheben möchten, nutzen Sie das **Arbeitsbereich**-Menü in der Dock-Toolbar oben im OPC UA-Tab:

- **Arbeitsbereich speichern unter…** schreibt den aktuellen Zustand in eine `.opcua-workspace`-Datei Ihrer Wahl. Passwörter werden nie in die Datei geschrieben — Bediener müssen sie beim erneuten Verbinden neu eingeben.
- **Arbeitsbereich laden…** öffnet eine beliebige frühere `.opcua-workspace`-Datei und wendet sie an. Der Picker akzeptiert auch die älteren `.json`-Beobachtungstabellen-Dateien aus dem Disketten-Symbol, sodass Legacy-Arbeitsbereiche weiterhin geladen werden.
- **Arbeitsbereich zurücksetzen** löscht den automatisch gespeicherten Snapshot und die Beobachtungsliste der aktiven Verbindung nach einer Bestätigungsabfrage — nützlich vor einer Bildschirmpräsentation oder wenn ein veralteter Arbeitsbereich immer wieder veralteten Zustand wiederherstellt.

Um einen vertraulichen Endpoint komplett aus dem Arbeitsbereich herauszuhalten, öffnen Sie den Settings-Flyout der Verbindung (Zahnrad-Symbol in der verbundenen Verbindungsleiste) und aktivieren Sie **Diese Verbindung nicht im Arbeitsbereich speichern**. Solange der Toggle aktiv ist, bleiben Endpoint, Beobachtungsliste, Abonnements, Ereignisfilter und Verlaufsbereich dieses Tabs aus der Workspace-Datei und dem automatischen Wiederherstellen heraus. Schalten Sie den Toggle wieder aus, sobald der Tab wieder gespeichert werden soll.

Der gespeicherte Arbeitsbereich merkt sich auch, wie Sie die Bereiche angeordnet haben — ob die Beobachtungstabelle unten oder rechts sitzt, ob die Typ-Definitionen angeheftet sind, wo Sie die Trenner platziert haben und welche Registerkarten aktiv waren. Beim Laden des Arbeitsbereichs wird jeder Bereich genau dorthin zurückgesetzt, wo Sie ihn verlassen haben.

### Beobachtungstabellen-Daten exportieren

Exportieren Sie die aktuellen Beobachtungstabellen-Werte für Dokumentation oder weitere Analyse:

**CSV-Export:**
1. Klicken Sie auf **Exportieren → CSV**
2. Wählen Sie eine Zieldatei
3. Eine CSV-Datei wird mit allen Zeilen inklusive Name, Knoten-ID, Datentyp, Wert, Status und Zeitstempel-Spalten erstellt

**JSON-Export:**
1. Klicken Sie auf **Exportieren → JSON**
2. Wählen Sie eine Zieldatei
3. Eine strukturierte JSON-Datei wird mit vollständigen Metadaten für jede Variable erstellt

### OPC UA MCP-Tools (KI-Integration)

Wenn der MCP-Server läuft, haben KI-Assistenten Zugriff auf OPC UA und Canvas Tools:

| Tool | `what` | Beschreibung |
|------|--------|--------------|
| `opcua` | `connect` | Verbindung zu einem OPC UA Endpunkt mit angegebener Authentifizierung herstellen |
| `opcua` | `disconnect` | Verbindung zum aktuellen OPC UA Server trennen |
| `opcua` | `browse` | Adressraum ab einem bestimmten Knoten durchsuchen |
| `opcua` | `read` | Aktuellen Wert einer oder mehrerer Variablen anhand der Knoten-ID lesen |
| `opcua` | `read_complex` | Strukturierte/komplexe Datentypen lesen (z.B. UDTs, Arrays) |
| `opcua` | `write` | Einen Wert anhand der Knoten-ID in eine Variable schreiben |
| `opcua` | `write_complex` | Einzelne Felder eines Datenbausteins schreiben (Read-Modify-Write) |
| `opcua` | `get_types` | Datentypendefinitionen vom Server abrufen |
| `opcua` | `subscribe` | Überwachte Element-Abonnements für einen oder mehrere Knoten erstellen |
| `canvas` | `bind_opcua` | OPC-UA-Werte pollen und das Canvas-Dashboard in Echtzeit aktualisieren |
| `canvas` | `unbind_opcua` | Alle Canvas OPC UA Lese-Bindings stoppen |
| `canvas` | `bind_opcua_write` | Canvas-Button-Klicks und Slider-Änderungen mit OPC-UA-Schreiboperationen verbinden |
| `canvas` | `unbind_opcua_write` | Alle Canvas OPC UA Schreib-Bindings stoppen |

**Beispiele für KI-Chat-Verwendung:**

Fragen Sie den KI-Assistenten im Chat-Panel z.B.:
- "Verbinde dich anonym mit der SPS unter 192.168.0.10 und durchsuche die Datenbausteine"
- "Lese den Wert von Knoten `ns=3;s="Tank1"."Fuellstand"` und sage mir, ob er über 80% liegt"
- "Abonniere alle Float-Variablen im 'Produktion'-Datenbaustein mit einem 1-Sekunden-Intervall"
- "Schreibe den Wert 1500 in `ns=3;s="Foerderband"."Sollgeschwindigkeit"`"

### Hinweise

- Die OPC UA Konnektivität setzt nicht voraus, dass TIA Portal geöffnet oder verbunden ist
- Die SPS muss OPC UA in ihrer Hardware-Konfiguration aktiviert haben (Allgemein → OPC UA → Server)
- Bei S7-1500 SPSen: Stellen Sie sicher, dass der OPC UA Server aktiviert ist und die relevanten PLC-Tags als "Aus HMI/OPC UA zugreifbar" markiert sind
- Zertifikatsbasierte Authentifizierung erfordert den Austausch von Zertifikaten zwischen Client und SPS

### 9c. AI Canvas mit OPC UA Live-Daten

Das AI Canvas kann interaktive Dashboards anzeigen, die mit Live-OPC-UA-Daten verbunden sind. Die KI erstellt visuelle Dashboards (Anzeigen, Buttons, Slider, Animationen) mit `canvas` (what: `eval`), und OPC-UA-Werte werden für Echtzeit-Updates an das Dashboard gebunden.

#### Funktionsweise

1. **Die KI erstellt ein Dashboard** mit `canvas` (what: `eval`) (HTML/CSS/JavaScript im Canvas-WebView)
2. **Lese-Bindings** (`canvas` (what: `bind_opcua`)) pollen OPC-UA-Werte und aktualisieren das Dashboard über `window.__tiaUpdateDashboard()`
3. **Schreib-Bindings** (`canvas` (what: `bind_opcua_write`)) verbinden Canvas-Button-Klicks und Slider-Änderungen mit OPC-UA-Schreiboperationen
4. Alle Updates erfolgen automatisch — kein manuelles Polling oder Subscription-Setup nötig

#### Canvas OPC UA Tools

| Tool | `what` | Richtung | Beschreibung |
|------|--------|----------|-------------|
| `canvas` | `bind_opcua` | SPS → Canvas | Pollt OPC-UA-Werte und aktualisiert das Dashboard in Echtzeit |
| `canvas` | `unbind_opcua` | — | Stoppt alle Lese-Bindings |
| `canvas` | `bind_opcua_write` | Canvas → SPS | Verbindet Button-Klicks und Slider-Änderungen mit OPC-UA-Schreiboperationen |
| `canvas` | `unbind_opcua_write` | — | Stoppt alle Schreib-Bindings |
| `opcua` | `write_complex` | Canvas → SPS | Schreibt einzelne Felder eines Datenbausteins (Read-Modify-Write) |

#### Beispiel: Prozesssteuerungs-Dashboard

Bitten Sie die KI, ein interaktives Dashboard zu erstellen:

> "Erstelle ein Prozesssteuerungs-Dashboard auf dem Canvas mit Start/Stop-Buttons, einem Drehzahl-Slider (0-3000 RPM) und Live-Anzeigen für Speed, Temperature, Pressure und FlowRate. Verbinde es mit dem Datenbaustein `Data_block_1` über OPC UA."

Die KI wird:
1. Das visuelle Dashboard mit `canvas` (what: `eval`) erstellen
2. Lese-Bindings mit `canvas` (what: `bind_opcua`) für die Live-Anzeige einrichten
3. Schreib-Bindings mit `canvas` (what: `bind_opcua_write`) einrichten, damit Buttons und Slider die SPS steuern

#### Dashboards mit OPC UA Bindings speichern und laden

Canvas-Dashboards können als JSONL-Dateien gespeichert und später geladen werden. **OPC-UA-Binding-Konfigurationen werden in der gespeicherten Datei eingeschlossen.**

**Speichern:**
1. Klicken Sie auf die **Speichern**-Schaltfläche in der Canvas-Toolbar
2. Die JSONL-Datei enthält das Dashboard-Layout, JavaScript und die OPC-UA-Binding-Konfiguration

**Laden:**
1. Verbinden Sie sich zuerst mit dem OPC-UA-Server
2. Klicken Sie auf die **Laden**-Schaltfläche in der Canvas-Toolbar und wählen Sie die gespeicherte JSONL-Datei
3. Das Dashboard wird wiederhergestellt und OPC-UA-Bindings werden automatisch neu angewendet
4. Live-Daten fließen sofort (wenn OPC UA verbunden ist)

> **Hinweis:** OPC-UA-Bindings bleiben auch beim Andocken/Abdocken des Canvas innerhalb derselben Sitzung erhalten.

#### Wichtige Hinweise

- Eine aktive OPC-UA-Verbindung ist erforderlich, bevor Bindings Daten liefern können
- `canvas` (what: `bind_opcua`) verwendet Polling (keine OPC-UA-Subscriptions) — das ist stabiler und vermeidet eine Überlastung des OPC-UA-Servers
- Alle Werte von OPC UA kommen als **Strings** im JavaScript-Callback an (verwenden Sie `parseFloat()` für Zahlen, vergleichen Sie mit `"True"`/`"False"` für Booleans)
- Die Canvas-Schaltfläche **Reset** stoppt alle OPC-UA-Bindings (Lesen und Schreiben)

---

## 9c. SCL Unit Testing (Enterprise)

Integriertes Unit-Test-Framework für SCL-Bausteine. Schreiben, ausführen und auswerten von Tests gegen eine laufende PLCSIM Advanced Instanz direkt in der App.

**Voraussetzungen:**
- Enterprise-Lizenz
- PLCSIM Advanced V3.0+ installiert (separate Siemens-Lizenz)
- Ein TIA-Projekt mit mindestens einer geöffneten SPS

### Unit-Testing-Workspace öffnen

1. Klicken Sie auf **SCL Unit Testing** in der linken Seitenleiste (oder drücken Sie `Strg+5`)
2. Der Workspace besteht aus vier Dock-Panels:
   - **Links (Analyse-Tools + Test Explorer):** Interface, Boundary Values, Dependencies, Test Explorer (als Tabs)
   - **Mitte (Document Dock):** Test-Suite-Editoren (JSON, Visual, SCL Modi)
   - **Rechts (Ergebnisse):** Test-Results-Panel — Live-Progress und Assertion-Details
   - **Toolbar:** SPS- und Block-Auswahl, Analyze, New Suite, Open Suite, Run/Stop

### Test Explorer

Der Test Explorer scannt automatisch den Ordner `{WorkingDirectory}/.tia-tests/` und zeigt jede `.json`-Datei als Suite-Knoten mit ihren Test-Cases als Kinder.

**Status-Icons (beim App-Start aus SQLite geladen):**
- ✓ **Bestanden** — grünes Häkchen, Test erfolgreich im letzten Lauf
- ✗ **Fehlgeschlagen** — rotes Kreuz, Test fehlgeschlagen
- ⚠ **Fehler** — orange Warnung, Test hatte einen Fehler (Exception, Timeout, S7-Fehler)
- ⊘ **Übersprungen** — grauer durchgestrichener Kreis, Test wurde aus dem letzten Lauf herausgefiltert (z.B. via „Run Single")
- ○ **Nicht ausgeführt** — grauer leerer Kreis, kein gespeichertes Ergebnis

**Interaktionen:**

| Aktion | Ergebnis |
|--------|----------|
| Doppelklick auf Suite | Öffnet die Suite als Dokument-Tab im mittleren Dock |
| Rechtsklick auf Suite → Run Suite | Führt nur diese Suite aus |
| Rechtsklick auf Suite → Open | Gleich wie Doppelklick |
| Rechtsklick auf Test Case → Run Test | Führt nur diesen einzelnen Case aus (andere werden als Skipped markiert) |
| Suite auswählen + **Run Selected** Button | Führt diese Suite aus |
| Test Case auswählen + **Run Selected** Button | Führt nur diesen Case aus |
| **Run All** Button | Führt alle sichtbaren Suites sequentiell aus |
| In das Suchfeld tippen | Filtert Suites nach Namen (Suite- + Test-Case-Namen, Groß-/Kleinschreibung wird ignoriert) |
| `✗ Fehler` Button einschalten | Zeigt nur Suites mit Fail/Error-Cases (Button wird rot wenn aktiv) |

### Live-Progress während eines Laufs

Während ein Test läuft zeigt der Workspace:

- **Statusbar:** Aktuelle Phase (z.B. „Creating PLCSIM instance", „Compiling PLC", „Running: TestCase_1")
- **Test Explorer:** Status-Icons werden live pro Test-Case aktualisiert (Pass/Fail erscheinen während der Lauf läuft)
- **Ergebnis-Panel:** Test-Case-Liste füllt sich inkrementell mit jedem abgeschlossenen Test
- **Stop-Button:** Bricht den laufenden Run am nächsten sicheren Punkt ab (S7-Verbindung und PLCSIM-Instanz werden immer aufgeräumt)

### Ergebnis-Panel

Nach einem Lauf zeigt das Ergebnis-Panel:

- **Zusammenfassung:** Gesamt Bestanden/Fehlgeschlagen/Fehler-Zähler + Gesamtdauer
- **Test-Case-Liste:** Jeder Case mit Status-Icon, Name und Dauer
- **Detail-Grid (bei Case-Auswahl):** Alle Assertions mit Variable, Operator, Erwartet, Tatsächlich, ✓/✗
- **Variablenverlauf (bei Case-Auswahl):** Ein Diagramm zeigt, wie sich jede Watch-Variable Zyklus für Zyklus während des Laufs verändert hat. Links listet eine Checkbox-Legende die Variablen — Haken raus nimmt die Linie aus dem Chart. Numerische Typen (BOOL/INT/REAL/TIME/…) werden als Linie gezeichnet; nicht-numerische Typen erscheinen in der Legende, werden aber nicht gezeichnet. Beim Hovern rastet ein Fadenkreuz auf den nächsten Datenpunkt ein und zeigt Variablenname, Zyklus und Wert im Titel

Um den Verlauf zu befüllen, füge ein `"watch": ["Var1", "Var2"]`-Array zu einem Testfall in der Suite-JSON hinzu und setze `"cycles"` größer als 1. Das Timeline-Sampling ist pro Testfall auf 100.000 Zyklen gedeckelt.

Test-Ergebnisse werden in `%LocalAppData%\TiaOpennessManager\db\test_results.db` persistiert — sie überleben App-Neustarts und erscheinen automatisch wieder im Test Explorer.

### Baustein-Analyse (vor dem Testen)

1. SPS aus dem Dropdown wählen
2. Baustein aus dem Dropdown wählen
3. **Analyze** klicken
4. Die drei Analyse-Tools werden gleichzeitig aktualisiert (ein TIA-Export, drei Analysen):
   - **Interface:** Alle Baustein-Parameter (Input, Output, InOut, Static, Temp) mit Typen und Defaultwerten
   - **Boundary Values:** Automatisch generierte Min/Max/Null/Eins-Werte pro Parametertyp
   - **Dependencies:** Aufgerufene Bausteine, referenzierte DBs, referenzierte UDTs

### Neue Test-Suite erstellen

1. Zuerst einen Baustein analysieren (siehe oben), damit das Interface bekannt ist
2. **New Suite** klicken — eine neue Suite-JSON wird mit dem Baustein-Namen erzeugt
3. Das Dokument öffnet sich mit dem Default-JSON-Skeleton (leeres `testCases`-Array)
4. In den **Visual**-Editor wechseln um Test-Cases per Drag-and-Drop zu bauen, oder direkt JSON bearbeiten
5. **Save** klicken (`Strg+S`) — die Suite wird nach `.tia-tests/{SuiteName}.json` geschrieben

### Vorhandene Suite öffnen

- **Aus dem Test Explorer:** Doppelklick auf die Suite im Baum
- **Aus dem Menü:** **Open Suite** Button in der Toolbar → Datei-Auswahl

### Wo werden Test-Suiten gespeichert?

Test-Suiten liegen in einem versteckten Ordner namens `.tia-tests` direkt neben Ihrer TIA-Projektdatei (`*.ap21`, `*.ap20`, …). Ein Klick auf **Open Suite** öffnet den Dialog in diesem Ordner; der AI-Assistent schreibt in denselben Ordner. Wenn noch kein TIA-Projekt geladen ist, zeigt der Test Explorer "Kein TIA-Projekt verbunden" und **Open Suite** ist deaktiviert — bitte erst ein Projekt verbinden.

Die KI kann diese Test-Suite-Dateien direkt aus dem Chat heraus lesen, auflisten und bearbeiten.

### Tests ausführen

1. Sicherstellen dass PLCSIM Advanced V3.0+ installiert ist
2. Suite öffnen (via Test Explorer oder Open Suite Button)
3. **▶ Run** in der Toolbar klicken, oder eine Kontextmenü-Aktion im Test Explorer verwenden
4. Den Live-Progress in der Statusbar und im Ergebnis-Panel verfolgen
5. Nach dem Lauf aktualisieren sich die Status-Icons im Test Explorer und Ergebnisse werden in SQLite gespeichert

Der Runner erledigt automatisch:
- Erstellt eine PLCSIM Advanced Instanz (Name konfigurierbar in der Suite-JSON)
- Schaltet sie ein und kompiliert das aktuelle SPS-Projekt
- Verbindet einen S7-Client mit der Instanz
- Schreibt die Test-Inputs, wartet die konfigurierten Zyklen, liest die Outputs, evaluiert die Assertions
- Räumt die S7-Verbindung auf und deregistriert die Instanz

### Transport auswählen

Der **Verbindungseinstellungen**-Dialog lässt Sie wählen, wie Test-Reads und -Writes zwischen App und PLC übertragen werden:

- **PLCSim Advanced** — Direkter Zugriff über die Siemens-PLCSim-API, schneller und ohne aktive S7-Session. Ideal für reine Simulator-Tests.
- **S7 Comm+** — Nutzt den S7-Communication-Treiber über TCP/IP. Wählen Sie diese Option für Tests gegen echte Hardware oder gegen PLCSim über den virtuellen Ethernet-Adapter mit Benutzerauthentifizierung.

Beide Transports haben eine eigene Konfigurations-Sektion im selben Dialog, sodass jede Suite unabhängig konfiguriert werden kann. Bei S7 Comm+ hat die Suite eigene IP, Port, Rack, Slot, TLS-Einstellung, Benutzername und Passwort — kein Cross-Tab-Lookup aus der PLC-Online-Ansicht.

### Simulation-Arbeitsbereich

Innerhalb des SCL-Unit-Testing-Tabs schaltet ein **Simulation**-Sub-Mode-Umschalter oben zwischen der Test-Suites-Ansicht und einer dedizierten **Simulation**-Ansicht für die PLCSim-Advanced-Instanzverwaltung um. Die Simulation-Ansicht zeigt:

- API-Version, Online-Zugriffsmodus (PLCSim / TCP/IP einzeln / TCP/IP mehrfach), Strict-Motion-Timing-Toggle und Runtime-Manager-Port.
- Eine **Virtueller Adapter**-Zeile mit dauerhaftem Status des Siemens PLCSIM Virtual Ethernet Adapters (Bereit / APIPA / Deaktiviert / Nicht installiert / Keine IPv4), seiner IPv4-Adresse und einem Refresh-Button. Wenn der Adapter im 169.254.x.y-APIPA-Bereich hängt, werden Downloads unzuverlässig — weisen Sie ihm in den Windows-Netzwerkeinstellungen eine statische IPv4-Adresse zu.
- Jede registrierte PLCSim-Instanz mit Inline-Buttons: Einschalten, Run, Stop, Memory-Reset, Ausschalten, Einstellungen, Netzwerk, Löschen. Jede Zeile zeigt die konfigurierte IP-Adresse; hat die Instanz mehrere Schnittstellen mit einer IP, werden diese als `X1: 192.168.0.1, X2: 10.0.0.5` aufgelistet.
- Einen **Neue Instanz**-Button, der nach Name und CPU-Typ fragt.
- Ein **Tag-Browser**-Panel, das sich mit jeder Instanz verbinden und alle Tags des laufenden Programms anzeigen kann — filterbar nach Namensuche, Bereich (Eingang / Ausgang / Merker / Datenbaustein) und Datentyp. Auto-Refresh kann für Live-Wertebeobachtung aktiviert werden. Jeder schreibbare Tag hat einen **Bleistift-Button**, der einen typ-spezifischen Write-Dialog öffnet (Schalter für Bool, numerische Eingabe mit passendem Bereich für Ganzzahlen und Gleitkomma, Ein-Zeichen-Feld für Char/WChar). String-Tags sind read-only.
- Eine **Gespeicherte Instanzen**-Sektion am unteren Rand, die jede PLCSim-Advanced-Instanz auflistet, die auf der virtuellen SIMATIC Memory Card persistiert ist. Klicken Sie **Laden**, um eine solche Instanz erneut zu registrieren und fortzuführen — PLCSim übernimmt automatisch den gespeicherten CPU-Typ, das E/A-Abbild und das Programm. Klicken Sie **Löschen** (mit Bestätigung), um den persistierten Ordner zu entfernen.

Der Sub-Mode wird zwischen Sitzungen gemerkt, und der Wechsel behält alle geöffneten Suite-Dokumente.

### PLCSIM-Vorbereitungsmodus

Der **Verbindungseinstellungen**-Dialog hat eine Auswahl für den Vorbereitungsmodus (innerhalb der PLCSim-Sektion). Dieser steuert, wie der Runner das Projekt in die PLCSIM-Instanz bekommt, bevor der Testlauf startet:

- **Ich lade selbst (empfohlen)** — Der Runner erwartet, dass Sie die PLCSIM-Instanz bereits manuell via TIA Portal gestartet und das Projekt geladen haben. Compile und Download werden übersprungen, der Runner verbindet sich direkt und führt die Tests aus. Schnellste Option für wiederholte Läufe am selben Projekt.
- **Automatischer TCP-Download** — Der Runner kompiliert das Projekt, startet eine frische PLCSIM-Instanz und lädt es via TCP über den PLCSIM Virtual Adapter. Keine manuelle TIA-Portal-Interaktion nötig — einfach Run klicken.

### Test-Läufe gegen geschützte Projekte

Wenn Ihr TIA-Projekt **„Schutz vertraulicher PLC-Konfigurationsdaten"** aktiviert hat, erscheint im Automatischer-TCP-Download-Modus im Verbindungseinstellungen-Dialog ein zusätzliches Passwortfeld:

1. **Verbindungseinstellungen…** öffnen
2. Unter PLCSIM-Vorbereitung **Automatischer TCP-Download** auswählen
3. Das Master-Secret-Passwort des Projekts eingeben
4. Optional: Haken bei **Passwort merken** setzen, um es im Windows Credential Manager zu speichern — dann holt sich der Runner das Passwort bei jedem Folge-Lauf automatisch, ohne erneut nachzufragen. Haken weglassen, wenn Sie das Passwort nur einmal verwenden möchten und es nach dem Lauf vergessen werden soll
5. **OK** klicken, dann **▶ Run**

Beim nächsten Öffnen des Dialogs erscheint der Hinweis *„Für diesen Benutzer ist ein Passwort gespeichert"*, wenn Sie es gespeichert haben. Lassen Sie das Passwortfeld leer, um das gespeicherte Passwort zu behalten. Haken bei **Passwort merken** entfernen und OK klicken löscht den gespeicherten Eintrag.

Das Passwort wird nie in die Suite-Datei, in Logs oder Einstellungs-Dateien geschrieben. Es lebt ausschliesslich im Windows Credential Manager unter dem Servicenamen `com.tiaopennessmanager` und wird vom Dialog zum Runner über einen benutzergebundenen DPAPI-Kanal übertragen, sodass ein anderer Windows-Benutzer es nicht lesen kann.

### Suites und Testfälle verwalten

- **Rechtsklick auf eine Test-Suite** im Test Explorer, um sie umzubenennen oder zu löschen. Beim Löschen wird auch die Testlauf-Historie dieser Suite entfernt.
- **Rechtsklick auf einen Testfall**, um Name oder Beschreibung zu ändern, ihn zu duplizieren, zu löschen oder in der Liste nach oben bzw. unten zu verschieben.
- Der **Verbindungseinstellungen…**-Button in der Toolbar erlaubt die Konfiguration von Transport, PLCSim-Instanz (aus der Simulation-Registry wählbar oder frei eingebbar), IP-Adresse, Zyklus-Wartezeit, S7-Comm+-Ziel (IP, Port, Rack, Slot, TLS, Benutzer, Passwort) und Auto-Connect für die aktive Suite. Setzen Sie den Haken bei *Als Default speichern*, damit neu erstellte PLCSim-Suites dieselben Werte übernehmen. Der Dialog hat einen **Verwalten…**-Button in der PLCSim-Sektion, der ohne Verlust der aktuellen Eingaben in den Simulation-Sub-Mode springt, um Instanzen anzulegen oder anzupassen.
- **Verbindungseinstellungen werden pro Suite gespeichert.** Ein Klick auf **OK** schreibt Ihre Auswahl — Transport, Instanzname, IP, S7-Verbindungsdaten und alle weiteren Felder — zurück in die Suite-Datei. Beim nächsten Öffnen zeigt der Dialog genau die zuletzt gewählten Werte, statt auf Defaults zurückzuspringen. Passwörter bleiben weiterhin im Windows Credential Manager — die Suite-Datei speichert nur eine Referenz, nie ein Klartext-Passwort.
- Vor jedem Lauf prüft der Manager, dass jeder Variablenname in Ihrer Suite exakt dem Baustein-Interface entspricht — inklusive Gross-/Kleinschreibung. Werden Abweichungen gefunden, zeigt ein Warndialog die Korrekturvorschläge an; Sie können den Lauf nach Bestätigung trotzdem starten.
- Schlägt ein Testfall fehl, wird die betroffene Variable direkt im generierten SCL-Code **rot unterstrichen**, die Fehlermeldung erscheint als Tooltip. **Doppelklicken Sie einen fehlgeschlagenen Testfall** im Ergebnis-Panel, um direkt zu der Variable im Suite-Editor zu springen.
- Wird eine Suite-Datei extern geändert — oder durch eine der Rename- / Delete- / Edit-Aktionen oben — lädt der offene Editor sie automatisch neu. Sind jedoch noch ungespeicherte Änderungen vorhanden, bleiben diese erhalten.

### Fehlerbehebung

- **Status-Icons aktualisieren sich nicht nach einem Lauf:** Prüfen ob der Suite-Dateipfad korrekt ist (absoluter Pfad unter `.tia-tests/`). Neue ungespeicherte Suites bekommen pro Klick einen eindeutigen Pfad.
- **„Run" Button ist ausgegraut:** Ein TIA-Projekt muss geöffnet sein, und das aktive Suite-Dokument muss valides JSON sein.
- **Test Explorer ist leer:** Das Arbeitsverzeichnis hat noch keinen `.tia-tests/` Ordner. **New Suite** klicken um die erste Suite zu erstellen — der Ordner wird automatisch angelegt.
- **PLCSIM-Fehler:** Prüfen ob PLCSIM Advanced V3.0+ installiert und lizenziert ist. Die genaue Version wird zur Laufzeit automatisch erkannt.
- **TLS-Verkehr für den Support aufzeichnen (fortgeschritten):** Wenn der Support einen Wireshark-Mitschnitt des S7-Comm+-Handshakes braucht, die Umgebungsvariable `SSLKEYLOGFILE` vor dem Start der App auf einen absoluten Dateipfad setzen — z.B. `setx SSLKEYLOGFILE "C:\Temp\s7-keys.log"` — und anschliessend neu starten. In Wireshark die TLS-Einstellung *(Pre)-Master-Secret log filename* auf dieselbe Datei zeigen lassen. Solange die Variable gesetzt ist, wird bei jeder Verbindung eine Warnung ins App-Log geschrieben, damit sie nicht vergessen wird. Im Normalbetrieb die Variable leer lassen.

### KI-geschriebene Test-Suites (Enterprise)

Der AI-Chat kann komplette SCL-Unit-Test-Suites für Sie entwerfen, verfeinern und (optional) ausführen. Benötigt eine Enterprise-Lizenz.

#### Skill „Write Unit Tests" (Hauptchat)

1. **AI Chat** öffnen und im Skill-Picker den Skill **Write Unit Tests** auswählen (🧪-Icon) — oder einfach fragen: *„schreib Unit-Tests für FB_MotorControl"*
2. Der Assistent liest das Baustein-Interface, berechnet Grenzwerte, plant Testfälle und fasst den Plan im Chat zusammen — ohne riesige JSON-Blöcke
3. Wenn er die Suite schreiben möchte, erscheint inline ein **Erlauben**- / **Ablehnen**-Prompt. Erlauben speichert die Suite nach `.tia-tests/`
4. Wenn Sie den Assistenten gebeten haben, die Suite auch auszuführen, erscheint ein zweiter Approval-Prompt für den Run selbst. Die Ergebnisse kommen als Pass/Fail-Zusammenfassung zurück in den Chat, und der Assistent bietet an, fehlgeschlagene Testfälle nachzubessern
5. Der Test Explorer übernimmt die neue Suite automatisch — öffnen, im Visual- oder JSON-Editor prüfen und nach Wunsch selbst laufen lassen
6. Nach dem Anlegen können Sie auch direkt *„öffne die Suite"* schreiben — die Suite wird als neuer Tab im Unit-Testing-Editor geöffnet, ohne dass Sie zum Test Explorer wechseln müssen

#### Inline-Chat im Suite-Editor (Strg+I)

Während eine Test-Suite im JSON-Editor geöffnet ist:

1. Den Cursor nahe des zu ändernden Testfalls platzieren (oder einen Bereich markieren)
2. **`Strg+I`** drücken — oberhalb des Editors erscheint ein kleines Prompt-Feld
3. Eingeben, was geändert werden soll, zum Beispiel:
   - *„füg einen Overflow-Test für Counter_Value hinzu"*
   - *„mach daraus einen parametrisierten Test mit fünf Sollwerten"*
   - *„setz die Toleranz aller REAL-Assertions auf 0.01"*
4. Der Assistent streamt das aktualisierte JSON, und im Editor erscheint ein Diff-Overlay
5. **Akzeptieren** übernimmt die Änderung (die Datei wird gespeichert und der Test Explorer lädt neu); **Ablehnen** verwirft sie

Der Inline-Chat nutzt dasselbe Baustein-Interface, mit dem die Suite geöffnet wurde, sodass Variablennamen und Typen gegen den echten Baustein geprüft werden — Abweichungen fallen vor dem Speichern auf.

#### KI-Badge im Test Explorer und Visual-Editor

Von der KI erstellte TestCases tragen ein kleines **AI**-Tag, das erscheint:
- neben dem Testfall-Namen im **Visual-Editor**
- im **Test Explorer**-Baum

Überprüfen Sie KI-geschriebene Testfälle wie einen Pull Request von einer Kollegin — jede Assertion lesen, erwartete Werte plausibilisieren, erst am Simulator laufen lassen und dann auf echter Hardware.

#### Safety-Schutz (F-CPU)

Das KI-gestützte Schreiben von Tests ist für Safety-Bausteine abgesichert:

- **Tests erstellen** — Der Assistent verweigert das Schreiben von Tests für einen F-CPU-Baustein ohne eine explizite Bestätigung im Gespräch. Auch die darunterliegenden Tools lehnen den Schreibvorgang ohne diese Bestätigung ab
- **Tests ausführen** — Der Assistent **kann keine Tests** gegen Safety-Bausteine laufen lassen. Punkt. Kein Override. Safety-Baustein-Verifikation erfordert eine zertifizierte Methodik (TÜV/CE), keinen KI-Run. Wenn Sie einen Test gegen einen Safety-Baustein laufen lassen wollen, starten Sie den Run selbst aus dem Test Explorer

#### Lizenzierung

Der Skill „Write Unit Tests" und die Unit-Test-MCP-Tools sind Enterprise-only. In den Tiers Basic oder Professional zeigt der Skill vor jedem KI-Call eine „Enterprise erforderlich"-Meldung.

---

## 10. Projektbibliothek-Verwaltung

Die Projektbibliothek speichert wiederverwendbare Elemente (Master Copies und Typen), die im gesamten Projekt geteilt werden können.

### Verfügbare Operationen

#### 1. In Bibliothek kopieren (Master Copy erstellen)

1. Rechtsklick auf einen Baustein im SPS-Baum
2. **"In Bibliothek kopieren"** auswählen
3. Erstellt eine Master Copy des ausgewählten Bausteins in der Projektbibliothek
4. Die Kopie kann später in jeder SPS instanziiert werden

#### 2. Aus Bibliothek instanziieren

1. Rechtsklick auf eine Master Copy im Bibliotheksbaum
2. **"Im Projekt instanziieren"** auswählen
3. Erstellt einen neuen Baustein in der SPS aus der Master Copy
4. Die ursprüngliche Master Copy bleibt unverändert

#### 3. Typversion exportieren

1. Rechtsklick auf einen Bibliothekstyp
2. **"Typversion exportieren"** auswählen
3. Exportiert die neueste freigegebene Version in eine XML-Datei

**Hinweis:** Nur freigegebene Versionen können exportiert werden; InWork-Versionen können nicht exportiert werden.

#### 4. Neuer Ordner

1. Rechtsklick auf Master Copies-Ordner, Typen-Ordner oder einen beliebigen Bibliotheks-Unterordner
2. **"Neuer Ordner"** auswählen
3. Erstellt einen neuen Organisationsordner

#### 5. Umbenennen

1. Rechtsklick auf eine Master Copy, einen Bibliothekstyp oder Ordner
2. **"Umbenennen"** auswählen
3. Ermöglicht das Ändern des Namens des ausgewählten Elements

#### 6. Löschen

1. Rechtsklick auf ein Bibliothekselement
2. **"Löschen"** auswählen
3. Entfernt das Element dauerhaft aus der Bibliothek (mit Bestätigung)

#### 7. Bibliothek aufräumen

1. Rechtsklick auf den "Projektbibliothek"-Wurzelknoten
2. **"Bibliothek aufräumen"** auswählen
3. Entfernt ungenutzte Typen und Versionen, um die Bibliothek organisiert zu halten

### Bekannte Einschränkungen

- Master Copies können nicht als XML-Dateien exportiert werden (Siemens API-Einschränkung)
- Nur freigegebene Bibliothekstyp-Versionen können exportiert werden (keine InWork-Versionen)

### MCP-Integration (KI-Assistenten)

Die folgenden MCP-Tools stehen für KI-Assistenten zur Verfügung:

- `library_create_master_copy` - Master Copy aus Baustein erstellen
- `library_instantiate` - Master Copy in SPS instanziieren
- `library_delete_item` - Bibliothekselement löschen
- `library_rename_item` - Bibliothekselement umbenennen
- `library_export_type` - Typversion exportieren
- `library_create_folder` - Neuen Ordner erstellen
- `library_cleanup` - Ungenutzte Typen aufräumen

---

## 11. Hardware Tab

Der Hardware Tab bietet eine umfassende Übersicht über alle Geräte in Ihrem TIA Portal Projekt mit der Möglichkeit, Netzwerkkonfigurationen anzuzeigen und zu bearbeiten.

### Geräteliste

Der Tab zeigt eine Tabelle mit allen Hardware-Geräten:

| Spalte | Beschreibung | Editierbar |
|--------|--------------|------------|
| Device | Gerätename aus dem Projekt | Nein |
| Device Type | SPS, HMI, Antrieb, Switch, etc. | Nein |
| PROFINET Name | PROFINET-Gerätename | Ja |
| Article Number | Siemens-Bestellnummer | Nein |
| Firmware Version | Aktuelle Firmware-Version | Nein |
| IP Address 1-4 | Bis zu 4 IP-Adressen pro Gerät | Ja |
| Input Addresses | E/A-Eingangsadressbereich | Ja |
| Output Addresses | E/A-Ausgangsadressbereich | Ja |

### Aktionen

**Refresh Hardware:**
Lädt die Geräteliste aus dem TIA Portal Projekt neu.

**Export to CSV:**
Exportiert die komplette Hardware-Liste als CSV-Datei für Dokumentation oder Weiterverarbeitung.

**Save Changes:**
Speichert geänderte PROFINET-Namen und IP-Adressen zurück ins TIA Portal Projekt.

### Unterstützte Gerätetypen

- S7-1200/1500 SPSen
- WinCC Unified HMI-Panels
- WinCC Comfort-Panels
- SINAMICS-Antriebe
- SCALANCE-Switches
- ET 200 dezentrale Peripherie
- Andere PROFINET-Geräte

### Hinweise

- Änderungen an PROFINET-Namen und IP-Adressen erfordern anschließendes Speichern des Projekts
- Einige Felder können je nach Gerätetyp schreibgeschützt sein
- WinCC Unified-Geräte werden vollständig unterstützt

---

## 12. Find Unused Blocks

### Funktion

Find Unused Blocks analysiert Ihr Projekt und findet Bausteine, die nirgends aufgerufen werden.

### Verwendung

1. Öffnen Sie ein Projekt
2. Klicken Sie auf **Find Unused Blocks** in der Toolbar
3. Die Analyse startet automatisch:
   - Phase 1: Blöcke sammeln
   - Phase 2: Nach XML exportieren
   - Phase 3: Call-Graph aufbauen
   - Phase 4: Unerreichbare Blöcke finden

### Ergebnis-Fenster

Ergebnisse sind in 8 Tabs organisiert:

**Standard-Blöcke:**
| Tab | Inhalt |
|-----|--------|
| Functions (FC/FB) | Ungenutzte Funktionen und Funktionsbausteine |
| Data Blocks (DB) | Ungenutzte globale Datenbausteine |
| UDTs | Ungenutzte benutzerdefinierte Datentypen |
| Variables/Tags | Ungenutzte PLC-Variablen |

**Safety-Blöcke (rot markiert):**
| Tab | Inhalt |
|-----|--------|
| Safety Functions | Ungenutzte F_FC/F_FB Blöcke |
| Safety DBs | Ungenutzte F_DB Blöcke |
| Safety UDTs | Ungenutzte Safety-Datentypen |
| Safety Tags | Ungenutzte Safety-Variablen |

### Aktionen

**Auswahl:**
- **Select All** - Wählt alle Einträge im aktuellen Tab
- **Deselect All** - Hebt Auswahl auf
- **Delete Selected** - Löscht nur ausgewählte Einträge

**Löschen nach Kategorie:**
- **Standard Blocks** - Löscht alle ungenutzten FC/FB
- **Data Blocks (DB)** - Löscht alle ungenutzten DBs
- **UDTs** - Löscht alle ungenutzten Datentypen
- **Tags** - Löscht alle ungenutzten Variablen

**Safety löschen (mit Warnung):**
- **⚠ Safety Blocks** - Löscht alle ungenutzten F_FC/F_FB
- **⚠ Safety DBs** - Löscht alle ungenutzten F_DBs
- **⚠ Safety UDTs** - Löscht alle ungenutzten F_UDTs
- **⚠ Safety Tags** - Löscht alle ungenutzten F_Tags

**Export:**
- **Export to Text** - Exportiert die Liste als Textdatei
- **Copy All** - Kopiert alle Einträge in die Zwischenablage

### Einstellungen

Klicken Sie auf das **Zahnrad-Symbol** in der linken Toolbar, um den Einstellungsdialog zu öffnen.

**Analyse-Umfang:**

| Einstellung | Standard | Beschreibung |
|-------------|----------|-------------|
| Bausteine einbeziehen (FC/FB) | An | Funktionen und Funktionsbausteine in die Analyse einbeziehen |
| Datenbausteine einbeziehen (DB) | An | Globale und Array-Datenbausteine einbeziehen. Instanz-DBs sind immer mit ihrem übergeordneten FB verknüpft |
| UDTs einbeziehen | An | Benutzerdefinierte Datentypen einbeziehen. UDTs, die von verwendeten Bausteinen referenziert werden, gelten als verwendet |
| Tags analysieren | An | PLC-Tags in die Aufrufgraph-Analyse einbeziehen |
| Bestehende Exporte wiederverwenden | An | Zuvor exportierte XML-Dateien für schnellere wiederholte Analyse nutzen |

**Ausschlüsse:**

| Einstellung | Beschreibung |
|-------------|-------------|
| Ausschlussmuster | Semikolon-getrennte Platzhaltermuster. Elemente, die einem Muster entsprechen, werden aus den Ergebnissen ausgeschlossen. Verwenden Sie `*` für beliebige Zeichen, `?` für ein einzelnes Zeichen. Beispiel: `FB_Test*;DB_Temp*;FC_Debug*` |

Alle Einstellungen werden automatisch gespeichert und bleiben nach dem Neustart der Anwendung erhalten.

### Hinweise

- OBs (Organization Blocks) werden nie als "unused" markiert, da sie Einstiegspunkte sind
- Safety-Blöcke erfordern Safety-Login für vollständige Analyse
- Das Löschen von Safety-Blöcken erfordert Bestätigung aufgrund der Sicherheitsauswirkungen

---

## 13. Einstellungen

### Öffnen

Wählen Sie **View → Settings** aus der Menüleiste.

### Verfügbare Einstellungen

| Einstellung | Beschreibung |
|-------------|--------------|
| Working Directory | Standard-Exportordner für Find Unused Blocks |
| Log Path | Pfad für Log-Dateien |
| Language | Sprache der Benutzeroberfläche (DE, EN, FR, IT) |
| Theme Mode | Dunkel- oder Hell-Modus |
| Akzentfarbe | Cyan, Blau, Grün, Bernstein oder Teal |
| Debug Logging | Aktiviert erweiterte Protokollierung |
| Auf Updates prüfen | Automatisch beim Start nach Updates suchen |
| Source-Ordner erstellen | Einen Source-Ordner-Wrapper in Exporte einfügen |

### Ordnernamen-Anpassung

Passen Sie die Ordnernamen für Export-Pfade und Baumansicht an:

| TIA Portal Name | Standard Export-Name | Konfigurierbar |
|-----------------|----------------------|----------------|
| (Gerät) | Source | ✓ |
| Programmbausteine | Blocks | ✓ |
| PLC-Datentypen | Datatypes | ✓ |
| PLC-Variablen | Tags | ✓ |
| Technologieobjekte | Technology Objects | ✓ |
| Software Units | Software Units | ✓ |

### Source-Ordner Option

Die **"Create Source folder"** Checkbox steuert, ob Exporte einen Source-Ordner-Wrapper enthalten:

| Einstellung | Export-Pfad |
|-------------|-------------|
| ✓ Aktiviert | `WorkingDir/Source/PLC_1/Blocks/...` |
| ☐ Deaktiviert | `WorkingDir/PLC_1/Blocks/...` |

Diese Einstellung beeinflusst auch die Projektbaumstruktur und die Import-Pfaderkennung.

### Log-Dateien

Bei aktiviertem Debug Logging werden detaillierte Logs erstellt:
- Speicherort: Konfigurierbar in Einstellungen
- Format: `TIA_Openness_Log_YYYYMMDD_HHMMSS.txt`

---

## 14. Lizenzierung

### Lizenz-Tiers

| Feature | Basic (GRATIS) | Professional (CHF 9.99/Mo) | Enterprise (CHF 29.99/Mo) |
|---------|----------------|---------------------------|--------------------------|
| Preis | Kostenlos | CHF 9.99/Mo oder CHF 99.99/Jahr | CHF 29.99/Mo oder CHF 299.99/Jahr |
| Dateien pro Vorgang | 1 | 1.000 | Unbegrenzt |
| Export/Import | Ja | Ja | Ja |
| Block Compare | Ja | Ja | Ja |
| Code Editor | Ja | Ja | Ja |
| Find Unused | Nein | Ja | Ja |
| Safety Blocks | Nein | Ja | Ja |
| Protection Profiles | Nein | Ja | Ja |
| MCP Server | Nein | Ja | Ja |
| Multi-User | Nein | Nein | Ja |

### Testphase

Beim ersten Start können Sie eine **30-tägige kostenlose Testphase** mit allen Enterprise-Funktionen starten. Nach Ablauf der Testphase fällt die Anwendung auf den Basic-Modus (kostenlos) zurück.

Testphase starten:
1. Klicken Sie auf **View → Einstellungen → Lizenz verwalten**
2. Klicken Sie auf **30-Tage-Testversion starten**
3. Alle Funktionen sind 30 Tage verfügbar

### Lizenz aktivieren (Online)

1. Kaufen Sie eine Subscription (Professional oder Enterprise) auf https://www.tiaopenessmanager.ch
2. Sie erhalten einen Aktivierungscode per E-Mail
3. Öffnen Sie **View → Einstellungen → Lizenz verwalten**
4. Geben Sie den Aktivierungscode ein
5. Klicken Sie auf **Aktivieren**
6. Die Lizenz wird an Ihre Hardware gebunden

**Abrechnung:** Sie können im Lizenz-Dialog zwischen monatlicher und jährlicher Abrechnung wechseln. Jahresabos sparen ca. 17%.

**Wichtig:** Die Software validiert die Lizenz alle 7 Tage online. Bei fehlender Internetverbindung kann die Software **bis zu 14 Tage offline** genutzt werden. Nach 14 Tagen ist eine erneute Online-Validierung erforderlich.

### Hardware-Bindung

Jede Lizenz ist an eine eindeutige Hardware-ID gebunden, die generiert wird aus:
- CPU-ID (Prozessor-Seriennummer)
- Mainboard-Seriennummer
- Primäre MAC-Adresse

### Abonnement verwalten

- Klicken Sie auf **Abonnement verwalten** im Lizenz-Dialog
- Öffnet das Stripe-Portal für:
  - Zahlungsmethode ändern
  - Rechnungen herunterladen
  - Abonnement kündigen

### Lizenz-Information anzeigen

Im Lizenz-Dialog sehen Sie:
- Aktueller Lizenz-Typ (Basic/Professional/Enterprise)
- Ablaufdatum der aktuellen Periode
- Hardware-ID
- Aktivierungscode

### Sicherheits-Hinweise

Wenn die App ein ungewöhnliches Sicherheits-Ereignis erkennt, erscheint oben im Hauptfenster ein gelber Hinweis-Balken. Diese Hinweise bleiben sichtbar, bis Sie sie über das **×** schliessen — sie werden nicht von anderen Status-Meldungen überschrieben.

Zwei Ereignisse können hier auftauchen:

- **Speicher-Warnung.** Die App konnte Ihre Lizenzdaten nicht vollständig in die Windows-Registry schreiben. Meist eine Berechtigungs-Situation auf verwalteten Notebooks. Die App läuft weiter mit den zwischengespeicherten Lizenzdaten — falls die Warnung direkt nach einer Aktivierung erscheint, starten Sie die App einmal als Administrator oder wenden Sie sich an Ihre IT.
- **Zertifikats-Warnung.** Das TLS-Zertifikat von `tiaopenessmanager.ch` hat sich unerwartet geändert. Ihre Verbindung ist weiterhin TLS-geschützt (sonst würde die App die Anfrage komplett verweigern), aber die Änderung sollte beobachtet werden — insbesondere wenn sie mit einem neu installierten Firmen-Proxy zusammenfällt. Die App arbeitet weiter; kontaktieren Sie den Support, falls die Warnung länger als 24 Stunden bestehen bleibt.

Beide Hinweise sind informell. Ihre Lizenz bleibt aktiv, während sie eingeblendet sind. Der Balken verschwindet automatisch, sobald der Auslöser nicht mehr zutrifft.

**Nicht vertrauenswürdige Umgebung (Basic-Modus)**

Wenn ein Debugger an den App-Prozess angehängt ist oder die Haupt-EXE nicht mit dem erwarteten Certum-Zertifikat signiert ist, schaltet die App still auf den Basic-Tier. Das ist eine Tiefen-Absicherung gegen Manipulation. Release-Builds haben immer die korrekte Signatur — erscheint diese Degradierung bei einer Standard-Installation, wurde die Binary verändert. Installieren Sie dann neu von https://www.tiaopenessmanager.ch.

---

## 14a. Git-Client

Der Git-Client ist eine integrierte Versionsverwaltungs-Oberfläche für die Arbeit mit Repositories direkt in TIA Openness Manager. Er ermöglicht einen visuellen Git-Workflow, ohne die Anwendung zu verlassen.

### Repository öffnen

1. Klicken Sie auf den Tab **Git** in der Hauptnavigation
2. Klicken Sie auf der Willkommensseite auf **Repository öffnen** und wählen Sie einen Ordner, oder ziehen Sie einen Repository-Ordner auf die Willkommensseite
3. Zuletzt verwendete Repositories werden in der Liste für den schnellen Zugriff angezeigt

### History-Ansicht

Die History-Ansicht zeigt den Commit-Graph mit Branch- und Tag-Abzeichen.

**Issue-Tracker-Links in Commit-Subjects**

Wenn Ihr Repository mit Issue-Tracker-Regeln konfiguriert ist, werden passende Muster in Commit-Subject-Zeilen automatisch als anklickbare Links angezeigt (z. B. `#123`, `PROJ-456`). Ein Klick auf den Link öffnet die entsprechende Issue-Seite im Browser.

Issue-Tracker konfigurieren:
1. Öffnen Sie die Repository-Einstellungen über das Zahnrad-Symbol in der Toolbar
2. Wechseln Sie zum Tab **Issue Tracker**
3. Fügen Sie eine Regel hinzu: Geben Sie einen regulären Ausdruck ein (z. B. `#(\d+)`) und ein URL-Template (z. B. `https://github.com/org/repo/issues/$1`)
4. Wählen Sie aus integrierten Vorlagen (GitHub, GitLab, JIRA usw.) oder definieren Sie eine eigene Regel

### Commit-Detailansicht

Durch Auswahl eines Commits in der History-Ansicht wird das Commit-Detail-Panel auf der rechten Seite geöffnet.

Die vollständige Commit-Nachricht wird mit Rich-Text-Formatierung angezeigt:

- **Issue-Tracker-Links** — Referenzen, die Ihren konfigurierten Issue-Tracker-Regeln entsprechen, werden als anklickbare Links dargestellt. Ein Klick öffnet das Issue im Browser.
- **URLs** — HTTP(S)- und FTP-URLs werden automatisch erkannt und unterstrichen. Ein Klick öffnet die URL im Browser.
- **Commit-SHA-Referenzen** — Enthält die Nachricht einen Commit-SHA (6–64 Hex-Zeichen), wird er als orangefarbener unterstrichener Link dargestellt. Ein Klick navigiert zu diesem Commit im History-Graph. Beim Hovern wird der Commit-Subject als Tooltip angezeigt.
- **Inline-Code** — Text in Backticks (`` `so wie das` ``) wird in Monospace-Schrift mit einem eigenen Hintergrund gerendert.

**Rechtsklick-Kontextmenü auf Links:**
- **Link kopieren** — Kopiert die URL in die Zwischenablage
- **Im Browser öffnen** — Öffnet die URL im Standard-Browser
- **Zum Commit navigieren** — Navigiert zum referenzierten Commit (nur SHA-Links)
- **SHA kopieren** — Kopiert den SHA in die Zwischenablage (nur SHA-Links)

### Working Copy

Die Working-Copy-Ansicht zeigt staged und unstaged Änderungen.

- Einzelne Dateien oder den gesamten Änderungssatz stagen oder entstagen
- Commit-Message eingeben und auf **Commit** klicken
- **Commit-Optionen** Checkboxen für Sign-Off, No-Verify (Hooks überspringen) und Reset-Author
- Änderungszustände werden als farbige, abgerundete Abzeichen angezeigt (Geändert, Hinzugefügt, Gelöscht, Umbenannt usw.) für eine schnelle visuelle Übersicht
- Rechtsklick auf eine ungestagete Datei zeigt **LFS**-Operationen: Track nach Dateiname oder Erweiterung sowie Lock/Unlock. Bei Repositories mit mehreren Remotes erscheint für Lock/Unlock ein Untermenü pro Remote

### Branches, Tags und Remotes

Die Sidebar auf der linken Seite zeigt alle lokalen Branches, Remote-Branches, Tags, Worktrees und Submodule. Rechtsklick auf ein Element öffnet ein Kontextmenü mit Aktionen (Checkout, Merge, Push, Löschen usw.).

### Befehlspalette (Command Palette)

Drücken Sie **Strg+Umschalt+P** im Git-Arbeitsbereich, um die Befehlspalette zu öffnen. Sie bietet schnellen, tastaturgesteuerten Zugriff auf die häufigsten Git-Operationen, ohne durch Menüs navigieren zu müssen.

**Verfügbare Befehle:**

| Befehl | Aktion |
|--------|--------|
| Checkout | Zu einem Branch wechseln |
| Merge | Einen Branch in den aktuellen Branch mergen |
| Compare | Einen Branch oder Tag mit dem aktuellen Branch vergleichen |
| Blame | Blame-Ansicht für eine Datei öffnen |
| File History | History einer bestimmten Datei öffnen |
| Open File | Eine Datei aus dem Repository im Editor öffnen |
| Create Branch | Neuen Branch erstellen |
| Create Tag | Neuen Tag erstellen |
| Fetch | Von einem Remote abrufen |
| Pull | Von einem Remote pullen |
| Push | Zu einem Remote pushen |
| Stash | Aktuelle Änderungen stashen |
| Apply Patch | Eine Patch-Datei anwenden |
| Configure | Repository-Einstellungen öffnen |

**Unterpaletten:** Befehle, die eine Branch-, Tag- oder Dateiauswahl erfordern, öffnen eine sekundäre Auswahlliste. Tippen Sie, um die Liste fuzzy zu filtern. Drücken Sie **Rücktaste** bei leerem Filter, um zur Hauptpalette zurückzukehren.

**Schliessen:** Drücken Sie **Escape** oder klicken Sie ausserhalb der Palette, um sie zu schliessen.

---

## 14b. Trace / Signal-Visualisierung

Das Trace-Register zeichnet OPC-UA-Signalwerte in festem Takt auf und stellt sie als Live-Diagramm dar — ähnlich einem Oszilloskop. Das ist das richtige Werkzeug, wenn eine Zahl in der Watch Table nicht reicht und Sie sehen wollen, wie sich ein Signal über die Zeit verändert: steigende Flanken, Überschwinger, Schwingungen oder Drift.

### Trace-Register öffnen

Wählen Sie **Trace** in der Haupt-Registerleiste. Für eine Aufzeichnung brauchen Sie eine aktive OPC-UA-Sitzung (zuerst über das OPC-UA-Register verbinden).

### Signale hinzufügen

In der linken Signal-Seitenleiste:

- **„+ Signal"** öffnet den OPC-UA-Browser zum Auswählen eines PLC-Tags.
- **„+ Computed"** fügt ein berechnetes Signal hinzu, dessen Wert aus einer Formel über die anderen Signale berechnet wird (siehe unten).

Jedes Signal hat eine Checkbox zum Aktivieren/Deaktivieren (ohne es zu entfernen), einen Farb-Indikator und einen Löschen-Button.

### Werkzeugleiste

| Schaltfläche | Aktion |
|--------------|--------|
| Start / Stop | Aufzeichnung starten bzw. stoppen |
| Modus | **Fortlaufend** hält die neuesten Samples in einem rollenden Fenster; **Einzel-Trigger** zeichnet ein festes Fenster um ein Trigger-Ereignis auf |
| Zykluszeit | Wie oft die SPS abgefragt wird (100 ms, 200 ms, 500 ms, 1 s, 2 s, 5 s) |
| Fenster | Zeitfenster im fortlaufenden Modus (30 s bis 1 h) |
| Trigger | Steigende/fallende/beide Flanken mit Schwellwert plus Pre-/Post-Samples konfigurieren |
| Auto-Skalierung | Automatische Y-Achsen-Anpassung ein/aus |
| Auto-Reconnect | Wenn aktiv, startet die Aufzeichnung nach einem OPC-UA-Verbindungsabbruch automatisch mit denselben Signalen neu |
| CSV exportieren | Aufzeichnung in eine CSV-Datei schreiben |

Während einer laufenden Aufzeichnung ist die Signalliste schreibgeschützt. Stoppen Sie den Trace, um Signale zu ändern, berechnete Signale hinzuzufügen oder die Skalierung zu wechseln.

### Plot-Interaktion (nach Stop)

Sobald die Aufzeichnung gestoppt ist, stehen zusätzliche Buttons zur Verfügung:

- **Pan** — ziehen verschiebt den Ausschnitt
- **Rechteck-Zoom** — ein Rechteck aufziehen zoomt in den Bereich
- **Zoom In / Zoom Out** — schrittweises Zoomen
- **100 %** — beide Achsen auf die volle Aufzeichnung zurücksetzen
- **Fit** — Y-Achse im aktuellen Zeitfenster automatisch anpassen

### Dual-Cursor

Klicken Sie in den Plot, um Cursor **t1** zu setzen; ein weiterer Klick setzt **t2**. Jeder weitere Klick wechselt, welcher Cursor bewegt wird. Ziehen Sie einen Cursor, um ihn präzise zu positionieren. **Strg** + Klick irgendwo auf den Plot löscht beide Cursor.

Die Zeitdifferenz **Δt** zwischen den Cursorn wird oben rechts im Plot angezeigt. Jeder Cursor trägt oben an der Linie ein kleines **t1**- oder **t2**-Label, und am zweiten Cursor werden Δt und ΔY live direkt an der Linie mitgeführt, während Sie ziehen.

In der Toolbar gibt es neben dem Export-Button einen Toggle **Messcursor anzeigen**. Beim ersten Einschalten nach einem gestoppten Trace platzieren sich die Cursor automatisch bei 25 % und 75 % des sichtbaren Zeitfensters, damit sie sofort sichtbar sind. Wird der Toggle ausgeschaltet, verschwinden die Cursor-Linien und die Spalten Y(t1) / Y(t2) / ΔY leeren sich — die zuletzt gesetzten Cursor-Positionen bleiben erhalten und erscheinen beim nächsten Einschalten wieder.

### Signal-Tabelle (unter dem Plot)

Jedes Signal erscheint als Zeile mit den editierbaren Spalten: **Name**, **Formel**, **Format** (Dezimal / Hex / Binär / Bool / Wissenschaftlich), **Linie** (Linear oder Stufen), **Min Y**, **Max Y** und **Skalierungsgruppe**. Änderungen wirken sofort — kein Trace-Neustart nötig. Die rechten Spalten **Y(t1)**, **Y(t2)** und **ΔY** zeigen die interpolierten Signalwerte an den beiden Cursorn sowie deren Differenz im gewählten Anzeigeformat.

Die **Linie**-Spalte steuert das Rendering im gestoppten Trace: Linear zieht eine Gerade zwischen Samples, Stufen zeichnet einen Rechteckverlauf — das passt zu booleschen oder bitweisen Signalen, die in der PLC tatsächlich sprunghaft zwischen diskreten Werten wechseln. Wird das Format eines Signals auf Bool gestellt, wird automatisch Stufen vorausgewählt. Sie können die Linien-Darstellung jederzeit manuell überschreiben; die Wahl bleibt bei späteren Format-Wechseln erhalten.

### Skalierungsgruppen

Mehrere Signale können sich eine Y-Achse teilen, indem sie in dieselbe Skalierungsgruppe gelegt werden:

- **Main** — die linke Hauptachse (Default für neue Signale)
- **A / B / C / D** — vier geteilte rechte Achsen; jedes Signal in derselben Buchstaben-Gruppe nutzt eine gemeinsame Achse mit neutraler Beschriftung
- **Eigene** — eine dedizierte rechte Achse pro Signal, in der Signalfarbe eingefärbt

Beispiel: Drei Temperaturfühler in Gruppe **A** liegen auf einer gemeinsamen Skala übereinander, während der Druck auf seiner eigenen Achse bleibt.

### Berechnete Signale (Formeln)

Ein berechnetes Signal hat keinen eigenen PLC-Tag. Sein Wert ergibt sich aus den Werten früherer Signale in der Liste, gemäss einer Formel, die Sie in die Spalte **Formel** eintragen.

**Syntax:**

- `$0`, `$1`, `$2` … referenzieren Signale nach ihrer Position in der Liste (null-basiert). Ein berechnetes Signal an Position *i* darf nur Signale **davor** referenzieren (`$0` … `$(i-1)`), wodurch zyklische Abhängigkeiten strukturell ausgeschlossen sind.
- Grundrechenarten `+`, `-`, `*`, `/` und Klammerung.
- Built-in-Funktionen: `abs`, `sqrt`, `min(a, b)`, `max(a, b)`, `pow(a, b)`, `sin`, `cos`, `tan`, `log`, `log10`, `exp`, `ceiling`, `floor`, `round`.
- Zwei zustandsbehaftete Funktionen: `deriv($i)` liefert die numerische Ableitung `(yₙ − yₙ₋₁) / Δt`, `integ($i)` das laufende Integral (Trapezregel). Jeder Aufruf hat seinen eigenen State, sodass `deriv($0) + deriv($1)` wie erwartet funktioniert. Der State wird bei jedem Trace-Neustart zurückgesetzt.

**Beispiele:**

```
$0 + $1                 # Summe zweier Signale
($0 + $1) / 2           # Mittelwert
$0 - $1                 # Differenz
abs($0 - $1) * 2        # doppelte absolute Differenz
deriv($0)               # numerische Ableitung
integ($0)               # numerisches Integral
$0 * 0.5 + 1.25         # Verstärkung + Offset
```

**Validierung:** Die Formel wird während der Eingabe geprüft. Eine ungültige Formel zeichnet einen roten Rahmen um die Zelle und zeigt den Fehler als Tooltip; der Start-Button bleibt deaktiviert, bis jede Formel gültig ist.

### Export

Über **CSV exportieren** wird die Aufzeichnung auf die Festplatte geschrieben. Jedes Signal (Quell- wie berechnetes) wird zu einer Spalte, jedes Sample zu einer Zeile, mit dem Zeitstempel in der ersten Spalte.

---

## 15. Fehlerbehebung & FAQ

### Häufige Probleme

#### "TIA Portal wird nicht gefunden"

**Ursache:** TIA Portal ist nicht installiert oder die falsche Version.

**Lösung:**
1. Prüfen Sie, ob TIA Portal V15 bis V21 installiert ist
2. Stellen Sie sicher, dass die Openness-Komponenten installiert sind
3. Stellen Sie sicher, dass der Bridge-Prozess (`TiaOpennessManager.V3.Bridge.exe`) starten kann

#### "Access denied" beim Öffnen

**Ursache:** Unzureichende Berechtigungen für den Zugriff auf TIA Portal oder die Projektdatei.

**Lösung:**
1. Führen Sie die Anwendung als Administrator aus
2. Stellen Sie sicher, dass die Projektdatei nicht schreibgeschützt ist
3. Prüfen Sie, ob keine andere Instanz das Projekt exklusiv geöffnet hat

#### "ObjectDisposedException" während Operation

**Ursache:** COM-Objekt wurde ungültig.

**Lösung:**
1. Schließen Sie das Projekt
2. Öffnen Sie es erneut
3. Bei großen Projekten: Verwenden Sie Attach Mode

#### Export dauert sehr lange

**Ursache:** Viele Blöcke oder langsame Festplatte.

**Lösung:**
1. Exportieren Sie in kleineren Batches
2. Verwenden Sie eine SSD
3. Schließen Sie andere Anwendungen

#### "Bridge nicht verbunden"

**Ursache:** Der Bridge-Prozess läuft nicht oder wurde blockiert.

**Lösung:**
1. Stellen Sie sicher, dass `TiaOpennessManager.V3.Bridge.exe` im gleichen Verzeichnis wie die Hauptanwendung existiert
2. Prüfen Sie, ob Antivirensoftware den Bridge-Prozess blockiert
3. Starten Sie die Anwendung neu

### FAQ

**F: Kann ich während des Exports in TIA Portal arbeiten?**
A: Nein. Bei Massenoperationen erscheint ein ExclusiveAccess-Dialog im TIA Portal, der die Benutzerinteraktion blockiert, bis die Operation abgeschlossen ist. Dies verhindert Konflikte und gewährleistet Datenintegrität.

**F: Werden Kommentare beim Export/Import erhalten?**
A: Ja, alle Block-Attribute werden in der XML-Datei gespeichert.

**F: Unterstützt die Anwendung Safety-Projekte?**
A: Ja, F-Blöcke werden vollständig unterstützt. Für einige Operationen ist ein Safety-Login erforderlich.

**F: Kann ich mehrere Projekte gleichzeitig öffnen?**
A: Nein, aktuell wird nur ein Projekt gleichzeitig unterstützt.

---

## Support

Bei weiteren Fragen oder Problemen kontaktieren Sie den Support:

- **E-Mail:** [support@tiaopenessmanager.ch]
- **Dokumentation:** Siehe `Information/` Ordner
- **Bug oder Funktionswunsch melden:** Help → Problem melden in der App

### Help → Problem melden

Öffnet einen Dialog zum Melden eines Fehlers oder Funktionswunschs direkt auf GitHub. Trage einen Titel und eine Beschreibung ein; die App fügt automatisch App-Version, Betriebssystem, .NET-Runtime, aktive TIA-Portal-Version, Sprache und Lizenz-Tier an. Bei Fehlerberichten kannst du außerdem die letzten 50 Log-Zeilen anhängen (Standard: an). Ein Klick auf „Im Browser öffnen" startet GitHub mit dem vorausgefüllten Issue — du musst nur noch auf „Submit new issue" klicken.

---

## Haftungsausschluss

Die Software wird „as is" geliefert. Der Anbieter übernimmt keine Haftung für:
- Schäden durch fehlerhafte LLM-Ausgaben
- Datenverlust oder Produktionsausfälle
- Engineering-Fehler oder fehlerhafte Code-Generierung
- Schäden durch unsachgemäße Nutzung

**Der Anwender trägt die volle Verantwortung für die Prüfung und Validierung aller generierten Inhalte.**

Siehe EULA und Haftungsausschluss auf https://www.tiaopenessmanager.ch für Details.

---

**© 2025-2026 AnyAutomation. Alle Rechte vorbehalten.**

**Ende des Benutzerhandbuchs**
