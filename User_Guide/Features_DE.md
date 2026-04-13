# TIA Openness Manager - Feature-Übersicht

## Produktbeschreibung

Der **TIA Openness Manager** ist ein leistungsstarkes Werkzeug für Siemens TIA Portal Entwickler, das den Export, Import und die Verwaltung von SPS-Programmbausteinen revolutioniert. Mit einer intuitiven Benutzeroberfläche und fortschrittlichen Funktionen wie Differenzvergleich, Schutzprofilen und KI-Integration steigert es die Produktivität und reduziert Fehler bei der Projektverwaltung erheblich.

---

## Hauptfeatures

### Import & Export

- **Bulk Export** - Exportieren Sie hunderte Blöcke mit einem Klick
- **Selektiver Export** - Wählen Sie genau die Blöcke, die Sie benötigen
- **XML & SCL Support** - Vollständige Unterstützung für Simatic ML und SCL-Dateien
- **S7DCL Export (V20+)** - Zusätzliches textbasiertes Export-Format (.s7dcl) für bessere Versionskontrolle
- **Ordnerstruktur-Erhaltung** - Die TIA Portal Ordnerstruktur wird beibehalten
- **Automatische Kompilierung** - Kompiliert und speichert automatisch nach Import
- **Konfigurierbare Ordnernamen** - Passen Sie Export-Ordnernamen an (Source, Blocks, Tags, etc.)
- **Optionaler Source-Ordner** - Source-Ordner im Export aktivieren/deaktivieren

### HMI Export/Import

- **Bildschirm-Export** - HMI-Bildschirme als XML exportieren
- **Bildschirmvorlagen-Export** - Wiederverwendbare Bildschirmvorlagen exportieren
- **HMI-Variablentabellen** - HMI-Variablentabellen exportieren/importieren
- **VB-Skripte** - HMI VB-Skripte exportieren
- **Verbindungen** - HMI-Verbindungskonfigurationen exportieren
- **Text- & Grafiklisten** - Vollständige Unterstützung für HMI-Listen

### Hardware-Tab

- **Geräteliste** - Vollständige Übersicht aller Geräte (SPSen, HMIs, Antriebe, Switches)
- **PROFINET-Namen** - PROFINET-Gerätenamen direkt anzeigen und bearbeiten
- **IP-Adressen** - IP-Adresskonfiguration für alle Geräte anzeigen
- **Firmware-Versionen** - Firmware-Version für jedes Gerät anzeigen
- **Artikelnummern** - Siemens Artikel-/Bestellnummern anzeigen
- **I/O-Mapping** - Ein-/Ausgabe-Adressbereiche anzeigen
- **CSV-Export** - Komplette Hardware-Liste als CSV für Dokumentation exportieren
- **WinCC Unified Support** - Volle Unterstützung für WinCC Unified HMI-Panels

### Hardware-Export

- **Gerätekonfiguration** - Hardware-Konfiguration als XML exportieren
- **Modulkonfiguration** - Individuelle Moduleinstellungen exportieren
- **Netzwerkkonfiguration** - Netzwerk-/Kommunikationseinstellungen exportieren

### Watch/Force-Tabellen

- **Tabellen-Export** - Watch-Tabellen und Force-Tabellen exportieren
- **Variablenlisten** - Überwachte Variablenkonfigurationen exportieren
- **Debug-Unterstützung** - Debugging-Setups projektübergreifend erhalten

### Projektbibliothek-Verwaltung

- **Master Copy erstellen** - Bausteine in Projektbibliothek kopieren zur Wiederverwendung
- **Aus Bibliothek instanziieren** - Bausteine aus Master Copies erstellen
- **Typversionen exportieren** - Freigegebene Bibliothekstyp-Versionen als XML exportieren
- **Ordner-Organisation** - Ordner in Bibliothek für bessere Struktur erstellen
- **Elemente umbenennen** - Master Copies, Typen und Ordner umbenennen
- **Elemente löschen** - Bibliothekselemente mit Bestätigung entfernen
- **Bibliothek aufräumen** - Ungenutzte Typen und Versionen automatisch entfernen
- **MCP-Integration** - 7 Bibliotheks-Tools für KI-Assistenten verfügbar

