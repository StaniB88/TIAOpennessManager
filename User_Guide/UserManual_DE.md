# TIA Openness Manager - Benutzerhandbuch

**Version:** 4.0
**Stand:** Mai 2026

---

## 0. Willkommen-Tab

### Was ist der Willkommen-Tab?

Der Willkommen-Tab ist das Erste, was Sie beim Start des TIA Openness Managers sehen. Er bündelt an einem Ort den Einstieg in eine neue Sitzung, eine kompakte Einführung in die wichtigsten Konzepte der Anwendung und den schnellen Wiedereinstieg in ein zuletzt genutztes Projekt. Der Tab ist nicht-modal — Sie können ihn parallel zu Ihrer Arbeit offen lassen oder schließen und später über das Hilfe-Menü wieder öffnen.

### Wann er sich öffnet

- **Beim ersten Start** öffnet sich der Willkommen-Tab automatisch.
- **Bei jedem weiteren Start** öffnet er sich so lange, bis Sie unten auf der Seite *„Willkommen-Seite beim Start anzeigen"* abwählen.
- **Jederzeit** können Sie ihn über **Hilfe → Willkommen-Guide** erneut öffnen. Ein erneutes Öffnen auf diesem Weg aktiviert die Startup-Einstellung nicht wieder.

### Schnellzugriff-Aktionen

Die linke Spalte bietet acht Abkürzungen für die häufigsten ersten Schritte:

- **Mit TIA Portal verbinden…** — auf eine laufende TIA-Portal-Instanz aufsetzen.
- **Neues TIA-Projekt…** — den Neues-Projekt-Wizard öffnen, um ein TIA-Projekt mit CPU, optionalen Modulen, Netzwerk und initialen Bausteinen anzulegen. TIA-Portal-Version direkt im Wizard wählen — keine vorherige Verbindung erforderlich. Siehe [Benutzerhandbuch → Neues-Projekt-Wizard](#4-projekt-management).
- **TIA-Projekt öffnen…** — eine `.ap1x`- / `.ap2x`-Projektdatei von der Platte wählen.
- **Export-Ordner auswählen…** — den Ordner festlegen, in den exportierte Blöcke geschrieben werden.
- **Git-Repository klonen…** — ein Repository direkt in der Anwendung klonen.
- **Neue SCL-Datei…** — einen leeren SCL-Editor-Tab öffnen.
- **Unit Testing…** — den Unit-Testing-Arbeitsbereich öffnen.
- **KI-Assistent konfigurieren…** — die KI-Chat-Einstellungen öffnen, um einen API-Schlüssel zu hinterlegen oder sich anzumelden.

### „Erste Schritte"-Anleitung

In der Mitte des Tabs finden Sie die interaktive **Erste Schritte**-Karte mit vier Schritten. Die Schritte haken sich automatisch ab, während Sie mit der Anwendung arbeiten:

1. **Mit TIA Portal verbinden** — wird abgehakt, sobald die Verbindung erfolgreich steht.
2. **Project Explorer kennenlernen** — erklärt die Checkboxen pro Zeile, den Unterschied zwischen *Export Selected* und *Export All*, die Protection-Spalte, an Import-/Export-Ordner gebundene Protection-Profile sowie Drag-&-Drop-Import. Ein Inline-Button öffnet den Protection-Profile-Speichern-Dialog; der Schritt wird abgeschlossen, sobald Sie ein Profil speichern (egal ob über diesen Button oder über Ihren normalen Project-Explorer-Ablauf).
3. **Ersten Baustein exportieren** — wird abgehakt, sobald ein Block-Export erfolgreich durchläuft.
4. **Nächsten Schritt wählen** — vier Buttons (Git, KI-Chat, Unit Testing, OPC UA) öffnen den jeweiligen Tab und schließen diesen Schritt ab.

Oben auf der Karte zeigt ein Fortschrittsbalken, wie viele Schritte bereits abgeschlossen sind. Unten auf der Karte setzt der Link **Anleitungs-Fortschritt zurücksetzen** alle vier Haken zurück, wenn Sie die Anleitung noch einmal durchlaufen wollen.

### Feature-Karten

Fünf Karten rechts im Tab beschreiben die Hauptbereiche der Anwendung. Ein Klick auf eine Karte öffnet den passenden Bereich:

- **KI-Chat** — öffnet den KI-Chat-Arbeitsbereich und den Einstellungsdialog.
- **Git-Versionsverwaltung** — öffnet den Git-Arbeitsbereich.
- **Unit Testing** — öffnet den Unit-Testing-Arbeitsbereich.
- **OPC-UA-Browser** — öffnet den OPC-UA-Arbeitsbereich.
- **Was ist neu in 3.x** — öffnet das mitgelieferte `CHANGELOG` mit den letzten nutzer-sichtbaren Änderungen.

### Zuletzt geöffnete Projekte

Die Liste **Zuletzt** zeigt bis zu fünf zuletzt geöffnete TIA-Projekte — neueste oben. Ein Klick auf einen Eintrag verbindet Sie direkt wieder damit. Einträge auf Projekte, die verschoben oder gelöscht wurden, werden automatisch ausgeblendet. Die Liste wird nach jedem erfolgreichen Verbindungsaufbau aktualisiert — egal ob Sie eine Projektdatei öffnen oder sich an eine laufende TIA-Portal-Instanz anhängen. Ist die Liste leer, bietet ein einzelner Inline-Link an, eine Verbindung zu starten.

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

### Anmelden

Beim ersten Start öffnet sich ein Anmelde-Dialog vor dem Hauptfenster. Klicken Sie auf **Sign in via browser** — Ihr Standard-Browser öffnet `tiaopenessmanager.ch/sign-in`, wo Sie Ihre E-Mail-Adresse und den 6-stelligen Verifizierungscode aus der zugesendeten E-Mail eingeben. Sobald der Browser den Vorgang bestätigt, schließt sich der Dialog automatisch und die Anwendung ist freigeschaltet.

Sie bleiben über App-Neustarts hinweg angemeldet; der nächste Start führt direkt zum Hauptfenster. Die Lizenz hängt am Account, nicht an einer bestimmten Maschine. Sie können sich auf bis zu drei verschiedenen Rechnern pro 30-Tage-Fenster anmelden.

Über **Einstellungen → License** wird das Lizenz-Panel geöffnet, das die angemeldete E-Mail, die aktive Tier-Stufe und einen **Sign out**-Button anzeigt. Beim Klick erscheint ein Bestätigungsdialog ("Abmelden und diese Maschine freigeben?") — ein versehentlicher Klick gibt die Maschinen-Bindung also nicht sofort frei. **Sign out** bestätigt, **Cancel** lässt die Anmeldung bestehen. Beim Abmelden wird die aktuelle Maschinen-Bindung freigegeben, sodass ein Kollege übernehmen kann. Die Anwendung benötigt eine aktive Anmeldung: unmittelbar nach dem Abmelden öffnet sich der Sign-In-Dialog erneut. Erneut anmelden um weiterzuarbeiten oder den Dialog schliessen um die Anwendung zu beenden.

Falls die Anmeldung wiederholt scheitert, prüfen Sie, dass Ihr Netzwerk `tiaopenessmanager.ch` erreichen kann. Firmen-Firewalls mit TLS-Inspection benötigen ggf. eine Ausnahme (siehe „Cert-Pin-Bypass" im Troubleshooting-Abschnitt).

Wenn der Lizenzserver beim Start nicht erreichbar ist (kein Internet, VPN nicht verbunden, Serverausfall), erscheint ein Dialog mit drei Optionen: **Erneut versuchen** versucht die Verbindung erneut, **Offline fortfahren** öffnet die Anwendung mit der gecachten Lizenz und der 14-Tage-Grace-Period (einige Funktionen sind ggf. bis zur nächsten erfolgreichen Anmeldung nicht verfügbar), und **Anwendung schliessen** beendet das Programm. Offline-Modus erteilt nie mehr Rechte als die letzte erfolgreiche Online-Prüfung; Subscription-Zugriff ist auf 14 Tage begrenzt, und es können weder neue Trials gestartet noch neue Lizenzen aktiviert werden solange offline.

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
│             │  [Project] [Import/Export] [Compare]           │
│  Projekt-   │  [Find Unused] [Find in Project] [Hardware]    │
│  Baum       │  [Vault]                                       │
│             ├───────────────────────────────────────────────┤
│  (Links)    │              Tab-Inhalt                       │
│             │                                               │
├─────────────┴───────────────────────────────────────────────┤
│  Unteres Panel: [Log Output] [Terminal] [Git Output] …      │
├─────────────────────────────────────────────────────────────┤
│  Statusleiste: ● Verbunden | Statusnachricht | Lizenz: ● Pro │
└─────────────────────────────────────────────────────────────┘
```

### Linker Bereich - Projektbaum

- Zeigt die Struktur des geöffneten TIA Portal Projekts
- Hierarchie: Projekt → Hardware → Source → PLC → Blocks/Datatypes/Tags
- Checkboxen ermöglichen Mehrfachauswahl für Export

### Rechter Bereich - Tabs

- **Project** - Code-Editor für ausgewählte Blöcke
- **Import/Export** - Haupt-Arbeitsbereich für Datei-Operationen
- **Compare** - Nebeneinander-Bausteinvergleich
- **Find Unused** - Dead-Code-Erkennung und Aufräumen
- **Find in Project** - Projektweite Symbol- und Referenzsuche
- **Hardware** - Geräteliste mit PROFINET-Namen und IP-Konfiguration
- **Vault** - Verschlüsselte Anmeldedaten-Verwaltung

### Menüleiste

| Menü | Wichtige Einträge |
|------|-------------------|
| File | Connect, Browse Folder, Archive Project, Disconnect, Exit |
| Project | Rescan PLC, Save, Compile, Safety Login/Logoff |
| View | Settings, Terminal, Import/Export Settings, Protection Profiles Folder, Vollbild, Tastaturkürzel |
| Help | Documentation, Release Notes, Problem melden, About |

### Benutzerhandbuch-Fenster

Öffnen Sie dieses Handbuch über **Hilfe → Dokumentation**. Das Benutzerhandbuch-Fenster passt sich dem App-Theme an, zeigt links ein an der Seite fixiertes Inhaltsverzeichnis und unterstützt:

- **Suchen** — über die Schaltfläche „Suchen" (oder Strg+F) eine seiteninterne Suche öffnen. Enter springt zum nächsten Treffer, Umschalt+Enter zum vorherigen, Esc schliesst die Suchleiste.
- **Zoom** — `−` / `+` schalten in 25%-Schritten zwischen 50 und 200%.
- **Sprache** — über das Dropdown ohne Seitenwechsel zwischen Deutsch und Englisch umschalten.
- **Code-Hervorhebung** — Code-Blöcke werden passend zum aktiven Theme syntaktisch hervorgehoben.

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

Das untere Panel enthält:
- **Log Output** - Anwendungs-Logmeldungen mit farbcodierter Schwere
- **Terminal** - Integriertes Terminal für Kommandozeilen-Operationen
- **Git Output** - Ausgabestrom der Git-Operationen
- **Probleme** - Diagnose über alle offenen Editor-Dateien; jede Zeile zeigt Dateiname mit Zeile und Spalte, und ein Klick springt im Editor an genau diese Stelle
- **Referenzen** - vom Language Service ermittelte Symbol-Referenzen

Das Panel kann mit den Steuerelementen in der oberen rechten Ecke eingeklappt, erweitert oder maximiert werden. Der Nebeneinander-Bausteinvergleich (**Compare**) liegt jetzt im Workspace-Dock neben **Import/Export** — Sie öffnen ihn über das Workspace-Ansichtsmenü.

### Werte aus Datenfeldern kopieren

Schreibgeschützte Datenfelder in der gesamten Anwendung können mit der Maus markiert und mit **Strg+C** wie ein normales Texteingabefeld kopiert werden. Das umfasst CPU-Identität (MLFB, Seriennummer, Firmware), OPC UA Diagnose (Server-Build, Sitzungszähler, Capabilities), Lizenzinformationen (Konto-E-Mail, Hardware-ID, Ablaufdatum), Verbindungsdetails (Endpunkt-URL, IP-Adresse, Sicherheitsmodus), MCP-Sitzungs-IDs sowie Fehler- und Statusmeldungen. Statische Feldbezeichnungen sind nicht markierbar; die Werte schon.

### Zeilen aus Tabellen kopieren

Tabellen in den OPC UA Panels (Node Attributes, References, Struct Fields, Diagnostics Buffer, Event Log, Server Diagnostics, Type Definitions, Watch Table, Endpoint List) unterstützen das Kopieren ganzer Zeilen: Eine Zeile mit einem Klick auswählen, mit **Shift** oder **Strg** mehrere Zeilen markieren (wo unterstützt), und mit **Strg+C** als tab-separierte Werte inklusive Spaltenüberschriften in die Zwischenablage kopieren. Anschliessend in eine Tabellenkalkulation, einen Texteditor, ein Ticket oder einen Chat einfügen.

---

## 3a. Schnellzugriff (Quick Open)

### Was ist die Schnellzugriff-Leiste?

Die Schnellzugriff-Leiste (Quick Open Bar) ist ein Suchfeld in der Titelleiste der Anwendung. Sie ist der schnellste Weg, in der Anwendung zu navigieren — zu einem Befehl, einem PLC- oder HMI-Symbol, einer Datei im Arbeitsverzeichnis, einem Git-Branch oder zu einer bestimmten Zeile im aktiven Code-Editor — ohne die Tastatur zu verlassen oder durch Menüs und Bäume zu klicken.

### Schnellzugriff öffnen

- Drücken Sie **Strg+Umschalt+P** an beliebiger Stelle der Anwendung. Das Suchfeld erhält den Fokus und wird mit **`>`** vorbelegt, sodass die Befehlsliste sofort erscheint.
- Klicken Sie in der Titelleiste in das Suchfeld. Es ist kein Präfix vorgewählt; tippen Sie ein Präfix (oder `?`), um eine Kategorie zu wählen.

Das Popup mit den Treffern öffnet sich, sobald das Suchfeld den Fokus bekommt, und bleibt offen, während Sie tippen. **Esc** schließt es; ein Klick außerhalb des Popups ebenfalls.

### Discovery-Liste (Klick auf die Leiste)

Wenn Sie ohne Tastenkürzel in das Suchfeld klicken, öffnet sich das Popup mit einer **Discovery-Liste**, die sieben Einträge anzeigt — einen pro Kategorie — jeweils mit Beschreibung und auslösendem Präfix:

- **Datei öffnen** — kein Präfix, zuletzt geöffnete und aus dem Arbeitsverzeichnis erreichbare Workspace-Dateien
- **Befehle anzeigen und ausführen** — Präfix `>`
- **Symbol im aktiven Tab** — Präfix `@`
- **Symbol im gesamten Workspace** — Präfix `#`
- **Git-Branch wechseln** — Präfix `git:`
- **Zu Zeile im Editor springen** — Präfix `:`
- **Mehr** — Präfix `?` (öffnet die vollständige Hilfe-Liste)

Unterhalb der Discovery-Liste werden zusätzlich Ihre **zuletzt geöffneten Dateien** gezeigt, damit der häufigste Treffer einen Klick entfernt ist. Klicken Sie eine Discovery-Zeile an, um das Suchfeld mit dem zugehörigen Präfix zu füllen und unter dieser Kategorie weiterzutippen, oder drücken Sie Enter auf einer kürzlich geöffneten Datei, um sie direkt zu öffnen.

### Präfixe

Das erste Zeichen Ihrer Eingabe wählt die Suchkategorie aus. Tippen Sie `?` und drücken Sie Enter auf einer Zeile, um das Präfix einzufügen, und tippen Sie weiter.

| Präfix | Sucht | Beispiel |
|--------|-------|----------|
| `>` | **Befehle** — alle Aktionen aus Menüs, Symbolleisten und globalen Tastaturkürzeln | `>compile`, `>save` |
| `@` | **Symbole im aktiven Kontext** — PLC-Symbole im TIA-Arbeitsbereich, HMI-Items im Screen-Editor, Testfälle im Unit Testing, Signale im Trace, OPC-UA-Knoten bei aktiver Verbindung | `@motor`, `@start` |
| `#` | **Symbole im gesamten Workspace** — gleiche Quellen wie `@`, jedoch nicht auf den aktiven Tab gefiltert | `#fb_motor` |
| `git:` | **Git-Branches** — lokale und Remote-Branches im offenen Repository | `git:main`, `git:feature/x` |
| `?` | **Hilfe** — listet alle Präfixe mit einer Kurzbeschreibung; Enter füllt das Suchfeld mit dem gewählten Präfix und hält das Popup offen | `?` |
| `:` | **Gehe zu Zeile** — springt im aktiven Code-Editor zur angegebenen Zeile; nur verfügbar, wenn ein Editor-Tab den Fokus hat | `:42` |

Ohne Präfix sucht die Leiste in zuletzt geöffneten Dateien und in den Workspace-Dateien, die über das aktuell konfigurierte Arbeitsverzeichnis erreichbar sind.

### Tastaturbedienung

- **Pfeil hoch / runter** — Auswahl in der Trefferliste verschieben.
- **Enter** — markierten Eintrag ausführen.
- **Esc** — Popup schließen.
- **Einfacher Mausklick** — führt eine Zeile sofort aus (entspricht Markieren + Enter).

Mit Enter wird sofort der oberste Treffer ausgeführt — der erste Eintrag ist bei jeder Aktualisierung vorausgewählt.

### Was bei Auswahl eines Treffers passiert

Jeder Treffertyp hat seine eigene Aktion. Die meisten Aktionen wechseln zusätzlich den aktiven Arbeitsbereich, wenn das Ziel anderswo liegt.

| Treffertyp | Aktion bei Enter / einfachem Klick |
|------------|------------------------------------|
| Befehl | Führt den Befehl aus (öffnet z.B. einen Dialog, startet einen Export). |
| Gehe-zu-Zeile | Springt im aktiven Code-Editor zur angegebenen Zeile. |
| Hilfe | Füllt das Suchfeld mit dem gewählten Präfix; Popup bleibt offen, damit Sie weitertippen können. |
| PLC-Symbol | Wechselt in den TIA-Manager-Arbeitsbereich und markiert das Symbol im Projektbaum. |
| Screen-Symbol | Wechselt in den Screen-Editor und markiert das passende Item. |
| Unit-Test-Symbol | Wechselt zu Unit Testing und öffnet das Test-Suite-Dokument. *Die Auswahl des einzelnen Testfalls in der Suite folgt in einer späteren Version.* |
| OPC-UA-Knoten | Wechselt in den PLC-Online-Arbeitsbereich. *Die Auswahl des passenden Knotens im Adressraum-Baum folgt in einer späteren Version.* |
| Git-Branch | Checked den Branch aus (nur lokale, nicht aktive Branches). Remote-Branches und der aktuell ausgecheckte Branch verwenden den bestehenden Checkout-Dialog. |
| Trace-Signal | Wechselt in den Trace-Arbeitsbereich. *Die Auswahl des passenden Signals in der Liste folgt in einer späteren Version.* |
| Zuletzt geöffnete Datei / Workspace-Datei | Öffnet die Datei in einem Code-Editor-Tab. |

### Zuletzt verwendete Treffer

Die Schnellzugriff-Leiste merkt sich Ihre zuletzt gewählten Einträge über Anwendungs-Neustarts hinweg, sodass die Dinge, die Sie am häufigsten brauchen, oben in der Liste stehen. Es werden bis zu 50 Einträge gehalten; ältere als 30 Tage werden automatisch entfernt.

### Verhältnis zur Git-Befehlspalette

Der Git-Arbeitsbereich besitzt seine eigene **Strg+Umschalt+P**-Befehlspalette (siehe [Git-Client](#14a-git-client) → *Befehlspalette*) mit 14 Git-spezifischen Aktionen. Beide Tastaturkürzel existieren parallel: Die Git-Befehlspalette ist auf den Arbeitsbereich beschränkt und hat Vorrang, wenn der Git-Tab den Fokus hat; die globale Schnellzugriff-Leiste sitzt in der Titelleiste und ist aus jedem anderen Arbeitsbereich erreichbar.

---

## 3b. Tastenkombinationen

### Tastenkürzel-Übersicht öffnen

Drücken Sie **Strg+K, Strg+S** an einer beliebigen Stelle in der Anwendung, um den Dialog **Tastenkombinationen** zu öffnen. Er listet alle Belegungen, auf die die App reagiert, gruppiert nach Bereich:

- **Allgemein** — anwendungsweite Belegungen: Projekt speichern, Einstellungen, Terminal, Arbeitsbereichswechsel, im Projekt suchen, Tastenkürzel-Übersicht selbst.
- **Editor** — Belegungen, die auf den aktiven Code-Editor und sein Inline-Edit-Overlay wirken.
- **Git** — Belegungen innerhalb des Git-Arbeitsbereichs (Tabs, Branches, Working Copy, Verlauf, Diff).
- **KI-Chat** — Schnellumschalt-Tastenkürzel innerhalb des KI-Chat-Panels.
- **Vergleich** — Belegungen innerhalb des Compare-Arbeitsbereichs.

Jede Zeile zeigt die Tastenkombination und eine kurze Beschreibung; ein Suchfeld oben filtert nach beidem. Derselbe Dialog ist über **Ansicht → Tastenkombinationen** erreichbar.

### Häufig benötigte Tastenkombinationen

| Tastenkombination | Aktion |
|-------------------|--------|
| **Strg+1 … Strg+8** | Arbeitsbereich wechseln (TIA Manager, Versionsverwaltung, PLC Online, Explorer, Bildschirm-Editor, Unit Testing, Trace, KI-Agent) |
| **Strg+Alt+1 … Strg+Alt+9** | Aktiven Assistenten innerhalb des KI-Chat-Panels umschalten |
| **Strg+S** | Aktiven Editor speichern; im Git-Diff den fokussierten Hunk stagen; in Compare die fokussierte Seite speichern |
| **Strg+Umschalt+S** | TIA-Portal-Projekt speichern |
| **Strg+K, Strg+S** | Diesen Tastenkombinationen-Dialog öffnen |
| **Strg+R** (Git-Tab) | Aktives Git-Repository aktualisieren |
| **Strg+Ö** | Integriertes Terminal umschalten |
| **F1** | Benutzerhandbuch öffnen |
| **F5** | TIA-Portal-Projekt neu einlesen |
| **F11** | Vollbildmodus umschalten |
| **Strg+Umschalt+F** | Referenzen im aktuellen Projekt suchen |

Wird eine Tastenkombination für zwei verschiedene Bereiche angezeigt (etwa **Strg+S** für *Projekt speichern* und *Hunk stagen*), entscheidet der Tastatur-Fokus, welche Belegung tatsächlich ausgeführt wird.

---

## 3c. Rechtsklick-Kontextmenüs

Jede Tabelle, jedes auswählbare Text-Feld und jede Baumansicht der Anwendung öffnet bei Rechtsklick ein Kontextmenü. Die Menüs sind in der Applikations-Sprache lokalisiert (Englisch / Deutsch / Französisch / Italienisch).

### Gemeinsame Standardeinträge (greifen auf jeder Tabelle / Text-Feld / Baum)

| Oberfläche | Einträge |
|------------|----------|
| Beliebige Tabelle | Zelle kopieren · Zeile kopieren · Alles als CSV kopieren · Alles auswählen |
| Beliebiges auswählbares Text-Feld | Kopieren · Kopieren (in Anführungszeichen) · Alles auswählen |
| Beliebige Baumansicht | Name kopieren · Alle ausklappen · Alle einklappen |

- **Zelle kopieren** — kopiert den Wert der Zelle unter dem Mauszeiger.
- **Zeile kopieren** — kopiert alle Spalten der ausgewählten Zeile als Tab-getrennten Text.
- **Alles als CSV kopieren** — kopiert sämtliche sichtbaren Zeilen inkl. Spaltenüberschriften im RFC-4180-CSV-Format. Bei sehr grossen Tabellen wird auf 10 000 Zeilen begrenzt; die Begrenzung erscheint im Log.
- **Kopieren (in Anführungszeichen)** — umschliesst die Auswahl (oder den ganzen Text) mit doppelten Anführungszeichen; nützlich beim Einfügen einer E-Mail oder eines Pfades in einen Satz.

### Feature-spezifische Einträge

Zusätzlich zu den Standardeinträgen bieten einige Oberflächen Aktionen, die zu ihrem Inhalt passen:

- **OPC UA — References-Tabelle** (PLC Online → References-Dock): NodeId kopieren · BrowseName kopieren · Als JSON kopieren · Abonnieren (fügt den referenzierten Knoten der Watch-Liste hinzu).
- **Compare — Dateilisten** (linke und rechte Liste): Vollen Pfad kopieren · Dateinamen kopieren · Ordner öffnen (Datei-Explorer „Datei markieren"-Modus) · Entfernen aus dem Vergleich.
- **Projektbaum** (TIA-Manager): Name kopieren · Nummer kopieren direkt nach Im Editor öffnen / Referenzen suchen im bestehenden Menü.
- **Git Blame** — der SHA-Badge bietet SHA kopieren (kurz, erste 8 Zeichen) und SHA kopieren (vollständig); der Betreff bietet Kopieren.
- **Git Commit-Detail** — der SHA bietet das gleiche Kurz/Voll-Paar; der Autor-Block bietet Name kopieren · E-Mail kopieren · „Name &lt;E-Mail&gt;" kopieren.

Rechtsklick in Code-Editoren (SCL-Editor, Diff-Ansicht, Blame-Inhalt, Git-Kommando-Ausgabe) behält das editor-eigene Ausschneiden/Kopieren/Einfügen-Menü — die neuen Menüs überschreiben es nicht. Textfelder (Eingabefelder) behalten das systemeigene Ausschneiden/Kopieren/Einfügen-Flyout.

---

## 3d. Datei-Explorer

Der Explorer-Arbeitsbereich (Strg+4) ist der Dateibaum auf der linken Seite. Er öffnet beliebige Ordner auf der Festplatte, zeigt Dateien und Unterordner und ermöglicht Erstellen, Umbenennen, Löschen, Verschieben und Suchen — und wenn der Ordner eine Git-Arbeitskopie ist, zeigt er dieselben Status-Markierungen wie ein Git-Client oder VS Code.

### Ordner öffnen

- Klick auf das Ordner-Symbol in der Toolbar (rechts) oder den „Ordner öffnen"-Button in der leeren Ansicht.
- Der Explorer merkt sich sonst nichts über den Ordner — er liest das Dateisystem jedes Mal neu und aktualisiert sich automatisch, sobald sich Dateien auf der Festplatte ändern.

### Toolbar

| Symbol | Aktion |
|--------|--------|
| ➕📄 | Neue Datei im ausgewählten Ordner (oder im Root, wenn nichts ausgewählt ist) |
| ➕📁 | Neuer Ordner im ausgewählten Ordner (oder im Root) |
| ↻ | Baum aktualisieren |
| ⌃ | Alle Ordner zuklappen |
| 👁 | Von Git ignorierte Dateien anzeigen / ausblenden |
| 📄 | Einzelne Datei öffnen, ohne den geöffneten Ordner zu wechseln |
| 📁 | Anderen Ordner öffnen |

### Datei- und Ordner-Symbole

Jede Zeile erhält ein Symbol passend zur Dateiendung oder zum Ordnernamen:

- Code-Dateien (`.cs`, `.scl`, `.xml`, `.axaml`, `.json`, `.html`, `.js`, `.ts`, `.py`, …) und bekannte Config-Dateien (`.csproj`, `.sln`, `.yaml`, `.toml`, `.ini`) erhalten eigene Symbole.
- Medien (`.png`, `.jpg`, `.svg`, `.mp4`, `.wav`), Archive (`.zip`, `.tar`, `.7z`), Skripte (`.exe`, `.dll`, `.bat`, `.ps1`, `.sh`) und Git-Config-Dateien (`.gitignore`, `.gitattributes`, `.gitmodules`) haben jeweils ein eigenes Glyph.
- Ordner mit Namen wie `src`, `lib`, `docs`, `tests`, `node_modules`, `.git`, `.vscode`, `scripts`, `assets`, `.worktrees` erhalten ebenfalls passende Symbole.

### Git-Status

Wenn der geöffnete Ordner in einem Git-Repository liegt, zeigt der Explorer den Working-Tree-Status für jede sichtbare Datei und jeden sichtbaren Ordner:

- **Glyph-Badge** rechts in der Zeile zeigt den Änderungs-Typ mit einem farbigen 14×14-Symbol: `±` modifiziert, `+` hinzugefügt, `−` gelöscht, `➜` umbenannt, `❏` kopiert, `★` untracked, `!` Konflikt, `T` Typ-Änderung. Der Badge-Tooltip nennt den Status in Ihrer UI-Sprache.
- **Folder-Bubble-Up:** ein Ordner erbt den *schlechtesten* Status aller darin enthaltenen Dateien und zeigt denselben Badge mit reduzierter Deckkraft, sodass eine einzelne modifizierte Datei tief im Baum von der Wurzel aus sichtbar bleibt.
- **Dateinamen** bleiben in der Standard-Textfarbe; der Status wird allein durch das Badge getragen.
- **Ignorierte Dateien** (von `.gitignore` erfasst) erscheinen in gedämpfter Farbe. Mit dem 👁-Toolbar-Toggle werden sie komplett ausgeblendet — die Auswahl bleibt sitzungsübergreifend erhalten.
- Der Explorer überwacht `.git/index` und `.git/HEAD` und aktualisiert die Status-Markierungen automatisch nach Stage, Commit, Branch-Wechsel oder anderen Git-Operationen außerhalb des TIA Openness Managers.

### Solution-Panel

Enthält der geöffnete Ordner eine `.sln`-Datei, erscheint unterhalb des Datei-Baums ein **Solution**-Panel mit allen C#-Projekten der Solution:

- **Frameworks** — jedes Ziel-Framework, für das das Projekt kompiliert (Multi-Targets werden aufgeteilt).
- **Pakete** — jeder NuGet `<PackageReference>` mit deklarierter Version.
- **Analysatoren** — Pakete, die Analyzer/Source-Generatoren beisteuern, erkannt aus expliziten `<Analyzer>`-Items, `PrivateAssets="all"` plus Name-Suffix wie `.Analyzers`, oder einer kuratierten Whitelist (StyleCop, .NET Analyzers, Roslynator, xUnit Analyzers, …). Transitive Analyzer aus SDK-Defaults werden nicht aufgelistet; der Empty-State weist explizit darauf hin, dass es sich um eine Best-Effort-Erkennung handelt.
- **Projekte** — jeder `<ProjectReference>` aufgelöst auf den Projektnamen.

Ein Refresh-Button in der Panel-Toolbar parst alles auf Anforderung neu; das Panel aktualisiert sich zudem automatisch, sobald sich `.sln` oder `.csproj` auf der Festplatte ändern (500 ms entprellt). Hat der geöffnete Ordner keine `.sln`, wird das Panel komplett ausgeblendet und der Datei-Baum nutzt die gesamte Panel-Höhe; sobald eine `.sln` erkannt wird, erscheint das Panel wieder. Doppelklick auf die Solution-Zeile oder einen Projekt-Eintrag öffnet die zugehörige `.sln`- bzw. `.csproj`-Datei im Editor.

### Sprach-spezifische Datei-Icons

Dateien im Explorer-Baum und im Solution-Panel zeigen das echte Brand-Glyph ihrer Sprache — das C#-Logo für `.cs` / `.csproj` / `.sln`, das TypeScript-Logo für `.ts` / `.tsx`, die Logos für JavaScript / Python / Rust / Go / Java / Kotlin / Swift / C / C++ / Ruby / PHP / Lua / R bei passender Erweiterung, die HTML5- / CSS3- / Sass-Marken für Web-Quellen, JSON- / YAML- / XML- / Markdown-Badges für Daten und Doku, die Shell- / Bash- / PowerShell-Prompts für Skripte, den Docker-Wal für `Dockerfile` und `.dockerignore` sowie das Git-Logo für `.gitignore` / `.gitattributes` / `.gitmodules`. Jedes Glyph wird in der Brand-Farbe der Sprache eingefärbt (C# Lila, TS Blau, JS Gelb, Python Blau, Rust Orange, Go Cyan, SCL/AWL/STL Siemens-Orange, …). Dateien ohne registrierte Sprache fallen auf das generische Datei-Glyph in der neutralen Sekundärtextfarbe zurück; ignorierte Dateien bleiben unabhängig von der Sprache gedämpft.

### Mehrfach-Auswahl

- **Klick** wählt eine Zeile aus.
- **Strg+Klick** schaltet die Auswahl einer weiteren Zeile um.
- **Umschalt+Klick** wählt einen zusammenhängenden Bereich aus.
- Ausgewählte Zeilen werden bei Löschen und Ziehen gemeinsam berücksichtigt.

### Datei öffnen

- **Doppelklick** auf eine Datei im Baum öffnet sie im Editor.
- Ordner-Zeilen werden bei Doppelklick aufgeklappt bzw. zugeklappt.

### Neue Datei oder Ordner anlegen

- Klick auf den ➕📄- oder ➕📁-Button, oder Rechtsklick und **Neue Datei** / **Neuer Ordner** wählen.
- Ein kleiner Dialog fragt nach dem Namen. Das neue Element wird im aktuell ausgewählten Ordner (oder im Root, falls nichts ausgewählt ist) angelegt und öffnet sich sofort im Editor, wenn es eine Datei ist.

### Umbenennen

- Zeile auswählen und **F2** drücken, oder Rechtsklick und **Umbenennen** wählen.
- Der Name wird zu einem Inline-Textfeld. Bei Dateien mit Erweiterung wählt der Cursor nur den Basis-Namen aus, damit das Tippen den Namen sofort ersetzt, ohne die Erweiterung zu stören.
- **Enter** committet den neuen Namen, **Esc** bricht ab, ein Klick außerhalb committet ebenfalls.
- Leere Namen, Namen mit ungültigen Pfad-Zeichen oder Namen, die mit einem bereits existierenden Geschwister kollidieren, werden stillschweigend abgelehnt.

### Löschen

- Eine oder mehrere Zeilen auswählen und **Entfernen** drücken, oder Rechtsklick und **Löschen** wählen.
- Ein Bestätigungsdialog erscheint mit der Anzahl der Elemente und der Gesamtzahl der enthaltenen Einträge (z. B. „3 Elemente löschen (47 Einträge)?"), damit ein rekursives Löschen nie mit unerwarteter Reichweite überrascht.
- Bestätigung verschiebt Dateien und Ordner in den Windows-Papierkorb (unter Windows), damit versehentliche Löschungen wiederhergestellt werden können. Symlinks und Junctions werden als Link selbst gelöscht, nie als Link-Ziel.
- Der Baum wird automatisch nach der Operation aktualisiert.

### Verschieben per Drag & Drop

- Eine Zeile gedrückt halten und auf einen Ordner *im selben Baum* ziehen, um sie dorthin zu verschieben.
- Die Drop-Markierung aktiviert sich nur, wenn das Ziel ein Ordner ist, nicht die Quelle selbst und nicht innerhalb des Quell-Teilbaums liegt — ein Ordner kann also nicht versehentlich in seine eigenen Kinder gezogen werden.
- Mehrere ausgewählte Zeilen werden gemeinsam verschoben; die Ziel-Datei oder der Ziel-Ordner darf nicht bereits existieren.

### Aus dem Explorer in ein anderes Fenster ziehen

- Ziehen aus dem Explorer in den Chat-Eingabe-Bereich hängt die ausgewählten Dateien an die nächste Nachricht an.
- Ziehen in den Windows-Explorer erstellt Kopien im Zielordner.

### Suchen und Filtern

- **Strg+F** im fokussierten Explorer-Panel klappt die Suchleiste oberhalb des Baums ein; das Feld erhält automatisch Fokus, der bestehende Inhalt ist vorselektiert.
- **Esc** im Suchfeld oder Klick auf das **X**-Button schliesst die Leiste und leert die Eingabe.
- Die Suche prüft den Datei- oder Ordnernamen, case-insensitive, an beliebiger Stelle im Namen. Ordner bleiben sichtbar, solange ein Nachkomme matched, und passende Nachkommen werden automatisch aufgeklappt, damit die Treffer im Blick sind.
- Leeren des Felds stellt den vollständigen Baum wieder her.
- Der `.gitignore`-Filter und der Such-Filter kombinieren sich: wenn „Von Git ignorierte Dateien anzeigen" aus ist, werden ignorierte Dateien auch aus den Suchergebnissen ausgeschlossen.

### Rechtsklick-Kontextmenü

| Eintrag | Aktion |
|---------|--------|
| Neue Datei | Datei in diesem Ordner erstellen |
| Neuer Ordner | Unterordner erstellen |
| Umbenennen | Inline-Umbenennen starten (wie F2) |
| Löschen | Datei oder Ordner entfernen (mit Bestätigung) |
| Im Explorer anzeigen | Übergeordneten Ordner im Windows-Explorer öffnen, Datei markiert |
| Pfad kopieren | Absoluten Pfad in die Zwischenablage kopieren |
| Relativen Pfad kopieren | Pfad relativ zum geöffneten Wurzelordner in die Zwischenablage kopieren |

---

## 3e. Arbeitsbereich-Layout

Der Arbeitsbereich zeigt Werkzeuge (Projekt-Explorer, Datei-Explorer) und Dokumente (Editor, Import/Export, Find Unused, Find in Project, Hardware, Tresor) in einer flexiblen Dock-Anordnung. Sie können jedes Panel umsortieren und das Ergebnis in einer Datei persistieren, die sich später wieder laden oder mit Kollegen teilen lässt.

### Panels umsortieren

- **Tab-Header ziehen** dockt das Panel an einen anderen Rand des Arbeitsbereichs, splittet eine bestehende Region oder kombiniert es als Tab-Gruppe mit einem anderen Panel.
- **Tab-Header aus dem Hauptfenster ziehen** löst ihn als freistehendes Fenster ab. Das schwebende Fenster bleibt synchron zum Projekt und lässt sich an seiner Titelleiste zurück in eine Andock-Hilfslinie ziehen.
- **Splitter zwischen zwei Regionen ziehen** ändert deren Grössenverhältnis.
- **Pin-Symbol** an einem Werkzeug-Tab klappt es auf einen seitlichen Streifen ein; ein erneuter Klick stellt das volle Panel wieder her.
- **Tab schliessen** über die Schliessen-Schaltfläche oder per Mittelklick. Geschlossene Dokumente und Werkzeuge werden ausgeblendet, nicht gelöscht — sie lassen sich über das **Ansicht**-Dropdown in der Arbeitsbereich-Symbolleiste (oben rechts) wieder einblenden.

### Ansicht-Dropdown

Das **Ansicht**-Dropdown (oben rechts in der Arbeitsbereich-Symbolleiste) schaltet einzelne Panels ein und aus. Ein Klick auf einen Eintrag blendet ein verstecktes Panel ein oder ein sichtbares aus:

| Gruppe | Einträge |
|--------|----------|
| Werkzeuge | Projekt-Explorer, Datei-Explorer |
| Dokumente | Editor, Import / Export, Unbenutzte finden, Im Projekt suchen, Hardware, Tresor |

### Arbeitsbereich-Dropdown

Das **Arbeitsbereich**-Dropdown (neben **Ansicht**) bündelt drei Aktionen, die auf die gesamte Dock-Anordnung des Haupt-Arbeitsbereichs wirken:

| Eintrag | Wirkung |
|---------|---------|
| Arbeitsbereich speichern unter… | Speichert das aktuelle Dock-Layout (Panel-Positionen, Splitter-Verhältnisse, Tab-Reihenfolge, schwebende Fenster) in eine `.tiamgr-workspace`-Datei. Die Datei ist ein kleines JSON-Dokument, das sich zwischen Maschinen kopieren oder als Teil eines Team-Setups versionieren lässt. |
| Arbeitsbereich laden… | Öffnet eine `.tiamgr-workspace`-Datei und wendet sie auf das aktuelle Hauptfenster an. Geöffnete Dokumente werden wiederverwendet; ihre visuelle Anordnung entspricht der Datei. |
| Arbeitsbereich zurücksetzen | Stellt die werkseitige Dock-Anordnung wieder her. Ein Bestätigungsdialog fragt vor der Änderung. Geöffnete Dokumente und Werkzeuge bleiben verfügbar — nur ihre Position wird zurückgesetzt. |

Das Arbeitsbereich-Dropdown wirkt nur auf das Layout. Projekt-Inhalte (Dateien, Bausteine, Einstellungen) werden weder von Speichern noch von Laden oder Zurücksetzen beeinflusst.

### Was wird gespeichert und was nicht

Wird in der `.tiamgr-workspace`-Datei gespeichert:

- Position und Ausrichtung jedes Werkzeug- und Dokument-Panels
- Breite-/Höhe-Verhältnisse zwischen Regionen
- Tab-Gruppierung und aktiver Tab pro Region
- Ob ein Werkzeug angepinnt, schwebend oder angedockt ist
- Aktives Dokument und aktives Werkzeug zum Zeitpunkt des Speicherns

Wird nicht gespeichert:

- Dokument-Inhalte (diese liegen im TIA-Portal-Projekt und in den Quelldateien)
- Editor-Scrollposition oder Auswahl innerhalb eines Dokuments
- Inhalt der KI-Chat-Seitenleiste
- Verbindungsstatus, Lizenz, Einstellungen

---

## 4. Projekt-Management

### Neues-Projekt-Wizard

Der Neues-Projekt-Wizard legt ein vollständiges TIA-Portal-Projekt an — mit CPU, optionalen Modulen, Netzwerk und initialen Programmbausteinen — ohne dass Sie den TIA Openness Manager verlassen müssen.

**Wizard öffnen:**

- Im **Willkommen**-Tab klicken Sie in der Schnellzugriff-Spalte auf **Neues TIA-Projekt…**.
- Der Wizard öffnet sich direkt. Sie müssen nicht vorher mit TIA Portal verbunden sein — wählen Sie die Version in Schritt 1; beim Klick auf **Weiter** wird die passende TIA-Portal-Instanz automatisch gestartet. Während des Starts zeigt der Wizard ein „TIA Portal V… wird gestartet…"-Overlay; die Katalog-Suche in Schritt 2 funktioniert, sobald das Overlay verschwindet.

**Schritt 1 — Projekt-Info:**

1. Wählen Sie die **TIA-Portal-Version** (V15…V21) — wenn bereits eine Instanz verbunden ist, wird deren Version vorausgewählt.
2. Geben Sie einen **Projektnamen** ein (bis zu 60 Zeichen; die üblichen Dateisystem-Zeichen `\\ / : * ? " < > |` sind nicht erlaubt).
3. Klicken Sie auf **Durchsuchen…**, um ein **Zielverzeichnis** zu wählen (muss ein absoluter Pfad auf einem lokalen Laufwerk sein — UNC-Pfade werden abgelehnt).
4. Optional **Autor** und **Kommentar** eingeben.

Falls Sie beim Klick auf **Weiter** mit einer anderen TIA-Portal-Version verbunden sind, fragt der Wizard zuerst nach Bestätigung, bevor die laufende Sitzung getrennt und die gewählte Version gestartet wird.

**Schritt 2 — CPU:**

1. Geben Sie einen Suchbegriff im **Hardware-Katalog**-Feld ein (zum Beispiel `1516` oder `S7-1500`).
2. Wählen Sie die gewünschte CPU aus der Trefferliste. F-CPUs werden zwar gelistet, sind aber nicht auswählbar — Safety-Konfiguration wird vom Wizard nicht unterstützt und muss manuell in TIA Portal erfolgen.
3. Geben Sie einen **Gerätenamen** ein (Standardwert `PLC_1`).

**Schritt 3 — Module (optional):**

Fügen Sie I/O-Module, Kommunikationsprozessoren oder andere rack-fähige Komponenten hinzu:

1. Klicken Sie auf **Modul hinzufügen**, durchsuchen Sie den Katalog und wählen Sie das Modul.
2. Geben Sie eine **Slot**-Nummer ein.
3. Wiederholen Sie den Vorgang für weitere Module. Namen müssen innerhalb der Liste eindeutig sein.
4. Wenn Sie zurück zu Schritt 2 gehen und die CPU wechseln, wird die Modul-Liste geleert, weil die vorher gewählten Module nicht mehr zum neuen Rack passen müssen.

**Schritt 4 — Netzwerk (optional):**

Konfigurieren Sie ein einzelnes Ethernet-Subnetz:

1. Geben Sie einen **Subnetz-Namen** ein (zum Beispiel `PN/IE_1`).
2. Geben Sie den **Interface-Pfad** der PROFINET-Schnittstelle der CPU innerhalb des Gerätebaums ein (zum Beispiel `Rack_0/PROFINET interface_1`).
3. Geben Sie die **IPv4-Adresse** in vier numerischen Feldern ein (jeweils 0–255).

PROFIBUS, MPI und AS-i werden vom Wizard nicht unterstützt.

**Schritt 5 — Initiale Bausteine (optional):**

Leere Programmbausteine anlegen:

1. Klicken Sie auf **Baustein hinzufügen**.
2. Wählen Sie eine **Art** (FB, FC, OB oder Global-DB).
3. Geben Sie einen **Namen** und optional eine **Nummer** ein (leere Nummer = automatische Nummerierung).
4. Wählen Sie eine **Programmiersprache** (SCL, LAD, FBD, STL, GRAPH oder ProDiag).
5. Wiederholen Sie den Vorgang für weitere Bausteine. F-Block-Namen (`F_*`, `Failsafe_*`, `Safety_*`, `F-…`) werden abgelehnt.

**Schritt 6 — Prüfen und anlegen:**

1. Prüfen Sie die Zusammenfassung (Projektname, Zielverzeichnis, CPU, Module, Netzwerk, Bausteine).
2. Klicken Sie auf **Projekt anlegen**.
3. Der Fortschritt wird unten im Wizard angezeigt. Der Wizard führt die gesamte Anlage als eine atomare Operation in TIA Portal aus — fällt ein Schritt aus, wird das gesamte Projekt zurückgerollt.
4. Nach Erfolg schließt sich der Wizard und das neue Projekt wird automatisch in der Anwendung geöffnet.

> **Hinweis:** F-CPU- und Safety-Konfiguration, mehrere CPUs in einem Projekt sowie PROFIBUS-/MPI-/AS-i-Netzwerke werden vom Wizard nicht unterstützt. Verwenden Sie für diese Szenarien direkt TIA Portal.

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

**Letzte Projekte:** Der Dialog merkt sich Ihre zuletzt geöffneten Projekte (bis zu zehn, neueste zuerst) für schnellen Zugriff. Einträge auf Projekte, die verschoben oder gelöscht wurden, werden automatisch ausgeblendet.

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

Liegt der gewählte Ordner innerhalb eines Git-Repositories, dekoriert der Right-Directory-Baum jede Zeile mit denselben Git-Status-Badges und Dimm-Effekten wie der Explorer-Workspace:

- Farbiges Status-Glyph (M, +, −, ➜, ❏, ★, ! oder T) neben dem Dateinamen (Modified, Added, Deleted, Renamed, Copied, Untracked, Conflicted, Type-changed). Tooltip beim Hovern zeigt die Änderungsart.
- Ordner zeigen in gedimmter Form den schlechtesten Status einer enthaltenen Datei, damit nicht-committeter Stand auf einen Blick sichtbar ist — ohne den Baum aufzuklappen.
- `.gitignore`-gematchte Dateien bleiben sichtbar, werden aber gedämpft grau dargestellt.
- Badges aktualisieren sich automatisch nach Commits, Checkouts, Merges und Rebases — kein manueller Reload nötig.

> **Hinweis:** Das "Working Directory" in den Einstellungen bezieht sich auf die "Find Unused Blocks" Funktion und ist ein separater Ordner.

### Suche im Datei-Baum (rechts)

Das Suchfeld über dem rechten Datei-Baum filtert die Datei-Liste während der Eingabe. Es unterstützt dieselbe Syntax wie die [Suche im Projektbaum](#suche-im-projektbaum):

- Teilzeichenkette (`motor`), Fuzzy (`fbmtr`), mehrere Begriffe (alle müssen passen), Phrase in Anführungszeichen (`"mein block"`), Ausschluss (`!safety`).
- Passende Zeichen werden in jeder sichtbaren Zeile in fetter Akzentfarbe hervorgehoben.
- Die Filterung ist um 250 ms entprellt, damit auch lange Listen während der Eingabe reaktiv bleiben.
- Das Leeren des Suchfelds stellt Ihre manuell aufgeklappten Ordner exakt so wieder her, wie sie vor der Eingabe waren.

### Rechtsklick auf Ordner und Dateien (rechter Baum)

Ein Rechtsklick auf einen beliebigen Knoten im rechten Datei-Baum öffnet ein Kontextmenü mit **Open in Editor**, **Import** und **Delete**:

- **Open in Editor** lädt die ausgewählte Datei in den Editor-Arbeitsbereich (für Ordner deaktiviert).
- **Import** führt denselben Import wie die *Import Selected*-Schaltfläche in der Seitenleiste auf den angehakten Zeilen aus.
- **Delete** entfernt die ausgewählte Datei *oder den Ordner* von der Festplatte. Bei einem Ordner wird der gesamte Inhalt (alle Dateien und Unterordner) rekursiv entfernt. Vorher erscheint eine Bestätigungsabfrage.

Dateien, deren Name mit einem Punkt beginnt (zum Beispiel der Delta-Import-Fingerprint-Cache, den *Preview Diff* neben Ihren Exports pflegt), werden jetzt im Baum angezeigt, damit Sie sie sehen und verwalten können. Dateien, die das Betriebssystem als „Versteckt" oder „System" markiert hat, bleiben weiterhin ausgeblendet.

### Export-Operationen

#### Export Selected
1. Setzen Sie Häkchen bei den gewünschten Blöcken im linken Baum
2. Klicken Sie auf **Export Selected**
3. Die ausgewählten Einträge werden als XML exportiert. Bestehende Dateien mit gleichem Namen werden überschrieben; alle übrigen Dateien im Export-Ordner bleiben erhalten.

#### Export All
1. Klicken Sie auf **Export All**
2. Der SPS-Export-Ordner wird zuerst geleert, danach werden ALLE Blöcke, Datentypen, Variablentabellen, Technologie-Objekte und Software-Units exportiert — ein vollständiger Projekt-Export

### Import-Operationen

#### Import Selected
1. Setzen Sie Häkchen bei den gewünschten XML-Dateien im rechten Baum
2. Klicken Sie auf **Import Selected**
3. Die ausgewählten Dateien werden importiert. Bestehende Blöcke mit gleichem Namen werden überschrieben; alle übrigen SPS-Inhalte bleiben unverändert.

#### Import All
1. Klicken Sie auf **Import All**
2. Das gesamte SPS-Programm wird zuerst gelöscht (alle Blöcke, Datentypen und Variablentabellen), danach werden ALLE XML-Dateien im Working Directory importiert — ein vollständiger Projekt-Reimport

**Wichtig:** Import All ersetzt den kompletten SPS-Inhalt durch das, was im Working Directory liegt. Im Schutzprofil markierte Blöcke bleiben erhalten.

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

**Linke und rechte Dateiliste:** Das Compare-Panel zeigt links eine Dateiliste für die TIA-Seite und rechts eine passende Dateiliste für die Disk-Seite. Beide Listen, die Diff-Toolbar und die Seitenleisten sind sichtbar, sobald Sie den Compare-Tab öffnen — auch ohne geladene Inhalte —, damit Sie sofort sehen, wo welche Information landet. Im leeren Zustand erscheint im Diff-Bereich ein dezent halbtransparenter Drop-Hinweis, der verschwindet, sobald Inhalte geladen werden. Geänderte Blöcke erscheinen in beiden Listen; Blöcke, die nur in TIA existieren (oder noch kompiliert werden müssen), erscheinen nur links, Blöcke, die nur auf der Platte existieren, nur rechts. Beide Listen haben einen eigenen Ein-/Ausblenden-Toggle in der Compare-Toolbar — Sie können sich wahlweise auf eine Seite konzentrieren oder beide nebeneinander anzeigen lassen.

**Mehrere Formate pro Block:** Wenn ein Block in mehreren Repräsentationen auf der Platte vorliegt (z. B. ein SCL-Baustein als `Block_2.scl` und `Block_2.xml` nebeneinander), erscheint pro Format eine eigene Zeile in der Dateiliste. Klicken Sie auf die Zeile mit der Endung, die Sie sehen möchten — der Diff lädt sofort. Es gibt keinen separaten SCL/XML-Umschalter mehr; die Endung der angeklickten Zeile entscheidet, welche Sicht der Editor zeigt.

**Farbbalken am Zeilenrand:** Jede Zeile in beiden Dateilisten trägt am rechten Rand einen schmalen farbigen Balken, der den Änderungstyp ohne Textabgleich signalisiert: Grün für Hinzugefügt, Rot für Gelöscht, Orange für Geändert, Gelb für Inkonsistent (muss kompiliert werden), Blau für Blöcke, die nur auf einer Seite existieren (links oder rechts). Unveränderte Zeilen zeigen keinen Balken.

### Sektionsweise Übernahme

Wenn sich zwei Dateien unterscheiden, erscheinen Pfeil-Buttons (`←` / `→`) in der mittleren Spalte zwischen den Editoren — ein Paar pro Änderungs-Abschnitt. Klick auf `→` kopiert den linken Abschnitt in den rechten Buffer, `←` umgekehrt. Die Änderungen werden im Speicher-Buffer angewendet; klicken Sie **Speichern**, um sie zu persistieren. Für TIA-Seiten-Buffer (linke Seite im Sync-Modus gegen einen Temp-Export) wird das Speichern übersprungen — der Block muss neu importiert werden, um die Änderung in TIA zurückzuschreiben.

### Identische Dateien

Wenn beide Seiten identischen Inhalt haben, zeigen beide Editoren die Datei ohne `+`/`-`-Marker und ohne Übernahme-Pfeile. Die Identität ist visuell aus den fehlenden Änderungsmarkierungen ersichtlich; ein separates Banner wird nicht angezeigt.

### Ad-hoc Compare (Drag and Drop)

Für schnelle Side-by-Side-Überprüfungen ohne Projektweiten Scan ziehen Sie Items direkt in das Compare-Panel. Beide Seiten sind unabhängige Drop-Ziele — auf welche Hälfte Sie ablegen, in dieser Hälfte taucht das Item auch auf:

1. Ziehen Sie einen oder mehrere Blöcke aus dem TIA-Projektbaum und lassen Sie sie über der linken oder rechten Hälfte des Compare-Panels fallen. Die abgelegten Items erscheinen in der zugehörigen Dateiliste (links bzw. rechts).
2. Die SPS wird kompiliert, die Blöcke werden mit Ihren aktuellen Import/Export-Einstellungen exportiert (dieselben Strip-Regeln wie beim normalen "Export Selected"), und jede exportierte Datei wird zu einer eigenen Zeile in der zugehörigen Dateiliste — ein SCL-Block erzeugt sowohl eine `.xml`- als auch eine `.scl`-Zeile, ein InstanceDB erzeugt `.xml` und `.db`.
3. Klicken Sie auf die Zeile mit dem Format, das Sie sehen möchten.
4. Die Quellen dürfen pro Seite unterschiedlich sein: Sie können einen TIA-Block auf die eine Seite und eine Windows-Datei auf die andere ziehen, oder zwei Dateien direkt für einen File-to-File-Vergleich ohne TIA-Export ablegen.
5. Der Diff-Viewer zeigt die Unterschiede Zeile für Zeile.

**Hinweise:**

- Die TIA-Seite wird kompiliert und genau gleich gestrippt wie bei einem normalen Export — der Vergleich erfolgt also Apfel gegen Apfel gegen eine Datei, die früher ins Working Directory exportiert wurde.
- Weitere Drops auf dieselbe Seite werden an die bestehende Liste angehängt statt sie zu ersetzen — ein TIA-Block lässt sich so gegen mehrere Kandidat-Dateien prüfen, ohne neu zu exportieren, und die andere Seite behält, was sie bereits geladen hat.
- Beim Überfahren einer Zeile in einer der beiden Dateilisten erscheint am rechten Rand ein `X`-Button — ein Klick entfernt genau diese Datei aus dem Vergleich, ohne den Rest zu berühren.
- Die Splitter der Dateilisten sind zwischen 180 und 500 Pixeln resizebar und merken sich die von Ihnen gewählten Breiten.

Für den projektweiten Vergleich mit selektivem Re-Import zurück in die SPS verwenden Sie stattdessen **Preview Diff** (Hash-basiert, produziert Modified / Only in TIA / Only on Disk-Kategorien und einen Sync-Mode Import-Button).

### Diff-Editor Toolbar

Die Toolbar des Diff-Editors enthält folgende Bedienelemente:

- **Änderungsnavigation** — Buttons Erste / Vorherige / Nächste / Letzte Änderung plus ein `1/N`-Zähler springen durch alle Hunks der aktuellen Datei.
- **Kontextzeilen** — `+=` und `-=` erhöhen oder verringern die Anzahl der unveränderten Zeilen um jede Änderung (Standard 3, Minimum 1). Die Bereiche zwischen Hunks werden hinter einer `@@ -a,b +c,d @@`-Kopfzeile eingeklappt.
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

Hardware-Konfiguration als AutomationML (.aml)-Datei exportieren:

1. Stellen Sie die Kategorie im Import-/Export-Tab auf **Hardware**.
2. Klicken Sie in der rechten Spalte auf **AML exportieren →**. Die Datei wird im konfigurierten Export-Ordner abgelegt.
3. **← AML importieren** in der gleichen Spalte holt eine `.aml`-Datei wieder ins Projekt zurück.

**Hinweis:** Der AML-Export deckt die komplette Hardware-Konfiguration der gewählten SPS ab. Die erzeugte `.aml`-Datei kann reimportiert oder zu Dokumentationszwecken aufbewahrt werden.

---

## 6. Project Tab

### Code-Anzeige

Wenn Sie einen Block im Projektbaum auswählen, wird sein Quellcode im Code-Editor angezeigt.

**Unterstützte Sprachen:**
- SCL (Structured Control Language)
- STL (Statement List)
- LAD/FBD/GRAPH (direkt als Netzwerke gerendert)

### Grafische Bausteinansicht

LAD-, FBD- und GRAPH-Bausteine öffnen sich im Tab **Grafisch** neben dem Code-Tab. Die Netzwerke werden direkt im Manager dargestellt — kein externes Vergleichs- oder Visualisierungswerkzeug ist erforderlich, und kein separates Siemens-Hilfsprogramm muss installiert sein. Jedes Netzwerk zeigt Titel, Kommentar und das LAD-/FBD-Layout so an, wie es im TIA Portal erscheint. Datenbausteine, UDTs und Variablentabellen werden ebenfalls inline strukturiert angezeigt.

Die Ansicht ist schreibgeschützt; Änderungen erfolgen über den Code-Tab oder den Inline-Chat. Wechseln Sie jederzeit zurück zum Code-Tab, um den SCL-/STL-Quelltext einzusehen oder zu bearbeiten.

### Schnittstellen-Tab

Bei Datenbausteinen (DB), Funktionsbausteinen (FB), Funktionen (FC), Anwender-Datentypen (UDT) und PLC-Variablentabellen erscheint neben dem **Code**-Tab ein **Schnittstelle**-Tab. Er zeigt die Schnittstelle in der gleichen Tabellen-Form wie TIA Portal, mit einer Zeile pro Member und folgenden Spalten:

- **Name** — Member-Name; verschachtelte Struct- oder UDT-Member werden unter dem Parent eingerückt dargestellt und lassen sich über den Pfeil-Chevron zuklappen.
- **Datentyp** — SIMATIC-Typ wie ihn TIA exportiert (z. B. `Bool`, `Int`, `Array[0..9] of "myUdt"`).
- **Startwert** — initialer Wert falls definiert, sonst leer.
- **Remanenz** — `Nicht remanent`, `Remanent` oder `In DB festgelegt`.
- **Erreichbar aus HMI / Beschreibbar aus HMI / Sichtbar in HMI** — die drei externen Zugriffs-Flags. Bei Datenbausteinen, Funktionsbausteinen, Funktionen und PLC-Variablentabellen zieht das Umschalten von **Erreichbar aus HMI** sowohl **Beschreibbar** als auch **Sichtbar** mit (aus → beide aus, ein → beide ein); bei Anwender-Datentypen bleiben die drei Flags unabhängig. **Beschreibbar** und **Sichtbar** lassen sich jederzeit einzeln umschalten, ohne die anderen zwei zu ändern.
- **Sollwert** — bearbeitbare Checkbox, markiert das Member als Sollwert.
- **Überwachung** — schreibgeschützter Text, zeigt die verknüpfte ProDiag-Überwachungs-Referenz (leer wenn keine zugewiesen).
- **Kommentar** — Kommentar in der aktuellen UI-Sprache; falls dieser fehlt, wird Englisch (`en-US`) verwendet; sonst die erste verfügbare Sprache.

Für PLC-Variablentabellen zeigt der gleiche Tab zwei Tabellen übereinander: oben die **Variablen**-Liste (Name · Datentyp · Logische Adresse · Remanenz · HMI-Flags · Überwachung · Kommentar) und unten die **Anwenderkonstanten**. Die **Überwachung**-Spalte ist schreibgeschützt und zeigt die verknüpfte ProDiag-Überwachungs-Referenz, analog zur gleichen Spalte auf Baustein-Schnittstellen. Variablen vom Typ Array oder Anwender-Datentyp klappen inline auf: jedes Array-Element wird als eigene Zeile mit berechneter Adresse angezeigt, und jedes UDT-Member erscheint darunter bis hinunter zur Primitive. Ist das Projekt nicht mit dem TIA Portal verbunden, lassen sich UDT-Definitionen nicht laden; ein gelber Hinweis über der Variablen-Liste erklärt, dass das Öffnen des Projekts im TIA Portal die vollständige Hierarchie nachlädt.

Oberhalb der Variablen-Liste bietet eine Toolbar **Bearbeiten / Verwerfen / Speichern / Speichern unter … / In TIA hochladen** denselben Ablauf wie bei Baustein-Schnittstellen: Variablen umbenennen, Datentyp oder Logische Adresse ändern, Remanenz und HMI-Flags umschalten, Kommentare inline editieren. **Speichern** schreibt die geänderte Variablentabellen-XML in das konfigurierte Working Directory (`{Working Directory}/{SPS}/{Variablen-Ordner}/{Tabellenname}.xml`); **Speichern unter …** erlaubt einen beliebigen Pfad; **In TIA hochladen** bleibt verfügbar, sobald eine TIA-Portal-Verbindung aktiv ist, und re-importiert die Variablentabelle in das Projekt.

#### Schnittstelle offline bearbeiten (File-Drop oder Dateiexplorer)

Sowohl **Drag-and-Drop auf den Editor / Welcome-Tab** als auch **Dateiexplorer-Rechtsklick → Im Editor öffnen** laden Dateien mit aktivem Schnittstellen-Tab. Zwei Datei-Formen werden unterstützt:

- **Quelldateien** — `.scl`, `.stl`, `.udt`, `.db`. Der Parser liest die Deklarationsbereiche (`VAR_INPUT` / `VAR_OUTPUT` / `VAR_IN_OUT` / `VAR_TEMP` / `VAR` / `VAR_STAT` / `STRUCT` / DB-Member) direkt aus der Datei. Für diesen Pfad ist keine TIA-Portal-Verbindung erforderlich.
- **SimaticML-XML** — `.xml`-Exporte aus TIA Portal. Der Bausteintyp wird aus dem Root-Element erkannt: `<SW.Blocks.FB>` / `<SW.Blocks.FC>` / `<SW.Blocks.OB>` / `<SW.Blocks.GlobalDB>` / `<SW.Blocks.InstanceDB>` / `<SW.Blocks.ArrayDB>` / `<SW.Types>` öffnen den Baustein-Schnittstellen-Editor; `<SW.Tags.PlcTagTable>` öffnet direkt die Variablen-Tabelle mit aktivierter Toolbar Bearbeiten / Verwerfen / Speichern / Speichern unter … / In TIA hochladen.

**Speichern** schreibt zurück in die abgelegte oder geöffnete Datei; **Speichern unter …** schreibt an einen beliebigen Pfad; **In TIA hochladen** bleibt deaktiviert, bis eine TIA-Portal-Verbindung aktiv ist.

Im Bearbeitungsmodus können Sie:

- einen Member umbenennen,
- den Datentyp eines Members ändern (in der SCL-Syntax, wie TIA Portal sie exportiert — inklusive Arrays und UDT-Referenzen),
- einen Startwert ändern,
- den Kommentar in der aktuellen UI-Sprache bearbeiten,
- einen neuen Member hinzufügen, einen Member löschen oder über den Drag-Griff links neben jeder Zeile umsortieren.

**Speichern (Strg+S** oder die Schaltfläche **Speichern**)** schreibt die Änderungen atomar in die ursprüngliche Quelldatei zurück. Header-Attribute, Decorations (`VERSION`, `NON_RETAIN`, `READ_ONLY`, `KNOW_HOW_PROTECT`, `AUTHOR`, `FAMILY`, `NAME`), Body-Code und nicht-bearbeitete Deklarationsbereiche bleiben byte-identisch erhalten; nur die tatsächlich geänderten Sektionen werden neu emittiert. Zeilenenden (CRLF oder LF) werden pro Datei beibehalten.

Ist die Quelldatei auf der Disk schreibgeschützt, wechselt das Speichern-Kommando automatisch in **Speichern unter…** und zeigt einen lokalisierten Hinweis-Banner, der den Fallback erklärt. **Speichern unter…** schreibt den Inhalt in einen neuen Pfad; nachfolgende Speichervorgänge zielen auf diesen neuen Pfad.

**Upload to TIA** bleibt eine separate Aktion und ist nur sichtbar, wenn eine TIA-Portal-Verbindung aktiv ist. Speichern und Speichern unter funktionieren unabhängig vom Verbindungsstatus.

#### Schnittstelle online bearbeiten (TIA-verbunden)

Wenn ein Baustein aus dem Projektbaum eines verbundenen TIA-Portal-Projekts geöffnet wird, unterstützt der Schnittstellen-Tab denselben Editier-Umfang wie der Offline-Pfad (Umbenennen, Datentyp ändern, Startwert ändern, Kommentar ändern, Mitglieder hinzufügen, entfernen und umsortieren). Das Hochladen der Änderungen zurück nach TIA Portal durchläuft drei Sicherungsstufen:

- **Querverweis-Auswirkungs-Vorschau** — vor dem Upload prüft der Manager bei Umbenennungen, Entfernungen und Datentyp-Änderungen projektweit, welche Aufrufstellen durch die Änderung brechen würden. Ein Bestätigungsdialog meldet die Anzahl betroffener Stellen, eine Stichprobe von bis zu zehn Aufrufern und einen Cap-Hinweis, falls die Suche gecapped wurde. **Abbrechen** bricht den Upload ab; **Fortfahren** erfordert eine Bestätigung und setzt fort.
- **Automatische Kompilierung nach dem Upload** — sobald die Änderungen angekommen sind, wird die SPS automatisch kompiliert. Compiler-Meldungen erscheinen in einem aufklappbaren Panel **Compiler-Meldungen** über der Tabelle mit Schweregrad-Symbol (× / ⚠ / ⓘ) und dem fehlerhaften Bausteinnamen. Ein Klick auf eine Zeile springt im Projektbaum zu diesem Baustein und öffnet ihn im Editor.
- **Edit-Modus-Sperre** — meldet TIA Portal den Baustein als Know-how-geschützt, schreibgeschützt oder konnten die Bausteinfähigkeiten nicht abgefragt werden, ist der **Bearbeiten**-Schalter deaktiviert und der Tooltip erklärt warum. Dieselbe Sperre greift auch direkt vor einem Upload — geschützte oder schreibgeschützte Bausteine sind über den Schnittstellen-Tab nicht editierbar, unabhängig vom Online-Status des Projekts.

Das Editieren eines Safety-(F-)Bausteins zeigt nach wie vor eine separate Warnung, die vor dem Upload bestätigt werden muss. Die Re-Validierung des Safety-Programms nach einer Schnittstellen-Änderung bleibt ein manueller Schritt in TIA Portal — TIA Openness bietet keine "Safety-Programm jetzt validieren"-Schnittstelle, der Manager kann das daher nicht automatisieren.

Beim Schließen eines Tabs mit ungespeicherten Schnittstellen-Änderungen erscheint dasselbe **Speichern / Verwerfen / Abbrechen**-Dialogfeld wie bei ungespeicherten Code-Änderungen. Speichern schreibt die Datei; Verwerfen schließt ohne Schreiben; Abbrechen lässt den Tab geöffnet.

### Speichern und Schließen

- **Strg+S** speichert die im Editor aktive Datei oder den aktiven Block. Bei Dateien wird auf Disk geschrieben. Bei TIA-Portal-Blöcken erscheint vor dem Hochladen ein Bestätigungsdialog („In TIA Portal übertragen?"); der *Upload to TIA*-Toolbar-Button fragt dieselbe Bestätigung ab.
- **Strg+Umschalt+S** speichert das gesamte TIA-Portal-Projekt (das frühere Verhalten von Strg+S).
- Beim Schließen eines Tabs oder des Managers mit ungespeicherten Änderungen erscheint ein Bestätigungsdialog mit den Optionen „Alle speichern", „Alle verwerfen" oder „Abbrechen".
- Beim Trennen von TIA Portal werden alle aus TIA geöffneten Editor-Tabs geschlossen. Bei ungespeicherten Änderungen erscheint vorab ein Speichern/Verwerfen/Abbrechen-Dialog.

### Drag & Drop aus dem Project Explorer

Sie können jeden Baustein (FB, FC, OB, DB, UDT, Variablentabelle) aus dem TIA-Baum direkt auf den Editor oder den Welcome-Tab ziehen — oder Quelldateien aus dem Offline-Ordner. Jedes abgelegte Objekt öffnet sich als eigener Editor-Tab; der Editor lädt den Inhalt genauso wie bei einem Doppelklick. Objekte, die nicht gefunden oder geöffnet werden konnten, werden in der Statusleiste gemeldet.

### Block-Details Panel

Neben dem Code werden Metadaten angezeigt:
- **Block-Typ:** OB, FB, FC, DB
- **Nummer:** z.B. OB1, FB10
- **Sprache:** Zeigt die tatsächliche Programmiersprache, die TIA Portal für den Block meldet (`SCL`, `STL`, `LAD`, `FBD`, `GRAPH`, `F_LAD`, …). Für Dateien aus dem File-Explorer entspricht die Anzeige dem Dateityp (`C#`, `Python`, `Markdown`, `TypeScript`, …) — unbekannte Endungen werden als `Text` angezeigt.
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
- **Teilwort-Match** — `motor` findet `FB_Motor`, `MotorController`, `drive_motor`.
- **Fuzzy-Match** — `fbmtr` findet `FB_Motor`, indem die Zeichen in Reihenfolge getroffen werden.
- **Mehrere Suchbegriffe** — durch Leerzeichen getrennt. Alle Begriffe müssen treffen. `motor plc1` findet nur Einträge, deren Name sowohl `motor` als auch `plc1` enthält. Reihenfolge der Begriffe ist egal.
- **Phrase in Anführungszeichen** — setzen Sie eine Phrase in doppelte Anführungszeichen, um sie wortwörtlich inklusive Leerzeichen zu suchen: `"my block"` findet genau den Teilstring `my block`.
- **Ausschluss** — stellen Sie einem Begriff ein `!` voran, um Treffer auszuschließen: `motor !safety` findet Einträge deren Name `motor` matcht, aber **nicht** `safety` enthält.
- **Bereichsfilter** — mit `kind:WERT` können Sie auf einen bestimmten Knotentyp einschränken. Bekannte Werte: `fb`, `fc`, `db`, `ob` (inkl. Safety-Varianten), `udt`, `tag`, `plc`, `block` (alle Block-Typen), `safety` (nur Safety-Blöcke), `folder`, `screen`. Beispiel: `kind:fb motor` listet nur Funktionsbausteine mit `motor` im Namen.
- **Ranking** — exakte Treffer stehen oben, danach Präfix-Treffer, danach Treffer an Wortgrenzen (`FB_Motor` vor `CalibrateMotor`), danach allgemeine Teilwort-Treffer, zuletzt Fuzzy-Treffer. Die Weiter/Zurück-Navigation springt in Rang-Reihenfolge.
- **Hervorhebung** — die matchenden Zeichen werden in jedem sichtbaren Treffer fett in Akzentfarbe dargestellt, damit Sie auf einen Blick erkennen, was getroffen wurde.
- **Groß-/Kleinschreibung** wird ignoriert — `MOTOR` und `motor` verhalten sich gleich.

Wenn Sie das Suchfeld leeren, wird der Projektbaum exakt so wiederhergestellt, wie er vor Ihrer Eingabe war — inklusive manuell ausgeklappter Knoten.

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
- Im Projektbaum mit einem grünen Schloss-Badge markiert (rotes Schloss = nicht geschützt, Klick zum Umschalten)
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

### Safety-Blöcke (F-Blöcke) schützen

Bevor ein Safety-Block (F_FB, F_FC, F_DB, F_OB) über den Tresor mit Know-How-Schutz versehen werden kann, muss das F-Programm in TIA Portal **vollständig übersetzt und konsistent** sein. Die Massen-Schutz-Operation ruft dieselbe Siemens-API auf, die TIA Portal intern verwendet — und Siemens lehnt diesen Aufruf für jeden F-Block ab, der nicht aktuell aus einer übersetzten F-Runtime-Gruppe referenziert wird.

**Erforderlicher Schritt vor dem Tresor-Schutz von Safety-Blöcken:**

1. In TIA Portal Rechtsklick auf den Programm-Ordner der F-CPU
2. **Software → Alles übersetzen (alles neu generieren)** wählen (je nach TIA-Portal-Version und Sprache auch beschriftet als **Software → Übersetzen → Software (alles neu generieren)**)
3. Warten Sie, bis die Neuübersetzung fehlerfrei abgeschlossen ist
4. Zurück zu TIA Openness Manager wechseln und **Massen-Schutz (Tresor)** ausführen

Wenn Sie die Neuübersetzung überspringen und versuchen, einen frisch hinzugefügten oder geänderten F-Block zu schützen, liefert der Tresor eine Safety-Block-Fehlermeldung mit den vier häufigsten Siemens-Ablehnungsgründen (Block nicht im Safety-Programm verwendet, Safety-Offline-Programm-Login fehlt, Block inkonsistent, Block im Editor geöffnet). Die Neuübersetzung beseitigt den Inkonsistenz-Fall für neu hinzugefügte oder geänderte Blöcke.

> **Warum „alles neu generieren" und nicht nur „übersetzen"?** Ein normales Übersetzen aktualisiert nur geänderte Blöcke. Das Hinzufügen oder Ändern eines F-Blocks invalidiert die Siemens-generierten F-Runtime-Gruppen-Glue-Blöcke (`F_PLK`, `F_RTG_OB` usw.), die F-OBs in das Safety-Programm einhängen. Solange diese Glue-Blöcke nicht neu generiert sind, sieht die Openness-API den neuen F-Block nicht als „called" — Protect wird abgelehnt. Erst **„alles neu generieren"** erzwingt die vollständige Neuerstellung jedes Glue-Blocks.

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

## 9. MCP Server (KI-Integration)

### Was ist MCP?

Das Model Context Protocol (MCP) erlaubt externen KI-Assistenten — Claude Desktop, Claude Code, Gemini CLI, Cursor, LM Studio, Continue.dev — über TIA Openness Manager auf Ihr TIA Portal Projekt zuzugreifen.

### So funktioniert es

Es gibt keinen MCP-Tab im Hauptfenster mehr. Der MCP-Server läuft als Hintergrund-Subprocess, den der KI-Client bei Bedarf selbst startet, indem er `TiaOpennessManager.V3.exe` mit dem Argument `--mcp-stdio` aufruft. Solange TIA Openness Manager geöffnet ist und mit einem TIA Portal Projekt verbunden ist, leitet der Subprocess jeden Tool-Aufruf transparent an die laufende Instanz weiter — alle 47 MCP-Tools (Projekt-Queries, Block-Code lesen, Exports, Vergleiche, KI-gestützte Analysen, OPC UA, Canvas, Git, PowerShell, Trace etc.) arbeiten gegen das Projekt, das Sie aktuell offen haben.

### Einrichtung mit einem KI-Assistenten

1. Öffnen Sie TIA Openness Manager und verbinden Sie es wie gewohnt mit Ihrem TIA Portal Projekt.
2. Tragen Sie in der MCP-Server-Konfiguration Ihres KI-Clients einen neuen Server ein, mit Kommando `TiaOpennessManager.V3.exe` und Argument `--mcp-stdio`. Die genaue Syntax hängt vom Client ab (jeder Anbieter veröffentlicht sein eigenes MCP-Server-Format) — siehe die Beispiel-Snippets unten.
3. Starten Sie einen Chat mit dem KI-Assistenten. Er kann jetzt Projektstruktur abfragen, Block-Code lesen, Analysen durchführen, OPC UA Lese-/Schreibzugriffe steuern und jedes andere Tool nutzen, das die aktive Lizenzstufe erlaubt.

### Capabilities

| Capability | Methoden | Was der KI-Client damit kann |
|------------|----------|------------------------------|
| Tools | `tools/list`, `tools/call` | 47 Tools — TIA-Projekt- und PLC-Operationen (Projekt-Queries, Projekterstellung, Code lesen, Exports, Vergleiche, Hardware-Geräteverwaltung, Netzwerk/Subnet, Tag-Tabellen, Screen-Tools, OPC UA, Canvas, Trace, Unit Testing, Git) plus universelle Helfer: `fs` (Dateisystem-Lesen/Schreiben/Suchen), `web_fetch` (HTTP-Outbound), `web_search`. Jeder Aufruf wird durch Lizenzstufe und den Permission-Filter gegated |
| Resources | `resources/list`, `resources/read`, `notifications/resources/list_changed` | Live-Resource `tia://project` plus 4 URI-Templates; Clients erhalten eine List-Changed-Benachrichtigung wenn sich das Projekt ändert (per-URI-Subscribe ist bewusst nicht advertised) |
| Sampling | `sampling/createMessage` | Das TIA-Portal-bewusste Tool `tia_ai_analyze` lässt den KI-Client ein Modell anstoßen — der Client steuert Modell und Credentials selbst |
| Prompts | `prompts/list`, `prompts/get` | 4 vorgefertigte Prompts: `analyze-block`, `generate-unit-tests`, `compare-blocks`, `review-safety-function` |
| Logging | `logging/setLevel`, `notifications/message` | Der KI-Client kann sich den Server-Log-Stream in einer wählbaren Verbosität liefern lassen |

### Konfigurations-Beispiele

Ersetzen Sie `C:\Program Files\TIA Openness Manager\TiaOpennessManager.V3.exe` durch Ihren tatsächlichen Installationspfad. Der Pfad muss auf einen schreibgeschützten Ort zeigen — das Default-Installationsverzeichnis unter `Program Files` verlangt Admin-Rechte zum Ändern, genau was Sie wollen. Wenn Sie den KI-Client auf ein user-schreibbares Verzeichnis zeigen lassen, wird der MCP-Server-Eintrag zum Code-Execution-Sink für jeden Prozess, der unter Ihrem User-Account läuft.

**Claude Desktop** (`%APPDATA%\Claude\claude_desktop_config.json`):

```json
{
  "mcpServers": {
    "tia-openness-manager": {
      "command": "C:\\Program Files\\TIA Openness Manager\\TiaOpennessManager.V3.exe",
      "args": ["--mcp-stdio"]
    }
  }
}
```

**Claude Code** — registrieren Sie den Server über die CLI:

```
claude mcp add tia-openness-manager "C:\Program Files\TIA Openness Manager\TiaOpennessManager.V3.exe" -- --mcp-stdio
```

Claude Code speichert MCP-Server-Einträge in seiner Root-Settings-Datei (`~/.claude.json` unter dem Schlüssel `mcpServers`); nutzen Sie die CLI statt die Datei direkt zu editieren.

**LM Studio** — Settings → MCP Servers → Add Server:

- Name: `tia-openness-manager`
- Command: `C:\Program Files\TIA Openness Manager\TiaOpennessManager.V3.exe`
- Arguments: `--mcp-stdio`

**Gemini CLI** (`~/.gemini/config.json`), **Cursor** (Settings → MCP Servers) und **Continue.dev** (`~/.continue/config.json` unter `experimental.modelContextProtocolServer`) akzeptieren dasselbe Format — `command` plus `args: ["--mcp-stdio"]`.

### Lizenz-Gating

MCP-Tool-Aufrufe erfordern eine Lizenzstufe, die MCP-Server-Zugriff enthält (Trial, Professional oder Enterprise). Die Basic-Stufe enthält kein MCP — Aufrufe vom KI-Client werden vom SDK pro Aufruf mit einem Tier-Reject zurückgewiesen. Die Prüfung läuft in der SDK-Filter-Chain bei jedem Tool-Aufruf; es gibt keinen App-Toggle.

### Diagnose

Subprocess-Logs liegen unter `%LocalAppData%/TiaOpennessManager/Logs/mcp-subprocess.log` (tägliche Rotation, 3-Datei-Retention). Damit lassen sich Verbindungsprobleme oder unerwartete Reject-Meldungen nachvollziehen.

### Session-Anzeige

Die Statusleiste am unteren Rand des Hauptfensters zeigt `MCP: <n>`, sobald ein KI-Client über den Proxy-Pfad verbunden ist. Das Stecker-Symbol leuchtet in Akzentfarbe, sobald mindestens ein Client online ist. Ein Klick auf den Indikator öffnet einen Dialog, der alle aktiven Sessions auflistet (Client-Name, Version, Connect-Zeit, Session-Id) und unten eine Setup-Anleitung mit Copy-fertigen Konfigurations-Snippets für Claude Desktop, Claude Code, LM Studio und Continue.dev bereitstellt. Der Desktop-App-Tab bietet zusätzlich einen *Ordner öffnen*-Button, der direkt nach `%APPDATA%\Claude` springt, damit Sie das Snippet in `claude_desktop_config.json` einfügen können.

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

Standard-Skills werden mitgeliefert und beim ersten Start automatisch bereitgestellt:

| Skill | Beschreibung |
|-------|--------------|
| Explore Project | Analysiert das verbundene TIA Portal-Projekt und erstellt eine Kontextdatei |
| Explain Block | Liest den Quellcode eines Bausteins und erklärt seine Logik |
| Generate SCL | Generiert SCL-Code nach Siemens-Programmierstandards |
| Compare Blocks | Vergleicht Bausteinversionen zwischen Projekt und Exportordner |
| Optimize SCL | Schlägt Refactorings vor, um einen Baustein schneller oder lesbarer zu machen |
| Safety Check | Prüft einen Baustein (oder eine Auswahl) auf sicherheitsrelevante Muster |
| Export Blocks | Begleitet den Export-Workflow inkl. Auswahl und Ordner-Handling |
| Document Block | Erzeugt eine baustein-bezogene Dokumentationsdatei |
| Document Project | Erzeugt projektweite Dokumentation |
| Describe Block | Erstellt eine kurze, allgemeinverständliche Zusammenfassung eines Bausteins |
| Describe Project | Erstellt eine kurze, allgemeinverständliche Projekt-Zusammenfassung |
| Git Commit | Entwirft eine Commit-Message aus dem aktuellen Diff anhand der aktiven Commit-Vorlage |
| Convert AWL → SCL | Konvertiert einen AWL-Baustein nach SCL gemäss den Siemens-Konvertierungsregeln |
| Review SCL | Prüft SCL-Code gegen den Siemens-Styleguide und meldet Befunde |
| Write Unit Tests | Erzeugt ein Unit-Testing-Suite-Skelett für den ausgewählten Baustein |

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

**Format:** Jede `.json`-Datei definiert einen Agenten. Folgende eingebaute Agenten werden mit der Anwendung ausgeliefert und beim ersten Start bereitgestellt:

| Agent | Zweck |
|-------|-------|
| Standard-Agent | Allgemeine Chat-Funktion mit vollem Tool-Zugriff |
| Git Assistant | Fokussiert auf Git-Operationen; Datei-Tools eingeschränkt |
| SCL Expert | Spezialisiert auf das Schreiben und Prüfen von SCL/SPS-Code |
| TIA Analyzer | Read-only-Analyse des verbundenen TIA-Projekts (keine Schreib-Tools) |
| TIA Modifier | Projekt-modifizierender Agent (Export, Import, Edit) mit expliziten Schreib-Rechten |
| Canvas Creator | Baut und bearbeitet AI-Canvas-Layouts (A2UI) |
| File Worker | Datei-fokussierter Agent (Lesen/Schreiben/Suchen über die registrierten Kontext-Ordner) |
| AWL Converter | Begleitet den AWL → SCL-Konvertierungs-Workflow mit dem Benutzer |
| Unit Test Author | Erzeugt Unit-Testing-Suites und Testfälle für die ausgewählten Bausteine |

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

**Mehrere Azure-Deployments pro Agent:** Ein einzelner Azure-OpenAI-Agent kann mehrere Deployments bedienen. Im Azure-Abschnitt des Agenten enthält die Liste **Zusätzliche Deployments** eine Zeile pro zusätzlichem Deployment-Namen; klicken Sie auf **Deployment hinzufügen**, um eine neue Zeile anzulegen, tippen Sie den Deployment-Namen ein, oder klicken Sie auf den ×-Button einer Zeile, um sie zu entfernen. Jedes registrierte Deployment erscheint als eigene Zeile in „Sprachmodelle verwalten"; über **Für aktiven Agent verwenden** schalten Sie zwischen den Deployments um. Das Haupt-Deployment oben ist immer Teil der Liste.

**Wissen & Referenzen (Einstellungen → KI-Chat → Agents → Bearbeiten):** Jeder Agent verfügt unter Name / Beschreibung / System-Prompt über einen Abschnitt **Wissen & Referenzen**. Hier steuern Sie, welches Referenzmaterial die KI beim Ausführen des Agents zu sehen bekommt.

- **Instruction-Dateien beim Start laden** (Schalter) — Wenn aktiviert, werden die unter **Instruction-Dateien (Eager)** aufgelisteten Dateien bei jedem Dispatch dieses Agents vollständig in den System-Prompt eingefügt. Wenn deaktiviert, liest der Agent die Liste **Verfügbare Referenzen (Lazy)** als kurzen Index und lädt den vollständigen Inhalt bei Bedarf per Tool-Call nach (spart typischerweise 30 + Sekunden pro Dispatch).
- **Instruction-Dateien (Eager)** — Liste aus Pfaden oder `builtin:<name>.md`-Einträgen, die der Agent vorab lädt. **Instruction-Datei hinzufügen** öffnet einen Dateipicker; **Eingebaute einfügen…** bietet die fünf mitgelieferten Referenzen (Siemens-Styleguide, AWL → SCL, SCL-Sprache, Canvas, Unit-Testing).
- **Auf Lazy umstellen** (Button, nur sichtbar wenn die Instruction-Dateien-Liste nicht leer ist) — Öffnet einen Bestätigungsdialog. Bestätigen verschiebt jede aufgelistete Instruction-Datei in die **Verfügbare Referenzen**-Liste mit vor-ausgefülltem Namen und Beschreibung und schaltet danach den Eager-Load-Schalter aus. Eine Statuszeile unter dem Button meldet, wie viele Referenzen hinzugefügt und wie viele als Duplikate übersprungen wurden, damit Sie auf einen Blick sehen, ob die bestehende Liste alles aufgenommen hat. Sie können jederzeit über den Schalter wieder in den Eager-Modus zurückwechseln; nichts geht verloren.
- **Verfügbare Referenzen (Lazy)** — Eine Zeile pro Referenz. Jede Zeile hat einen Namen (Lookup-Key), eine Quelle und eine frei formulierbare Beschreibung (wird der KI als Hinweis angezeigt, wann sie die Referenz laden soll). Buttons pro Zeile: nach oben / unten verschieben, **Durchsuchen…** für eine Markdown-Datei, **Eingebaute einfügen…** für eine bekannte Referenz und × zum Entfernen. Der Validierungs-Banner warnt vor doppelten Namen und vor Zeilen, in denen nur Name oder nur Quelle ausgefüllt ist — solche Zeilen werden beim Speichern verworfen.
- **Quellpfade** — Verwenden Sie `builtin:<name>.md` für den eingebauten Katalog. Für eigene Dateien wählen Sie eine beliebige Markdown-Datei unter `%LocalAppData%\TiaOpennessManager\instructions\` oder `%LocalAppData%\TiaOpennessManager\references\` (andere Verzeichnisse werden aus Sicherheitsgründen abgelehnt). Pro Referenz gilt ein Limit von 1 MiB.

Änderungen speichern automatisch mit kurzer Verzögerung, wirken ab dem nächsten Dispatch und überleben App-Updates: Eingebaute Agents erhalten weiterhin neue System-Prompt- und Capability-Updates, aber Ihre angepasste Referenzliste bleibt über Versions-Bumps erhalten.

**Reasoning-Aufwand (Niedrig / Mittel / Hoch):** Für Agents, deren Modell Deep Thinking unterstützt, legen Sie fest, wie intensiv das Modell vor der Antwort nachdenkt. Einstellbar pro Agent unter **Einstellungen → Agents → Capabilities → Reasoning-Aufwand** oder direkt in der Composer-Bar über das Gehirn-Chip neben der Tool-Call-Schaltfläche. Höher = besseres Reasoning, aber langsamer und mehr Tokens. Mit **App-Standard verwenden** heben Sie die Agent-Überschreibung wieder auf und der Agent folgt dem globalen Standard.

**Anbieter-Einstellungen (Einstellungen → Anbieter):** Agentenübergreifende Übersicht der unterstützten KI-Anbieter. Die GitHub-Copilot-Karte zeigt Anmeldestatus, alle von Copilot-Agents verwendeten Enterprise-Domains, den Status der Reasoning-Modell-Policy sowie Schaltflächen, um die Policy-Freigabe erneut auszulösen oder den Copilot-Modellkatalog zu prüfen — alles aus dem Einstellungs-Dialog heraus. Platzhalter-Karten für Anthropic, OpenAI, Google Gemini, Azure OpenAI, AWS Bedrock, Ollama und OpenRouter verweisen auf den Modell-Browser. Anmeldung und Enterprise-Domain bleiben pro Copilot-Agent im Agents-Tab gepflegt — der Anbieter-Tab ist eine Read-only-Konsole.

**Sprachmodelle verwalten (Manage Language Models):** Das Zahnrad-Symbol neben dem Assistenten-Wähler in der Composer-Bar öffnet einen provider-übergreifenden Katalog aller Modelle, die die App kennt. Das Fenster kombiniert drei Zeilenarten: den live abgefragten Copilot-Katalog (wird direkt vom `/models`-Endpoint von GitHub Copilot beim ersten Öffnen oder beim Klick auf Aktualisieren geholt — kein Offline-Fallback, Copilot-Zeilen erscheinen sobald der Discovery-Call zurückkommt); die OAuth-Kataloge für OpenAI Codex, Google Gemini CLI und Antigravity; und — neu — eine **live abgefragte** Modell-Liste für jeden Agent, den Sie mit API-Key konfiguriert haben. Die App fragt das `/models`-Endpoint jedes Anbieters direkt ab, also erscheinen Anthropic, OpenAI, OpenRouter, Mistral, XAI, Groq, Cerebras, DeepSeek, Perplexity, Together, HuggingFace, Z.AI, MiniMax, Fireworks, Moonshot, Vercel AI Gateway, SGLang, vLLM, Qwen, Alibaba Model Studio, Arcee, Cloudflare AI Gateway, Ollama, LM Studio und Custom-OpenAI-kompatible Endpoints jeweils mit dem, was der Anbieter aktuell anbietet. AWS-Bedrock-Zeilen bleiben statisch, weil AWS kein öffentliches Modell-Discovery-Endpoint bereitstellt. Suchen nach Modellname oder ID, Filtern nach Anbieter. Die Spalte **Quelle** unterscheidet die drei Zeilenarten. Die Statuszeile zeigt eine Live-Zählung (z. B. *120 von 240 Modellen · 75 live*), sobald mindestens eine sichtbare Zeile live geholt wurde. Die Spalte **Fähigkeiten** zeigt pro Modell Tool-, Vision- und Reasoning-Badges; die Spalte **Request-Multiplikator** zeigt die Copilot-Premium-Request-Kosten pro Modell (`0x`, `0.33x`, `1x`, `3x`, `7.5x`, …). Die Spalte **Richtlinie** ist Copilot-spezifisch: *Aktiviert* zeigt Modelle, die Ihr Account erfolgreich eingeschaltet hat; *Fehlgeschlagen* markiert Modelle, bei denen die letzte Aktivierung abgelehnt wurde (Mouseover zeigt den genauen Fehler); *Admin-verwaltet* erscheint, wenn Ihr Copilot-Plan die Modellverfügbarkeit den Tenant-Admin überlässt. Bei *Fehlgeschlagen* öffnet Rechtsklick → **Copilot-Modellrichtlinie erneut anwenden** einen neuen Aktivierungsdurchlauf gegen Ihren Copilot-Tenant. Rechtsklick auf eine Zeile oder **Für aktiven Agent verwenden** setzt das Modell des aktiven Agents (nur verfügbar, wenn der Anbieter zur Zeile passt). Die Schaltfläche **Aktualisieren** invalidiert den 5-Minuten-Modell-Cache und fragt jedes Endpoint erneut ab — praktisch nach dem Hinzufügen eines API-Keys oder wenn ein Anbieter ein neues Modell ankündigt.

**Numerische Parameter (Request Timeout, Max. Wiederholungen, Context Window Override, Temperature, Top-P, Session Memory Count):** Tippen Sie den Wert direkt ein. **Enter** übernimmt, **Escape** verwirft, oder klicken Sie neben das Feld, um automatisch zu übernehmen. Werte ausserhalb des erlaubten Bereichs werden auf die nächste Grenze gekürzt. Leere **Max. Wiederholungen**, **Context Window Override**, **Temperature** oder **Top-P** bedeuten, dass der Provider-SDK-Standard (typisch 2–3 Wiederholungen mit exponentiellem Backoff für **Max. Wiederholungen**) bzw. der Katalog-/Provider-Standard verwendet wird (kein Override gesendet). **Max. Wiederholungen** akzeptiert 0–10 und gilt für Anthropic-, OpenAI-, OpenAI-Responses- und Azure-OpenAI-Agenten.

**GitHub-Copilot-Provider:** Melden Sie sich über den Device Flow in **Einstellungen → Agenten → GitHub-Authentifizierung** an. Für Firmenkonten tragen Sie vor der Anmeldung Ihre **GitHub-Enterprise-Domain** (z. B. `firma.ghe.com`) ein — OAuth- und API-Aufrufe laufen dann gegen Ihre Enterprise-Instanz. Nach der Anmeldung nutzen Sie **Modelle erneut aktivieren**, falls Claude- oder Grok-Modelle einen Policy-Fehler melden. Die Model-Auswahl zeigt automatisch das zugehörige Kontextfenster pro Modell; Copilot routet jedes Modell an die richtige Upstream-API.

**Globale Copilot-Enterprise-Domain:** Wenn alle Copilot-Agenten Ihrer Installation dieselbe GitHub-Enterprise-Instanz nutzen, setzen Sie die Domain einmal in **Einstellungen → Provider → GitHub Copilot → Globale GitHub-Enterprise-Domain**. Jeder Copilot-Agent ohne eigene Domain erbt den globalen Wert automatisch; Agenten mit eigener Domain behalten Vorrang. Die Agenten-Karte zeigt einen Hinweis *„Erbt die globale GitHub-Enterprise-Domain: …"*, sobald der geerbte Wert aktiv ist.

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

### Ordner droppen

Ziehen Sie einen beliebigen Ordner aus dem Windows-Explorer (oder aus dem integrierten Datei-Baum des Managers) auf den Chat-Eingabebereich. Der Ordner wird als Verzeichnis-Listing seiner direkten Kinder angehängt (Einträge alphabetisch sortiert, Großschreibung wird ignoriert). Größere Ordner werden gekürzt; die Eintragsgrenze ist standardmäßig 1000 und in den KI-Chat-Einstellungen anpassbar (Bereich 100–10000). Gekürzte Listings werden mit dem Hinweis `… and N more entries` markiert. Der Assistent erhält das Listing als strukturierten Verzeichnis-Block — verschachtelte Dateien werden nicht automatisch expandiert. Für tiefere Inspektion droppen Sie den jeweiligen Unterordner separat oder verwenden Sie die `@`-Datei-Erwähnung.

### Eingeschränkte Ordner

Der Assistent akzeptiert weder Drops noch `@`-Erwähnungen, die in bekannte sicherheitsrelevante Verzeichnisse zeigen: das SSH-Schlüssel-Verzeichnis (`~/.ssh`), das AWS-Anmeldedaten-Verzeichnis (`~/.aws`), die Windows-Anmeldeinformationsspeicher, den TIA-Openness-Manager-Tresor und das Windows-Systemkonfigurationsverzeichnis. Versuche werden stillschweigend abgelehnt mit einem kurzen Hinweis am unteren Chat-Rand, der die blockierte Pfad-Kategorie nennt.

### Ordner-Anhang-Beschriftungen

Angehängte Ordner-Chips zeigen ihren Pfad relativ zum aktuell geöffneten Repository-Root, sofern möglich. Werden zwei gleichnamige Ordner aus verschiedenen Elternverzeichnissen gezogen (z.B. `src/utils/` und `tests/utils/`), entstehen optisch unterscheidbare Chips. Ordner außerhalb jedes Repositories zeigen ihren Blattnamen mit Schrägstrich.

### Zeilenbereiche und PDF-Erwähnungen

Beim Tippen einer `@`-Erwähnung kann ein Zeilenbereich angehängt werden, um auf einen bestimmten Ausschnitt zu fokussieren: `@src/utils/helper.cs#L10-20` hängt die Datei mit Start-/Endzeilen-Hinweis in den Kontext des Assistenten ein. PDF-Dateien größer als 25 MB werden als leichtgewichtige Referenzen angehängt (nur Pfad + Größe); kleinere PDFs und andere Binärdateien werden wie gewohnt inline eingebunden.

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

Sitzungen werden in einer lokalen SQLite-Datenbank unter `%LocalAppData%\TiaOpennessManager\` abgelegt (`chat.db`); angehängte Dateien und grosse Nachrichten-Payloads landen daneben in einem content-addressed Blob-Store. Beide Dateien sind benutzerprivat und verlassen die Workstation nicht.

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

**Transparenz bei Tool-Aufrufen.** Wenn der Assistent ein Tool ausführt, zeigt der Chat auf einen Blick Operation und Ziel — zum Beispiel *„Lesen (src/main.cs · Zeilen 1-50)"* beim Lesen einer Datei oder *„Git Status"* bei einem Git-Befehl. Erfolgreiche Aktionen erhalten einen grünen Haken mit kurzer Zusammenfassung, Fehler ein rotes X, und abgelehnte Freigaben ein gelbes Schild — so wissen Sie immer, was der Assistent getan hat, ohne die Zeile aufklappen zu müssen. Dateipfade in diesen Zeilen sind anklickbar: Ein Klick öffnet die Datei im Code-Editor-Tab, damit Sie nachsehen können, was der Assistent gelesen oder geschrieben hat, ohne den Pfad selbst abzutippen. Destruktive Tools wie das Löschen eines Bausteins oder das Importieren von externem Code zeigen ihren Namen auf rotem Hintergrund — ein zweiter visueller Warnhinweis vor Ihrer Freigabe.

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
| `Event` | Zeitpunkt. Einer von: `PreToolUse`, `PostToolUse`, `PostToolUseFailure`, `SessionStart`, `SessionEnd`, `SubagentStart`, `SubagentStop`, `PreCompact`, `PostCompact`, `Stop`, `UserPromptSubmit`, `PlanModeExit`. (`Stop` feuert zusätzlich zu `SessionEnd` aus Kompatibilitätsgründen.) |
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

**Steuerungs-Modus (Voreinstellung):** Unter **AI Chat Einstellungen → Bei Eingabe waehrend einer Antwort** ist *In laufende Antwort einspielen (Modell steuern)* die Voreinstellung — eine waehrend des Streamings getippte Nachricht wird am naechsten sicheren Punkt innerhalb der laufenden Antwort an das Modell uebergeben, sodass es sofort reagieren kann. Eingespielte Nachrichten erhalten ihre normale Sprechblase plus einen kleinen Hinweis "↪ in laufende Antwort eingespielt". Sub-Agent- und Benachrichtigungs-Eintraege folgen weiterhin den normalen Warteschlangenregeln. Wer das alte Verhalten bevorzugt, schaltet die Einstellung auf *Auf aktuelle Antwort warten*.

**Unterbrechen (Shift+Enter):** Waehrend eine Antwort streamt, bricht **Shift+Enter** die aktuelle Antwort ab und startet sofort einen frischen Turn mit der getippten Nachricht. ESC allein bricht ohne Senden ab; Shift+Enter bricht ab *und* sendet — nuetzlich wenn die KI in eine falsche Richtung laeuft und mit neuen Anweisungen in einer Geste neu gestartet werden soll.

---

### Multi-Session

Führen Sie mehrere KI-Chat-Sessions gleichzeitig aus. Jede Session hat einen eigenen Konversationskontext, Canvas-State und Modell-Override.

**Sidebar-Layout:** Klicken Sie auf das Sidebar-Toggle-Icon (PanelLeftOpen/PanelLeftClose) im Chat-Header, um die Agent-Sidebar ein-/auszublenden. Sie gleitet als Overlay von links heraus, ohne den Chat-Inhalt zu verschieben. Sessions sind unter Workspace-Überschriften gruppiert (TIA-Projekt, Git-Repository oder manuell hinzugefügter Ordner). Jede Gruppe ist neuste-zuerst nach der letzten Aktivität sortiert; Sessions, deren Workspace unbekannt oder aus der Liste entfernt wurde, landen in einer abschließenden **OTHER**-Gruppe. Jede Gruppe zeigt bis zu fünf Sessions; eine `+N more`-Zeile blendet weitere ein, `Show less` blendet sie wieder aus.

**Workspace-Picker:** Klicken Sie auf den `▾`-Button neben dem `+` im Sidebar-Header, um den Workspace-Picker-Flyout zu öffnen. Drei Tabs:

- **Local** — Listet alle zuletzt verwendeten Workspaces mit Ordner-Icon, Namen und gedimmtem Pfad. Klicken Sie auf eine Zeile, um diesen Workspace als aktiv zu setzen (neue Sessions landen in dessen Gruppe, der Chat übernimmt den Dateisystem-Scope). Die führende **(None)**-Zeile löscht den aktiven Workspace. Beim Überfahren einer Zeile erscheint ein X-Button, der den Eintrag aus der Liste entfernt. Die abschließende **Select…**-Zeile öffnet einen Ordner-Picker, mit dem Sie einen beliebigen Pfad manuell hinzufügen können.
- **GitHub** — Demnächst verfügbar. Wird das Auswählen von GitHub-Repositorys ermöglichen.
- **Remote** — Demnächst verfügbar. Wird SSH-getunnelte Remote-Workspaces ermöglichen.

Workspaces werden automatisch erfasst, wenn Sie ein TIA-Projekt öffnen oder einen Ordner in der Git-Sidebar öffnen; bis zu 30 Einträge werden gespeichert, deduplikiert nach Pfad, mit dem zuletzt geöffneten an oberster Stelle.

**Sessions erstellen:** Klicken Sie auf den **+**-Button im Sidebar-Header, um eine neue Session unter dem aktuell aktiven Workspace zu erstellen. Neue Sessions erscheinen oben in ihrer Workspace-Gruppe.

**Sessions wechseln:** Klicken Sie auf eine Session-Zeile, um zu ihr zu wechseln. Chat-Kontext, Canvas und Modell-Override wechseln zur gewählten Session.

**Sessions schließen:** Klicken Sie auf den **X**-Button einer Session-Zeile. Bei laufenden Sessions erscheint ein Bestätigungsdialog. Das Schließen bricht aktives Streaming ab, beendet Subagenten und bereinigt den Session-Kontext.

**Ungelesene-Badges:** Wenn eine andere Session eine Nachricht empfängt während Sie eine andere Session betrachten, erscheint ein Ungelesen-Badge mit kurzer Blink-Animation auf der Session-Zeile.

**Sessions umbenennen:** Doppelklicken Sie auf einen Session-Namen zum Bearbeiten. Drücken Sie Enter oder klicken Sie außerhalb zum Speichern.

**Canvas pro Session:** Jede Session verwaltet ihren eigenen Canvas-State. Beim Wechsel wird das WebView zurueckgesetzt und der Canvas-Inhalt der Ziel-Session automatisch wiedergegeben.

**Live-Modellwechsel:** Verwenden Sie den Modell-Picker-Button im Chat-Header, um das KI-Modell nur fuer die aktuelle Session zu wechseln. Andere Sessions und die globale Einstellung sind nicht betroffen.

### Workspace — Dateisystem-Zugriffsschutz

Das `fs`-Tool des KI-Chats (lesen, schreiben, erstellen, bearbeiten, loeschen, auflisten, suchen) wird durch eine mehrschichtige Zugriffsrichtlinie gesteuert. Konfiguration unter **KI-Chat-Einstellungen → Workspace**.

**Automatisch erlaubt:**
- Das Verzeichnis des aktuell geoeffneten TIA-Projekts
- Desktop, Dokumente und Temp-Ordner (Standard)

**Ordner hinzufuegen:** Klicken Sie in den Einstellungen → Workspace auf **Ordner hinzufuegen…**, um dem KI-Assistenten dauerhaften Zugriff auf weitere Verzeichnisse zu gewaehren (z. B. Projekt-Netzlaufwerke, gemeinsame SCL-Bibliotheken). Pfade in Systemverzeichnissen (Windows, Program Files, AppData-Root, Laufwerks-Root) werden abgewiesen.

**Anfrage-Dialog:** Wenn der KI-Assistent einen Pfad ausserhalb des erlaubten Bereichs anfordert, erscheint ein Dialog mit Operationstyp (lesen / schreiben / loeschen) und Pfad:

- **Einmalig erlauben** — gewaehrt diese eine Operation
- **Diese Session erlauben** — gewaehrt das uebergeordnete Verzeichnis bis zum App-Ende
- **Dauerhaft erlauben** — fuegt das uebergeordnete Verzeichnis zu den gespeicherten Workspace-Wurzeln hinzu (Warnhinweis zeigt das genaue Verzeichnis, das persistiert wird)
- **Ablehnen** — verweigert die Anfrage

**Immer abgewiesen, unabhaengig vom Bereich:** Vault, Lizenz, Chat-Datenbank, Agent-Memory, App-Einstellungen, SSH/AWS/Azure/Kubernetes-Anmeldedaten, Windows/Program Files/AppData-Interna, Browser- und OS-Sperrdateien. Diese Liste kann der KI-Assistent auch durch Permanent-Approval auf ein Eltern-Verzeichnis nicht umgehen.

### MCP-Server-Plugins (externe Tool-Integrationen)

Der KI-Chat kann zusätzlich **nach aussen** zu externen MCP-Servern verbinden — Figma Remote, Notion, Linear, Atlassian, GitHub-MCP, eigene interne Dienste — und deren Tools neben den eingebauten TIA-Tools verfügbar machen. Konfiguration unter **KI-Chat-Einstellungen → MCP-Server**.

**MCP-Server hinzufügen:**

1. Klicken Sie im Bereich MCP-Server auf **+ Hinzufügen**.
2. Wählen Sie einen Transport: **Stdio** (lokaler Subprozess) oder **HTTP** (Remote-URL).
3. Für Stdio: **Befehl**, **Argumente**, **Arbeitsverzeichnis** und ggf. **Umgebungsvariablen** (eine `KEY=VALUE` pro Zeile) eintragen.
4. Für HTTP: **Endpoint**-URL eintragen und einen **Auth-Modus** wählen.
5. **Beim Öffnen des KI-Chats automatisch starten** aktivieren, wenn der Server beim Chat-Start mithochfahren soll.
6. Auf **Speichern** klicken.

**HTTP-Auth-Modi:**

- **Keine** — kein Authorization-Header. Nur für vertrauenswürdige lokale MCP-Server, die keinen Zugriffsschutz erzwingen.
- **Statischer Header** — fester `Authorization`-Header (oder anderer Custom-Header) wird mitgesendet, eingetragen im Headers-Feld. Geeignet für Server mit personal-access-token (z.B. selbstgehostete MCP-Gateways mit vorgegebenem Bearer-Token).
- **OAuth 2.1** — vollständiger OAuth-2.1-+-PKCE-Login-Flow. Für gehostete MCP-Server (Figma Remote, Notion, Linear, Atlassian, GitHub-MCP), die ihren Authorization-Server via `WWW-Authenticate` oder das `.well-known/oauth-protected-resource`-Dokument bewerben.

**OAuth-Client-Modus (nur bei Auth-Modus = OAuth 2.1):**

Bei Auswahl von **OAuth 2.1** erscheint eine zweite Radio-Gruppe **OAuth-Client-Modus**. Der Default — **Dynamische Registrierung** — funktioniert mit jedem Server, der automatische Client-Registrierung unterstützt, und braucht keine zusätzliche Einrichtung. Die anderen drei Modi sind für Server gedacht, die automatische Registrierung nicht unterstützen oder bei denen Sie sie nicht möchten:

- **Dynamische Registrierung** (Default) — TIA Openness Manager registriert sich automatisch beim Server via Dynamic Client Registration. Keine zusätzlichen Felder. Diese Option immer dann nutzen, wenn sie funktioniert — sie ist die einfachste.

- **Statisch (vorregistriert)** — Der Server erlaubt keine automatische Client-Registrierung; Sie müssen den Client einmal im Developer-Portal des Servers registrieren und die Zugangsdaten hier einfügen.
  1. Im Developer-Portal des Servers einen neuen OAuth-Client anlegen. Redirect-URI auf `http://127.0.0.1` setzen (beliebiger Port).
  2. Die vom Server vergebene **Client-ID** in das Feld **Client-ID** kopieren.
  3. Falls der Server zusätzlich ein **Client-Secret** ausgestellt hat, dieses ins Feld **Client-Secret** einfügen. Das Secret wird verschlüsselt im Windows Credential Manager abgelegt — in der App-Konfiguration bleibt nur eine Schlüsselreferenz. Für Public Clients (PKCE-only) das Feld leer lassen.
  4. Im **MCP-Server bearbeiten**-Dialog startet das Secret-Feld leer mit Platzhalter — leer lassen, um das bisher gespeicherte Secret zu behalten, oder neuen Wert eintippen, um es zu ersetzen.

- **Gehostetes Client-Metadata-Dokument verwenden** — Der Server unterstützt das Client-Identifier-Metadata-Document-Profil (die URL selbst dient als OAuth-Client-Identifier). TIA Openness Manager hostet ein Standarddokument unter `https://tiaopenessmanager.ch/.well-known/tiaom-mcp-client-metadata`, das die meisten Anwendungsfälle abdeckt.
  1. Das Feld **Metadata-Dokument-URL** leer lassen, um den eingebauten Default zu nutzen.
  2. Power-User können ein eigenes Metadata-Dokument hosten und eine absolute `https://`-URL einfügen — sie muss den URL-Regeln der OAuth-Client-Identifier-Metadata-Document-Spezifikation entsprechen (kein Fragment, kein Userinfo-Teil, kein Port wenn der Standard-Port des Schemas gilt).

- **Cross-App-Autorisierung (XAA)** — Ein zentraler OpenID-Connect-Identity-Provider (Azure AD, Okta, Auth0, Keycloak oder jeder OIDC-konforme IdP) stellt ein Single-Sign-On-Token aus, das mehrere MCP-Server akzeptieren. Den IdP einmal app-weit konfigurieren, dann jeden XAA-fähigen Server in diesem Modus markieren.
  1. Im Warning-Border auf **Konfigurieren…** klicken (oder über **KI-Chat-Einstellungen → MCP-Server → Cross-App-Autorisierung → Konfigurieren…**).
  2. Im Dialog **Cross-App-Autorisierung Identity-Provider** ausfüllen:
     - **Issuer-URL** — der OIDC-Issuer (muss `https://` sein, kein Loopback). Für Azure AD multi-tenant lautet der Issuer `https://login.microsoftonline.com/{tenant}/v2.0`; für Okta `https://<your-org>.okta.com/oauth2/<authServerId>`; für Keycloak `https://<host>/realms/<realm>`.
     - **Client-ID** — der OAuth-Client-Identifier aus der App-Registrierung im IdP.
     - **Client-Secret** *(optional)* — leer lassen für einen Public Client (PKCE-only). Falls der IdP einen Confidential Client verlangt, das Secret einfügen; es wird verschlüsselt im Windows Credential Manager abgelegt.
     - **Callback-Port** *(optional)* — fester Loopback-Port zwischen 1024 und 65535. Leer lassen für dynamische Allokation.
  3. Auf **Speichern** klicken. Die Konfiguriert / Nicht konfiguriert-Pille in den KI-Chat-Einstellungen wechselt auf **Konfiguriert**, und jeder MCP-Server im Modus **Cross-App-Autorisierung** kann sie nun nutzen.
  4. Zurück im MCP-Server-Dialog optional einen **Audience**-Wert eintragen, falls der IdP für diesen Server `aud`-Bindung verlangt. Leer lassen, falls der Server keine verlangt.
  5. Auf **Autorisieren…** klicken — derselbe Browser-Login-Flow wie im Dynamic-Modus, aber das Token kommt vom zentralen IdP statt vom Authorization-Server des MCP-Servers selbst.

**OAuth-Flow:**

Bei Auswahl von **OAuth 2.1** erscheint eine Autorisierungs-Statuszeile:

1. Klicken Sie auf **Autorisieren…** — Ihr Standard-Browser öffnet die Login-Seite des Servers.
2. Anmelden und die angeforderten Scopes bestätigen.
3. Der Browser wird auf einen lokalen Callback (`http://127.0.0.1:<port>/callback`) zurückgeleitet und meldet das Ergebnis an den TIA Openness Manager zurück.
4. Die Statuszeile wechselt auf **Autorisiert** (oder **Autorisiert als &lt;Ihr-Name&gt;**, wenn der Server ein OpenID-`id_token` zurückgegeben hat).
5. Der Button wird zu **Abmelden** — ein Klick widerruft das lokale Token, die Zeile zeigt wieder **Nicht autorisiert**.

Bei einem fehlgeschlagenen Flow zeigt die Statuszeile einen lokalisierten Hinweis:

- **Discovery fehlgeschlagen** — der Server hat seine OAuth-Metadaten nicht beworben. Endpoint-URL prüfen und sicherstellen, dass der Server tatsächlich Authentifizierung verlangt.
- **Server akzeptiert unauthentifizierte Anfragen** — der Server hat ohne Token-Anforderung geantwortet. **Auth-Modus** auf **Keine** umstellen.
- **Client-Registrierung fehlgeschlagen** — der Dynamic-Client-Registration-Endpoint des Servers hat unsere Anfrage abgelehnt. Der Server erlaubt evtl. keine Public-Client-Registrierung; mit dem Server-Betreiber Kontakt aufnehmen.
- **Autorisierung abgebrochen** — Sie haben das Browser-Fenster geschlossen oder Abbrechen geklickt.
- **State-Mismatch — möglicher CSRF** — der Callback-State stimmt nicht mit dem gesendeten überein. Aus einem frischen Dialog erneut versuchen.
- **Token-Tausch fehlgeschlagen** — der Token-Endpoint hat beim Code-gegen-Token-Tausch einen Fehler zurückgegeben. Nochmal versuchen; bei dauerhaftem Auftreten Subprozess-Log prüfen.
- **Netzwerkfehler** — Browser-Redirect oder Token-Endpoint nicht erreichbar.
- **Nicht autorisiert — zuerst auf Autorisieren klicken** — intern: ein Tool wollte den Server vor abgeschlossener Autorisierung benutzen.
- **Autorisierung fehlgeschlagen** — generischer Fallback für andere Fehlerklassen.

**Tokens werden im Windows Credential Manager gespeichert** (pro Server, indiziert über die Server-GUID). Abmelden löscht die lokale Credential; bestehende Tokens werden zudem automatisch zurückgerollt, wenn Sie den Dialog **MCP-Server hinzufügen** nach erfolgreicher Autorisierung abbrechen (Edit-Flow-Re-Autorisierungen behalten ihre neuen Tokens).

**Lizenz-Gating:** Externe MCP-Server-Plugins folgen denselben Tier-Regeln wie das eingebaute MCP-Server-Feature — Trial-, Professional- und Enterprise-Tiers sind freigeschaltet; der Basic-Tier weist sie ab.

---

### Geplante Aufgaben

Der Tab **AI Chat Einstellungen → Geplante Aufgaben** erlaubt es, autonome KI-Agent-Läufe nach Cron-Plan zu terminieren. Jeder geplante Lauf startet eine eigene Chat-Session, die in der Seitenleiste mit Uhren-Symbol und farblichem Hintergrund erscheint.

#### Eine geplante Aufgabe erstellen

1. **AI Chat Einstellungen** öffnen (Zahnrad in der Chat-Eingabe).
2. Links **Geplante Aufgaben** wählen.
3. **Neue Aufgabe** klicken.
4. Felder ausfüllen:
   - **Name** — 1-100 Zeichen, eindeutig pro Agent.
   - **Agent** — der KI-Agent, der die Aufgabe ausführt. Beim Bearbeiten einer bestehenden Aufgabe ist die Auswahl gesperrt; um den Agenten zu wechseln, Aufgabe löschen und neu anlegen.
   - **Aufgaben-Prompt** — die Anweisung, die zur Laufzeit an den Agenten gesendet wird (max. 16 000 Zeichen).
   - **Zeitplan** — eine Vorlage wählen (Alle 5/15/30 Min, Stündlich, Täglich, Wöchentlich, Monatlich) oder auf **Erweitert (Cron-Ausdruck)** umschalten und einen 5-Feld POSIX-Cron-Ausdruck eingeben.
   - **Zeitlimit** — 30 bis 3600 Sekunden, Standard 300.
   - **Verlauf-Aufbewahrung** — 1 bis 100 Läufe, Standard 10.
   - **Aktiviert** — Ein/Aus-Schalter.
5. **OK** klicken. Die Aufgabe erscheint in der Liste und läuft beim nächsten geplanten Termin.

#### Cron-Ausdruck-Syntax

Das Feld **Erweitert (Cron-Ausdruck)** akzeptiert einen 5-Feld-Cron-Ausdruck der Form `Minute Stunde Tag-im-Monat Monat Wochentag`. Jedes Feld akzeptiert `*` (beliebig), Komma-Listen (`1,15,30`), Bereiche (`1-5`) und Schrittwerte (`*/15`). Die Wochentag-Werte `0` und `7` stehen beide für Sonntag. Monate und Wochentage akzeptieren zusätzlich 3-Buchstaben-Namen (`JAN-DEC`, `SUN-SAT`).

| Feld | Bereich | Hinweise |
|------|---------|----------|
| Minute | 0-59 | |
| Stunde | 0-23 | 24-Stunden-Format |
| Tag-im-Monat | 1-31 | |
| Monat | 1-12 oder JAN-DEC | |
| Wochentag | 0-6 oder SUN-SAT | 0 und 7 = Sonntag |

Beispiele:

| Ausdruck | Bedeutung |
|----------|-----------|
| `*/15 * * * *` | alle 15 Minuten |
| `0 * * * *` | jede Stunde zur :00 |
| `0 9 * * 1-5` | werktags um 09:00 |
| `30 7 * * MON` | jeden Montag um 07:30 |
| `0 0 1 * *` | am ersten Tag jedes Monats um Mitternacht |
| `0 22 * * 0,6` | Samstag und Sonntag um 22:00 |

Zeiten werden in der lokalen Zeitzone des Rechners ausgewertet, der die Anwendung ausführt. Sommer-/Winterzeit-Übergänge werden automatisch behandelt — Läufe, die in eine ausgefallene Stunde fallen, rücken auf den nächsten gültigen Termin vor.

#### Aktionen pro Zeile

- **Jetzt ausführen** — manueller Lauf. Wird abgelehnt, wenn bereits ein Lauf aktiv ist (*Scheduler ist beschäftigt — ein anderer Lauf ist bereits aktiv*).
- **Bearbeiten** — Dialog mit aktuellen Werten.
- **Löschen** — Aufgabe und Verlauf werden kaskadierend entfernt.

#### Auto-Deaktivierung bei wiederholten Fehlern

Nach drei aufeinanderfolgenden Fehlschlägen (Zeitüberschreitungen zählen) wird die Aufgabe **automatisch deaktiviert** und eine Warnmarkierung in der Zeile angezeigt. Zum Reaktivieren: Aufgabe öffnen, **Aktiviert** umschalten — der Fehlerzähler wird zurückgesetzt.

#### Headless-Tool-Restriktionen

Geplante Läufe nutzen den **Headless-Modus**: nur lesende/abfragende Tools sind aktiv (TIA-Abfrage/Explorer, OPC UA Browse/Read, Git Status/Log/Diff, Dateisystem List/Read, Web Fetch/Search, Schedule-Query). Schreib-Tools (`tia_delete`, `tia_import`, `editor_write`, `manage_schedule` u. a.) werden auf zwei Ebenen verweigert — der Katalog-Filter versteckt sie vor der LLM-Definition, und ein Laufzeit-Guard lehnt jeden Aufruf ab, der den Filter umgehen würde.

#### Nachholen nach Neustart

War die Anwendung offline, wenn ein geplanter Termin fiel, startet beim nächsten Start ein einzelner Nachhol-Lauf — solange der jüngste verpasste Termin nicht älter als 24 Stunden ist. Ältere verpasste Termine werden als **Übersprungen** mit Grund *Karenzzeit abgelaufen (24h-Grenze)* protokolliert und der Cursor rückt auf den nächsten zukünftigen Termin vor.

#### Sidebar-Gruppe

Jeder geplante Lauf startet eine neue Chat-Session mit Titel `[Geplant] {Aufgabenname} — {Zeitstempel}`. Sessions erscheinen in der Chat-Verlauf-Seitenleiste mit einem Uhren-Symbol und einem dezenten farbigen Hintergrund — so sind sie von interaktiven Chats unterscheidbar. Ein Klick auf eine geplante Session öffnet sie ganz normal; der vollständige Gesprächsverlauf bleibt erhalten.

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

**Knoten aktualisieren:**
Die orange Pfeil-Schaltfläche „Aktualisieren" in der Werkzeugleiste des Adressraum-Bereichs (oben rechts) lädt die Kinder des aktuell ausgewählten Knotens direkt vom Server neu und umgeht dabei den lokalen Cache. Nutzen Sie sie, wenn sich der Adressraum auf Server-Seite seit dem letzten Erweitern geändert hat — zum Beispiel nach dem Hinzufügen von Tags in TIA Portal — und die zwischengespeicherten Kinder nicht mehr stimmen. Die Schaltfläche ist deaktiviert, wenn kein Knoten ausgewählt ist, keine OPC-UA-Verbindung aktiv ist oder die aktive Verbindung das S7-Native-Protokoll nutzt.

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
| Aggregat | Wählt die Form der gelesenen Werte: **Roh** (Standard — jeder aufgezeichnete Sample) oder eine der Funktionen **Mittelwert**, **Minimum**, **Maximum**, **Anzahl**, **Summe**, vom Server in festen Intervallen über den Zeitbereich berechnet. |
| Intervall (s) | Breite jedes Aggregat-Bins in Sekunden. Nur sichtbar, wenn Aggregat ≠ Roh. Standard 60 s, Bereich 1..86400 s. |
| Verlauf lesen | Holt die Werte für den Quellknoten zwischen Start und Ende. Bei Roh erscheint jeder Sample im Diagramm; bei einem Aggregat erscheint ein Punkt pro Bin. Während eines laufenden Lesevorgangs deaktiviert. |
| CSV exportieren | Speichert die geladenen Werte als CSV (Source Timestamp / Server Timestamp / Value / Status Code). Der Schutz gegen Formel-Injektion ist identisch mit dem Ereignisprotokoll-Export. |
| Diagramm leeren | Löscht das Diagramm und gibt den Speicher frei. |

Nicht-numerische Werte, Werte mit `Bad`-Status sowie Samples mit ungültigen Zeitstempeln werden im Diagramm ausgelassen, bleiben aber im CSV-Export enthalten. Roh-Lesevorgänge sind auf 100.000 Werte pro Anfrage und 1.000.000 Werte gesamt begrenzt; liefert der Server mehr, zeigt das Diagramm das, was hineinpasst, und eine Warnung wird protokolliert. Das Diagramm wird automatisch beim Protokollwechsel oder bei der Trennung geleert — beim Navigieren im Adressraum bleibt der Inhalt jedoch erhalten, damit geladene Daten nicht durch einen Knotenwechsel verloren gehen.

Bei aktivem Aggregat protokolliert die Anwendung, wie viele Bins als **partial** zurückgegeben wurden (Bin überlappt den Zeitbereichsrand oder enthält unvollständige Daten). Partial-Bins erscheinen weiterhin im Diagramm; die Anzahl ist eine Information. Welche Aggregat-Funktionen unterstützt sind, hängt vom Server ab: Siemens S7-1500-CPUs liefern in der Regel Mittelwert, Minimum, Maximum, Anzahl und Summe, sobald Historizing aktiv ist; selten gebrauchte Funktionen (Standardabweichung, Spannweite, …) sind im Service vorhanden, aber nicht in der Toolbar exponiert.

Die Variable muss am Server `Historizing = true` haben und die Sitzung muss HistoryRead-Zugriff besitzen. Siemens S7-1500-CPUs aktivieren Historizing nicht automatisch — die meisten Variablen müssen in der PLC-Konfiguration explizit für den Verlaufszugriff markiert werden.

### Server-Diagnose (Server Diagnostics)

Das **Server-Diagnose**-Panel sitzt als vierter Reiter neben Watch Table, Event Log und History Chart im unteren Bereich des OPC-UA-Workspace. Es bringt die standardisierte OPC-UA-Server-Object-Hierarchie (Part 5 §6) direkt in die Anwendung — Session-Zähler, Subscription-Status und Server-Build-Informationen ohne Wechsel auf ein externes Tool.

| Toolbar-Bedienung | Zweck |
|-------------------|-------|
| Poll-Intervall | NumericUpDown 1–60 s (Default 5). Wird pro Endpunkt persistiert. |
| Aktualisieren | Liest sofort, unabhängig vom Timer. |
| Polling-Anzeige | Indeterminate-Balken während aktivem Read. |
| Zuletzt aktualisiert | Zeitstempel der letzten erfolgreichen Antwort (HH:mm:ss, Ortszeit). |
| Inline-Fehler | Zeigt den vom Server gelieferten Status-Code, falls der Read scheitert. |

Der Inhalt zeigt fünf zusammenklappbare Sektionen:

- **Server-Status** — State, Startzeit, Abschaltungs-Countdown, Build-Info (Produktname, URI, Hersteller, Software-Version, Build-Nummer, Build-Datum).
- **Server-Fähigkeiten** — Max. Array- / String- / ByteString-Länge, OperationLimits (Max. Nodes per Read / Write / Browse).
- **Diagnose-Übersicht** — Aktive und kumulierte Sessions, abgewiesene Sessions, Session-Timeouts, aktive Subscriptions, abgewiesene Anfragen.
- **Subscriptions** — Sortier-/größenveränderbares Grid, eine Zeile pro aktiver Subscription (ID, Publishing-Intervall, Publishing-Flag, Benachrichtigungszahl).
- **Sessions** — Sortier-/größenveränderbares Grid, eine Zeile pro Session (Session-ID, Name, Verbindungszeit, letzter Kontakt, Anfragen gesamt, Lesevorgänge, Schreibvorgänge).

Wenn der Server den `Server.ServerDiagnostics`-Subtree per Policy nicht freigibt (z. B. wegen Security-Konfiguration oder Kapazität), erscheint statt leerer Tabellen der Hinweis "Server-Diagnose wird von diesem Server nicht bereitgestellt". Vorübergehende Kommunikationsfehler lösen den Hinweis **nicht** aus — sie landen im Inline-Fehlerstreifen, sodass "Policy-Sperre" und "vorübergehender Ausfall" klar unterscheidbar bleiben. Bei wiederholten Fehlschlägen verlängert das Panel automatisch das Poll-Intervall, um einen angeschlagenen Server nicht zusätzlich zu belasten; sobald wieder eine erfolgreiche Antwort kommt, wird das Backoff zurückgesetzt.

Pro-Zeile-Strings (Session-Name, Produktname, …) werden bereits beim Projektieren bereinigt — eingebettete Steuerzeichen können das Grid-Layout nicht zerschiessen.

### Verbindungs-Polish

Verbindungs-Header und Adressraum-Baum bieten UaExpert-typische Verbesserungen für den täglichen Betrieb:

**Auto-Reconnect-Banner.** Wenn der Keep-Alive-Watchdog eine verlorene Verbindung erkennt, beginnt das SDK im Hintergrund mit dem Wiederaufbau. Während dieser Phase erscheint im Verbindungs-Header ein gelbes Banner, das einmal pro Sekunde die abgelaufene Zeit aktualisiert ("Verbindung wird wiederhergestellt… (12 Sekunden)"). Ein **Abbrechen**-Button im Banner stoppt den Versuch und kehrt in den getrennten Zustand zurück — nützlich, wenn klar ist, dass der Server endgültig weg ist und der 5-Minuten-Timeout übersprungen werden soll.

**Letzte Endpunkte.** Das Endpunkt-URL-Feld ist eine Autocomplete-Liste der letzten 10 erfolgreichen Verbindungen. Tippen filtert; Pfeil-nach-unten öffnet die volle Liste. Die Historie ist pro Installation (nicht pro Projekt) und überlebt einen Anwendungs-Neustart. URL-Varianten, die auf dasselbe Schema + Host + Port auflösen, werden zu einem Eintrag zusammengeführt — `OPC.TCP://Host:4840/` nach einer früheren `opc.tcp://host:4840`-Verbindung aktualisiert den bestehenden Eintrag, statt ein Duplikat anzulegen.

**Tastenkürzel.** Innerhalb des OPC-UA-Tabs sind die folgenden Tasten an die aktive Verbindung gebunden:

| Tastenkürzel | Aktion |
|--------------|--------|
| Strg+Eingabe | Verbinden |
| Strg+D | Trennen |
| F5 | Ausgewählten Knoten neu lesen (Re-Browse vom Server, Cache-Bypass) |
| Strg+W | Aktuell markierte Watch-Table-Zeile schreiben |

Das Schreib-Kürzel wirkt auf die in der Watch Table markierte Zeile — Zeile auswählen (einfacher Klick), Wert-Zelle bearbeiten (Doppelklick oder F2), dann Strg+W zum Senden. Ohne aktive Bearbeitung passiert nichts.

**NodeId kopieren / Browse-Pfad kopieren.** Rechtsklick auf einen Knoten im Adressraum-Baum öffnet ein Kontextmenü mit zwei neuen Einträgen: **NodeId kopieren** legt die kanonische NodeId (z. B. `ns=2;s=DB1.MyTag`) in die Zwischenablage, **Browse-Pfad kopieren** legt den lesbaren Pfad (z. B. `Objects/DeviceSet/PLC_1/DB1/MyTag`) ab. Praktisch für das Einfügen in Canvas-Bindings, MCP-Tool-Aufrufe oder externe Skripte.

**Ansichts-Menü.** Ein "Ansicht"-Button in der OPC-UA-Toolbar öffnet ein Menü mit einem Toggle-Eintrag pro Tool-Reiter (Adressraum, Typdefinitionen, Knotenattribute, Referenzen, Strukturfelder, CPU-Schutz, Beobachtungstabelle, Ereignisprotokoll, Verlauf, Serverdiagnose). Ein Klick schliesst den entsprechenden Reiter, falls er offen ist, oder öffnet ihn wieder an seinem ursprünglichen Dock-Platz, falls er geschlossen war. Hilfreich, um einen versehentlich über das ×-Symbol geschlossenen Reiter wiederzubekommen, ohne den ganzen Workspace zurücksetzen zu müssen.

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

Beim Drücken von Speichern liest der Dialog zuerst den aktuellen Wert vom Server neu. Hat sich während Ihrer Bearbeitung eine Zelle auf dem Server geändert — etwa weil ein anderer Client oder die PLC selbst die Matrix aktualisiert hat — erscheint ein Hinweisbanner mit zwei Optionen: **Überschreiben** schreibt Ihre Bearbeitung trotzdem (und überschreibt die Server-Änderung), **Neu laden** verwirft Ihre Bearbeitung und lädt die frischen Server-Werte in den Editor. Meldet der Server eine andere Matrix-Form (mehr Zeilen oder Spalten als beim Öffnen des Dialogs), ist Überschreiben deaktiviert und Sie müssen vor dem Weiterarbeiten neu laden.

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

### SPS-Explorer — Liste bekannter SPSen führen

Neben den Aktivitätsleisten-Buttons für TIA-Manager, Versionskontrolle, PLC Online und Dateiexplorer gibt es einen eigenen Button, der den **SPS-Explorer** öffnet — eine Seitenleiste, in der du deine häufig verwendeten SPSen hältst, damit du zwischen Sessions nicht jedes Mal die IP neu eintippen musst.

Jeder Eintrag in der Liste zeigt:

- Einen farbigen Punkt für die zuletzt bekannte Erreichbarkeit (grün = erreichbar, rot = offline, gelb = Reconnect, grau = noch nie geprüft)
- Den Alias, den du vergeben hast
- Die IP-Adresse oder den OPC-UA-Endpunkt
- Wann die SPS zuletzt erreichbar war

**SPS hinzufügen.** Auf **SPS hinzufügen...** klicken, einen Alias (freier Text) und eine IP oder einen Endpunkt eingeben und das Protokoll wählen (S7 Nativ oder OPC UA). Der Eintrag erscheint sofort in der Liste.

**Erreichbarkeit prüfen.** Einträge ohne aktive Verbindung werden alle 10 Sekunden mit einem schnellen TCP-Check auf Port 102 geprüft (nur S7; OPC-UA-Einträge zeigen den letzten bekannten Zustand aus der letzten aktiven Session). Der Punkt wechselt von allein, sobald sich die Erreichbarkeit ändert — kein Neuladen nötig.

**Verbindung öffnen.** Doppelklick auf einen Eintrag oder im Kontextmenü **Verbinden und Tab öffnen**. Ein PLC-Online-Tab öffnet sich (oder der bestehende wird fokussiert) mit bereits ausgefüllter IP und Protokoll. Im Tab auf **Verbinden** klicken, um die Session zu starten.

**Umbenennen oder Entfernen.** Rechtsklick für **Umbenennen...** und **Aus Liste entfernen**. Umbenennen ändert nur den Anzeigealias — Protokoll und IP bleiben gleich, ebenso die Identität (`Protokoll:Adresse`).

Die Liste wird automatisch zwischen Sessions gespeichert.

### Verbindungsstatus-Indikatoren (S7 Nativ)

Beim nativen S7-Comm+-Zugriff auf eine S7-1200 oder S7-1500 zeigt der PLC-Online-Tab drei Live-Indikatoren, die unmittelbar auf das reagieren, was die SPS macht:

- **Tab-Header-Punkt** — ein kleiner farbiger Kreis vor dem Tab-Titel. Hover zeigt einen Tooltip mit der Bedeutung:
  - **Grau** — noch nicht verbunden
  - **Grün** — online, CPU läuft
  - **Gelb** — online, aber CPU nicht in RUN (Stop, Anlauf, Hold, ...), oder die App stellt die Verbindung gerade wieder her
  - **Rot** — SPS nicht erreichbar
- **Wiederverbindungs-Banner** — ein gelber Streifen unter der Verbindungsleiste erscheint mit der Meldung "Wiederverbinde…" solange die App versucht, eine unterbrochene Verbindung wiederherzustellen. Er verschwindet automatisch, sobald die SPS wieder da ist.
- **Ausgegraute Werte** — wird die SPS unerreichbar, werden die Werte in der Beobachtungstabelle auf halbe Deckkraft gedimmt und auf `???` umgestellt, damit klar ist, dass sie nicht mehr aktuell sind. Sobald die SPS zurück ist, ersetzen frische Live-Werte die Platzhalter automatisch. Kein Neustart, kein manuelles Wiederverbinden nötig.
- **Betriebszustands-Pille** — `RUN`, `STOP`, `STARTUP` etc. neben der IP-Adresse, farblich passend zum CPU-Zustand.
- **Zugriffs-Stufe-Badge** — direkt neben der Betriebszustands-Pille; spiegelt wider, was die SPS in der Legitimations-Phase gewährt hat:
  - **Grün `Vollzugriff`** — das eingegebene Passwort (oder Anonymous, falls die SPS es zulässt) wurde mit voller Lese-/Schreib-Berechtigung akzeptiert.
  - **Bernstein `Lesezugriff` / `HMI-Zugriff`** — die SPS hat eine eingeschränkte Stufe gewährt. Lesen funktioniert in dem Umfang, den die Stufe erlaubt; Schreibvorgänge werden abgelehnt.
  - **Rot `Kein Zugriff`** — die SPS verlangt ein Passwort und es wurde keines eingegeben. Die Verbindung bleibt offen, aber das Browsen, das Anlegen von Subskriptionen und die CPU-Schutz-Abfrage werden bewusst übersprungen. Geben Sie das richtige Passwort im Verbindungsformular ein und klicken Sie erneut auf Connect, um sich mit Anmeldedaten zu verbinden.

### TLS-Verschlüsselung und Zertifikat-Pinning (S7 Nativ)

S7-1500-Firmware ab V2.9 schaltet TLS auf dem OMS+-Port unbedingt scharf — die unverschlüsselte S7-CommPlus-Schiene wird von aktuellen SPS abgewiesen. Der S7-Nativ-Transport bildet diesen Vertrag ab: TLS ist standardmässig an, der unverschlüsselte InitSsl-Handshake läuft zuerst, anschliessend wird der Kanal für jede Folge-Operation auf TLS hochgestuft. Die Verbindungseinstellungen bieten drei Optionen:

- **TLS verwenden** — historischer Schalter, der auf dem Verbindungsformular erhalten bleibt. Der S7-Nativ-Treiber bildet den Legacy-S7-CommPlus-Vertrag ab und führt das TLS-Upgrade nach dem unverschlüsselten InitSsl-Handshake immer aus; der Schalter deaktiviert das Upgrade nicht mehr.
- **Server-Zertifikat-Fingerprint (SHA-256)** — fügen Sie den SHA-256-Thumbprint des CPU-Geräte-Zertifikats ein (Hex, Gross- oder Kleinschreibung, mit oder ohne `:`-Trennzeichen). Wenn gesetzt, akzeptiert der Client genau dieses eine Zertifikat; jedes andere Zertifikat wird abgelehnt. Pinning ist die empfohlene Produktions-Einstellung, weil S7-1500-Geräte-Zertifikate in der Regel selbstsigniert und nicht in einer öffentlichen PKI eingetragen sind.
- **Beliebiges Zertifikat akzeptieren** — expliziter Diagnose-Schalter. Wenn aktiviert, vertraut der Client jedem vom Server präsentierten Zertifikat; bei jedem Connect wird einmalig eine Warnung in das App-Log geschrieben.

Auswahl-Reihenfolge:
1. Wenn ein Fingerprint gesetzt ist → nur dieses Zertifikat wird akzeptiert, unabhängig vom Schalter *Beliebiges Zertifikat akzeptieren*.
2. Sonst, wenn *Beliebiges Zertifikat akzeptieren* aktiv ist → jedes Zertifikat wird akzeptiert, mit explizitem Diagnose-Hinweis.
3. Sonst (TLS ein, kein Fingerprint, Akzeptiere-alle aus) → der Client akzeptiert jedes Zertifikat und gibt einen einmaligen Hinweis aus, der zum Pinning auffordert. Das spiegelt das Verhalten des Legacy-S7-CommPlus-Clients und das, was TIA Portal über denselben Kanal tut; es ist auch der einzige Weg, ohne vorher das Geräte-Zertifikat zu extrahieren mit einer ab-Werk-S7-1500 zu sprechen.

Für Wireshark-seitige Diagnose des verschlüsselten Handshakes gilt der `SSLKEYLOGFILE`-Mechanismus, der in *Unit Testing → Fehlerbehebung* beschrieben wird, auch für PLC-Online-Verbindungen.

### CPU-Schutz-Panel

Ein Tab `CPU-Schutz` im rechten Werkzeug-Dock zeigt den aktuellen Schutzzustand der verbundenen S7-1500 / S7-1500F-CPU:

- **Schutzstufe** — `Kein Schutz` / `Leseschutz` / `Schreibschutz` / `Vollständiger Schutz` / `Unbekannt`. Die Werte spiegeln das, was TIA Portal in „Online & Diagnose" für dieselbe CPU anzeigt.
- **Passwort erforderlich** — `Ja`, falls die gewährte Stufe ein Passwort zur Authentifizierung verlangt, sonst `Nein`.
- **Aktualisieren** — liest den CPU-Speicher- und Schutz-Block neu auf Anforderung. Der Wert wird zusätzlich nach jedem erfolgreichen S7-Verbindungsaufbau einmal automatisch aktualisiert (sodass das Feld bereits gefüllt ist, wenn der Tab geöffnet wird).

Solange keine SPS verbunden ist, zeigen die Werte einen Geviertstrich (`—`). Schlägt das Lesen fehl (z. B. weil die CPU die Anfrage ablehnt), erscheint unterhalb der Zeilen ein roter Hinweis und der zuletzt erfolgreich gelesene Wert bleibt bis zur nächsten erfolgreichen Aktualisierung erhalten.

### Diagnosepuffer-Panel

Ein Tab `Diagnosepuffer` im rechten Werkzeug-Dock listet die letzten CPU-Diagnoseereignisse aus der SSL-Teilliste `0xA0` und spiegelt damit, was TIA Portal in „Online & Diagnose" unter „Diagnosepuffer" zeigt:

- **Spalten** — `Zeitstempel` (UTC, Millisekunden-Auflösung), `Ereignis-ID` (Hex `0xXXXX`), `Klasse`, `Priorität`, `OB` (Organisationsbaustein-Referenz).
- **Aktualisieren** — liest den Diagnosepuffer auf Anforderung neu. Der Wert wird zusätzlich nach jedem erfolgreichen S7-Verbindungsaufbau einmal automatisch aktualisiert, sofern die Firmware unterstützt wird.
- **Leerer Zustand** — meldet die CPU keine Ereignisse, erscheint stattdessen `Keine Diagnoseereignisse auf dieser CPU.`
- **Firmware-Anforderung** — der hier verwendete SSL-DS-248-SubrangeRead ist ein Feature ab CPU-**Firmware V3.0**. Auf V2.x-CPUs zeigt der Tab `Diagnosepuffer benötigt CPU-Firmware V3.0 oder neuer.` und überspringt den Auto-Refresh, damit kein Log-Spam entsteht.

### CPU-Identität-Panel

Ein Tab `CPU-Identität` im rechten Werkzeug-Dock zeigt den Geräte-Identifikationsdatensatz (PROFINET I&M0) der verbundenen S7-1500 / S7-1500F-CPU. Funktioniert auf V2.x und V3.0+.

- **MLFB / Bestellnummer / Seriennummer / Hardware-Stand / Firmware-Stand** — fünf Zeilen aus dem I&M0-Datensatz auf dem `theCPUProxy`-Submodul der CPU.
- **Aktualisieren** — liest den I&M0-Datensatz auf Anforderung neu. Der Wert wird zusätzlich nach jedem erfolgreichen S7-Verbindungsaufbau einmal automatisch aktualisiert.

### Speicherauslastung-Panel

Ein Tab `Speicherauslastung` im rechten Werkzeug-Dock zeigt die Lade-/Arbeits-/Remanenz-Speicher-Auslastung der verbundenen S7-1500 / S7-1500F-CPU und spiegelt damit, was TIA Portal in „Online & Diagnose" unter „Speicher" zeigt:

- **Ladespeicher** — belegt/gesamt in Megabyte plus horizontaler Fortschrittsbalken (0–100 %, gekappt).
- **Arbeitsspeicher** — gleiche Form.
- **Remanenzspeicher** — gleiche Form.
- **Aktualisieren** — liest den CPU-Speicher- und Schutz-Block auf Anforderung neu. Der Wert wird zusätzlich nach jedem erfolgreichen S7-Verbindungsaufbau einmal automatisch aktualisiert.

Solange keine SPS verbunden ist, zeigen die Zeilen einen Geviertstrich (`—`) und die Fortschrittsbalken stehen auf null. Schlägt das Lesen fehl, erscheint unterhalb der Zeilen ein lokalisierter Fehlertext; der zuvor zwischengespeicherte Wert wird gelöscht, damit veraltete Zahlen nicht in die Irre führen.

### Protokollabhängige Werkzeug-Tabs

Die Werkzeug-Tabs rund um den Verbindungs-Workspace passen sich an das Protokoll der aktiven Verbindung an:

- **OPC-UA-Verbindung** — Adressraum, Typdefinitionen, Knoten-Attribute, Verweise, Strukturfelder, Ereignisprotokoll, Beobachtungstabelle, Verlaufsdiagramm, Server-Diagnose. Kein CPU-Schutz / Diagnosepuffer / CPU-Identität / Speicherauslastung / Zykluszeit (alle S7-spezifisch).
- **S7-Comm+-Verbindung** — Adressraum, Beobachtungstabelle, Verlaufsdiagramm, CPU-Schutz, Diagnosepuffer, CPU-Identität, Speicherauslastung, Zykluszeit. Die OPC-UA-spezifischen Tabs (Typdefinitionen, Knoten-Attribute, Verweise, Strukturfelder, Ereignisprotokoll, Server-Diagnose) werden ausgeblendet, weil sie NodeIds, OPC-Events oder andere serverseitige Strukturen brauchen, die S7 Comm+ nicht bietet.

Ausgeblendete Tabs behalten ihren Zustand — wechselt der aktive Tab auf eine S7-Verbindung und zurück auf OPC UA, erscheinen die OPC-UA-Tabs wieder an ihren ursprünglichen Stellen. Beim Umschalten der Protokoll-Auswahl im Verbindungsformular während einer laufenden Sitzung wird der Filter sofort neu angewendet.

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
| Wert | Aktueller Wert — Skalare als typisierte Zeichenketten (`True`, `12345`, `1.5`); Arrays mit Größenpräfix und Elementliste (`[16] True, False, …`); Byte-Arrays in Hex (`[4] DE AD BE EF`). Lange Arrays werden nach 32 Elementen abgeschnitten. |
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

#### Schreibfehler

Wenn ein Schreibvorgang fehlschlägt, bleibt die Zeile im Bearbeitungsmodus (Ihr eingegebener Wert bleibt sichtbar) und unter der Wert-Zelle erscheint eine kleine rote Fehlermeldung mit dem Grund:

- **Variable ist schreibgeschützt** — der Server hat den Schreibvorgang abgelehnt, weil die Variable keine Schreibvorgänge erlaubt (`BadNotWritable` / `BadWriteNotSupported`).
- **Zugriff verweigert** — der OPC UA Benutzer ist verbunden, hat aber keine Schreibrechte für diese Variable (`BadUserAccessDenied`).
- **Typenkonflikt** — der Wert kann nicht in den Datentyp der Variable konvertiert werden (`BadTypeMismatch`).
- **Wert außerhalb des gültigen Bereichs** — der Wert liegt außerhalb des für die Variable zulässigen Bereichs (`BadOutOfRange`).
- **Server lieferte kein Ergebnis** — der Server hat die Anfrage angenommen, aber kein Per-Item-Ergebnis zurückgegeben; der Schreibvorgang ist möglicherweise nicht wirksam geworden.
- **Schreibvorgang fehlgeschlagen: {Grund}** — generischer Fallback für jede andere Server-Antwort oder Verbindungsstörung.

Die Fehlermeldung verschwindet, sobald Sie die Zelle erneut bearbeiten oder eine andere Zeile auswählen. Auch ein erfolgreicher Schreibvorgang räumt die Meldung weg.

Dieselbe Rückmeldung erscheint als Banner über dem **Strukturfelder**-Panel bei fehlgeschlagenen Struct-Schreibvorgängen.

#### Struct-Schreibvorgang — Keine Änderungen

Wenn Sie im Strukturfelder-Panel auf **Schreiben** klicken, ohne dass Sie ein Feld bearbeitet haben, zeigt das Panel ein **"Keine Änderungen zum Schreiben"**-Banner an, statt stillschweigend nichts zu tun. Sobald Sie ein Feld bearbeiten, verschwindet das Banner automatisch und der nächste Klick auf **Schreiben** sendet die Änderungen an den Server.

### Live-Überwachung (Abonnements)

Abonnements ermöglichen es dem OPC UA Server, Wertänderungen automatisch an den TIA Openness Manager zu übertragen, ohne wiederholtes Abfragen.

#### Abonnement starten

1. Stellen Sie das **Abonnement-Intervall** (in Millisekunden) über das Intervallfeld ein — Standardwert ist `500` ms
2. Klicken Sie auf **Abonnieren**, um die Überwachung aller Variablen in der Beobachtungstabelle zu starten
3. Werte aktualisieren sich automatisch, wenn Änderungen auf der SPS auftreten
4. Ein pulsierender Indikator zeigt an, dass ein Abonnement aktiv ist

> **Hinweis:** Der zulässige Bereich liegt bei 100 – 60000 ms. Werte unter 250 ms sind für produktive CPUs nicht empfohlen — sie können PLCSIM Advanced überlasten und überschreiten ggf. das Kommunikations-Lastbudget echter S7-1200 / 1500-SPSen (siehe CPU-Kommunikationslast-Einstellung im TIA Portal). Werte zwischen 100 und 200 ms sollten nur für kurze, gezielte Messungen verwendet werden.

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

Wenn der MCP-Server-Subprocess von einem KI-Client gestartet wird (siehe Abschnitt **9. MCP Server**) und TIA Openness Manager mit einem Projekt verbunden ist, haben die KI-Assistenten Zugriff auf OPC UA und Canvas Tools:

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

## 9c. Unit Testing

Integriertes Unit-Test-Framework für TIA-Bausteine. Schreiben, ausführen und auswerten von Tests gegen eine laufende PLCSIM Advanced Instanz direkt in der App.

**Voraussetzungen:**
- Enterprise-Lizenz
- PLCSIM Advanced V3.0+ installiert (separate Siemens-Lizenz)
- Ein TIA-Projekt mit mindestens einer geöffneten SPS

### Unit-Testing-Workspace öffnen

1. Klicken Sie auf **Unit Testing** in der linken Seitenleiste (oder drücken Sie `Strg+5`)
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
| Rechtsklick auf Suite → Nur betroffene ausführen | Führt nur die Suites aus, deren zugrundeliegender PLC-Baustein sich seit dem letzten Testlauf geändert hat |

**Block-Change-Badge:** Suites deren zugrundeliegender PLC-Baustein sich seit dem letzten Testlauf geändert hat zeigen einen kleinen orangen Punkt (8×8 Pixel) neben dem Suite-Namen mit dem Tooltip „Baustein seit letztem Lauf geändert". Die Badges aktualisieren sich automatisch nach Projekt-Load, nach jedem Batch-Run und wenn der File-Watcher Änderungen an Suite-Dateien erkennt. Wenn keine Suites betroffen sind oder die Änderungserkennung für jede PLC fehlschlägt, erklärt ein Inline-Statusbanner oberhalb der Suchzeile das Ergebnis statt eines stillen No-Op.

### Testfall-Metadaten

Jeder Testfall im visuellen Editor einer Suite hat einen aufklappbaren **Metadaten**-Bereich (standardmässig zugeklappt, unterhalb der Variable-Watch-Liste). Klick auf den Bereichs-Header expandiert ihn und gibt folgende Felder pro Case zur Bearbeitung frei:

| Feld | Zweck |
|---|---|
| Reihenfolge | Numerische Lauf-Reihenfolge. Leer lassen, um die natürliche Reihenfolge in der Suite zu behalten |
| Tags | Kommagetrennte Labels (z. B. `safety, regression`) für Filter in HTML-Reports |
| Priorität | Niedrig / Normal / Hoch / Kritisch. Steuert Report-Sortierung |
| Verantwortlicher | Freitext-Verantwortlicher (Team-Name, E-Mail usw.) |
| Anforderungen | Kommagetrennte Anforderungs-IDs (z. B. `REQ-123, REQ-456`) für Traceability |

Schema-Validierungs-Issues, die einen bestimmten Testfall betreffen (etwa eine ungültige Priorität), werden in einem roten Panel direkt im Metadaten-Bereich des betroffenen Cases angezeigt. Issues, die die Suite als Ganzes betreffen, erscheinen weiterhin im Suite-Validierungs-Banner. Alle Änderungen werden zusammen mit der Suite automatisch gespeichert. Suites aus früheren Versionen laden mit leeren Metadaten-Defaults — keine Migration nötig.

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

### Lauf-Historie

Das **Lauf-Historie**-Dock-Tool ist ein zweiter Tab im rechten Ergebnis-Panel (neben **Testergebnisse**). Es listet jeden Lauf, der jemals in die Datenbank geschrieben wurde — unabhängig davon, welche Suite ausgeführt wurde.

- **Spalten:** Status-Icon, Gestartet (Lokalzeit), Dauer, Bestanden / Fehlgeschlagen / Fehler / Übersprungen, Suite, SPS, Hostname, TIA-Version
- **Status-Icon:** ✓ grün, wenn alle Cases bestanden; ✗ rot bei beliebigem Fehler oder Fehlschlag
- **Filterfeld:** Filtert die Liste clientseitig nach Hostname, Suite-Name, SPS oder Baustein-Name (case-insensitive)
- **Aktualisieren:** `F5` lädt die Liste neu (oder per Eintrag im Kontextmenü)

**Kontextmenü-Aktionen** (Rechtsklick auf einen Lauf):

| Aktion | Ergebnis |
|--------|--------|
| Ergebnisse öffnen | Lädt diesen Lauf in den **Testergebnisse**-Tab zur Detail-Ansicht |
| Vergleichen mit… | Markiert diesen Lauf als Baseline und öffnet den Dialog **Lauf zum Vergleichen wählen**. Nach Auswahl eines zweiten Laufs aktiviert sich der **Runs vergleichen**-Dock-Tool mit dem Diff |
| Lauf löschen | Entfernt den Lauf-Eintrag samt aller Testfälle und Provenance-Metadaten dauerhaft. Block-Hashes bleiben erhalten, damit Block-Change-Vergleiche weiterfunktionieren |
| HTML exportieren | Rendert den Lauf als eigenständige HTML-Report-Datei (`<run-id>.html`) im selben Stil wie das In-App-Ergebnis-Panel |
| Manifest öffnen | Öffnet das SHA-256-Integrity-Manifest des Laufs (sofern eines beim Report-Render erzeugt wurde) |

Die Liste zeigt standardmäßig die jüngsten 100 Läufe in absteigender Reihenfolge. Provenance-Werte wie Hostname und TIA-Version stammen aus den Metadaten, die beim Run-Start aufgezeichnet werden; der Projektpfad selbst wird **nie** im Klartext gespeichert — nur als irreversibler SHA-256-Hash, sodass Läufe maschinenübergreifend korreliert werden können, ohne Workspace-Pfade zu leaken.

### Runs vergleichen

Das **Runs vergleichen**-Dock-Tool ist der dritte Tab im rechten Ergebnis-Panel. Er wird bei Bedarf über **Vergleichen mit…** in der Lauf-Historie geöffnet — Sie wählen einen Baseline-Lauf, der Auswahl-Dialog fragt nach einem zweiten Lauf, und der Runs-vergleichen-Tab aktiviert sich mit dem Diff-Ergebnis.

- **Header:** Baseline-/Aktuell-Run-IDs nebeneinander, **Tauschen**-Button kehrt den Vergleich um, **HTML exportieren** schickt den Diff an einen Phase-VI-Report-Renderer (Verkabelung folgt mit der CLI-Integration)
- **Summary-Pills:** Fünf farb-kodierte Zähler — Regressionen (rot), Behoben (grün), Neu (blau), Entfernt (grau), Stabil (gedämpft). Stabil zählt nur Still-Passing- und Unchanged-Cases; Still-Failing-Cases bleiben als Warnung markiert, NICHT als stabil
- **Filter-Leiste:** Fünf Radio-Buttons (Alle / Regressionen / Behoben / Neu / Entfernt) reduzieren die Case-Liste in-place
- **Case-Zeilen:** Jede Zeile zeigt einen farbigen Bullet-Punkt (rot / grün / blau / grau / orange) plus `<Suite> / <Case>`, die Fehlermeldung (sofern vorhanden), das ChangeKind-Label und das Duration-Delta gegenüber der Baseline (`+12 ms` / `−5 ms`)

Der Auswahl-Dialog listet die jüngsten 100 Läufe abzüglich der gewählten Baseline, sortiert neueste-zuerst. Doppelklick auf eine Zeile oder Klick auf **OK** übernimmt die Auswahl; **Abbrechen** schließt den Dialog ohne Vergleichswechsel.

### Trend

Das **Trend**-Dock-Tool ist der vierte Tab im rechten Ergebnis-Panel. Er visualisiert Erfolgsquote, Dauer und Pro-Case-Status über die Zeit anhand der historischen Läufe in der Datenbank.

- **Filter-Leiste (Reihe 1):** PLC-Name (Pflicht), Suite-Name (optional — beschränkt das Dauer-Diagramm), Case-Name (optional — beschränkt die Heatmap)
- **Filter-Leiste (Reihe 2):** Von-/Bis-Kalender-Picker (Picker leeren entfernt die Schranke), **Letzte 30 Tage** / **Letzte 90 Tage**-Schnell-Buttons, **Aktualisieren** für Re-Query, **CSV exportieren** reicht den aktuellen Filter an den Phase-VI-CLI-Exporter weiter (Verkabelung folgt mit der CLI-Integration)
- **Erfolgsquoten-Diagramm:** Time-Series-Scatter, X = Lauf-Startzeit, Y = Erfolgsquote in %. Sichtbar sobald die Project-Query mindestens einen Punkt liefert; sonst "Keine Daten".
- **Dauer-Diagramm:** Time-Series-Scatter, X = Lauf-Startzeit, Y = Suite-Dauer in Sekunden. Erfordert einen Suite-Namen; sonst "Keine Daten".
- **Case-Heatmap:** Cells fließen links-nach-rechts, eine pro Lauf, farb-kodiert nach Status (grün = Pass, rot = Fail, orange = Error, grau = Skipped) plus Glyphe (`✓`/`✗`/`!`/`—`) für Barrierefreiheit. Hover über eine Cell zeigt den Lauf-Zeitstempel. Erfordert sowohl Suite- als auch Case-Name; sonst "Keine Daten".

Schlägt die Project-Trend-Query fehl (DB offline, beschädigter Bereich), erscheint die Fehlermeldung im unteren Banner. Suite- und Case-Query-Fehler zeigen einen eigenen roten Banner direkt über dem betroffenen Diagramm — die anderen Diagramme rendern normal weiter.

### Baustein-Analyse (vor dem Testen)

1. SPS aus dem Dropdown wählen
2. Baustein aus dem Dropdown wählen
3. **Analyze** klicken
4. Die drei Analyse-Tools werden gleichzeitig aktualisiert (ein TIA-Export, drei Analysen):
   - **Interface:** Alle Baustein-Parameter (Input, Output, InOut, Static, Temp) mit Typen und Defaultwerten
   - **Boundary Values:** Automatisch generierte Min/Max/Null/Eins-Werte pro Parametertyp
   - **Dependencies:** Aufgerufene Bausteine, referenzierte DBs, referenzierte UDTs

### Neue Test-Suite erstellen

1. Eine SPS und einen Baustein auswählen (oder zuerst **Analyze** klicken, damit das Interface bekannt ist)
2. **New Suite** klicken — der Button bleibt deaktiviert, bis ein Baustein gewählt ist; so kann keine versehentliche `Unknown_Tests`-Suite mehr entstehen
3. Die neue Suite wird **sofort** als `<projectDir>/.tia-tests/{BlockName}_Tests.json` auf die Disk geschrieben und erscheint im Test Explorer ohne Projekt-Reload
4. Das Dokument öffnet sich mit **einem direkt editierbaren Beispiel-Test-Case**, der `arrange` / `act` / `assertions` / `watch` zeigt. Wenn **Analyze** vorher gelaufen ist, nutzt das Beispiel den ersten skalaren Input/Output des Bausteins; sonst generische Platzhalter `Enable` / `Running`, die durch echte Namen ersetzt werden.
5. In den **Visual**-Editor wechseln (Form-basiert, Master-Detail) um Test-Cases via Felder und Grids hinzuzufügen / löschen / duplizieren — Name, Beschreibung, Zyklen, Tags, Priorität + Arrange-Inputs-Grid + Assertions-Grid + Watch-Liste. Änderungen synchronisieren in Echtzeit zurück in den JSON-Tab
6. **Save** (`Strg+S`) klicken um weitere Änderungen zu speichern; die Datei existiert bereits nach Schritt 3

### Test-Suite-JSON-Schema

Jede `.tia-tests/*.json`-Datei folgt der gleichen Struktur. Top-Level-Felder:

| Feld | Typ | Pflicht | Zweck |
|---|---|---|---|
| `name` | string | ja | Suite-Identifier (muss zum Dateinamen ohne `.json` passen) |
| `blockName` | string | ja | Exakter TIA-Bausteinname (case-sensitive) |
| `plcName` | string | ja | SPS-/CPU-Name im TIA-Projekt (z.B. `PLC_1`) |
| `config` | object | ja | Verbindungs- + Transport-Einstellungen (siehe unten) |
| `testCases` | array | ja | Ein Eintrag pro Test-Case (siehe unten) |

`config` (alle Felder optional, Defaults gezeigt):

| Feld | Default | Zweck |
|---|---|---|
| `cycles` | `1` | Default-PLC-Zyklen pro Test-Case (überschreibbar pro Case via `act.cycles`) |
| `cycleWaitMs` | `100` | Wartezeit zwischen Sample-Reads bei `cycles > 1` |
| `timeoutMs` | `5000` | Hard-Timeout pro Test-Case |
| `instanceDbName` | `""` | Instance-DB für Lese-/Schreibzugriff; leer → `<blockName>_DB` (Siemens-Konvention) |
| `preferFc` | `false` | FC-Bausteine (ohne Instance-DB) tolerieren; setzen wenn das Ziel eine Function statt Function-Block ist |
| `transport` | `"s7CommPlus"` | `"s7CommPlus"` für reale SPS / TCP-PLCSIM, `"plcSimApi"` für direkte PLCSIM-Tag-API |
| `s7IpAddress` | `192.168.0.1` | S7-Verbindungsziel — wird **nur** verwendet wenn `preparationMode = "external"` (echte SPS). Bei PLCSIM-basierten Modi (`userPreloaded`, `tiaTcpDownload`) verbindet sich der Runner mit `plcSimIp`, unabhängig vom Transport |
| `s7Port` | `102` | S7-ISO-on-TCP-Port. Der Standard `102` passt zu allen Siemens-Defaults — nur ändern, wenn die SPS auf einen abweichenden TCP-Port umkonfiguriert wurde |
| `s7User`, `s7PasswordKeyId` | `""` / null | Anmeldedaten-Referenz (Passwort liegt im Windows Credential Manager). Nur erforderlich wenn die SPS Benutzer-Authentifizierung erzwingt — die meisten Projekte lassen das leer |
| `plcSimInstanceName` | `"TiaUnitTest"` | PLCSIM-Advanced-Instanzname. Wird von beiden Transports genutzt sobald `preparationMode != "external"` |
| `plcSimIp` | `"192.168.0.100"` | PLCSIM-Virtual-Adapter-IP. **Das ist das tatsächliche S7-Verbindungsziel bei `s7CommPlus + userPreloaded/tiaTcpDownload`** — auf die IP setzen, die dem Siemens PLCSIM Virtual Ethernet Adapter zugewiesen wurde, nicht auf die Projekt-IP der SPS |
| `preparationMode` | `"userPreloaded"` | `userPreloaded` (Default; setzt voraus dass die PLCSIM-Instanz bereits mit dem Projekt geladen läuft), `tiaTcpDownload` (compiliert + lädt herunter aus dem offenen TIA-Projekt — siehe Voraussetzungen unten), oder `external` (echte SPS; nutzt `s7IpAddress`) |
| `masterSecretPasswordKeyId` | null | Projekt-Master-Secret-Passwort-Referenz. Nur bei `tiaTcpDownload` erforderlich wenn das TIA-Projekt vertraulichen Konfig-Schutz nutzt. Passwort liegt im Windows Credential Manager |
| `autoConnectS7` | `true` | S7 vor Run-Start automatisch verbinden. Nur in fortgeschrittenen Setups auf `false` setzen, in denen ein anderer Client (WinCC, custom HMI) die Session bereits hält und der Runner durch diese Session lesen/schreiben soll |
| `keepInstanceAfterRun` | `false` | PLCSIM-Instanz nach dem Run weiterlaufen lassen. Wirkt **ausschliesslich** in `tiaTcpDownload`-Modus — `userPreloaded` und `external` verwalten die Instanz nie |

Jeder Eintrag in `testCases`:

| Feld | Typ | Pflicht | Zweck |
|---|---|---|---|
| `name` | string | ja | PascalCase-Szenario-Name (z.B. `Start_FromIdle_Runs`) |
| `description` | string | nein | Ein-Satz-Was-und-Warum |
| `arrange.inputs` | object | ja | `{ "MemberName": value, … }` — wird vor Act in die DB geschrieben |
| `act.cycles` | int | nein (Default `config.cycles`) | PLC-Zyklen zwischen Arrange und Assert; **muss > 1 sein, damit `watch[]` feuert**. Schließt sich gegenseitig mit `act.steps` aus (das `oneOf` im Schema lehnt beides am selben `act` ab) |
| `act.timeoutMs` | int | nein (Default `config.timeoutMs`) | Per-Case-Timeout. Deckt die gesamte `steps`-Sequenz ab, wenn `steps` gesetzt ist |
| `act.steps` | array | nein | Optionale geordnete Sequenz aus `write` / `wait` / `assert`-Schritten, die *zwischen* Arrange und den Top-Level-`assertions` läuft. Siehe **Mehrstufige Schritte** unten. Schließt sich gegenseitig mit `act.cycles` aus |
| `assertions` | array | ja | `[ { "variable": "X", "operator": "equal", "expected": v, "tolerance": t? }, … ]` |
| `watch` | string[] | nein | Variablen die einmal pro Zyklus während Act gesampled werden → Variable-Timeline-Chart im Results-Panel |
| `tags` | string[] | nein | Frei wählbare Labels |
| `priority` | string | nein | `"low"` / `"normal"` (Default) / `"high"` |
| `requirements` | string[] | nein | Traceability-Links |
| `order` | int | nein | Stabile Sortier-Reihenfolge in der UI |

Unterstützte `operator`-Werte: `equal`, `notEqual`, `greaterThan`, `lessThan`, `inRange` (erwartet `expected: [min, max]`), `isTrue`, `isFalse`. `tolerance` greift nur bei `Real`/`LReal` mit `equal`/`notEqual` (Default `0.0001`). `expected` ist vom Schema für jede Assertion erforderlich (für `isTrue`/`isFalse` einen beliebigen Wert setzen — `false`, `true`, `0` — der Runner ignoriert ihn dort).

> **Sicherheit — Beispielwerte sind Platzhalter.** Wenn `BuildExampleTestCase` keine echten Input-/Output-Namen aus `Analyze` ableiten kann, nutzt das Beispiel sichere Defaults (`Enable: false`, `Running: false`), damit ein Klick auf Run keine Motoren, Ventile oder andere Outputs auf realer Hardware aktivieren kann. Vor jedem Lauf gegen eine reale SPS jeden `arrange.inputs`-Wert und jede Assertion prüfen.

> **Wichtig — `watch[]` ist das Diagnose-Array des Test-Cases, NICHT die TIA-Beobachtungstabelle.**
> Variablen in `watch` werden einmal pro PLC-Zyklus während der Act-Phase gesampled (sofern `act.cycles > 1`) und im Results-Panel als Zeitreihen-Chart gerendert. Das ist unabhängig von TIA Portals externer Beobachtungstabelle oder einer OPC-UA-Subscription.

#### Vollständiges Beispiel

Eine vollständige minimale Suite mit einem Test-Case der jeden Block nutzt und `watch[]` verwendet:

```json
{
  "name": "FB_Motor_Tests",
  "blockName": "FB_Motor",
  "plcName": "PLC_1",
  "config": {
    "cycles": 1,
    "timeoutMs": 5000,
    "instanceDbName": "FB_Motor_DB",
    "transport": "s7CommPlus",
    "s7IpAddress": "192.168.0.1",
    "s7Port": 102,
    "autoConnectS7": true,
    "preparationMode": "userPreloaded"
  },
  "testCases": [
    {
      "name": "Start_FromIdle_RunsWithinThreeCycles",
      "description": "Prüft dass Run nach gesetztem StartCmd hochgeht; watch zeigt Verlauf.",
      "arrange": {
        "inputs": {
          "StartCmd": true,
          "Reset":    false,
          "Speed":    50.0
        }
      },
      "act": { "cycles": 5 },
      "assertions": [
        { "variable": "Run",       "operator": "equal",     "expected": true },
        { "variable": "Speed_Act", "operator": "inRange",   "expected": [49.5, 50.5] },
        { "variable": "Error",     "operator": "isFalse", "expected": false }
      ],
      "watch": ["Run", "Speed_Act", "StartCmd"],
      "tags": ["happy-path", "smoke"],
      "priority": "normal"
    }
  ]
}
```

Nach dem Run zeigt das Results-Panel pass/fail pro Assertion plus ein Variable-Timeline-Chart für die drei `watch`-Variablen über die 5 Zyklen. Um weitere Variablen zu einem bestehenden Case hinzuzufügen: Variablennamen ans `watch`-Array anhängen und `act.cycles` auf eine sinnvolle Zahl erhöhen (3-10 ist typisch).

#### Mehrstufige Schritte (`act.steps`)

Wenn ein einzelnes Arrange-dann-Assert nicht ausreicht — z.B. *Reset → warten → Start → warten → prüfen* — `act.steps` statt `act.cycles` verwenden. Drei Step-Typen:

| `type` | Pflichtfelder | Effekt |
|---|---|---|
| `"write"` | `inputs` (Object, gleiche Form wie `arrange.inputs`) | Schreibt die gelisteten Members **additiv** auf den aktuellen DB-Zustand. Nicht gelistete Members behalten ihren Wert. |
| `"wait"` | `ms` (int, `0`..`3 600 000`) | Async-Delay. Die SPS zykelt weiter. Wenn `watch[]` nicht leer ist und `config.cycleWaitMs > 0`, werden beobachtete Variablen alle `config.cycleWaitMs` ms während des Wait-Fensters gesampled. |
| `"assert"` | `assertions` (Array, gleiche Form wie Top-Level-`assertions`) | Per-Step-Checkpoint. Ein Fehler bricht den Case sofort ab und meldet `Step <N> (assert): <Grund>` (1-basiert). |

**Reihenfolge der Operationen:**

1. `arrange.inputs` wird einmal am Case-Start geschrieben (nicht zwischen Steps wiederholt).
2. Jeder Eintrag in `steps` läuft in Deklarationsreihenfolge.
3. Nach dem letzten Step läuft das **Top-Level**-`assertions[]` als Final-Gate. Per-Step-Asserts und Top-Level-Asserts sind unabhängig — beide müssen passen. Das Schema verlangt `minItems: 1` auf Top-Level-`assertions`, also mindestens eine triviale Top-Level-Assertion authoren auch wenn man primär per-Step-Asserts nutzt.
4. `watch[]` sampled durchgehend während jedem `wait`-Step (unter den oben genannten Bedingungen); das Time-Series-Chart annotiert Step-Grenzen.

**Caps (vom Runner erzwungen):**

| Limit | Wert |
|---|---|
| Steps pro Case | `1024` |
| Inputs pro `write`-Step | `256` |
| Assertions pro `assert`-Step | `256` |
| `wait.ms` | `0`..`3 600 000` (1 Stunde) |

**Visual-Editor:** Die Case-Detail-Ansicht zeigt einen **Steps (optional)**-Bereich mit **+ Write**, **+ Wait**, **+ Assert**-Buttons zum Anhängen, per-Step **↑ / ↓**-Buttons zum Umsortieren, und **−** zum Entfernen. Der Editor lässt `cycles` automatisch im serialisierten JSON weg, sobald der Steps-Bereich nicht leer ist (das Schema lehnt die `cycles + steps`-Kombination ab, der Editor produziert sie also nie).

**Backwards-Kompatibilität:** Ein Case ohne `steps` läuft den bestehenden Single-Phase-`cycles`-Pfad ohne Verhaltensänderung. Ältere Suites brauchen keine Migration.

##### Vollständiges Beispiel — getakteter Motor-Start

`StartCmd` wird nach einem 500 ms langen Reset-Fenster gesetzt, dann warten wir 2 s bis der FB `Run` erreicht, plus eine abschließende Speed-Prüfung.

```json
{
  "name": "MotorStart_ReachesRun",
  "description": "Reset, warten, Start, warten, Run prüfen.",
  "arrange": { "inputs": { "Enable": true } },
  "act": {
    "timeoutMs": 10000,
    "steps": [
      { "type": "write", "inputs": { "Reset": true } },
      { "type": "wait",  "ms": 500 },
      { "type": "write", "inputs": { "Reset": false, "StartCmd": true } },
      { "type": "wait",  "ms": 2000 },
      { "type": "assert", "assertions": [
          { "variable": "Run", "operator": "isTrue", "expected": true }
        ]
      }
    ]
  },
  "assertions": [
    { "variable": "Speed_Act", "operator": "greaterThan", "expected": 1000 }
  ],
  "watch": ["Run", "Speed_Act"]
}
```

Wenn der Per-Step-`assert` fehlschlägt (z.B. `Run` ist nicht innerhalb von 2 s true geworden), gibt der Runner `Step 5 (assert): variable Run is not true` aus und bricht den Case ab. Wenn die Per-Step-Asserts alle passen aber das Top-Level-`Speed_Act > 1000` fehlschlägt, scheitert der Case mit der Top-Level-Assertion-Message.

Im Zweifel: zuerst einen einfachen Arrange + `cycles ≥ N` + Assert-Case schreiben. Erst in eine `steps`-Sequenz konvertieren wenn die einfache Form das Timing nicht ausdrücken kann, von dem der Test wirklich abhängt.

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
- **S7 Nativ** — Nutzt den S7-Communication-Treiber über TCP/IP. Wählen Sie diese Option für Tests gegen echte Hardware (in Kombination mit dem Vorbereitungsmodus **Reale PLC**) oder gegen PLCSim über den virtuellen Ethernet-Adapter mit Benutzerauthentifizierung. Gleiche Bezeichnung wie im PLC-Online-Tab.

Beide Transports haben eine eigene Konfigurations-Sektion im selben Dialog, sodass jede Suite unabhängig konfiguriert werden kann. Bei S7 Nativ hat die Suite eigene IP, TCP-Port, Benutzername und Passwort — kein Cross-Tab-Lookup aus der PLC-Online-Ansicht. Rack und Slot sind nicht konfigurierbar: S7-1200/1500 verbinden sich über das S7CommPlus-Protokoll mit fixem Routing-Handshake, und TLS ist auf jeder Verbindung Pflicht — beides erledigt der Transport.

### Simulation-Arbeitsbereich

Innerhalb des SCL-Unit-Testing-Tabs schaltet ein **Simulation**-Sub-Mode-Umschalter oben zwischen der Test-Suites-Ansicht und einer dedizierten **Simulation**-Ansicht für die PLCSim-Advanced-Instanzverwaltung um. Die Simulation-Ansicht zeigt:

- API-Version, Online-Zugriffsmodus (PLCSim / TCP/IP einzeln / TCP/IP mehrfach), Strict-Motion-Timing-Toggle und Runtime-Manager-Port.
- Eine **Virtueller Adapter**-Zeile mit dauerhaftem Status des Siemens PLCSIM Virtual Ethernet Adapters (Bereit / APIPA / Deaktiviert / Nicht installiert / Keine IPv4), seiner IPv4-Adresse und einem Refresh-Button. Wenn der Adapter im 169.254.x.y-APIPA-Bereich hängt, werden Downloads unzuverlässig — weisen Sie ihm in den Windows-Netzwerkeinstellungen eine statische IPv4-Adresse zu.
- Jede registrierte PLCSim-Instanz mit Inline-Buttons: Einschalten, Run, Stop, Memory-Reset, Ausschalten, Einstellungen, Netzwerk, Löschen. Jede Zeile zeigt die konfigurierte IP-Adresse; hat die Instanz mehrere Schnittstellen mit einer IP, werden diese als `X1: 192.168.0.1, X2: 10.0.0.5` aufgelistet.
- Eine **TIA-PLC**-ComboBox pro Instanz-Card: Wählen Sie die TIA-Portal-PLC, die der Instanz zugrunde liegt. Nötig, sobald die PLCSim-Instanz mit einem Snapshot beladen wurde, der aus einer anderen TIA-PLC kompiliert wurde als unter der die Instanz registriert ist (Beispiel: eine Instanz mit Namen `PLC_2`, die aber das Programm aus `PLC_1` enthält). Ohne explizite Wahl gleicht die App per Name ab und greift auf die einzige PLC im Projekt zurück, wenn nur eine vorhanden ist — ausreichend für die meisten Setups, liefert aber einen leeren Tag-Baum, wenn die Namen nicht übereinstimmen. Die Auswahl wird pro Instanz gemerkt.
- Einen **Neue Instanz**-Button, der nach Name und CPU-Typ fragt.
- Ein **Tag-Browser**-Panel, das sich mit jeder Instanz verbinden und alle Tags des laufenden Programms anzeigen kann — filterbar nach Namensuche, Bereich (Eingang / Ausgang / Merker / Datenbaustein) und Datentyp. Auto-Refresh kann für Live-Wertebeobachtung aktiviert werden. Jeder schreibbare Tag hat einen **Bleistift-Button**, der einen typ-spezifischen Write-Dialog öffnet (Schalter für Bool, numerische Eingabe mit passendem Bereich für Ganzzahlen und Gleitkomma, Ein-Zeichen-Feld für Char/WChar). String-Tags sind read-only. Struct-Tags und Array-Tags werden mit ihren inneren Membern und Elementen als ausklappbare Zeilen aufgelistet, sodass einzelne Felder wie `OUT[5]` oder `DI10.Channel` direkt durchsucht, beobachtet und geschrieben werden können; die Toolbar-Buttons **Alle ausklappen** und **Alle einklappen** schalten den gesamten Baum auf einmal um. Strukturierte Eingangs-/Ausgangs-Tags, deren Layout aus einer Projekt-Typdefinition stammt (zum Beispiel ein `PNPN`-Block an `%I0.0`, deklariert als `Array[0..63] of Byte`), klappen in benannte Member-Zeilen auf, sobald die App mit dem TIA-Portal-Projekt verbunden ist, das sie definiert — sodass `IN.PNPN[12]` aus demselben Dialog beschrieben werden kann, der auch den Rest des Baums verarbeitet.
- Eine **Gespeicherte Instanzen**-Sektion am unteren Rand, die jede PLCSim-Advanced-Instanz auflistet, die auf der virtuellen SIMATIC Memory Card persistiert ist. Neben der Überschrift zeigt ein Zähler die Gesamtzahl gespeicherter Instanzen; die Liste zeigt maximal drei Zeilen gleichzeitig und scrollt bei mehr, damit der Simulationsbereich darüber sichtbar bleibt. Klicken Sie **Laden**, um eine solche Instanz erneut zu registrieren und fortzuführen — PLCSim übernimmt automatisch den gespeicherten CPU-Typ, das E/A-Abbild und das Programm. Klicken Sie **Löschen** (mit Bestätigung), um den persistierten Ordner zu entfernen.

Der Sub-Mode wird zwischen Sitzungen gemerkt, und der Wechsel behält alle geöffneten Suite-Dokumente.

### PLCSIM-Vorbereitungsmodus

Der **Verbindungseinstellungen**-Dialog hat eine Auswahl für den Vorbereitungsmodus, der steuert, wie der Runner das Projekt vor dem Testlauf bereitstellt:

- **Ich lade selbst (empfohlen)** — Der Runner erwartet, dass Sie die PLCSIM-Instanz bereits manuell via TIA Portal gestartet und das Projekt geladen haben. Compile und Download werden übersprungen, der Runner verbindet sich direkt und führt die Tests aus. Schnellste Option für wiederholte Läufe am selben Projekt.
- **Automatischer TCP-Download** — Der Runner kompiliert das Projekt, startet eine frische PLCSIM-Instanz und lädt es via TCP über den PLCSIM Virtual Adapter. Keine manuelle TIA-Portal-Interaktion nötig — einfach Run klicken.
- **Reale PLC (kein PLCSim)** — Überspringt den PLCSim-Lebenszyklus komplett. Der Runner verbindet sich via S7 Nativ direkt mit der echten S7-Hardware unter der konfigurierten IP und dem TCP-Port und führt die Tests dort aus. **Nur verwenden, wenn die Anlage in einem sicheren Testzustand ist.** Die Auswahl dieses Modus blendet die PLCSim-Sektion aus und erzwingt den Transport S7 Nativ; PLCSim API ist inkompatibel.

**Vor der Verwendung von Automatischem TCP-Download:** Vier Voraussetzungen müssen erfüllt sein, sonst schlägt der Run mit einem generischen Transport-Fehler fehl: (1) der **PLCSIM Virtual Adapter** muss installiert sein und eine statische IPv4-Adresse haben, die zur `plcSimIp` der Suite passt (der Simulation-Tab zeigt den aktuellen Adapter-Status); (2) das TIA-Portal-**Projekt muss in TIA Portal geöffnet** sein — der Runner stösst vor dem Download eine Compile-Aktion gegen das offene Projekt an; (3) bei aktiviertem **Vertraulichen Konfig-Schutz** muss das Master-Secret-Passwort in den Verbindungseinstellungen eingetragen sein (liegt im Vault); (4) eine bestehende PLCSIM-Instanz mit demselben Namen wird bei jedem Run **zerstört und neu angelegt**, sodass andere Anwendungen, die mit dieser Instanz verbunden sind, ihre Session verlieren.

### Tests gegen reale PLC ausführen

Mit der Auswahl **Reale PLC** im Vorbereitungsmodus laufen Tests direkt gegen echte S7-1200/S7-1500-Hardware ohne PLCSim:

1. Stellen Sie sicher, dass die Anlage **im sicheren Testzustand** ist — Aktoren freigeschaltet oder verriegelt, keine Produktionslast auf der PLC, Bediener informiert.
2. Öffnen Sie **Verbindungseinstellungen…**, wählen Sie **S7 Nativ** als Transport, geben Sie die echte IP-Adresse und (falls die SPS auf einen abweichenden TCP-Port konfiguriert wurde) den Port ein; Benutzer/Passwort nur falls die SPS Authentifizierung erzwingt.
3. Stellen Sie den Vorbereitungsmodus auf **Reale PLC (kein PLCSim)**. Die PLCSim-Sektion verschwindet.
4. **OK** klicken, dann **▶ Run**.
5. Bevor der Runner die PLC kontaktiert, erscheint ein Bestätigungsdialog: *„Tests gegen reale PLC ausführen?"* Lesen Sie die Warnung, setzen Sie den Haken bei **„Verstanden — die Anlage ist im sicheren Testzustand."**, dann klicken Sie **Tests starten**. Der Button bleibt deaktiviert, bis die Checkbox gesetzt ist. Mit **Abbrechen** wird der Lauf ohne Netzwerk-Verkehr verworfen.

F-Bausteine (mit Safety-Attribut markiert) bleiben in diesem Modus weiterhin hart geblockt — der Runner verweigert den Start jedes Tests gegen einen Safety-Block, unabhängig vom Vorbereitungsmodus.

Bricht der Lauf sofort mit **„S7 connection succeeded but access denied — verify username/password"** ab, hat die PLC den TLS-Handshake akzeptiert, aber die Credentials abgelehnt. Prüfen Sie Benutzer/Passwort im Verbindungseinstellungen-Dialog und den passenden Eintrag unter **Vault → S7-Passwort**. Der Runner meldet das jetzt direkt beim Connect statt den Test später mit irreführendem „tag not found" scheitern zu lassen.

**Batch-Läufe und Reale-PLC-Suiten:** Wenn Sie **Alle ausführen** klicken oder anders einen Batch-Lauf starten, der eine oder mehrere Suiten im Modus **Reale PLC** enthält, werden diese Suiten übersprungen (der Pro-Suite-Bestätigungsdialog kann nicht aus einem Batch heraus angezeigt werden). Der Test-Explorer zeigt einen schliessbaren Banner, der die übersprungenen Suiten namentlich aufführt; öffnen Sie jede betroffene Suite und klicken Sie einzeln auf **Run**, um den Bestätigungsdialog zu durchlaufen. Übersprungene Suiten zählen nicht mehr als Fehler in der Batch-Zusammenfassung.

**CPU-Betriebszustands-Gate:** Reale-PLC-Läufe lesen direkt nach Connect den Betriebszustand der CPU. Ist die CPU in **Stop**, **StartUp**, **Hold**, **Defect** oder einem anderen Nicht-RUN-Zustand, bricht der Runner sofort mit `Cannot run tests against real PLC: CPU is in <STATE>, not Run. Switch the CPU to Run before retrying.` ab. Damit schreibt der Runner nicht in den DB-Speicher, solange das Anwenderprogramm nicht läuft — sonst würde jeder Test residuale Daten zurücklesen und irreführende PASS/FAIL-Ergebnisse liefern. Schalten Sie die CPU auf RUN (TIA Portal Online & Diagnose, oder den Betriebsart-Wahlschalter an der CPU) und klicken Sie erneut auf Run.

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
- Der **Verbindungseinstellungen…**-Button in der Toolbar erlaubt die Konfiguration von Transport, PLCSim-Instanz (aus der Simulation-Registry wählbar oder frei eingebbar), IP-Adresse, Zyklus-Wartezeit, S7-Comm+-Ziel (IP, TCP-Port, Benutzer, Passwort) und Auto-Connect für die aktive Suite. Setzen Sie den Haken bei *Als Default speichern*, damit neu erstellte PLCSim-Suites dieselben Werte übernehmen. Der Dialog hat einen **Verwalten…**-Button in der PLCSim-Sektion, der ohne Verlust der aktuellen Eingaben in den Simulation-Sub-Mode springt, um Instanzen anzulegen oder anzupassen.
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

Library-Master-Copy- und Typversions-Operationen sind für KI-Assistenten nur über die oben beschriebenen Kontextmenü-Aktionen im Projektbaum verfügbar. Aktuell existieren keine dedizierten `library_*` MCP-Tools — KI-Clients können Bibliotheksinhalte über die Standard-Projekt-Resource (`tia://project`) lesen, aber keine Bibliothekselemente per MCP erstellen, instanziieren, umbenennen, löschen, exportieren oder aufräumen.

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
Speichert geänderte PROFINET-Namen, IP-Adressen und Karten-E/A-Startadressen zurück ins TIA Portal Projekt.

Wenn beim Schließen des Managers oder beim Trennen von TIA Portal noch ungespeicherte Hardware-Änderungen vorhanden sind, fragt der Manager nach: speichern, verwerfen oder abbrechen.

### Karten-Bereich

Bei Auswahl einer Station in der Geräteliste werden deren Karten in einem zweiten Raster darunter geladen. Jede Zeile zeigt eine Karte mit Steckplatz, Name, Bestellnummer sowie den Eingangs- und Ausgangs-Adressbereichen als **Start / Ende / Länge** in Bytes — in denselben Byte-Einheiten wie die TIA Portal Geräteansicht, sodass eine in TIA Portal als `I 160...223` angezeigte Karte hier mit Eingang Start `160`, Eingang Ende `223`, Eingang Länge `64` erscheint. Editierbar sind nur die Spalten „Eingang Start" und „Ausgang Start"; Ende und Länge sind schreibgeschützt und aktualisieren sich automatisch mit dem Start-Wert. Änderungen werden zusammen mit den Stations-Änderungen verfolgt — „Save Changes" schreibt beide in einem Vorgang zurück nach TIA Portal, „Discard" verwirft beide. „Refresh" lädt sowohl die Stationsliste als auch den Karten-Bereich neu, damit Änderungen, die woanders in TIA Portal gemacht wurden, in beiden Ansichten erscheinen.

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

## 11a. Hardware-Simulation

Der Tab Hardware-Simulation schreibt simulierte Tag-Werte in eine laufende PLCSim-Advanced-Instanz, sodass SPS-Logik gegen wechselnde Eingangswerte getestet werden kann — ohne physische Hardware. Verfügbar in Trial- und Enterprise-Abonnements; in Basic- und Professional-Abonnements zeigt der Tab ein "Lizenz erforderlich"-Overlay.

### Öffnen

Den Tab Hardware-Simulation öffnen Sie über die Activity-Bar links. Der Workspace enthält oben eine Symbolleiste sowie vier andockbare Panels: Geräte-Panel, Override-Liste, Linker-Regeln und Funktions-Editor.

### Mit PLCSim Advanced verbinden

1. Wählen Sie in der Symbolleiste eine PLCSim-Advanced-Instanz aus dem **Instance**-Dropdown.
2. (Optional) Wählen Sie die zugehörige TIA-Portal-PLC im **TIA-PLC**-Dropdown, damit Topologie-Namen sauber aufgelöst werden.
3. Klicken Sie **Connect**. Der Status-Text zeigt das hergestellte Transport-Protokoll.
4. Klicken Sie **Reload topology**, um das Geräte-Panel mit Hardware-Modulen und Tag-Baum aus TIA Portal zu füllen.

### Engine und Tick-Intervall

Die Simulations-Engine führt alle konfigurierten Funktionen in einem periodischen Tick aus. Mit dem **Tick**-Slider in der Symbolleiste stellen Sie ein Intervall zwischen 10 ms und 1000 ms ein. Die Start-, Pause- und Stop-Buttons steuern die Engine; der aktuelle Zustand erscheint im Status-Text.

### Sim-Funktionen (Funktions-Editor)

Rechtsklick im Funktions-Editor-Tab fügt eine neue Funktion hinzu; Doppelklick auf eine Zeile bearbeitet sie. Jede Funktion schreibt auf einen Tag und ist einer der folgenden Typen:

- **Constant** — Schreibt jeden Tick einen festen Wert.
- **Ramp** — Linearer Verlauf zwischen zwei Werten über eine konfigurierbare Dauer.
- **Sine** — Sinuswelle mit Amplitude, Offset, Frequenz und Phase.
- **Square** — Rechteckwelle mit High-Level, Low-Level und Frequenz.
- **Triangle** — Dreieckwelle mit Amplitude, Offset und Frequenz.
- **Random** — Zufallswert in einem [min, max]-Bereich pro Tick.

Jeder Funktionstyp wird in der Dropdown-Liste mit einem Wellenform-Symbol dargestellt, sodass die Form auf einen Blick erkennbar ist. Der Dialog füllt den Datentyp aus dem gewählten Tag automatisch aus. Über den Tag-Picker auf der rechten Seite durchsuchen Sie die Topologie und wählen einen Tag aus; der Picker umfasst Hardware-Kanal-Tags, Merker-Tags, System-Tags und Datenbaustein-Variablen.

### Force-Overrides (Override-Liste)

Mit einem Force-Override schreiben Sie einen festen Wert auf einen Tag, unabhängig von den Engine-Funktionen. Rechtsklick im Override-Liste-Tab fügt einen neuen Override hinzu. Ein Override hat Vorrang vor jeder Engine-Funktion, die denselben Tag schreibt; Sie können ihn aktivieren oder deaktivieren, ohne ihn zu entfernen.

### Watch-Liste

Der Watch-List-Tab zeigt die Live-Werte ausgewählter Tags. Über das Augen-Icon im Tag-Baum des Geräte-Panels fügen Sie Tags zur Watch-Liste hinzu. Werte aktualisieren sich bei jedem Engine-Tick, solange die Engine läuft; auch Tag-Tabellen-Tags erhalten Live-Updates auf dieselbe Weise wie Hardware-Kanal-Tags.

### Linker-Regeln

Eine Linker-Regel schreibt den Wert eines Tags auf einen anderen Tag, sobald ein boolescher Ausdruck wahr ist. Öffnen Sie den Linker-Regeln-Tab, um Regeln hinzuzufügen oder zu bearbeiten. Der Tag-Picker umfasst IO-Bereich-, Merker-, System- und Datenbaustein-Variablen. Der Regel-Editor bietet zwei Tabs:

- **Guided builder** — Bis zu acht Bedingungen mit Operator, Wert und AND/OR-Verknüpfungen. Wählen Sie Quell-Tag, Ziel-Tag und Zuweisungswert.
- **Expression text** — Freie Ausdrucks-Syntax `WHEN <Bedingungen> THEN <Ziel> := <Wert>` mit IEC-Operatoren (`=`, `<>`, `<`, `>`, `<=`, `>=`).

Beide Tabs bleiben synchron — Edits in einem aktualisieren den anderen, sobald der Ausdruck sauber parst.

### F-Safety-Auto-Acknowledge

PLCSim Advanced verlangt nach jedem PLC-Neustart ein manuelles Acknowledge für geforcte F-Kanäle. Mit geladener Hardware-Topologie klicken Sie **Acknowledge F-tags** in der Geräte-Panel-Symbolleiste, um alle F-Kanäle in einem Klick zu acknowledgen; **Revoke** macht das rückgängig. Der Acknowledge-Zustand wird pro PLC gespeichert.

### Verbindung trennen

Klicken Sie **Disconnect** in der Symbolleiste, um die PLCSim-Advanced-Session freizugeben und die Engine zu stoppen. Watch-Liste, Override-Liste, Linker-Regeln und Funktions-Editor-Inhalte bleiben über Reconnects erhalten.

---

## 11b. Im Projekt suchen (Cross-Reference-Suche)

### Was sie tut

Der Tab "Im Projekt suchen" ist eine projekt-weite Referenzsuche. Geben Sie einen Baustein-, Tag- oder UDT-Namen ein und die Anwendung listet jede Cross-Reference auf, die Siemens TIA Portal dazu im offenen Projekt kennt. Die Ergebnisse sind nach Quell-PLC und Quell-Baustein gruppiert, dann nach Zugriffskategorie (Aufrufe / Lesezugriffe / Schreibzugriffe / Sonstige), mit der genauen Referenzposition und Zeilennummer pro Treffer.

Damit beantworten Sie Fragen wie:

- "Wo wird `FB_Motor` aufgerufen?"
- "Welche Bausteine lesen oder schreiben das Tag `xStartBtn`?"
- "Welche Bausteine nutzen den UDT `typ_Recipe`?"

### Tab öffnen

| Trigger | Aktion |
|---------|--------|
| Rechte Tabs | Klick auf **Im Projekt suchen** im TIA Manager-Arbeitsbereich |
| Tastenkürzel | `Strg+Umschalt+F` von überall — der Arbeitsbereich wechselt automatisch und das Suchfeld erhält den Fokus |
| Project Tree | Rechtsklick auf einen Baustein-Knoten und **Referenzen suchen** wählen; der Tab öffnet sich mit dem Bausteinnamen vorbefüllt |

### Suchen

1. Namen (oder Namensteil) ins Suchfeld tippen. Die Suche startet nach 250 ms Pause, damit nicht jede Taste einen vollen Scan triggert.
2. (Optional) **Scope** wählen: Alle, Bausteine, Tags oder UDTs. Default ist Alle.
3. (Optional) **PLC** auswählen, um in Multi-PLC-Projekten auf eine einzelne PLC zu beschränken.
4. Fortschrittsbalken zeigt, wie viele Kandidaten gescannt wurden.
5. Doppelklick auf eine Trefferzeile öffnet den Quell-Baustein im SCL-Editor und springt zur Quellzeile, oder Rechtsklick auf die Zeile für **Im Editor öffnen** und **Referenzpfad kopieren**.

Die Suche ist groß-/klein- und diakritika-unabhängig: `förder` findet `Förder_DB`, `muller` findet `Müller_FB`, und `GROSSE` findet `Größe_Tag`.

Wenn der Suchbegriff selbst einem Baustein-, Tag- oder UDT-Namen entspricht, erscheint dieses Objekt als eigene **Definitionen**-Gruppe oben im Ergebnis-Baum. Doppelklick auf die Definition-Zeile (oder Rechtsklick-Menü) öffnet den Baustein direkt.

### Banner und Grenzen

| Banner | Bedeutung |
|--------|-----------|
| Ergebnis bei 2000 Treffern abgeschnitten | Die Suche hat mehr Treffer als das Cap gefunden. Suche eingrenzen durch mehr Zeichen oder schmaleren Scope/PLC. |
| Suche fehlgeschlagen: \<Grund\> | Bridge oder TIA Portal hat einen Fehler gemeldet (Projekt mid-Scan geschlossen, COM disposed, V15–V17 ohne `CrossReferenceService`). |
| Keine Treffer | Suche fertig, nichts gefunden. |

### Performance und Cache

- Identische Suchen innerhalb von 30 Sekunden werden aus einem In-Memory-Cache bedient — gleiche Eingabe = sofortiges Ergebnis ohne Bridge-Roundtrip.
- Cache wird automatisch invalidiert beim Projekt-Wechsel, beim Schließen eines Projekts oder beim Trennen der TIA-Portal-Verbindung.
- Suchen laufen im Bridge-Prozess, nicht auf dem UI-Thread; Sie können während eines langen Scans weitertippen oder navigieren.

### Voraussetzungen

Der Cross-Reference-Service ist nur ab TIA Portal V18 stabil. Auf V15–V17 erscheint "Find-References requires TIA Portal V18 or later" im Fehler-Footer.

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

Ein einziges Einstellungs-Fenster ersetzt die bisherigen separaten Dialoge für Anwendungs-Einstellungen, Import/Export, Git-Preferences und AI Chat. Das Fenster hat oben eine Suchleiste, links eine Kategorien-Baumstruktur und rechts die zugehörigen Einstellungen.

### Öffnen

- Menüleiste: **View → Settings** (oder `Strg+,`).
- AI-Chat-Eingabeleiste: Zahnrad-Symbol → öffnet das Fenster direkt auf der AI-Chat-Sektion.
- Import/Export-Tab: Zahnrad-Symbol → öffnet auf der Import/Export-Sektion.
- Git-Repository-Panel: Einstellungs-Zahnrad → öffnet auf der Git-Sektion.

Änderungen werden automatisch gespeichert — kein Save- oder Cancel-Button. Ein farbiger Akzent-Balken am linken Rand einer Sektion zeigt an, dass darin etwas vom Wert abweicht, der beim Öffnen des Fensters geladen wurde.

### Kategorien

| Kategorie | Was darin liegt |
|-----------|-----------------|
| General | UI-Sprache, Theme (Dark-, Light- oder Midnight-Modus + Akzentfarbe), Auf-Updates-prüfen beim Start. Midnight ist eine echte Schwarz-Variante, optimiert für OLED-Displays. |
| Files & Folders | Log-Verzeichnis, Working-Folder für Import/Export, Ordnernamen-Anpassung, "Create Source folder"-Schalter. |
| Import/Export | Import-Optionen (Strukturänderungen ignorieren, fehlende Referenzen ignorieren, fault-tolerant), Export-Optionen pro Typ (DBs / UDTs / Tags / Technologieobjekte / HMI), zusätzlicher S7-DCL-Export (V20+), Fingerprint-Cache, Version-Control-Normalisierung. |
| Git | Datumsformat, Default-Klon-Verzeichnis, History-Limits, Erscheinungsbild (Fonts), Git User/Email/CRLF/Fetch, GPG-Signierung, Shell- und externe Diff/Merge-Integration, KI-Commit-Message-Prompt. |
| AI Chat | Agents, Chat-Tools, Approvals, Instructions, Templates, Providers, MCP-Servers, Memory, Geplante Aufgaben, Dictation, Workspace, Storage. |
| Compare | Diff-Editor- und Minimap-Farben, Deckkraft und Minimap-Breite. |
| Editor | C#-Sprachfunktionen (standardmässig aus — mitgelieferter Sprachserver, Neustart erforderlich). |
| Logging | Debug-Logging-Schalter. |

### Ordnernamen-Anpassung (unter Files & Folders → Ordnernamen)

| TIA-Portal-Name | Standard-Export-Name | Konfigurierbar |
|-----------------|----------------------|----------------|
| (Gerät) | Source | ✓ |
| Programmbausteine | Blocks | ✓ |
| PLC-Datentypen | Datatypes | ✓ |
| PLC-Variablen | Tags | ✓ |
| Technologieobjekte | Technology Objects | ✓ |
| Software Units | Software Units | ✓ |

Die "Create Source folder"-Checkbox steuert, ob Exporte einen Source-Wrapper enthalten:

| Einstellung | Export-Pfad |
|-------------|-------------|
| ✓ Aktiviert | `WorkingDir/Source/PLC_1/Blocks/...` |
| ☐ Deaktiviert | `WorkingDir/PLC_1/Blocks/...` |

Diese Einstellung beeinflusst auch die Projekt-Baumstruktur und die Import-Pfaderkennung.

### File Explorer — Watcher-Excludes (unter Files & Folders → File Explorer)

Der File-Explorer-Baum überspringt beim Einlesen des geöffneten Working-Folders alle Ordner, die auf die **Watcher-Excludes**-Liste passen. Vorgaben: `.git`, `.vs`, `.idea`, `bin`, `obj`, `node_modules`, `.claude`, `.worktrees`.

Die Liste lässt sich bearbeiten, um:

- **Zusätzliche Ordner auszublenden** — pro Zeile ein Ordnername (z. B. `dist`, `coverage`, `.next`).
- **File-Watcher-Last zu reduzieren** — grosse Build-Output-Ordner (`bin/obj`) können den Betriebssystem-Watcher-Puffer überfüllen; werden sie ausgeschlossen, entfällt unnötige Scan-Arbeit bei jedem Build.
- **Die Standardliste wiederherzustellen** — Textfeld leeren; beim nächsten Refresh greifen wieder die Vorgaben.

Änderungen werden wirksam, sobald der Working-Folder neu geöffnet oder aktualisiert wird.

### Editor — Rechtsklick-Kontextmenü

Ein Rechtsklick innerhalb eines Editor-Tabs öffnet ein Menü mit fünf Gruppen. Einträge, die an der aktuellen Cursor-Position oder Auswahl nicht anwendbar sind, werden ausgeblendet — die Menü-Länge folgt also den verfügbaren Aktionen:

- **KI-Unterstützung** — *Inline-Chat öffnen* (Strg+I), *Markdown-Vorschau*, *Datei zu Chat hinzufügen*, *Erklären* (auswahlabhängig), *Überprüfen* (auswahlabhängig).
- **Bearbeiten** — *Alle Vorkommen ändern* (Strg+F2, benennt nach einer kurzen Eingabe jedes Vorkommen des Bezeichners am Cursor im aktuellen Dokument um), *Symbol umbenennen* (F2, sprachserver-basierte Umbenennung, die das Symbol über Dateien hinweg im Workspace verfolgt; erscheint nur, wenn der aktive Server die Fähigkeit anbietet), *Dokument formatieren* (Shift+Alt+F) und *Auswahl formatieren* (Strg+K Strg+F). Wenn ein Sprachserver mit Formatierungs-Unterstützung gebunden ist (z. B. C# über den mitgelieferten Server), nutzt der Editor dessen Formatter; SCL fällt auf den eingebauten Formatter zurück. *Auswahl formatieren* erscheint nur, wenn der aktive Server Bereichs-Formatierung anbietet und der Editor eine Auswahl hat.
- **Navigation** — *Gehe zu Definition* (F12) und *Verweise suchen* (LSP-basiert; beide erscheinen, sobald der Sprachserver der geöffneten Datei die Fähigkeit meldet).
- **Git** — *Dateiverlauf anzeigen* (Alt+H) wechselt die Activity-Bar zu Version Control, öffnet das Repository-Tab der Datei und listet jeden Revision-Eintrag, der die Datei berührt hat. Dateien ausserhalb eines Git-Repositorys zeigen stattdessen einen kurzen Status-Hinweis.
- **Zwischenablage** — *Ausschneiden* (Strg+X), *Kopieren* (Strg+C), *Einfügen* (Strg+V), *Alles auswählen* (Strg+A).

Tastatur-Shortcuts funktionieren weiterhin auch ohne Menü-Öffnung — die Einträge machen die gleichen Aktionen nur sichtbarer.

### Editor — C#-Sprachfunktionen

Unter **Einstellungen → Editor** aktiviert der Schalter **C#-Sprachfunktionen aktivieren** einen mitgelieferten Sprachserver für `.cs`-Dateien, die im File Explorer geöffnet werden. Mit eingeschaltetem Schalter:

- Werden Compiler-Fehler und Warnungen direkt während des Tippens mit Wellenlinien unterstrichen.
- Erscheint jede Diagnose über alle offenen `.cs`-Dateien hinweg im neuen Tab **Probleme** am unteren Rand des Arbeitsbereichs (neben Log Output, Terminal, Git Output). Ein Klick auf eine Zeile springt an die Stelle im Editor.
- Zeigt eine Banner-Zeile über der Problems-Liste den Status des Sprachservers (startet, bereit, startet neu, deaktiviert).
- Öffnet beim Verweilen mit der Maus über einem Symbol einen Tooltip mit Typ, Signatur und XML-Kommentaren.
- Springt mit **F12** oder **Strg+Klick** zur Definition eines Symbols; bei mehreren Treffern erscheint eine kleine Auswahl.
- Listet jede Aufruf-Stelle eines Symbols auf, wenn du das Symbol rechtsklickst und **Verweise suchen** wählst. Die Treffer erscheinen im neuen Tab **References** am unteren Rand des Arbeitsbereichs (Datei, Zeile, Vorschau). Ein Klick auf eine Zeile springt an die Stelle. Der Menü-Eintrag ist ausgeblendet, solange keine Sprachsitzung für die aktuelle Datei verhandelt wurde.
- Blendet beim Tippen von `(` oder `,` innerhalb eines Aufrufs ein kleines Popup mit der Methoden-Signatur ein, in dem der aktive Parameter hervorgehoben ist. **Escape**, ein Klick ausserhalb oder ein Caret-Move aus dem Aufruf schliesst es.
- Bietet während des Tippens eine Vervollständigungsliste mit Member- und Symbol-Vorschlägen. Die Liste öffnet sich ab dem zweiten Zeichen, sortiert nach Relevanz und dedupliziert nach Name. Pfeiltasten navigieren, **Eingabe** oder **Tab** fügt den hervorgehobenen Eintrag ein. SCL, AWL und andere Siemens-Baustein-Formate behalten ihre bestehende Schlüsselwort- und Wortvervollständigung; nur `.cs`-Dateien nutzen die Vorschläge des Sprachservers.
- Bietet Quick-Fixes für Diagnosen unter dem Caret an. Eine kleine Glühbirne erscheint im Editor-Rand auf der Caret-Zeile, sobald Fixes oder Refaktorierungen verfügbar sind; ein Klick auf die Glühbirne oder **Strg+.** öffnet das Aktionsmenü. Die ausgewählte Aktion wird als einzelner rückgängig-machbarer Edit angewendet, das Ergebnis erscheint in der Statuszeile (Anwenden… → Aktion angewendet / Keine Quick-Fixes verfügbar / Aktion konnte nicht angewendet werden / Details konnten nicht geladen werden).
- Benennt ein Symbol und alle Verweise darauf über den Workspace hinweg per Sprachserver um. Cursor auf den Bezeichner setzen und **F2** drücken (oder Rechtsklick → **Symbol umbenennen**); im Inline-Overlay den neuen Namen tippen und mit **Eingabe** anwenden oder mit **Escape** abbrechen. Die Statuszeile meldet Umbenennen… → Umbenannt / Dokument hat sich während des Umbenennens geändert / Ungültiger Bezeichner / Umbenennen fehlgeschlagen. Wird das Dokument während des laufenden Vorgangs geändert, wird die Änderung verworfen und der Editor behält seinen Zustand.
- Formatiert das gesamte Dokument (**Shift+Alt+F**) oder die aktuelle Auswahl (**Strg+K Strg+F**) über den Sprachserver. Die Statuszeile meldet Formatiere… → Formatiert / Dokument ist bereits formatiert / Formatieren fehlgeschlagen / Dokument hat sich während der Formatierung geändert. Wenn kein Sprachserver gebunden ist oder dieser keine Formatierung anbietet, behält SCL seinen eingebauten Formatter und andere Sprachen zeigen einen kurzen Status-Hinweis.
- Öffnet decompilierte Metadaten als schreibgeschütztes Tab, wenn **F12** auf ein Symbol einer externen Bibliothek oder einer generierten Quelle landet. Die Statuszeile meldet Externe Quelle wird geladen… → ein neuer Tab öffnet sich mit dem synthetisierten Quellcode (BCL-Typen, NuGet-Assemblies, Source-Generator-Output). Der Puffer kann nicht bearbeitet werden; **F12** im Puffer löst weitere Symbole transitiv auf. URI-Schemata, die der Sprachserver nicht unterstützt, zeigen weiterhin einen kurzen Hinweis.
- Aktualisiert die Probleme-Liste auf Knopfdruck: eine kleine Aktualisieren-Schaltfläche in der Toolbar der Probleme-Anzeige holt die Diagnosen für jede offene `.cs`-Datei in einer Runde neu. Der Sprachserver fordert die Aktualisierung zudem automatisch an, wenn sich Pakete, Analyzer oder Projektstand ändern, sodass die Probleme-Liste ohne Eingreifen aktuell bleibt.

Der Schalter ist **standardmässig deaktiviert**, weil der Sprachserver beim Indexieren grosser Lösungen zwischen 1 GB und 10 GB Arbeitsspeicher belegen kann. Aktiviere ihn, wenn du regelmässig C#-Dateien im Manager bearbeitest.

**Neustart erforderlich.** Die Sprachserver-Registrierung wird beim Programmstart entschieden, die Änderung greift also erst beim nächsten Start der Anwendung.

#### Eine .NET-Solution für volle IntelliSense laden

Nur den Schalter zu aktivieren weckt den Sprachserver für Einzeldatei-Funktionen — du bekommst Inline-IDE-Hinweise (z.B. *Using-Direktive ist unnötig*), Syntax-Hervorhebung und Vervollständigung, aber dateiübergreifende Funktionen bleiben aus: keine `CS0246` / `CS0103`-Compiler-Fehler, kein F12 über Dateien hinweg, keine Method-vs-Variable-Unterscheidung in der Färbung. Um diese zu aktivieren, muss der Sprachserver eine `.sln` (oder `.csproj`) laden, damit er einen Projektgraph bauen kann.

Unter **Einstellungen → Editor → C#-Sprachfunktionen** steuern zwei zusätzliche Bedienelemente das Laden der Solution:

- **Solution automatisch laden** — wenn aktiv, sucht der Sprachserver ausgehend von der geöffneten `.cs`-Datei aufwärts nach der nächsten `.sln`/`.slnx` (mit Fallback auf `.csproj`) und lädt diese. **Standardmässig deaktiviert**, weil der Sprachserver beim Laden einer Solution Analyzer-Code aus dem Projekt ausführen kann; nur für vertrauenswürdige Solutions aktivieren. Nach dem Umschalten muss die Anwendung neu gestartet werden.
- **Expliziter Solution-Pfad** — optionaler absoluter Pfad zu einer `.sln`-, `.slnx`- oder `.csproj`-Datei. Wenn gesetzt, wird diese Datei unabhängig vom Auto-Load-Schalter geladen, sodass du eine einzelne vertrauenswürdige Solution gezielt freigeben kannst, ohne die Aufwärtssuche generell zu erlauben. Per **Durchsuchen…**-Schaltfläche eine Datei auswählen oder leer lassen, um auf die Aufwärtssuche zurückzufallen.

Sobald ein Pfad aktiv ist und ein Projekt geladen wird, zeigt der Editor kurz den Status *Projektinitialisierung läuft…* in der Probleme-Anzeige, bis die Design-Time-Builds abgeschlossen sind, danach wechselt er auf *Bereit*. Dateiübergreifende Diagnosen, Verweise suchen und Metadata-as-Source funktionieren dann wie oben beschrieben.

C#-Dateien behalten ihre Syntax-Hervorhebung, Vervollständigung und übliche Editor-Funktionalität unabhängig von diesen Einstellungen — nur die Live-Diagnose und die Problems-Anzeige hängen am Schalter. SCL-, AWL-, UDT- und andere Siemens-Baustein-Formate sind nicht betroffen; sie nutzen den eigenen Editor-Stack des Managers.

### Suche

In das Suchfeld eintippen, um den Kategorien-Baum nach Sektion-Namen oder einem Stichwort aus den Such-Tags einer Sektion zu filtern. Übergeordnete Kategorien bleiben sichtbar, solange mindestens eine ihrer Unter-Kategorien matched.

<!-- feature:eplan start -->
### Lizenz

Lizenz-Aktivierung, Trial-Status, Hardware-ID und das EPLAN-Add-on werden weiterhin in einem eigenen, fokussierten Fenster verwaltet — erreichbar über die Startup-Abfrage, das Trial-Banner oder den **Manage License**-Einstieg.

<!-- feature:eplan end -->
### Log-Dateien

Bei aktiviertem Debug-Logging werden detaillierte Logs erstellt:
- Speicherort: konfigurierbar unter Files & Folders → Log Directory.
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
| KI-Chat | Nein | Ja | Ja |
| Projektbibliothek | Nein | Ja | Ja |
| Passwort-Tresor | Nein | Nein | Ja |
| Unit Testing | Nein | Nein | Ja |

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

**Wichtig:** Die Software erfordert **mindestens alle 14 Tage** eine Online-Validierung der Lizenz. Bei fehlender Internetverbindung kann die Software **bis zu 14 Tage offline** genutzt werden. Nach 14 Tagen ist eine erneute Online-Validierung erforderlich.

### Hardware-Bindung

Jede Lizenz ist an eine eindeutige Hardware-ID gebunden, die generiert wird aus:
- CPU-ID (Prozessor-Seriennummer)
- Mainboard-Seriennummer
- Primäre MAC-Adresse

### Maschinen-Wechsel-Limit

Die Lizenz hängt am **Konto**, nicht an einer einzelnen Maschine — Sie können sie ohne Support-Kontakt zwischen Rechnern umziehen. Die Anwendung erzwingt ein gleitendes Limit von **bis zu 3 verschiedenen Maschinen pro 30-Tage-Fenster**: jede Anmeldung auf einer bisher unbekannten Hardware-ID zählt als ein Wechsel. Die vierte unterschiedliche Maschine im gleichen 30-Tage-Fenster wird bei der Anmeldung abgelehnt. Das Fenster gleitet — Wechsel, die älter als 30 Tage sind, zählen nicht mehr. Bei der Anmeldung auf einer neuen Maschine wird die Bindung der vorherigen automatisch freigegeben.

Die aktuelle Nutzung ist im Lizenz-Fenster sichtbar (siehe unten). Bei 3/3 erscheint ein Banner im Fenster mit Hinweis, wann der nächste Slot wieder frei wird.

### Lizenz-Fenster

Öffnen über **View → Einstellungen → Lizenz verwalten** (oder über den Lizenz-Eintrag in der Hauptsymbolleiste). Das Lizenz-Fenster vereint zwei Bereiche an einer Stelle:

- **Konto & Lizenz** (oben, sichtbar wenn angemeldet) — die gleichen Zeilen, die zuvor in einem separaten Einstellungs-Tab lebten. Aktive Subskription prüfen und sich von dieser Maschine abmelden.
- **Pläne & Aktivierung** (unten, immer sichtbar) — die bestehende Hardware-ID-Anzeige, das Aktivierungscode-Feld, die Monats-/Jahres-Preiskarten und der Aktiv-Tarif-Indikator.

| Zeile | Bedeutung |
|-------|-----------|
| **Angemeldet als** | Die zur Anmeldung verwendete E-Mail-Adresse. |
| **Tier** | Aktive Stufe — Basic / Trial / Professional / Enterprise. |
| **Status** | Aktiv, Abgelaufen oder Validierung ausstehend. |
| **Läuft ab am** | Ende der aktuellen Abrechnungsperiode (Trial: Ende des 30-Tage-Fensters). |
| **Hardware-ID** | Die aus dieser Maschine abgeleitete 16-stellige ID. |
| **Gebunden seit** | Wann diese Maschine die Lizenz erstmals aktiviert hat. |
| **Ausstellungs-Datum** | Wann die Lizenz ursprünglich ausgestellt wurde. |
| **Maschinen-Wechsel** | Wechsel im letzten 30-Tage-Fenster, z. B. *2 von 3 Maschinen in 30 Tagen genutzt*. |
| **Sign out** | Gibt die Bindung dieser Maschine frei. Ein Bestätigungsdialog ("Abmelden und diese Maschine freigeben?") erscheint zuerst — **Sign out** bestätigt, **Cancel** bricht ab. Nach dem Abmelden öffnet sich der Sign-In-Dialog erneut; ein Schliessen dieses Dialogs beendet die Anwendung. |
| **Auf Webseite verwalten** | Öffnet die Konto-Seite im Browser für Subscription-Änderungen, Rechnungen und Lizenz-Transfer. |
| **Manuell migrieren** | Erscheint nur, wenn eine lokale Trial-Signatur ohne gebundenes Konto existiert oder eine automatische Migration einen Fehler gemeldet hat. Öffnet einen Dialog für die Eingabe der ursprünglichen 16-Zeichen-Hardware-ID, unter der die Testversion registriert wurde. Recovery für DPAPI-Korruption oder Hardware-Wechsel, bei denen die Legacy-Hardware-ID nicht mehr automatisch erkannt werden kann. |

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

### Trial-Migrations-Banner

Findet die App eine bestehende Testphase auf dieser Maschine, ohne dass ein Konto angemeldet ist, erscheint oben im Fenster ein gelber Banner mit der Bitte, sich vor Ablauf der Frist anzumelden. Klicken Sie auf **Sign in** im Banner — der Anmelde-Dialog öffnet sich. Nach erfolgreicher Anmeldung wird die Testphase auf Ihr Konto übertragen, und der Banner wird durch eine "Trial migriert"-Bestätigung ersetzt. Die Migration läuft automatisch — Sie müssen ausser der Anmeldung nichts tun.

Schlägt die Migration fehl (Server-Fehler, abgelaufenes Fenster, Trial gehört bereits einem anderen Konto), ersetzt ein roter Banner den ursprünglichen mit der Fehlerursache. Starten Sie die Anwendung neu und versuchen Sie es erneut, oder kontaktieren Sie den Support bei wiederkehrendem Fehler.

Kann die automatische Migration die Legacy-Hardware-ID nicht finden (z. B. nach Plattenwechsel oder Wiederherstellung eines Windows-Backups), öffnen Sie **View → Einstellungen → Lizenz** und klicken Sie auf **Manuell migrieren**. Geben Sie die 16-stellige Hardware-ID aus einer Sicherung, einer Support-E-Mail oder einem alten Registry-Export ein und bestätigen Sie — der manuelle Pfad benutzt dieselbe Trial-Migrations-Pipeline wie der automatische Banner, sodass Fehler unmittelbar unterhalb des Buttons in derselben Diagnose-Sprache erscheinen.

### Account-Seite (Browser)

Klicken Sie im Lizenz-Fenster auf **Auf Webseite verwalten** (oder rufen Sie nach der Anmeldung `https://tiaopenessmanager.ch/profile` auf), um Ihre browserbasierte Account-Seite zu öffnen. Die Seite bietet vier Operationen über das hinaus, was das Desktop-Lizenz-Fenster zeigt:

- **Profil** — E-Mail, Konto-Erstellungs-Datum und letzte Anmeldung.
- **Abonnement verwalten** — öffnet das Stripe-Kunden-Portal in einem neuen Tab für Zahlungsmethode, Rechnungen oder Kündigung.
- **Diese Maschine freigeben** — gibt die aktuelle Maschinen-Bindung frei, sodass Sie ohne Warten auf das 30-Tage-Fenster auf einem anderen Computer aktivieren können. Ein Bestätigungsdialog erscheint vor der Freigabe. Die nächste Anmeldung auf einer neuen Maschine wird zur neuen aktiven Bindung.
- **Konto löschen** (Gefahren-Zone) — löscht Ihr Konto endgültig, widerruft alle angemeldeten Sitzungen und gibt die Lizenz frei. Der Dialog verlangt die Eingabe von **DELETE** in Grossbuchstaben zur Bestätigung. Nicht umkehrbar.

Die Seite ist nur über HTTPS erreichbar und erfordert eine aktive Anmeldung. Nach dem Abmelden (entweder aus der Desktop-App oder von der Seite selbst) leitet die Seite Sie beim nächsten Besuch zur Anmeldung um.

**Nicht vertrauenswürdige Umgebung (Basic-Modus)**

Wenn ein Debugger an den App-Prozess angehängt ist oder die Haupt-EXE nicht mit dem erwarteten Certum-Zertifikat signiert ist, schaltet die App still auf den Basic-Tier. Das ist eine Tiefen-Absicherung gegen Manipulation. Release-Builds haben immer die korrekte Signatur — erscheint diese Degradierung bei einer Standard-Installation, wurde die Binary verändert. Installieren Sie dann neu von https://www.tiaopenessmanager.ch.

### Unternehmenslizenz verwalten

Volume Pro und Volume Enterprise sind Mehrplatz-Subscriptions für Unternehmen. Der Owner (die Person, die die Subscription gekauft hat) verwaltet die Sitze über das Web-Dashboard, Mitarbeiter melden sich mit ihrer eigenen E-Mail an und nutzen jeweils einen Sitz.

**Owner — Subscription anlegen.** Gehen Sie auf https://www.tiaopenessmanager.ch und wählen Sie **Volume Professional** oder **Volume Enterprise** mit der gewünschten Sitzanzahl (2-200). Nach dem Stripe-Checkout erhalten Sie zwei E-Mails: einen Magic-Login-Code für die Owner-Anmeldung in der Desktop-App und eine Org-Bestätigung mit Org-ID + Owner-Rolle.

**Owner — Mitarbeiter einladen.** Öffnen Sie nach Anmeldung in der Desktop-App den Lizenz-Dialog (**View → Einstellungen → Lizenz verwalten**) und klicken Sie auf **Auf Webseite verwalten**. Das Web-Dashboard zeigt belegte und freie Sitze. Tragen Sie die E-Mail eines Mitarbeiters ein und klicken Sie auf **Einladen** — der Mitarbeiter erhält eine E-Mail mit einem Magic-Link, der 7 Tage gültig ist.

**Mitarbeiter — Einladung annehmen.** Klick auf den Magic-Link öffnet die Web-Seite mit dem Org-Namen und einem **Annehmen**-Button. Nach Annahme wird der Account an die Org gebunden. In der Desktop-App melden Sie sich mit derselben E-Mail an — der Lizenz-Dialog zeigt die Mitgliedschaft mit Rolle "Mitglied" und einem Hinweis, dass die Verwaltung beim Owner liegt.

**Owner — Sitz freigeben.** Im Web-Dashboard klicken Sie auf **Sitz freigeben** neben der Mitarbeiter-Zeile. Der Sitz wird sofort frei und kann erneut eingeladen werden. Der ehemalige Mitglieds-Account fällt auf den Basic-Tier zurück (sofern keine eigene Solo-Subscription vorhanden ist).

**Sitzanzahl ändern.** Im Stripe-Kunden-Portal können Sie `quantity` jederzeit erhöhen — die zusätzlichen Sitze stehen sofort zum Einladen bereit. Reduzieren ist nur möglich, wenn entsprechend viele Sitze frei sind; geben Sie ggf. erst Sitze frei, bevor Sie die Sitzanzahl im Stripe-Portal senken.

<!-- feature:eplan start -->
**Add-ons im Volume-Modell.** Das EPLAN-Add-on kann Org-weit gebucht werden — alle Mitglieder erben den Zugang automatisch beim nächsten Login. Owner sieht das im Lizenz-Dialog unter Add-ons → EPLAN als "Org-aktiviert"; Mitglieder sehen "Aktiviert (Org)" ohne eigenen Verwalten-Button.

### EPLAN-Add-on aktivieren

Das EPLAN-Add-on ist eine separat lizenzierbare Erweiterung für die Anbindung an EPLAN Electric P8. Verfügbar für Pro, Enterprise, Trial und Volume-Subscriptions.

**Solo-Aktivierung.** Im Lizenz-Dialog → Abschnitt **Add-ons** → Karte **EPLAN** → **Erwerben**-Button öffnet den Stripe-Checkout für CHF 19.99/Monat oder CHF 199.99/Jahr (Jahresabo spart 17 %). Nach Zahlung schaltet die Karte auf "Aktiviert"; einmal abmelden + anmelden (oder **Aktualisieren** im Lizenz-Dialog) lädt die neue Berechtigung — der EPLAN-Tab erscheint links in der Aktivitätsleiste.

**Volume-Aktivierung (Owner).** Im Web-Dashboard → **Add-ons → EPLAN → Hinzufügen** öffnet einen Stripe-Checkout für die org-weite Add-on-Subscription mit `quantity` passend zur Sitzanzahl. Nach Zahlung erbt jeder Mitarbeiter beim nächsten Validate-Cycle den EPLAN-Zugang automatisch.

**Trial-Konten.** Während der 30-tägigen Testphase ist das EPLAN-Add-on automatisch enthalten — keine separate Aktivierung nötig.

**Add-on kündigen.** Solo: über Stripe-Portal die Add-on-Subscription beenden — der EPLAN-Tab verschwindet beim nächsten Validate-Cycle. Volume: Owner kündigt im Web-Dashboard, alle Mitarbeiter verlieren den Zugang gleichzeitig.

<!-- feature:eplan end -->
---

## 14a. Git-Client

Der Git-Client ist eine integrierte Versionsverwaltungs-Oberfläche für die Arbeit mit Repositories direkt in TIA Openness Manager. Er ermöglicht einen visuellen Git-Workflow, ohne die Anwendung zu verlassen.

### Activity-Bar-Badge

Das Git-Icon in der Activity-Bar (linke Navigationsleiste) zeigt einen kleinen akzentfarbenen Count-Badge, sobald irgendein offenes Repository nicht-committete Änderungen hat. Der Badge zeigt die Gesamtzahl der gestaged + unstaged + untracked Dateien **summiert über alle offenen Repository-Tabs**.

- Werte bis 999 werden exakt angezeigt (z.B. `5`, `42`, `999`)
- Werte von 1000 bis 99 999 werden im kompakten `K`-Format angezeigt (z.B. `1K`, `10K`, `99K`)
- Werte ab 100 000 werden als `99K+` angezeigt
- Der Badge ist ausgeblendet, wenn nirgendwo nicht-committete Änderungen vorhanden sind

Beim Hovern über das Git-Icon erscheint ein Tooltip mit dem lokalisierten Count (z.B. *"Versionsverwaltung (Ctrl+2) — 5 nicht committete Änderungen"*) in der korrekten Plural-Form Ihrer UI-Sprache.

### Repository öffnen

1. Klicken Sie auf den Tab **Git** in der Hauptnavigation
2. Klicken Sie auf der Willkommensseite auf **Repository öffnen** und wählen Sie einen Ordner, oder ziehen Sie einen Repository-Ordner auf die Willkommensseite
3. Zuletzt verwendete Repositories werden in der Liste für den schnellen Zugriff angezeigt

**Tastenkürzel:** Drücken Sie **Strg+Umschalt+O** an beliebiger Stelle im Git-Arbeitsbereich, um das Popup **Lokales Repository öffnen** zu starten. Das Popup nimmt Pfad, Ziel-Workspace und Bookmark-Gruppe in einem Schritt entgegen — das Repository wird bei Erfolg direkt der gewählten Gruppe zugeordnet, ohne zusätzlichen Edit-Schritt.

### Tabs-Palette

Der **Tabs**-Icon-Button neben der Workspace-Auswahl (oder **Strg+P** an beliebiger Stelle im Git-Arbeitsbereich) öffnet eine Quick-Switch-Palette mit allen offenen Repository-Tabs plus zuletzt verwendeten Repositories. Tippen filtert die Liste; Enter wechselt zum hervorgehobenen Tab; Escape schließt die Palette ohne Wechsel.

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

> **Zwei Paletten teilen sich Strg+Umschalt+P.** Diese Git-Befehlspalette ist auf den Arbeitsbereich beschränkt und enthält die 14 Git-spezifischen Aktionen unten. Die globale [Schnellzugriff-Leiste](#3a-schnellzugriff-quick-open) (ebenfalls Strg+Umschalt+P, vorbelegt mit `>`) liegt in der Titelleiste und arbeitet mit Präfixen (`>` `@` `#` `git:` `?` `:`). Die Git-Befehlspalette hat Vorrang, wenn der Git-Tab den Fokus hat; überall sonst öffnet sich die Schnellzugriff-Leiste.

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

### Diff-Ladefehler

Wenn ein Revisionsvergleich oder ein Datei-Diff nicht geladen werden kann (z. B. weil Git die Änderungen zwischen den beiden SHAs nicht ermitteln konnte), erscheint ein Inline-Fehlerbanner oberhalb des Diff-Bereichs — sowohl in der Commit-Detailansicht als auch in der Revisionsvergleichsansicht und im Submodul-Vergleichsfenster. Der bisherige Diff-Inhalt bleibt sichtbar; das Banner verschwindet automatisch, sobald die nächste Auswahl oder der nächste Vergleich erfolgreich lädt. Technische Details (Exception-Typ, Befehlsausgabe) werden in das Anwendungslog geschrieben.

### Submodul-Revisionen vergleichen

Wenn ein Commit den Pointer eines Submoduls ändert, erscheint die Datei in der Commit-Detailansicht als **Submodul**-Eintrag mit den alten und neuen Commit-SHAs. Ein Klick auf **Details öffnen** auf dem Submodul-Eintrag öffnet ein eigenes, schreibgeschütztes Fenster **Submodul-Vergleich**. Das Fenster zeigt:

- Zwei CommitDetail-Panes nebeneinander — den alten und neuen Submodul-Commit mit Author, Datum und Message
- Einen zentralen Änderungs-Pane, der die tatsächlichen Änderungen innerhalb des Submoduls zwischen den beiden Pointern als Text- und Binary-Diff abbildet

Das Fenster ist schreibgeschützt und ändert weder das Eltern-Repository noch das Submodul. Schnelle Doppelklicks auf **Details öffnen** erzeugen kein zweites Fenster — das vorhandene Fenster wird stattdessen in den Vordergrund geholt.

Tastenkürzel in der Datei-Liste:

- `Strg+C` — relative Datei-Pfade in die Zwischenablage kopieren
- `Strg+Umschalt+C` — absolute Datei-Pfade in die Zwischenablage kopieren
- `Strg+F` — Suchfeld über der Datei-Liste fokussieren

### Submodul-Badge bei nicht committeten Änderungen

Jedes Submodul in der Sidebar zeigt ein Inline-Badge, sobald das Submodul selbst lokale, nicht committete Änderungen hat (z. B. *„+ 3 nicht committete Änderungen"*). Der Wert entspricht dem trailing `+`-Marker aus `git submodule status` — also Modifikationen im eigenen Working-Tree des Submoduls. Das Badge aktualisiert sich beim Refresh des Eltern-Repositories oder des Submoduls.

### Klonen mit Gruppe und Bookmark

Das Popup **Repository klonen** bietet beim Klonen die Auswahl einer Workspace-**Gruppe** sowie einer **Bookmark-Farbe**. Bei Erfolg wird das geklonte Repository als Knoten in der gewählten Gruppe mit dem ausgewählten Bookmark eingefügt — ohne separaten Edit-Schritt. Beide Felder sind optional; bleiben sie leer, landet das Klone im Workspace-Root ohne Bookmark.

### Custom Actions — Argument-Format und Branch-Selektoren

Custom Actions verwenden jetzt einen frei wählbaren **Argument-Format**-String anstelle einer fixen Argumentliste. Der Format-String unterstützt Variablen, die zur Laufzeit ersetzt werden:

- `${REPO}` — Pfad des Repository-Roots
- `${BRANCH}` — Name des gewählten Branches
- `${BRANCH_FRIENDLY_NAME}` — Friendly-Name des Branches (ohne Remote-Prefix)
- `${SHA}` — SHA des gewählten Commits (bei Aufruf aus der History-Ansicht)
- `${FILE}` — Pfad der gewählten Datei (bei Aufruf aus einem Datei-Kontextmenü)
- `${REMOTE}` — Remote-Name (bei Aufruf auf einem Remote)
- `${TAG}` — Tag-Name (bei Aufruf auf einem Tag)

Ein neuer **Branch-Selector**-Control-Typ befüllt `${BRANCH}` und `${BRANCH_FRIENDLY_NAME}` mit getrennten Modi für lokale und Remote-Tracking-Branches. Konfiguration erfolgt im Custom-Action-Einstellungsdialog (Zahnrad → Custom Actions → Controls konfigurieren).

### Stash-Diff-Toolbar

Der Diff-Bereich der Stash-Ansicht enthält zwei Toolbar-Toggles, analog zur Working-Copy-Diff:

- **Whitespace ignorieren** — berechnet die Diff so, dass reine Whitespace-Änderungen ausgeblendet werden
- **Side-by-Side** — schaltet zwischen Unified-Diff und Side-by-Side-Layout um

Klicks während ein vorheriger Reload noch läuft, brechen den laufenden Ladevorgang ab und starten einen neuen — der zuletzt gewählte Toggle gewinnt.

### Auto-Fetch

Hintergrund-Auto-Fetch ist jetzt eine einzige globale Einstellung unter **Einstellungen → Git → Auto-Fetch** und gilt für alle offenen Repositories. Das frühere Per-Repository-Toggle wurde entfernt und vorhandene Per-Repo-Settings werden ignoriert. Das Intervall (Default 10 Minuten) wird im selben Einstellungsblock konfiguriert. Der Auto-Fetch-Indikator in der Git-Sidebar ist ausgeblendet, solange die Einstellung deaktiviert ist.

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

<!-- feature:eplan start -->
---

## 14c. EPLAN-Integration (Add-on)

Die EPLAN-Integration ist ein optionales, separat lizenziertes Add-on. Sie verbindet die Anwendung mit einer lokalen Installation von **EPLAN Electric P8** (2025.0.3 oder kompatibel), so dass Sie EPLAN-Projekte durchsuchen und exportieren können, ohne den Manager zu verlassen.

### Voraussetzungen

- Eine gültige EPLAN-Electric-P8-Installation auf demselben Rechner.
- Eine aktive EPLAN-License-Manager-Sitzung (ELM) — das Add-on hält keine eigene EPLAN-Lizenz, es nutzt Ihre bestehende.
- Das EPLAN-Add-on auf Ihrer Manager-Lizenz freigeschaltet. Das Add-on wird vom Lizenz-Backend gewährt und erscheint unter **Lizenz → Add-ons** als grünes "Aktiviert"-Badge. Ohne Add-on bleibt der EPLAN-Tab ausgeblendet.

### Aktivierung

Das Add-on wird separat erworben. Nach Freischaltung melden Sie sich einmal ab und wieder an (oder lösen über die Lizenzseite eine erneute Validierung aus), damit die neue Berechtigung übernommen wird. Die Karte unter **Lizenz → Add-ons → EPLAN** wechselt von "Nicht aktiviert" auf "Aktiviert", und der EPLAN-Tab erscheint links in der Aktivitätsleiste.

### Projekt öffnen

Klicken Sie auf den EPLAN-Tab. Der Arbeitsbereich zeigt Ihre zuletzt geöffneten EPLAN-Projekte (neueste zuerst) und einen **EPLAN-Projekt öffnen…**-Button. Wählen Sie eine `.elk`-Datei über den Dateidialog oder klicken Sie auf einen Eintrag in der Liste — der Manager startet beim ersten Mal einen versteckten EPLAN-Bridge-Prozess und öffnet anschliessend das Projekt.

Falls mehr als eine EPLAN-Variante installiert ist (Electric P8, ProPanel, Preplanning …), erscheint ein einmaliger Variantenwähler. Die Auswahl wird zwischen Sitzungen gemerkt; pro Anwendungssitzung läuft aufgrund der ELM-Lizenz-Beschränkung nur eine Bridge / eine Variante.

Die Bridge-Statusanzeige im Header des Arbeitsbereichs zeigt den aktuellen Zustand:

- **Bridge verbunden** — Bridge läuft und ein Projekt ist geöffnet.
- **Bridge wird verbunden …** — Bridge startet oder verbindet sich neu.
- **Bridge getrennt** — keine Bridge läuft.

Stürzt die Bridge mitten in der Sitzung ab, erscheint ein Hinweisbanner mit einem **Neu verbinden**-Button. Neu verbinden startet die Bridge und öffnet automatisch das zuvor offene Projekt erneut.

### Projekt durchsuchen

Im rechten Bereich liegt der **Projekt-Explorer**. Er gruppiert den Projektinhalt in zwei Oberkategorien:

- **Seiten** — alle Schaltplanseiten des Projekts mit Bezeichner, Dokumenttyp und Beschreibung.
- **Funktionen** — die aus den Schaltplänen extrahierten Hauptfunktionen mit Tag (z. B. `=A1+K2-K1`), dem Bezeichner der zugehörigen Seite und ggf. einer Artikelnummer.

Über das Filterfeld am oberen Rand filtern Sie beide Kategorien per Teilstring-Suche über alle sichtbaren Spalten. Die Kategorien-Header aktualisieren die Trefferanzahl live.

### Export

Der Toolbar-Button **Export…** öffnet einen Dialog mit zwei Formaten:

- **PXF (EPLAN-Austausch)** — verlustfreies EPLAN-Austauschformat, geeignet für den Re-Import in EPLAN.
- **PDF** — flache PDF aller Schaltplanseiten.

Wählen Sie über **Durchsuchen…** eine Zieldatei aus und klicken Sie auf **Exportieren**. Längere Exporte laufen mit einer unbestimmten Fortschrittsanzeige — die EPLAN-Engine liefert in dieser Version keine seitenweise Fortschrittsmeldung. Die exportierte Datei landet am gewählten Pfad.

### Zuletzt verwendete Projekte

Jedes erfolgreich geöffnete Projekt landet in der Liste der zuletzt verwendeten Projekte (max. 10 sichtbar, 50 gespeichert). Klicken Sie auf einen Eintrag, um ihn erneut zu öffnen; das kleine **×** entfernt einen Eintrag, ohne die EPLAN-Datei auf der Festplatte zu berühren. Wurde die Datei verschoben oder gelöscht, entfernt der Manager den toten Eintrag automatisch und zeigt einen Hinweis.

### Seiten-Vorschau

Doppelklick auf eine Seite im EPLAN-Baum öffnet die Vorschau-Tab. Mausrad zum Zoomen, mittlere Maustaste zum Verschieben, ein Fadenkreuz folgt dem Mauszeiger über die gesamte Seite. Die Seite wird auf weißem Hintergrund dargestellt, damit der Seitenrand bei jedem Zoom-Level sichtbar bleibt.

### Einschränkungen dieser Version

- **Authoring nur über MCP-Tools, nicht direkt in der UI.** Seiten- und Funktions-Anlegen/Löschen/Umbenennen, Symbol-Einfügen, Stückliste/PDF/Label-Report-Erzeugung sind ausschliesslich über AI-Chat oder externe MCP-Clients zugänglich — der Arbeitsbereich selbst bleibt read-only plus Export aus der Toolbar; Tag-Synchronisation mit TIA wird noch nicht unterstützt.
- **Eine EPLAN-Variante pro Sitzung.** Da der EPLAN-License-Manager pro Maschine nur eine Electric-P8-Sitzung lizenziert, erfordert ein Variantenwechsel einen Neustart des Managers.

Sollte der EPLAN-Tab nach Aktivierung des Add-ons nicht erscheinen, starten Sie den Manager einmal neu, damit die Aktivitätsleiste die neue Berechtigung übernimmt.

<!-- feature:eplan end -->
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
