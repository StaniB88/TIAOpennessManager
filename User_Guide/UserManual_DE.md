# TIA Openness Manager - Benutzerhandbuch

**Version:** 3.0
**Stand:** Februar 2026

---

## Inhaltsverzeichnis

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
9c. [AI Canvas](#9c-ai-canvas)
10. [Projektbibliothek-Verwaltung](#10-projektbibliothek-verwaltung)
11. [Hardware Tab](#11-hardware-tab)
12. [Find Unused Blocks](#12-find-unused-blocks)
13. [Einstellungen](#13-einstellungen)
14. [Lizenzierung](#14-lizenzierung)
14a. [Git-Client](#14a-git-client)
15. [Fehlerbehebung & FAQ](#15-fehlerbehebung--faq)

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
| Help | Documentation, Release Notes, About |

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
2. Die Anwendung vergleicht Fingerprints (Hashes) der Blöcke
3. Ein Fenster zeigt:
   - **Geändert** - Blöcke, deren Inhalt sich unterscheidet
   - **Neu in TIA** - Blöcke, die nur im Projekt existieren
   - **Gelöscht** - Blöcke, die nur im Working Directory existieren

### Compare (Manueller Vergleich)

Die Compare-Funktion ermöglicht einen detaillierten Zeilenvergleich zwischen einem TIA Portal Block und einer beliebigen XML-Datei.

**So verwenden Sie den manuellen Vergleich:**

1. Wählen Sie einen Block im linken Baum (TIA Projekt)
2. Wählen Sie eine XML-Datei im rechten Baum (Working Directory)
3. Klicken Sie auf **Compare**
4. Das Compare-Fenster öffnet sich und zeigt:
   - **Links (TIA Portal):** Name des ausgewählten Blocks
   - **Rechts (Dateisystem):** Name der ausgewählten Datei
5. Klicken Sie auf **Vergleich starten**
6. Der Diff-Viewer zeigt die Unterschiede Zeile für Zeile

**Vorteile des manuellen Vergleichs:**

- **Freie Zuordnung** - Vergleichen Sie beliebige Blöcke mit beliebigen Dateien, unabhängig vom Namen
- **Schneller Einzelvergleich** - Ideal für gezielte Überprüfungen ohne alle Dateien zu scannen
- **SCL-Unterstützung** - Falls verfügbar, wird automatisch die besser lesbare SCL-Datei verwendet

**Hinweis:** Im Gegensatz zu Preview Diff (Hash-basiert) führt Compare einen direkten Textvergleich durch. Der Block wird temporär exportiert und Zeile für Zeile mit der Datei verglichen.

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

### Terminal-Modus

Der Terminal-Modus bettet ein PowerShell-Terminal direkt in das KI-Chat-Panel ein. Verwenden Sie es, um CLI-Tools (z.B. Claude CLI, git oder andere Kommandozeilen-Tools) mit vollem Zugriff auf MCP-Tools auszuführen, die mit TIA Portal verbunden sind.

**Modus wechseln:**
- Klicken Sie auf den **Chat** / **Terminal** Umschalter in der Kopfzeile
- Das Terminal öffnet PowerShell im TIA Portal-Projektverzeichnis (wenn ein Projekt geöffnet ist)

**MCP-Integration:**
Beim Aktivieren des Terminal-Modus führt TIA Openness Manager automatisch folgende Schritte durch:
1. Startet den MCP-Server (falls nicht bereits aktiv)
2. Schreibt eine `.mcp.json`-Datei ins Projektverzeichnis, damit CLI-Tools die verfügbaren MCP-Tools erkennen können
3. Schreibt optional eine `CLAUDE.md`-Datei mit Projektkontext (SPSen, Architektur, KI-Analyse) — siehe Einstellung unten

**CLAUDE.md-Generierung:**
Standardmässig wird beim Wechsel in den Terminal-Modus eine `CLAUDE.md`-Datei ins TIA Portal-Projektverzeichnis geschrieben. Diese Datei enthält Projektkontext, den Claude CLI automatisch liest. Wenn Sie Claude CLI nicht verwenden, können Sie dieses Verhalten deaktivieren:

1. Öffnen Sie **View → AI Chat Settings**
2. Navigieren Sie zum Abschnitt **Context**
3. Deaktivieren Sie **CLAUDE.md beim Terminal-Start ins Projektverzeichnis schreiben**

**In Terminal einfügen:**
Der KI-Chat kann Befehle oder Code ins Terminal einfügen. Wenn die KI einen Befehl vorschlägt, klicken Sie auf das Einfüge-Symbol, um ihn direkt an die Terminal-Eingabe zu senden.

**Tastenkürzel:**
- **Strg+Umschalt+V** — Zwischenablage-Inhalt ins Terminal einfügen

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

Sie koennen Nachrichten eingeben und senden waehrend der KI-Agent aktiv arbeitet. Statt die Eingabe waehrend des Streamings zu blockieren, werden Nachrichten in eine Prioritaetswarteschlange gestellt und nach jedem abgeschlossenen Turn automatisch verarbeitet.

**Senden waehrend der Agent arbeitet:** Geben Sie einfach Ihre Nachricht ein und druecken Sie Enter waehrend der Agent streamt. Die Nachricht wird als "in Warteschlange" angezeigt und das Eingabefeld wird geleert, damit Sie weitertippen koennen. Ein kleiner Indikator neben dem Eingabebereich zeigt an, wie viele Nachrichten warten (z.B. "2 Nachrichten in Warteschlange").

**Prioritaetsstufen:**

| Prioritaet | Verwendung | Verhalten |
|------------|-----------|----------|
| Naechstes | User-Nachrichten (Standard) | Verarbeitung nach aktuellem Turn |
| Spaeter | Agenten-Benachrichtigungen | Verarbeitung nach User-Nachrichten |

**ESC-Verhalten:**

- **Waehrend Streaming:** Bricht die aktuelle KI-Antwort ab und leert alle wartenden Nachrichten
- **Im Leerlauf mit wartenden Nachrichten:** Holt alle editierbaren Nachrichten aus der Warteschlange zurueck ins Eingabefeld, damit Sie sie bearbeiten oder verwerfen koennen

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
1. Klicken Sie auf **View → Settings → Manage License**
2. Klicken Sie auf **Start 30-Day Trial**
3. Alle Funktionen sind 30 Tage verfügbar

### Lizenz aktivieren (Online)

1. Kaufen Sie eine Subscription (Professional oder Enterprise) auf https://www.tiaopenessmanager.ch
2. Sie erhalten einen Aktivierungscode per E-Mail (Format: `ACT-XXXX-XXXX-XXXX`)
3. Öffnen Sie **View → Settings → Manage License**
4. Geben Sie den Aktivierungscode ein
5. Klicken Sie auf **Activate**
6. Die Lizenz wird an Ihre Hardware gebunden

**Abrechnung:** Sie können im License-Dialog zwischen monatlicher und jährlicher Abrechnung wechseln. Jahresabos sparen ca. 17%.

**Wichtig:** Die Software validiert die Lizenz alle 7 Tage online. Bei fehlender Internetverbindung kann die Software **bis zu 14 Tage offline** genutzt werden. Nach 14 Tagen ist eine erneute Online-Validierung erforderlich.

### Hardware-Bindung

Jede Lizenz ist an eine eindeutige Hardware-ID gebunden, die generiert wird aus:
- CPU-ID (Prozessor-Seriennummer)
- Mainboard-Seriennummer
- Primäre MAC-Adresse

### Subscription verwalten

- Klicken Sie auf **Manage Subscription** im License-Dialog
- Öffnet das Stripe-Portal für:
  - Zahlungsmethode ändern
  - Rechnungen herunterladen
  - Subscription kündigen

### Lizenz-Information anzeigen

Im License-Dialog sehen Sie:
- Aktueller Lizenz-Typ (Basic/Professional/Enterprise)
- Ablaufdatum der aktuellen Periode
- Hardware-ID
- Aktivierungscode

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

- **E-Mail:** [tiaopenessmanager@outlook.com]
- **Dokumentation:** Siehe `Information/` Ordner

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