### Differenzvergleich (Preview Diff)

- **Fingerprint-basiert** - Schneller Vergleich ohne vollständigen Export
- **Änderungserkennung** - Erkennt geänderte, neue und gelöschte Blöcke
- **Detaillierter Diff-Viewer** - Zeigt Unterschiede Zeile für Zeile
- **Selektiver Re-Export** - Nur geänderte Blöcke exportieren

### Code-Editor

Der integrierte Code-Editor bietet professionelle Bearbeitungsfunktionen für SCL und andere Dateitypen.

- **Split View** — Editoren horizontal oder vertikal teilen, Tabs zwischen Gruppen ziehen, Panels andocken und anheften (Dateibaum, Markdown-Vorschau)
- **Syntax-Hervorhebung** — SCL, C#, XML, JSON, Python und 60+ weitere Sprachen
- **Code-Faltung** — Coderegionen, IF/FOR-Blöcke und VAR-Abschnitte ein-/ausklappen
- **Auto-Vervollständigung** — Ab 2 Zeichen werden SCL-Schlüsselwörter, Datentypen und Funktionen vorgeschlagen
- **Suche** — Strg+F für Suchen und Ersetzen mit Regex-Unterstützung
- **Code-Snippets** — `if`, `for`, `while`, `case`, `fb`, `fc` oder `region` eingeben und Tab drücken
- **Aktuelle Zeile** — Visuelle Hervorhebung der aktuellen Cursorzeile
- **Theme-Unterstützung** — Editor-Farben passen sich automatisch beim Wechsel zwischen Dark und Light an
- **Inline-Chat (Strg+I)** — Strg+I öffnet einen KI-Chat direkt im Code-Editor. Optional Code markieren, dann Frage oder Anweisung eingeben — die KI antwortet und kann Änderungen inline vorschlagen. Übernehmen mit Tab, Ablehnen mit Escape
- **Block-Details** - Zeigt Metadaten wie Nummer, Sprache, Autor
- **Schnelle Navigation** - Suche im Projektbaum

#### Tastenkürzel
| Kürzel | Aktion |
|--------|--------|
| Strg+F | Suchen und Ersetzen |
| Strg+I | Inline AI-Chat (nur SCL-Editor) |
| Tab | Snippet einfügen (bei Triggerwort) |
| Tab | AI-Änderung übernehmen |
| Escape | AI-Änderung ablehnen |

### Schutz-System (Protected Items)

- **Block-Schutz** - Schützen Sie wichtige Blöcke vor versehentlichem Überschreiben
- **Export-Schutz** - Geschützte Blöcke optional vom Export ausschliessen, Ordnerstruktur bleibt erhalten
- **Profile** - Speichern und laden Sie Schutz-Konfigurationen
- **Visuelle Markierung** - Geschützte Blöcke sind klar mit grünem Schild gekennzeichnet
- **Hierarchischer Schutz** - Schützen Sie ganze Ordner oder einzelne Blöcke

### Passwort-Tresor (Password Vault)

- **Sichere Speicherung** - AES-256-GCM-verschlüsselter Tresor für TIA Portal Know-How-Schutz-Passwörter
- **Master-Passwort** - Ein einziges Master-Passwort schützt alle Tresoreinträge (PBKDF2 Key Derivation)
- **Block-Zuordnung** - Tresor-Passwörter über Kontextmenü oder Tresor-Toggle-Checkboxen Blöcken oder Ordnern zuordnen
- **Massen-Schutz/Entschutz** - Know-How-Schutz auf alle zugeordneten Blöcke gleichzeitig anwenden oder entfernen
- **Crash-Recovery** - Blöcke, die durch einen Absturz ungeschützt geblieben sind, werden beim nächsten Projektöffnen automatisch wieder geschützt
- **CSV-Export** - Exportieren Sie alle Tresor-Einträge als CSV für Sicherung (inklusive Passwörter im Klartext, verfügbar wenn Tresor entsperrt ist)
- **Lokalisiert** - Verfügbar in Englisch, Deutsch, Französisch und Italienisch

### Find Unused Blocks

