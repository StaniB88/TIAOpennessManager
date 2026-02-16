# TIA Openness Manager - Benutzerhandbuch

**Version:** 1.2
**Stand:** Januar 2026

---

## Inhaltsverzeichnis

1. [Einführung](#1-einführung)
2. [Installation & Systemvoraussetzungen](#2-installation--systemvoraussetzungen)
3. [Benutzeroberfläche](#3-benutzeroberfläche)
4. [Projekt-Management](#4-projekt-management)
5. [Import/Export/Compare Tab](#5-importexportcompare-tab)
6. [Project Tab](#6-project-tab)
7. [Schutz-System](#7-schutz-system)
8. [MCP Tab (KI-Integration)](#8-mcp-tab-ki-integration)
9. [Hardware Tab](#9-hardware-tab)
10. [Find Unused Blocks](#10-find-unused-blocks)
11. [Einstellungen](#11-einstellungen)
12. [Lizenzierung](#12-lizenzierung)
13. [Fehlerbehebung & FAQ](#13-fehlerbehebung--faq)

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
| TIA Portal | V15, V16, V17, V18, V19 oder V20 |
| .NET Framework | 4.8 oder höher |
| RAM | Mindestens 4 GB (8 GB empfohlen) |
| Festplatte | 500 MB |

> **Hinweis:** Die TIA Portal Version wird automatisch erkannt, wenn Sie ein Projekt öffnen oder sich mit einer laufenden Instanz verbinden. Keine manuelle Konfiguration erforderlich.

### Installation

1. Laden Sie das TiaOpennessManager-Archiv herunter
2. Entpacken Sie das Archiv in einen Ordner Ihrer Wahl (z.B. `C:\Tools\TiaOpennessManager`)
3. Starten Sie `TiaOpennessManager.exe`

> **Hinweis:** Es ist keine separate Installation erforderlich. Die Anwendung ist portable. TIA Portal muss auf dem System installiert sein.

---

## 3. Benutzeroberfläche

### Hauptfenster-Übersicht

Die Anwendung ist in mehrere Bereiche unterteilt:

```
┌───────────────────────────────────────────────────────────────────────────────┐
│  TIA Openness Manager - V20       [Benutzerhandbuch] [About] [Settings] [_][□][X] │
├───────────────────────────────────────────────────────────────────────────────┤
│  [Archive] [Disconnect] [Rescan] [Save] [Compile] [Safety Login] [Safety Logoff]   │
├─────────────┬─────────────────────────────────────────────────────────────────┤
│             │  [Project] [Import/Export] [Find Unused] [MCP] [Hardware]       │
│  Projekt-   ├─────────────────────────────────────────────────────────────────┤
│  Baum       │                                                                 │
│             │              Tab-Inhalt                                         │
│  (Links)    │                                                                 │
│             │                                                                 │
├─────────────┴─────────────────────────────────────────────────────────────────┤
│  Status-Leiste mit Fortschrittsanzeige                                        │
└───────────────────────────────────────────────────────────────────────────────┘
```

### Linker Bereich - Projektbaum

Der Projektbaum unterstützt zwei Modi, auswählbar über Radio-Buttons oben:

- **TIA Projekt Modus** - Zeigt die Struktur des verbundenen TIA Portal Projekts
- **Offline-Ordner Modus** - Durchsuchen eines lokalen Ordners mit exportierten XML-Dateien

**Baum-Funktionen:**
- Hierarchie: Projekt → Hardware → Source → PLC → Blocks/Datatypes/Tags
- Grüne Checkboxen für Export-Auswahl (links von jedem Element)
- Schutz-Checkboxen für Import-Schutz (rechts von jedem Element)
- "Selected"-Badge zeigt Anzahl der für Export ausgewählten Elemente
- "Protect"-Badge zeigt Anzahl der geschützten Elemente
- Suchleiste mit Vorwärts-/Rückwärts-Navigation
- Aktualisieren-Button um den Baum aus TIA Portal neu zu laden

### Rechter Bereich - Tabs

- **Project** - Code-Editor für ausgewählte Blöcke, mit Block-Details
- **Import/Export** - Haupt-Arbeitsbereich für Datei-Operationen mit Kategorie-Tabs
- **Find Unused** - Dead-Code-Erkennung und Aufräumen
- **MCP** - KI-Integrations-Status und Tools
- **Hardware** - Geräteliste mit PROFINET-Namen und IP-Konfiguration

## 4. Projekt-Management

### Toolbar Buttons

| Button | Funktion |
|--------|----------|
| **Archive Project** | Komprimiertes Archiv (.zap) erstellen |
| **Disconnect** | Aktuelle Projektverbindung trennen |
| **Rescan PLC** | Projektbaum aktualisieren |
| **Save** | Projekt speichern |
| **Compile** | Projekt kompilieren |
| **Safety Login** | Mit Safety-Anmeldedaten für F-Blöcke einloggen |
| **Safety Logoff** | Safety-Modus abmelden |

### Mit TIA Portal verbinden

Wenn kein Projekt verbunden ist, erscheint im Projektbaum-Bereich ein leerer Zustand mit einem **Connect**-Button. Ein Klick darauf öffnet den Verbindungs-Dialog.

Der Verbindungs-Dialog bietet zwei Möglichkeiten über Tab-Buttons:

**Tab 1: Attach to Running**
1. Der Dialog zeigt eine Liste der aktuell laufenden TIA Portal Instanzen
2. Wählen Sie die gewünschte Instanz aus der Liste
3. Klicken Sie auf **Connect**
4. Verwenden Sie den **Refresh**-Button um die Liste zu aktualisieren

**Vorteile des Attach Mode:**
- Schnellere Verbindung (kein Projekt-Laden erforderlich)
- Sie können gleichzeitig in TIA Portal arbeiten
- Änderungen sind sofort in beiden Anwendungen sichtbar

**Tab 2: Open Project**
1. Klicken Sie auf **Browse...** um zu Ihrer TIA Portal Projektdatei zu navigieren
2. Wählen Sie die Datei (`.ap15`, `.ap16`, `.ap17`, `.ap18`, `.ap19`, `.ap20`, `.apx`)
3. Klicken Sie auf **Connect**

Die TIA Portal Version wird automatisch aus der Projektdatei-Erweiterung erkannt. Open Project startet TIA Portal im Hintergrund ohne sichtbare Benutzeroberfläche (Headless Mode).

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

### Safety Logoff

Klicken Sie auf **Safety Logoff**, um sich vom Safety-Modus abzumelden. Dies ist erforderlich, nachdem Sie die Arbeit mit Safety-Blöcken abgeschlossen haben.

### Projekt schließen

Klicken Sie auf **Disconnect**, um die Projektverbindung zu trennen.

---

## 5. Import/Export/Compare Tab

Der Import/Export/Compare Tab ist das Herzstück der Anwendung.

### Layout

Der Import/Export Tab ist mit einer vertikalen Toolbar links und einem Datei-Browser rechts organisiert:

```
┌───────────────┬──────────────────────────────────────┐
│  Auswahl: 5   │  Right Folder: C:\Export\...         │
│  [Cancel]     │  [Refresh] [Preview Diff] [Compare] [⚙] │
│               │                                      │
│  ┌─────────┐  │  🔍 [Suche___________] [×] [↑] [↓]  │
│  │Software │  │                                      │
│  │HMI      │  │  □ Blocks/                           │
│  │Safety   │  │    □ Main [OB1].xml                  │
│  │Watch    │  │    □ Motor [FB1].xml                  │
│  │Hardware │  │  □ Datatypes/                         │
│  ├─────────┤  │  □ Tags/                              │
│  │Export → │  │                                      │
│  │Export All│  │                                      │
│  │← Import │  │                                      │
│  │← Import All│                                      │
│  └─────────┘  │                                      │
└───────────────┴──────────────────────────────────────┘
```

### Kategorie-Tabs

Die linke Toolbar organisiert Operationen in Kategorie-Pill-Tabs:

| Kategorie | Operationen |
|-----------|-------------|
| **Software** | Export Selected, Export All, Import Selected, Import All |
| **HMI** | Export HMI Selected, Export HMI All, Import HMI Selected, Import HMI All |
| **Safety** | Export F-Signatures |
| **Watch/Force** | Export Watch Tables, Export Force Tables, Import Tables |
| **Hardware** | AML Export, AML Import |

Wählen Sie einen Kategorie-Tab um die relevanten Export-/Import-Buttons zu sehen.

### Right Directory (Export-/Import-Verzeichnis)

Das Right Directory ist der Ordner auf Ihrem Dateisystem, in dem exportierte Dateien gespeichert werden und aus dem Dateien importiert werden.

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

### Import/Export-Einstellungen

Klicken Sie auf das **Zahnrad-Symbol** (⚙) in der Toolbar, um den Dialog für Import/Export-Einstellungen zu öffnen. Dieser Dialog ermöglicht die Anpassung des Import- und Export-Verhaltens.

#### Import-Optionen

Diese Einstellungen steuern, wie Blöcke in Ihr TIA Portal Projekt importiert werden:

| Option | Was es bewirkt |
|--------|----------------|
| **IgnoreStructuralChanges** | Import erlauben, auch wenn sich die Blockstruktur geändert hat (z.B. Interface-Änderungen). Mit Vorsicht verwenden, da dies zu Laufzeitproblemen führen kann. |
| **IgnoreMissingReferencedObjects** | Blöcke importieren, auch wenn referenzierte Objekte (aufgerufene Blöcke, UDTs) fehlen. Fehlende Referenzen müssen manuell aufgelöst werden. |
| **Fault Tolerant (bei Fehlern fortfahren)** | Import verbleibender Dateien fortsetzen, auch wenn einige Dateien fehlschlagen. Ermöglicht Teil-Imports statt Abbruch beim ersten Fehler. |

#### Export-Optionen (Pro Typ)

Diese Einstellungen steuern, wie verschiedene Blocktypen exportiert werden. Jeder Typ kann separat konfiguriert werden:

**Data Blocks (DBs):**
| Option | Was es bewirkt |
|--------|----------------|
| **None** | DBs ohne Standardwerte oder schreibgeschützte Attribute exportieren |
| **With Defaults** | Standardparameterwerte in DB-Exporte einschließen |
| **With ReadOnly** | Schreibgeschützte Eigenschaften in DB-Exporte einschließen |

**User Defined Types (UDTs):**
| Option | Was es bewirkt |
|--------|----------------|
| **None** | UDTs ohne Standardwerte oder schreibgeschützte Attribute exportieren |
| **With Defaults** | Standardparameterwerte in UDT-Exporte einschließen |
| **With ReadOnly** | Schreibgeschützte Eigenschaften in UDT-Exporte einschließen |

**Tags:**
| Option | Was es bewirkt |
|--------|----------------|
| **None** | Variablentabellen ohne Standardwerte oder schreibgeschützte Attribute exportieren |
| **With Defaults** | Standardwerte in Variablentabellen-Exporte einschließen |
| **With ReadOnly** | Schreibgeschützte Eigenschaften in Variablentabellen-Exporte einschließen |

#### Geschützte Dateien exportieren

| Option | Was es bewirkt |
|--------|----------------|
| **Export Protected Files** | Wenn aktiviert (Standard), werden alle Elemente einschließlich geschützter Elemente exportiert. Wenn deaktiviert, werden geschützte Elemente beim Export übersprungen, aber die Ordnerstruktur bleibt erhalten. |

Diese Option arbeitet zusammen mit dem Schutz-System (siehe [Schutz-System](#7-schutz-system)). Wenn Sie Blöcke als geschützt markiert haben und nur ungeschützte Blöcke exportieren möchten (z.B. um sie ohne proprietäre geschützte Blöcke an externe Partner weiterzugeben), deaktivieren Sie diese Option.

**Verhalten:**
- **Aktiviert (Standard):** Alle Blöcke werden exportiert, unabhängig vom Schutzstatus
- **Deaktiviert:** Geschützte Blöcke, Datentypen, Variablentabellen und Technologieobjekte werden übersprungen. Ordnerverzeichnisse werden trotzdem erstellt, um die Projektstruktur beizubehalten.

#### Zusätzlicher S7DCL Export (nur V20+)

S7DCL-Dateien sind textbasierte Quelldokumente, die einfacher zu lesen und zu vergleichen sind als XML. Sie bieten bessere Lesbarkeit für Versionskontrolle und Code-Reviews.

| Option | Was es bewirkt |
|--------|----------------|
| **SCL + S7DCL** | SCL-Blöcke zusätzlich als S7DCL-Format (.s7dcl) neben .scl und .xml exportieren. Erfordert TIA Portal V20+. |
| **AWL + S7DCL** | AWL/STL-Blöcke zusätzlich als S7DCL-Format (.s7dcl) neben .awl und .xml exportieren. Erfordert TIA Portal V20+. |
| **LAD/FBD + S7DCL** | LAD/FBD/GRAPH-Blöcke zusätzlich als S7DCL-Format (.s7dcl) neben .xml exportieren. Ermöglicht Text-Export für grafische Sprachen. Erfordert TIA Portal V20+. |

**Warum S7DCL Export verwenden?**
- **Bessere Lesbarkeit** - S7DCL-Dateien sind reiner Text, ideal für Diff-Vergleiche
- **Versionskontrolle** - Sehen Sie genau, was sich zwischen Versionen in Git oder SVN geändert hat
- **Code-Review** - Einfacher, Änderungen Zeile für Zeile zu überprüfen
- **Grafische Sprachen** - Textbasierte Darstellung von LAD/FBD-Blöcken erhalten

> **Hinweis:** S7DCL-Dateien dienen nur zur Ansicht und Versionskontrolle. Sie können nicht zurück in TIA Portal importiert werden. Diese Option erfordert TIA Portal V20 oder später.

#### Versionskontroll-Optionen

Diese Einstellungen helfen, sauberere Exporte für Git, SVN oder andere Versionskontrollsysteme zu erstellen. Sie entfernen Daten, die sich ändern, auch wenn sich der eigentliche Code nicht geändert hat.

| Option | Was es bewirkt |
|--------|----------------|
| **Exclude Document Info (empfohlen)** | Verwendet TIA Portal API DocumentInfoOptions.None um Timestamps und InstalledProducts aus Exporten auszuschließen. Standardmäßig aktiviert für saubere Versionskontroll-Diffs. |
| **Normalize Timestamps** | Alle Datumsangaben auf 2000-01-01 setzen, um Git-Diff-Rauschen zu reduzieren |
| **Clear Installed Products** | Maschinenspezifische Produktversionsinformationen aus Exporten entfernen |
| **Remove Object List** | ObjectList für Code-Blöcke mit Quelldateien (.scl, .awl, .db) entfernen |
| **Normalize Whitespace** | Leerzeichen in MultiLanguageText-Elementen trimmen |
| **Export Fingerprints** | Wenn aktiviert, werden Fingerprints für Änderungserkennung extrahiert und gespeichert. Deaktivieren um Fingerprint-Extraktion beim Export zu überspringen (beschleunigt Export wenn Änderungserkennung nicht benötigt wird). |

> **Tipp:** Wenn Sie Git oder SVN verwenden, aktivieren Sie alle Versionskontroll-Optionen außer "Export Fingerprints" wenn Sie die Preview Diff Funktion nicht benötigen. Dies verhindert "falsche Änderungen", bei denen Dateien unterschiedlich aussehen, obwohl sich der tatsächliche Code nicht geändert hat.

### Preview Diff

Die Preview Diff Funktion zeigt Unterschiede zwischen dem TIA Portal Projekt und dem Working Directory:

**Voraussetzungen:**
- Sie müssen zuvor Blöcke mit aktivierter Option **Export Fingerprints** exportiert haben
- Diese Option finden Sie im **Import/Export-Einstellungen** Dialog (Zahnrad-Symbol ⚙) unter **Versionskontroll-Optionen**
- Ohne exportierte Fingerprints kann Preview Diff keine Änderungen erkennen

**Verwendung:**
1. Klicken Sie auf **Preview Diff**
2. Die Anwendung vergleicht Fingerprints (Hashes) der Blöcke
3. Ein Fenster zeigt:
   - **Geändert** - Blöcke, deren Inhalt sich unterscheidet
   - **Neu in TIA** - Blöcke, die nur im Projekt existieren
   - **Gelöscht** - Blöcke, die nur im Working Directory existieren

> **Tipp:** Wenn Sie die Preview Diff Funktion nicht benötigen, können Sie "Export Fingerprints" in den Import/Export-Einstellungen deaktivieren um Exporte zu beschleunigen.

### Compare (Manueller Vergleich)

Die Compare-Funktion ermöglicht einen detaillierten Zeilenvergleich zwischen beliebigen zwei Elementen - Blöcke, Dateien oder jede Kombination.

**So verwenden Sie den manuellen Vergleich:**

1. Wählen Sie ein Element im linken Baum (TIA Projekt Block oder exportierte Datei)
2. Wählen Sie ein Element im rechten Baum (Working Directory Datei oder TIA Block)
3. Klicken Sie auf **Compare**
4. Das Compare-Fenster öffnet sich und zeigt:
   - **Links:** Name des ausgewählten linken Elements
   - **Rechts:** Name des ausgewählten rechten Elements
5. Klicken Sie auf **Vergleich starten**
6. Der Diff-Viewer zeigt die Unterschiede Zeile für Zeile

**Cross-Vergleich Feature:**

- **Alles-mit-Allem** - Vergleichen Sie alles mit allem: Block↔Datei, Datei↔Datei, Block↔Block
- **Format-Matching** - Der Vergleich passt automatisch die Formate an (SCL↔SCL, XML↔XML, AWL↔AWL)
- **Freie Zuordnung** - Vergleichen Sie beliebige Elemente miteinander, unabhängig von Name oder Typ
- **Schneller Einzelvergleich** - Ideal für gezielte Überprüfungen ohne alle Dateien zu scannen

**Hinweis:** Im Gegensatz zu Preview Diff (Hash-basiert) führt Compare einen direkten Textvergleich durch. Blöcke werden temporär im passenden Format exportiert und Zeile für Zeile verglichen.

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

### Hardware-Export

Hardware-Konfiguration als AML/XML exportieren:

1. Erweitern Sie den **Hardware**-Knoten im Projektbaum
2. Wählen Sie Geräte oder Module zum Export
3. Klicken Sie auf **Export Selected**

**Hinweis:** Der Hardware-Export erstellt AutomationML (.aml) Dateien, die reimportiert oder für Dokumentation verwendet werden können.

---

## 6. Project Tab

### Code-Anzeige

Wenn Sie einen Block im Projektbaum auswählen, wird sein Quellcode im Project Tab im Code-Editor angezeigt.

**Unterstützte Sprachen:**
- SCL (Structured Control Language)
- STL (Statement List)
- LAD/FBD (als XML-Darstellung)

### Code und Graphical Tabs

Der Editor hat zwei Tabs:

**Code Tab:**
- Zeigt textbasierten Quellcode (SCL, STL, AWL)
- Syntax-Highlighting für bessere Lesbarkeit
- Suchfunktion mit Optionen für Groß-/Kleinschreibung und Ganze Wörter

**Graphical Tab:**
- Zeigt LAD/FBD/GRAPH-Blöcke grafisch an
- **Voraussetzung:** SIMATIC Automation Compare Tool (SIMATIC ACT) muss installiert sein
- Klicken Sie auf "Open in SIMATIC ACT" oder wechseln Sie zum Graphical Tab um den Block anzuzeigen
- Wenn SIMATIC ACT nicht installiert ist, ist die grafische Ansicht nicht verfügbar

> **Hinweis:** Das SIMATIC Automation Compare Tool ist ein kostenloses Tool von Siemens, das von der Siemens Support-Website heruntergeladen werden kann.

### Block-Details Panel

Neben dem Code werden Metadaten angezeigt:
- **Block-Typ:** OB, FB, FC, DB
- **Nummer:** z.B. OB1, FB10
- **Sprache:** SCL, STL, LAD, FBD, GRAPH
- **Autor:** Falls verfügbar
- **Letzte Änderung:** Zeitstempel

### Suche im Projektbaum

Nutzen Sie das Suchfeld über dem Projektbaum, um Blöcke schnell zu finden:
- Suche nach Name
- Suche nach Nummer
- Groß-/Kleinschreibung wird ignoriert

### Neuen Block erstellen

Der Code-Editor unterstützt das Erstellen neuer SCL-Blöcke:

1. Klicken Sie auf den **+ New** Button in der Code-Editor Toolbar
2. Schreiben Sie Ihren SCL-Code im Editor
3. Klicken Sie auf einen der Erstellen-Buttons:
   - **Create FC** - Funktion erstellen
   - **Create FB** - Funktionsbaustein erstellen
   - **Create DB** - Datenbaustein erstellen
   - **Create UDT** - Benutzerdefinierter Datentyp erstellen
   - **Create Tag Table** - Variablentabelle erstellen
4. Klicken Sie auf **Cancel** um abzubrechen

### Speichern und Verwerfen

Wenn Sie den Code eines bestehenden Blocks bearbeiten, erscheinen die Buttons Speichern und Verwerfen:

- **Save** - Geänderten Code zurück in TIA Portal schreiben
- **Discard** - Zum Originalcode zurückkehren

---

## 7. Schutz-System

### Konzept

Das Schutz-System verhindert, dass wichtige Blöcke während Import-Operationen versehentlich überschrieben werden. Der Schutz wird direkt im Projektbaum verwaltet - es gibt keinen separaten Tab.

### Blöcke schützen

Im Projektbaum hat jeder Block eine Schutz-Checkbox auf der rechten Seite:

1. Klicken Sie auf die Schutz-Checkbox neben einem Block, Datentyp oder einer Variablentabelle
2. Die Checkbox verwendet drei Zustände:
   - **Nicht aktiviert** - Kein Schutz
   - **Aktiviert** - Geschützt (Block wird beim Import übersprungen)
   - **Unbestimmt** - Einige Unterelemente sind geschützt (für Ordner-Knoten)

### Schutz-Badges

Der Projektbaum-Header zeigt zwei Badges:

- **"Selected: N"** (grün) - Anzahl der für Export ausgewählten Elemente
- **"Protect: N"** (orange) - Anzahl der geschützten Elemente, mit einem Löschen-Button (×) um allen Schutz zu entfernen

### Schutz-Optionen für Organisationsbausteine (OBs)

Wenn Sie einen OB (Organization Block) schützen, erscheinen zusätzliche Checkboxen daneben:

| Checkbox | Symbol | Was es bewirkt |
|----------|--------|----------------|
| **Allow SCL code updates** | C | Wenn aktiviert, können SCL-Quelltextänderungen dieses geschützten OBs beim Import aktualisiert werden, während andere Attribute geschützt bleiben. |
| **Allow Attribute updates** | A | Wenn aktiviert, können Block-Attribute (Kommentare, Titel, etc.) beim Import aktualisiert werden, während der eigentliche Code geschützt bleibt. |

**Anwendungsfälle:**
- **Beide deaktiviert:** Vollständiger Schutz - Block wird beim Import komplett übersprungen
- **Nur C aktiviert:** Code-Updates importieren, aber Original-Attribute behalten
- **Nur A aktiviert:** Attribut-Änderungen importieren, aber Original-Code behalten
- **Beide aktiviert:** Vollständige Updates erlauben (entspricht keinem Schutz)

> **Hinweis:** Diese zusätzlichen Checkboxen werden nur für geschützte OBs angezeigt. FBs, FCs und DBs verwenden den standardmäßigen vollständigen Schutz.

### Profile

Profile speichern Ihre Schutz- und Export-Auswahl-Konfiguration. Die Profil-Leiste befindet sich über dem Projektbaum.

**Profil speichern:**
1. Konfigurieren Sie Ihre geschützten Blöcke und Export-Auswahl
2. Geben Sie einen Namen im Feld Profilname ein
3. Klicken Sie auf **Save Profile**

**Profil laden:**
1. Wählen Sie ein Profil aus dem Dropdown
2. Klicken Sie auf **Apply**

**Profil löschen:**
- Wählen Sie ein Profil und klicken Sie auf **Delete**

**Profile neu laden:**
- Klicken Sie auf **Reload** um die Profilliste zu aktualisieren

**Profile-Ordner öffnen:**
- Klicken Sie auf das Ordner-Symbol um den Profile-Ordner im Explorer zu öffnen
- Nützlich um Profile zwischen Rechnern oder Team-Mitgliedern zu teilen

---

## 8. MCP Tab (KI-Integration)

### Was ist MCP?

Das Model Context Protocol (MCP) ermöglicht KI-Assistenten, auf Ihr TIA Portal Projekt zuzugreifen. Wenn aktiv, können KI-Clients Blöcke auflisten, Code lesen, Dateien exportieren/importieren und Analysen durchführen.

### MCP Server Status

Der Tab zeigt:
- **Server Status:** Running / Stopped
- **Connection Settings** Button zur Server-Konfiguration

### Connection Settings

Klicken Sie auf **Connection Settings** um den MCP Connection Info Dialog zu öffnen:

**Server Connection:**
- **Named Pipe:** `\\.\pipe\TiaOpennessMcp` - Die Verbindungsadresse für MCP-Clients
- **Status:** Zeigt ob der Server läuft oder gestoppt ist
- **Available Tools:** Anzahl der verfügbaren MCP-Tools (z.B. 23 tools)

**Security Settings:**
| Option | Beschreibung |
|--------|--------------|
| **Allow Write Operations** | Import, Delete, Compile, Save Operationen via MCP erlauben |
| **Require User Approval** | Wenn aktiviert, erscheint für jede Schreiboperation ein Bestätigungsdialog |

**Client Configuration Tabs:**
Der Dialog bietet fertige Konfigurationen für verschiedene KI-Clients:
- **LM Studio** - Konfiguration für LM Studio MCP-Einstellungen
- **Ollama** - Konfiguration für Ollama
- **Continue.dev** - Konfiguration für Continue.dev Extension
- **Claude Desktop** - Konfiguration für Claude Desktop App

Jeder Tab zeigt:
- Die JSON-Konfiguration zum Hinzufügen in Ihren Client
- Einen **Copy Config** Button zum Kopieren der Konfiguration
- Schritt-für-Schritt Setup-Anleitung

### Verwendung mit KI-Assistenten

1. Öffnen Sie ein TIA Portal Projekt im TIA Openness Manager
2. Gehen Sie zum **MCP** Tab
3. Klicken Sie auf **Connection Settings**
4. Wählen Sie Ihren KI-Client Tab (z.B. Claude Desktop)
5. Klicken Sie auf **Copy Config** und fügen Sie es in die MCP-Einstellungen Ihres Clients ein
6. Starten Sie Ihren KI-Client neu
7. Der KI-Assistent kann nun:
   - Projektstruktur abfragen
   - Block-Code lesen und analysieren
   - Dateien exportieren/importieren (wenn Schreiboperationen aktiviert)
   - Code für Ihr Projekt generieren

---

## 9. Hardware Tab

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

## 10. Find Unused Blocks

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

### Hinweise

- OBs (Organization Blocks) werden nie als "unused" markiert, da sie Einstiegspunkte sind
- Safety-Blöcke erfordern Safety-Login für vollständige Analyse
- Das Löschen von Safety-Blöcken erfordert Bestätigung aufgrund der Sicherheitsauswirkungen

---

## 11. Einstellungen

### Öffnen

Klicken Sie auf das **Zahnrad-Symbol** in der oberen rechten Ecke.

### Verfügbare Einstellungen

| Einstellung | Beschreibung |
|-------------|--------------|
| **Language** | Sprache der Benutzeroberfläche (Deutsch, Englisch, Französisch, Italienisch). Erfordert Neustart. |
| **Working Directory** | Standardordner für "Find Unused Blocks" Exporte |
| **Log Path** | Speicherort für Log-Dateien wenn Debug Logging aktiviert ist |
| **Debug Logging** | Aktiviert detaillierte Protokollierung für Fehlerbehebung |
| **Auto-Update Check** | Automatisch beim Programmstart nach neuen Versionen suchen |

> **Hinweis:** Die TIA Portal Version wird jetzt automatisch erkannt, wenn Sie ein Projekt öffnen oder sich mit einer laufenden Instanz verbinden. Eine manuelle Auswahl ist nicht mehr erforderlich.

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

## 12. Lizenzierung

### Lizenz-Tiers

| Feature | Basic (GRATIS) | Pro (CHF 9.99/Mo) | Enterprise (CHF 29.99/Mo) |
|---------|----------------|---------------------|---------------------------|
| Preis | Kostenlos | CHF 9.99/Mo oder CHF 99.99/Jahr | CHF 29.99/Mo oder CHF 299.99/Jahr |
| Dateien | 1 | 1.000 | Unbegrenzt |
| Export/Import | Ja | Ja | Ja |
| Block Compare | Ja | Ja | Ja |
| Code Editor | Ja | Ja | Ja |
| Find Unused | Nein | Ja | Ja |
| Safety Blocks | Nein | Ja | Ja |
| Protection Profiles | Nein | Ja | Ja |
| MCP Server | Nein | Ja | Ja |
| Multi-User | Nein | Nein | Ja |

### Lizenz aktivieren (Online)

1. Kaufen Sie eine Subscription (Pro oder Enterprise)
2. Sie erhalten einen Aktivierungscode per E-Mail
3. Klicken Sie auf **License** in der Toolbar
4. Geben Sie den Aktivierungscode ein
5. Klicken Sie auf **Activate**
6. Die Lizenz wird an Ihre Hardware gebunden

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
- Aktueller Lizenz-Typ (Basic/Pro/Enterprise)
- Ablaufdatum der aktuellen Periode
- Hardware-ID
- Aktivierungscode

---

## 13. Fehlerbehebung & FAQ

### Häufige Probleme

#### "TIA Portal wird nicht gefunden"

**Ursache:** TIA Portal ist nicht installiert oder keine kompatible Version verfügbar.

**Lösung:**
1. Prüfen Sie, ob TIA Portal V15, V16, V17, V18, V19 oder V20 installiert ist
2. Stellen Sie sicher, dass die Openness-Komponenten installiert sind (Teil der TIA Portal Installation)

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

**© 2026 AnyAutomation. Alle Rechte vorbehalten.**

**Ende des Benutzerhandbuchs**