- **Dead Code Erkennung** - Findet nicht verwendete Bausteine
- **Call-Graph Analyse** - Basiert auf tatsächlichen Aufrufen, nicht nur Referenzen
- **Safety-Block Support** - Unterstützt auch F-Blöcke (F_FB, F_FC, F_DB, F_OB)
- **Konfigurierbarer Analyse-Umfang** - Bausteine (FC/FB), Datenbausteine (DB), UDTs und Tags einzeln ein-/ausschalten
- **Ausschlussmuster** - Platzhaltermuster definieren (z.B. `FB_Test*;DB_Temp*`) um Elemente auszuschließen
- **Exporte wiederverwenden** - Vorherige XML-Exporte für schnellere wiederholte Analyse nutzen
- **Persistente Einstellungen** - Alle Analyse-Einstellungen über Zahnrad-Symbol gespeichert
- **Export-Funktion** - Ergebnisse als Textdatei exportieren
- **In Zwischenablage kopieren** - Alle Ergebnisse für Dokumentation kopieren
- **Lösch-Funktion** - Ungenutzte Blöcke direkt entfernen

### KI-Integration (MCP Server)

- **Model Context Protocol** - Integration mit jedem MCP-kompatiblen KI-Assistenten
- **Projekt-Kontext** - KI hat Zugriff auf Ihre Projektstruktur
- **Code-Generierung** - KI kann SCL-Quellcode für Bausteine generieren
- **DB-Generierung** - KI kann Datenbausteine mit Simatic ML-Vorlagen erstellen
- **UDT-Generierung** - KI kann benutzerdefinierte Datentypen erstellen
- **Variablentabellen-Generierung** - KI kann Variablentabellen erstellen
- **Auto-Import** - Generierter Code kann automatisch in TIA Portal importiert werden
- **Block-Analyse** - KI kann bestehende Bausteine lesen und analysieren

### KI-Chat

- **Kontext-Ordner** - Registrieren Sie Ordner, die die KI mit Datei-Lese- und Suchwerkzeugen durchsuchen kann
- **Anweisungsdateien** - Markdown-Dateien werden automatisch zu Sitzungsbeginn in den System-Prompt der KI eingefügt
- **Git-Integration** - Die KI kennt Ihr Git-Repository, den aktuellen Branch und Änderungen; kann Status anzeigen, Dateien stagen, committen, pushen und pullen (schreibende Operationen erfordern Benutzerbestätigung)
- **Commit-Vorlagen** - Definieren Sie Commit-Message-Vorlagen; die KI folgt der aktiven Vorlage beim Erstellen von Commits
- **Skills** - Legen Sie `.md`-Dateien in `%LocalAppData%\TiaOpennessManager\skills\` ab, um wiederverwendbare Prompt-Befehle zu erstellen, die über die `/`-Befehlspalette in der Chat-Eingabe aufrufbar sind; kein Frontmatter nötig (reiner Text genügt), optionales YAML-Frontmatter für Name, Beschreibung und Icon
- **Agent-Konfigurationen** - Legen Sie `.json`-Dateien in `%LocalAppData%\TiaOpennessManager\agents\` ab, um KI-Personas mit eigenen System-Prompts und Tool-Zugriff zu definieren; drei eingebaute Agenten (General Assistant, Git Assistant, SCL Expert)
- **Dateianhänge** - Ziehen Sie Bilder (`.png`, `.jpg`, `.bmp`, `.gif`, `.webp`) oder Textdateien (`.cs`, `.xml`, `.json`, `.txt`, `.md`, `.yaml`, `.csv`, `.log`, `.scl`, `.cfg`) per Drag & Drop in den Chat; Bilder werden skaliert und als multimodaler Inhalt gesendet
- **Zwischenablage einfügen** - Drücken Sie Strg+V, um einen Screenshot aus der Zwischenablage direkt in den Chat einzufügen; auch über das Anhang-Menü verfügbar
- **Chat-Sitzungen** - Konversationen werden automatisch gespeichert; erstellen Sie neue Chats, wechseln Sie zwischen Sitzungen und setzen Sie frühere Gespräche über das Verlauf-Panel fort
- **Sitzungsarchiv** - Archivieren Sie alte Sitzungen, um die Sitzungsliste übersichtlich zu halten; archivierte Sitzungen wiederherstellen oder dauerhaft löschen
- **Agenten-Gedächtnis** - Jeder Agent hat einen eigenen, sitzungsübergreifenden Gedächtnisspeicher mit Scope-Isolierung (Lokal, Projekt oder Benutzer); der Agent speichert automatisch wichtige Fakten und fügt relevante Erinnerungen beim Sitzungsstart in den Kontext ein; unterstützt die Tools `memory_store`, `memory_search`, `memory_list`, `memory_update` und `memory_delete`; konfigurierbarer Embedding-Anbieter (OpenAI, Google, Ollama, LM Studio) für semantische Suche mit Schlüsselwort-Fallback; Gedächtnis-Einstellungen zum Anzeigen, Löschen, Exportieren (JSON), Importieren und Aufräumen alter Erinnerungen; Memory-Snapshots ermöglichen das Vorbefüllen von Agenten mit teamweit geteiltem Wissen über JSON-Dateien
- **Subagenten-Steuerung** - Agent kann Teilaufgaben an unabhängige Subagenten delegieren (`run_subagent`); bis zu 5 gleichzeitige Subagenten; laufende Subagenten verwalten mit `manage_subagents list/kill/steer`; nicht-blockierender Modus ermöglicht dem Hauptagenten, weiterzuarbeiten, während Teilaufgaben im Hintergrund laufen
- **Hooks** - Konfigurierbare Event-Hooks, die vor/nach KI-Tool-Aufrufen ausgeführt werden; eigene Hooks in den KI-Chat-Einstellungen als Shell-Befehle oder HTTP-Callbacks hinzufügen; eingebaute Hooks schützen Safety-Blöcke und protokollieren TIA-Operationen; Hooks können Tool-Input modifizieren, Ausführung blockieren oder Kontext zu Ergebnissen hinzufügen; konfigurierbarer Timeout pro Hook (Standard 60s)
- **Inline Tool-Genehmigungen** - KI-Werkzeugaufrufe werden direkt in der Tool-Nachricht im Chat genehmigt oder abgelehnt; die Buttons sind Teil des scrollbaren Inhalts, sodass Nachrichten weiterhin gelesen, die Historie gescrollt und Tabs gewechselt werden können, während eine Genehmigung aussteht; vier Auswahlmöglichkeiten pro Aufruf: Ablehnen, Einmal erlauben, Für Sitzung erlauben, oder Immer erlauben (dauerhaft gespeichert); wird die Anwendung während einer Genehmigung geschlossen, lässt sich die Sitzung sicher fortsetzen
- **Berechtigungsmodi** - Toggle-Button neben dem Senden-Button wählt durch, wie Schreiboperationen genehmigt werden: **Standard** fragt bei jeder Schreiboperation, **Änderungen akzeptieren** genehmigt Datei-Edits automatisch, fragt aber weiterhin bei Shell-Befehlen und destruktiven Operationen wie Löschen oder Force-Push, **Auto** genehmigt alles außer gefährlichen Operationen (PowerShell, Prozesszugriff, Netzwerk-Schreiboperationen); der aktuelle Modus wird durch ein farbiges Icon und einen Tooltip angezeigt; der Planmodus ist ein separater Toggle, der die KI zwingt, einen genehmigten Plan einzureichen, bevor Schreiboperationen möglich sind
- **Inline Plan-Genehmigung** - Wenn die KI einen Ausführungsplan einreicht, erscheint dieser als editierbares Textfeld direkt im Chat mit Genehmigen- und Ablehnen-Buttons; der Plan kann vor der Genehmigung bearbeitet werden; nicht-blockierend — während der Prüfung kann durch die Historie gescrollt oder zwischen Tabs gewechselt werden
- **Befehlswarteschlange** - Nachrichten senden waehrend der KI-Agent arbeitet; Nachrichten werden mit Prioritaetsstufen (Jetzt/Naechstes/Spaeter) in eine Warteschlange gestellt und nach jedem Turn automatisch verarbeitet; Warteschlangen-Anzeige zeigt die Anzahl ausstehender Nachrichten; ESC bricht die aktuelle Operation ab und leert die Warteschlange, oder holt wartende Nachrichten zurueck ins Eingabefeld wenn der Agent untaetig ist
- **Multi-Session** - Mehrere KI-Chat-Sessions gleichzeitig ausfuehren; die Agent-Sidebar (umschaltbar ueber PanelLeftOpen/PanelLeftClose-Icon) gleitet als Overlay von links heraus und zeigt alle Sessions gruppiert nach Status (In Bearbeitung / Abgeschlossen); jede Session hat eigenen Chat-Kontext, Canvas und Agent/Provider; Subagenten werden automatisch ihrer Eltern-Session zugeordnet; Ungelesene-Nachrichten-Badges mit Blink-Animation zeigen Aktivitaet in anderen Sessions; Doppelklick auf Session-Name zum Umbenennen; Sessions schliessen ueber X-Button (mit Bestaetigung wenn noch aktiv); Canvas-State wird pro Session gespeichert und beim Wechsel wiederhergestellt; Live-Vorschau unter dem Session-Namen zeigt eingehende Nachrichten und Antworten aus anderen Sessions
- **Agent pro Session** - Jede Session merkt sich ihre Agent/Provider/Modell-Auswahl unabhaengig; in einer Session einen anderen Provider waehlen ohne andere Sessions zu beeinflussen; der Agent wechselt automatisch beim Session-Wechsel
- **Cross-Session-Kommunikation** - Agents koennen Nachrichten an andere Sessions senden via send_agent_message; Ziel-Sessions starten automatisch ohne manuelles Eingreifen; die KI sieht alle aktiven Sessions mit Provider/Modell im System-Prompt

### Git-Client

- **Integrierte Git-Oberfläche** - Vollständiger visueller Git-Workflow direkt in der Anwendung
- **Commit-History** - Visueller Commit-Graph mit Branch- und Tag-Abzeichen, Autor, Datum und Subject
- **Issue-Tracker-Links** - Commit-Nachrichten zeigen anklickbare Links für Issue-Referenzen, die konfigurierbaren Mustern entsprechen (z.B. `#123`, `PROJ-456`); öffnet die Issue-Seite im Browser; Muster per Repository konfigurierbar über Repository-Einstellungen → Issue-Tracker-Tab; integrierte Vorlagen für GitHub, GitLab, JIRA u.v.m.
- **Anklickbare URLs** - HTTP(S)- und FTP-URLs in Commit-Nachrichten werden automatisch erkannt und öffnen sich beim Klick im Browser
- **Commit-SHA-Navigation** - SHA-Referenzen in Commit-Nachrichten sind anklickbar und navigieren zum referenzierten Commit im History-Graph
- **Inline-Code-Darstellung** - Backtick-Code-Spans in Commit-Nachrichten werden in Monospace-Schrift mit eigenem Hintergrund gerendert
- **Kontextmenüs auf Links** - Rechtsklick auf Links: Link kopieren, Im Browser öffnen, Zum Commit navigieren, SHA kopieren
- **Working Copy** - Dateien stagen/entstagen, Commit-Messages schreiben, Commit mit Sign-Off / No-Verify / Reset-Author Optionen
- **Diff-Ansicht** - Unified und Side-by-Side Diff mit TextMate-Syntax-Highlighting und Hunk-Level-Staging/Verwerfen
- **Stash** - Stashes erstellen, anwenden, poppen und löschen; Stash-Detailansicht mit Diff-Vorschau
- **Branches & Tags** - Visueller Branch-Baum, Branches erstellen/löschen/umbenennen/mergen/rebasen, Tags pushen/pullen
- **Remotes** - Fetch, Pull, Push, Remotes verwalten
- **Submodule & Worktrees** - Vollständige Unterstützung für Git-Submodule und Worktrees
- **GitFlow** - GitFlow-Workflow-Unterstützung (Init, Start, Finish für Feature/Release/Hotfix)
- **Datei-History & Blame** - Datei-spezifische Commit-History und Git-Blame-Ansicht
- **Interactive Rebase** - Visuelles Interactive Rebase mit Drag-and-Drop Commit-Sortierung
- **Branch-Beschreibungen** - Branch-Beschreibungen in Tooltips sichtbar
- **Bisect** - Gut/Schlecht-Markierungen pro Commit für binäre Suche bei der Fehlersuche
- **Farbige Status-Abzeichen** - Änderungszustände (Geändert, Hinzugefügt, Gelöscht, Umbenannt usw.) in der Working Copy und der Commit-Detailansicht werden als farbige, abgerundete Abzeichen statt als einfacher Text dargestellt
- **LFS-Dateioperationen** - Rechtsklick auf eine Datei in der Working Copy bietet LFS Track (nach Dateiname oder Erweiterung) sowie LFS Lock/Unlock; bei Repositories mit mehreren Remotes erscheint für Lock/Unlock ein Untermenü pro Remote
- **Befehlspalette** - Strg+Umschalt+P öffnet eine fuzzy-filterbare Palette mit 14 Schnellaktionen (Checkout, Merge, Compare, Blame, Datei-History, Datei öffnen, Branch erstellen, Tag erstellen, Fetch, Pull, Push, Stash, Patch anwenden, Konfigurieren); Befehle mit Branch-/Tag-/Dateiauswahl öffnen eine Unterpalette; Rücktaste bei leerem Filter kehrt zur Hauptpalette zurück; Escape oder Klick ausserhalb schliesst die Palette
- **GPG-Signaturprüfung** - Commits zeigen ein farbiges Schild-Badge (grün = gut, orange = abgelaufen/widerrufen, rot = schlecht) in der SHA-Zeile der Commit-Detailansicht; Hover zeigt Signer-Identität und Schlüssel-ID; GPG-Signierung pro Repository in Repository-Einstellungen konfigurierbar
- **Erweiterter Commit-Nachrichten-Editor** - AvaloniaEdit-basierter Editor mit Subject-Line-Guide (gestrichelte "SUBJECT END"-Linie), Subject-Zeichenzähler mit Warnung bei über 72 Zeichen, Spaltenpositions-Anzeige und Autovervollständigung für 13 Git-Trailer (Signed-off-by, Co-authored-by, etc.); Werkzeugleiste mit Commit-Vorlagen/Verlauf-Picker und Conventional-Commit-Builder
- **Externe Diff/Merge-Tools** - Externes Diff/Merge-Tool pro Repository konfigurierbar unter Repository-Einstellungen → Diff / Merge Tool Tab; 13 Tools unter Windows, 9 unter macOS, 9 unter Linux vorkonfiguriert (VS Code, Visual Studio, KDiff3, Beyond Compare, WinMerge, Meld u.v.m.); Aufruf über Kontextmenüs auf geänderten Dateien in Working Copy und Commit-Detail
- **Stash-Anwendung mit Optionen** - Rechtsklick auf einen Stash zum Anwenden oder Poppen mit Optionen: "Index wiederherstellen" (--index) stellt zuvor gestagede Änderungen wieder her, "Nach Anwendung löschen" kombiniert Anwenden + Löschen zu einer Pop-Operation
- **Multi-Branch-Merge** - Mehrere Branches in der Seitenleiste oder mehrere Commits in der History auswählen, dann alle gleichzeitig mergen mit Strategie-Auswahl (Standard, Octopus oder Ours) und optionalem Auto-Commit
- **Syntax-Highlighting für Revisions-Dateien** - Dateien, die bei einem bestimmten Commit im "Dateien"-Tab angezeigt werden, erhalten vollständiges TextMate-Syntax-Highlighting (konsistent mit der Diff-Ansicht)

### OPC UA Client

- **Direkte Verbindung** - Verbindung zu jedem OPC UA Server über Endpunkt-URL (z.B. `opc.tcp://192.168.0.1:4840`)
- **Auto-Erkennung** - Automatisches Erkennen von PLC OPC UA Endpunkten aus dem verbundenen TIA Portal-Projekt
- **Authentifizierungsmodi** - Anonym, Benutzername/Passwort und Zertifikatsbasierte Authentifizierung
- **Adressraum-Browser** - Vollständigen OPC UA Adressraum in einer Baumansicht mit Knotenklassen-Symbolen durchsuchen
- **Knotensuche** - Adressraum-Knoten nach Namen filtern, um Variablen schnell zu finden
- **Beobachtungstabelle** - Variablen per Doppelklick oder Drag-and-Drop hinzufügen; Name, Knoten-ID, Datentyp, Wert, Status und Zeitstempel pro Zeile anzeigen
- **Werte lesen** - Alle Beobachtungstabellen-Variablen mit einer einzigen Serveranfrage lesen oder einzelne Zeilen auf Anfrage
- **Werte schreiben** - Werte direkt in PLC-Variablen schreiben durch Bearbeitung von Beobachtungstabellen-Zellen
- **Live-Abonnements** - Wertänderungen mit konfigurierbarem Intervall (in Millisekunden) abonnieren; Werte aktualisieren sich automatisch ohne Polling
- **Variablen-spezifische Abonnements** - Bestimmte Zeilen unabhängig von der vollständigen Beobachtungstabelle abonnieren
- **Konfiguration speichern/laden** - Beobachtungstabellen-Konfigurationen (Endpunkt-URL + Variablenliste) als `.opcua-watch` JSON-Dateien speichern und wiederherstellen
- **CSV-Export** - Beobachtungstabellen-Daten mit allen Spalten (Name, Knoten-ID, Datentyp, Wert, Status, Zeitstempel) als CSV exportieren
- **JSON-Export** - Beobachtungstabellen-Daten als strukturiertes JSON mit vollständigen Metadaten exportieren
- **MCP-Integration** - Vereinheitlichtes `opcua`-Tool mit 9 Unterbefehlen für KI-Assistenten: connect, disconnect, browse, read, read_complex, write, write_complex, get_types, subscribe

### SCL Unit Testing (Enterprise)

Integriertes Unit-Test-Framework für SCL-Bausteine — schreiben, ausführen und auswerten ohne TIA Portal Test Suite. Erfordert PLCSIM Advanced V3.0+.

- **Test Explorer** — Baum aller Test-Suites im Projektordner `.tia-tests/`, automatisches Erkennen neuer/gelöschter/geänderter Dateien per FileSystemWatcher (500 ms Debounce)
- **Live-Status-Icons** — Jeder Test-Case zeigt seinen aktuellen Status während und nach der Ausführung: ✓ Bestanden, ✗ Fehlgeschlagen, ⊘ Übersprungen, ⚠ Fehler
- **Persistente Ergebnisse** — Letzte Test-Ergebnisse werden in SQLite gespeichert und erscheinen beim nächsten App-Start automatisch im Explorer
- **Kontext-Menü pro Suite** — Run Suite (Suite ausführen), Open (als Dokument-Tab öffnen)
- **Kontext-Menü pro Test-Case** — Run Test (einzelnen Test ausführen, via TestCaseFilter — restliche Cases werden als Skipped markiert)
- **Doppelklick auf Suite** — Öffnet die Suite als Dokument-Tab im Editor
- **Run All / Run Selected** — Batch-Ausführung mehrerer Suites sequentiell (PLCSIM-Einzelinstanz-Limitation)
- **Search-Filter** — Live-Textsuche in Suite- und Test-Case-Namen (case-insensitive Substring)
- **Nur-Fehler-Toggle** — Button `✗ Fehler` blendet alle bestandenen Suites aus und zeigt nur solche mit Fail/Error-Cases — nützlich bei großen Test-Historien
- **Live-Progress** — Während ein Test läuft werden Phase, aktueller Test-Case und Completed/Total-Zähler in Echtzeit angezeigt
- **Ergebnis-Detail-Grid** — Pro Test-Case werden alle Assertions mit Variable, Operator, Erwartet, Tatsächlich und Pass/Fail-Markierung dargestellt
- **Stop mid-run** — Laufende Test-Ausführung kann jederzeit abgebrochen werden
- **Automatische Block-Analyse** — Interface, Boundary-Werte und Dependencies werden mit einem Klick aus dem TIA-Projekt extrahiert
- **Dock-Layout** — Test Explorer, Analyse-Tools, Test-Editoren und Ergebnis-Panel sind frei verschiebbare Dock-Tools

### Problem-Meldung

Melde Bugs und schlage neue Funktionen vor, ohne die App zu verlassen. Der Help-Menü-Eintrag „Problem melden" öffnet einen Dialog, in dem du das Problem beschreibst; die App sammelt System-Informationen (App-Version, Betriebssystem, .NET-Runtime, aktive TIA-Portal-Version, Sprache, Lizenz-Tier) und aktuelle Logs und öffnet dann GitHub im Browser mit dem vorausgefüllten Issue. Kein GitHub-Login innerhalb der App nötig — die eigentliche Einreichung machst du selbst auf GitHub.

---

## Unterstützte TIA Portal Versionen

| Version | Status |
|---------|--------|
| TIA Portal V15 | Unterstützt |
| TIA Portal V16 | Unterstützt |
| TIA Portal V17 | Unterstützt |
| TIA Portal V18 | Vollständig unterstützt |
| TIA Portal V19 | Vollständig unterstützt |
| TIA Portal V20 | Vollständig unterstützt |
| TIA Portal V21 | Vollständig unterstützt |

---

## Unterstützte Block-Typen

### PLC-Bausteine
- **OB** - Organisationsbausteine (inkl. F_OB)
- **FB** - Funktionsbausteine (inkl. F_FB)
- **FC** - Funktionen (inkl. F_FC)
- **DB** - Datenbausteine (Global, Instanz, Array, inkl. F_DB)
- **UDT** - Benutzerdefinierte Datentypen
- **Tag Tables** - Variablentabellen
- **Technologieobjekte** - Motion Control, PID-Regler, Zähler, etc.
- **Software Units** - V18+ Software-Unit-Container

### HMI-Elemente
- **Bildschirme** - HMI-Bildschirme und Popups
- **Bildschirmvorlagen** - Wiederverwendbare Bildschirmvorlagen
- **HMI-Variablentabellen** - HMI-spezifische Variablentabellen
- **VB-Skripte** - VB-Skriptfunktionen
- **Verbindungen** - PLC/HMI-Verbindungen
- **Textlisten** - Mehrsprachige Textlisten
- **Grafiklisten** - Grafik-/Symbollisten

### Hardware
- **Gerätekonfiguration** - Hardware-Setup als AML/XML

---

## Lizenz-Optionen

### Basic (KOSTENLOS)
- **Für immer gratis** - Keine Testphase, kein Ablauf
- 1 Datei Export/Import pro Vorgang
- Block Compare
- Code Editor
- Hardware Overview

### Professional (CHF 9.99/Monat oder CHF 99.99/Jahr)
- **1.000 Dateien** Export/Import pro Vorgang
- **Jahresabo spart 17%** (2 Monate gratis)
- Alles aus Basic, plus:
- Find Unused Blocks
- Safety Block Support (F_FB, F_FC, F_DB, F_OB)
- Protection Profiles
- MCP Server Integration
- Priority Support

### Enterprise (CHF 29.99/Monat oder CHF 299.99/Jahr)
- **Unbegrenzte Dateien**
- **Jahresabo spart 17%** (2 Monate gratis)
- Alles aus Professional
- Multi-User Lizenzen
- Dedizierter Support
- Mengenrabatte

### Testphase
- **30-tägige kostenlose Testphase** mit allen Enterprise-Funktionen
- Keine Kreditkarte erforderlich
- Nach 30 Tagen Rückfall auf Basic (kostenlos)

---

## Aktivierung

### Online-Aktivierung
1. Subscription kaufen unter: https://www.tiaopenessmanager.ch
2. Aktivierungscode per E-Mail erhalten (Format: `ACT-XXXX-XXXX-XXXX`)
3. Code im Programm eingeben unter **View → Settings → Manage License**
4. Lizenz ist an Ihre Hardware gebunden

### Subscription verwalten
- Klicken Sie auf "Manage Subscription" im License-Dialog
- Öffnet das Stripe-Portal für Zahlungen, Rechnungen und Kündigung

---

- **Mehrsprachig** - Deutsch, Englisch, Französisch, Italienisch

---

## Haftungsausschluss

Die Software wird „as is" geliefert. Der Anbieter übernimmt keine Haftung für Schäden, die durch die Nutzung entstehen. Der Anwender trägt die volle Verantwortung für die Prüfung aller generierten Inhalte. Siehe EULA auf https://www.tiaopenessmanager.ch

---

**Kontakt:** Für Fragen kontaktieren Sie uns unter [tiaopenessmanager@outlook.com]

**© 2025-2026 AnyAutomation. Alle Rechte vorbehalten.**
