# TIA Openness Manager - Feature-Übersicht

## Produktbeschreibung

Der **TIA Openness Manager** ist ein leistungsstarkes Werkzeug für Siemens TIA Portal Entwickler, das den Export, Import und die Verwaltung von SPS-Programmbausteinen revolutioniert. Mit einer intuitiven Benutzeroberfläche und fortschrittlichen Funktionen wie Differenzvergleich, Schutzprofilen und KI-Integration steigert es die Produktivität und reduziert Fehler bei der Projektverwaltung erheblich.

---

## Hauptfeatures

### Willkommen-Tab

- **Willkommen-Tab** — Interaktive Einführung mit „Erste Schritte"-Anleitung und Schnellzugriff-Aktionen.
- **„Erste Schritte"-Anleitung** - Vier Schritte (Verbinden, Project-Explorer-Grundlagen, Exportieren, Nächsten Bereich wählen), die sich während der Nutzung automatisch abhaken
- **Sieben Schnellzugriff-Aktionen** - Verbinden, Projekt öffnen, Export-Ordner wählen, Git-Repository klonen, Neue SCL-Datei, Unit Testing, KI-Assistent konfigurieren
- **Feature-Karten** - Ein-Klick-Sprung zu KI-Chat, Git, Unit Testing, OPC UA und zum „Was ist neu"-Changelog
- **Zuletzt geöffnete Projekte** - Bis zu fünf neueste Einträge, aktualisiert nach jedem erfolgreichen Verbindungsaufbau (Datei öffnen oder anhängen); Klick stellt die Verbindung direkt wieder her, fehlende Dateien werden automatisch ausgeblendet
- **Jederzeit wieder öffnen** - Hilfe → Willkommen-Guide öffnet den Tab unabhängig von der Startup-Einstellung

### Import & Export

- **Export Selected** - Nur angehakte Blöcke, Datentypen, Variablentabellen, Technologie-Objekte oder Software-Unit-Einträge exportieren. Bestehende Dateien mit gleichem Namen werden überschrieben; andere Dateien im Export-Ordner bleiben erhalten
- **Export All** - Vollständiger Projekt-Export; der SPS-Export-Ordner wird zuerst geleert, danach werden alle Blöcke, Datentypen, Variablentabellen, Technologie-Objekte und Software-Units neu geschrieben
- **XML & SCL Support** - Vollständige Unterstützung für Simatic ML und SCL-Dateien
- **S7DCL Export (V20+)** - Zusätzliches textbasiertes Export-Format (.s7dcl) für bessere Versionskontrolle
- **Ordnerstruktur-Erhaltung** - Die TIA Portal Ordnerstruktur wird beibehalten
- **Automatische Kompilierung** - Kompiliert und speichert automatisch nach Import
- **Konfigurierbare Ordnernamen** - Passen Sie Export-Ordnernamen an (Source, Blocks, Tags, etc.)
- **Optionaler Source-Ordner** - Source-Ordner im Export aktivieren/deaktivieren
- **Import Selected** - Zielgerichteter Import; nur angehakte Dateien werden geschrieben. Bestehende Blöcke mit gleichem Namen werden überschrieben, der Rest der SPS bleibt unverändert
- **Import All** - Vollständiger Projekt-Reimport; alle bestehenden Blöcke, Datentypen und Variablentabellen werden zuerst gelöscht, danach wird alles aus dem Working Directory importiert. Im Schutzprofil markierte Blöcke bleiben erhalten

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

- **Projektweiter Scan** - Kompiliert zuerst die SPS, dann Vergleich von TIA-Portal-Fingerprints und Datei-Hashes gegen den gespeicherten Stand vom letzten Export
- **Funktioniert beim ersten Klick** - Kein vorheriger Export erforderlich; beim ersten Lauf baut die Anwendung still eine Baseline auf, indem sie die SPS temporär exportiert, und schaltet danach für alle Folge-Vergleiche auf den schnellen Pfad um
- **Änderungserkennung** - Erkennt geänderte, neue und gelöschte Blöcke in fünf Kategorien (Geändert / Nur in TIA / Nur auf Platte / Unverändert / Inkonsistent)
- **Block-Icons in der Dateiliste** - Jede Zeile zeigt das passende Block-Icon (FC / FB / OB / DB, mit Safety-Varianten), konsistent zum Projektbaum
- **Symmetrische Links/Rechts-Dateilisten** - TIA-Seite und Disk-Seite haben jeweils eine eigene Dateiliste mit eigenem Ein-/Ausblenden-Toggle; geänderte Blöcke erscheinen in beiden Listen, nur-in-TIA und inkonsistent nur links, nur-auf-Platte nur rechts
- **Farbstreifen pro Zeile** - Ein schmaler farbiger Balken am rechten Rand jeder Dateizeile signalisiert den Änderungstyp auf einen Blick: Grün für Hinzugefügt, Rot für Gelöscht, Orange für Geändert, Gelb für Inkonsistent, Blau für Nur in TIA
- **Detaillierter Diff-Viewer** - Zeigt Unterschiede Zeile für Zeile
- **Selektiver Re-Import** - Haken Sie die Blöcke an, die Sie in die SPS zurückschreiben möchten; transaktional, Rollback bei jedem Fehler

### Ad-hoc Compare (Drag and Drop)

- **Blöcke ins Compare-Panel ziehen** - Der Block wird kompiliert und mit denselben Strip-Einstellungen exportiert wie bei "Export Selected"; sowohl XML- als auch Source-Code-Formate (SCL, DB) erscheinen als eigene Zeilen
- **Unabhängige linke und rechte Drop-Ziele** - Blöcke und Dateien lassen sich auf beiden Seiten ablegen; das Item landet auf der Hälfte, auf die Sie droppen, und weitere Drops hängen an statt die Seite zu ersetzen
- **Resizebare Dateiliste** - Splitter zwischen Dateiliste und Diff-Editor zieht zwischen 180 und 500 Pixel; Breite wird über Anzeigen/Ausblenden hinweg gemerkt

### Diff-Editor

- **Syntax-Highlighting** - SCL, AWL, DB, XML und weitere Sprachen werden anhand der Dateiendung erkannt
- **Side-by-side und Unified** - Layout in der Toolbar umschaltbar
- **Änderungsnavigation** - Erste / Vorherige / Nächste / Letzte Änderung mit `1/N`-Zähler
- **Kontextzeilen-Collapse** - Unveränderte Bereiche hinter einem Hunk-Header einklappen; Kontextbreite mit `+=`/`-=` anpassen oder die ganze Datei aufklappen
- **Edit-Modus** - Eine Seite entsperren und direkt bearbeiten; per Klick zurück in Datei oder SPS speichern
- **Diff-Optionen** - Whitespace ignorieren, verborgene Zeichen anzeigen, Zeilenumbruch ein/aus

### Code-Editor

Der integrierte Code-Editor bietet professionelle Bearbeitungsfunktionen für SCL und andere Dateitypen.

- **Split View** — Editoren horizontal oder vertikal teilen, Tabs zwischen Gruppen ziehen, Panels andocken und anheften (Dateibaum, Markdown-Vorschau)
- **Drag & Drop aus dem Project Explorer** — Einen oder mehrere Bausteine bzw. Offline-Quelldateien auf den Editor oder Welcome-Tab ziehen; jedes Objekt öffnet sich als eigener Editor-Tab
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

### Im Projekt suchen (Cross-Reference-Suche)

- **Projekt-weite Referenzsuche** - Eine Suchbox findet jede Block-, Tag- und UDT-Referenz im offenen TIA-Projekt
- **Hotkey + Rechtsklick** - `Strg+Umschalt+F` öffnet den Tab von überall, oder rechtsklicke einen Baustein im Project-Tree und wähle "Referenzen suchen"
- **Doppelklick zum Springen** - Doppelklick auf ein Ergebnis öffnet den Quell-Baustein im SCL-Editor mit Cursor auf der passenden Zeile
- **Rechtsklick-Menü** - Rechtsklick auf eine Trefferzeile für **Im Editor öffnen** oder **Referenzpfad kopieren** in die Zwischenablage
- **Definitionen-Gruppe** - Wenn der Suchbegriff einem Bausteinnamen entspricht, erscheint dieser Baustein als eigene Gruppe oben im Ergebnis-Baum
- **Diakritik-unabhängig** - `förder` findet `Förder_DB`; funktioniert für alle deutschen Umlaute und `ß`
- **Scope-Filter** - Einschränken auf Bausteine, Tags, UDTs oder Alle durchsuchen
- **PLC-Filter** - Optional auf eine einzelne PLC in Multi-PLC-Projekten beschränken
- **Determiniertes Fortschritt** - Fortschrittsbalken zeigt aktueller Kandidat / Gesamtkandidaten während des Scans
- **Ergebnis-Cache** - Identische Suche innerhalb von 30 Sekunden liefert sofort ohne Bridge-Roundtrip
- **Cancel-freundlich** - Jeder Tastendruck cancelt den laufenden Scan via 250 ms Debounce
- **Live-Sprachwechsel** - Scope-Labels und Gruppen-Headlines aktualisieren sich sofort beim Sprachwechsel
- **Ergebnis-Cap** - Harte Obergrenze 2000 Treffer mit "Suche eingrenzen"-Banner bei Erreichen
- **Benötigt TIA Portal V18 oder neuer** - Frühere Versionen zeigen erklärende Meldung im Fehler-Footer

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

- **Live-Session-Indikator** - Statusleiste zeigt `MCP: <n>` aktiver Proxy-Mode-KI-Client-Verbindungen; Klick öffnet Sessions-Dialog mit Client-Details und integrierter Setup-Anleitung (Claude Desktop, Claude Code, LM Studio, Continue.dev) mit Copy-fertigen Snippets
- **Model Context Protocol** - Integration mit jedem MCP-kompatiblen KI-Assistenten
- **Projekt-Kontext** - KI hat Zugriff auf Ihre Projektstruktur
- **Code-Generierung** - KI kann SCL-Quellcode für Bausteine generieren
- **DB-Generierung** - KI kann Datenbausteine mit Simatic ML-Vorlagen erstellen
- **UDT-Generierung** - KI kann benutzerdefinierte Datentypen erstellen
- **Variablentabellen-Generierung** - KI kann Variablentabellen erstellen
- **Auto-Import** - Generierter Code kann automatisch in TIA Portal importiert werden
- **Block-Analyse** - KI kann bestehende Bausteine lesen und analysieren

### KI-Chat

- **Reasoning-Aufwand** - Legen Sie pro Agent fest, wie intensiv Deep-Thinking-Modelle vor der Antwort nachdenken (Niedrig / Mittel / Hoch). Über das Gehirn-Chip in der Composer-Bar oder unter Einstellungen → Agents → Capabilities jederzeit umschaltbar.
- **Anbieter-Tab** - Agent-übergreifende Anbieter-Konsole in den AI-Chat-Einstellungen. GitHub-Copilot-Karte zeigt Anmeldestatus, Enterprise-Domains, Reasoning-Modell-Policy und Retry-/Verify-Schaltflächen. Platzhalter-Karten verweisen auf den Modell-Browser.
- **Sprachmodelle verwalten** - Provider-übergreifender Modellkatalog hinter dem Zahnrad in der Composer-Bar. Kombiniert den GitHub-Copilot-Katalog, die OAuth-Kataloge (OpenAI Codex, Google Gemini CLI, Antigravity), eine live abgefragte Liste für jeden API-Key-Agent (Anthropic, OpenAI, OpenRouter, Mistral, XAI, Groq, Cerebras, DeepSeek, Perplexity, Together, HuggingFace, Ollama, LM Studio und mehr) sowie die statischen AWS-Bedrock-Zeilen. Eine Copilot-spezifische Spalte **Richtlinie** zeigt Aktiviert / Fehlgeschlagen / Admin-verwaltet pro Modell mit Rechtsklick-Aktion **Copilot-Modellrichtlinie erneut anwenden** bei fehlgeschlagenen Zeilen. Azure-OpenAI-Agents können mehrere Deployments pro Agent registrieren, jedes davon erscheint als eigene Zeile. Die Statuszeile zeigt die Live-Zählung; **Aktualisieren** invalidiert den 5-Minuten-Cache. Rechtsklick oder **Für aktiven Agent verwenden** setzt das Modell in einem Schritt.
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
- **Transparenz bei Tool-Aufrufen** - Jeder KI-Tool-Aufruf im Chat zeigt Operation und Ziel auf einen Blick (z. B. *„Lesen (src/main.cs · Zeilen 1-50)"*, *„Git Status"*); abgeschlossene Aufrufe erhalten einen grünen Haken mit kurzer Zusammenfassung, Fehler ein rotes X, und abgelehnte Freigaben ein gelbes Schild — so wissen Sie immer, was der Assistent getan hat, ohne die Zeile aufklappen zu müssen
- **Berechtigungsmodi** - Toggle-Button neben dem Senden-Button wählt durch, wie Schreiboperationen genehmigt werden: **Standard** fragt bei jeder Schreiboperation, **Änderungen akzeptieren** genehmigt Datei-Edits automatisch, fragt aber weiterhin bei Shell-Befehlen und destruktiven Operationen wie Löschen oder Force-Push, **Auto** genehmigt alles außer gefährlichen Operationen (PowerShell, Prozesszugriff, Netzwerk-Schreiboperationen); der aktuelle Modus wird durch ein farbiges Icon und einen Tooltip angezeigt; der Planmodus ist ein separater Toggle, der die KI zwingt, einen genehmigten Plan einzureichen, bevor Schreiboperationen möglich sind
- **Inline Plan-Genehmigung** - Wenn die KI einen Ausführungsplan einreicht, erscheint dieser als editierbares Textfeld direkt im Chat mit Genehmigen- und Ablehnen-Buttons; der Plan kann vor der Genehmigung bearbeitet werden; nicht-blockierend — während der Prüfung kann durch die Historie gescrollt oder zwischen Tabs gewechselt werden
- **Befehlswarteschlange** - Nachrichten senden waehrend der KI-Agent arbeitet; Nachrichten werden mit Prioritaetsstufen (Jetzt/Naechstes/Spaeter) in eine Warteschlange gestellt und nach jedem Turn automatisch verarbeitet; Warteschlangen-Anzeige zeigt die Anzahl ausstehender Nachrichten; ESC bricht die aktuelle Operation ab und leert die Warteschlange, oder holt wartende Nachrichten zurueck ins Eingabefeld wenn der Agent untaetig ist
- **Multi-Session** - Mehrere KI-Chat-Sessions gleichzeitig ausfuehren; die Agent-Sidebar (umschaltbar ueber PanelLeftOpen/PanelLeftClose-Icon) gleitet als Overlay von links heraus und zeigt alle Sessions gruppiert nach Status (In Bearbeitung / Abgeschlossen); jede Session hat eigenen Chat-Kontext, Canvas und Agent/Provider; Subagenten werden automatisch ihrer Eltern-Session zugeordnet; Ungelesene-Nachrichten-Badges mit Blink-Animation zeigen Aktivitaet in anderen Sessions; Doppelklick auf Session-Name zum Umbenennen; Sessions schliessen ueber X-Button (mit Bestaetigung wenn noch aktiv); Canvas-State wird pro Session gespeichert und beim Wechsel wiederhergestellt; Live-Vorschau unter dem Session-Namen zeigt eingehende Nachrichten und Antworten aus anderen Sessions
- **Agent pro Session** - Jede Session merkt sich ihre Agent/Provider/Modell-Auswahl unabhaengig; in einer Session einen anderen Provider waehlen ohne andere Sessions zu beeinflussen; der Agent wechselt automatisch beim Session-Wechsel
- **Cross-Session-Kommunikation** - Agents koennen Nachrichten an andere Sessions senden via send_agent_message; Ziel-Sessions starten automatisch ohne manuelles Eingreifen; die KI sieht alle aktiven Sessions mit Provider/Modell im System-Prompt
- **Workspace-Dateisystem-Zugriffsschutz** - Das `fs`-Tool der KI (lesen/schreiben/erstellen/bearbeiten/loeschen/auflisten/suchen) wird durch eine 5-Schichten-Richtlinie plus fest eingebaute Blocklist geschuetzt. Das aktuelle TIA-Projektverzeichnis sowie Desktop/Dokumente/Temp sind automatisch erlaubt. Weitere Ordner werden ueber **KI-Chat-Einstellungen → Workspace** dauerhaft hinzugefuegt. Pfade ausserhalb des Bereichs loesen einen Inline-Dialog aus mit **Einmalig erlauben / Diese Sitzung erlauben / Dauerhaft erlauben / Ablehnen**; dauerhafte Genehmigungen zeigen das genaue Verzeichnis das persistiert wird. Vault, Lizenz, Chat-Datenbank, Agent-Memory, App-Einstellungen, SSH/AWS/Azure/Kubernetes-Anmeldedaten, Windows/Program Files/AppData-Interna, Browser- und OS-Sperrdateien werden immer abgewiesen — auch wenn die KI sie ueber ein zuvor erlaubtes Eltern-Verzeichnis anfordert. Symbolische Links und Junctions werden vor der Blocklist-Pruefung aufgeloest, sodass Reparse-Points die Sperre nicht umgehen koennen. UNC-Pfade, `\\?\`, `\\.\` Device-Paths werden grundsaetzlich abgewiesen.

### Git-Client

- **Integrierte Git-Oberfläche** - Vollständiger visueller Git-Workflow direkt in der Anwendung
- **Activity-Bar-Badge** - Git-Icon zeigt einen Count-Badge für nicht-committete Änderungen summiert über alle offenen Repository-Tabs; kompaktes Format bis 99K+; Tooltip nennt den Count mit korrekter Plural-Form pro UI-Sprache; Badge ausgeblendet bei null
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
- **Stash-Diff-Toolbar** - Diff-Bereich der Stash-Ansicht trägt Toggles für „Whitespace ignorieren" und „Side-by-Side"; rapid clickende Toggles brechen den laufenden Reload ab und starten einen neuen, last-toggle-wins
- **Multi-Branch-Merge** - Mehrere Branches in der Seitenleiste oder mehrere Commits in der History auswählen, dann alle gleichzeitig mergen mit Strategie-Auswahl (Standard, Octopus oder Ours) und optionalem Auto-Commit
- **Syntax-Highlighting für Revisions-Dateien** - Dateien, die bei einem bestimmten Commit im "Dateien"-Tab angezeigt werden, erhalten vollständiges TextMate-Syntax-Highlighting (konsistent mit der Diff-Ansicht)
- **Lokales Repository öffnen (Strg+Umschalt+O)** - Eigenes Popup nimmt Pfad, Ziel-Workspace und Bookmark-Gruppe in einem Schritt entgegen; das Repository wird bei Erfolg direkt der gewählten Gruppe zugeordnet, ohne separaten Edit-Schritt
- **Submodul-Vergleichsfenster** - „Details öffnen" auf einem Submodul-Pointer-Wechsel öffnet ein schreibgeschütztes Vergleichsfenster mit zwei CommitDetail-Panes (alter und neuer Submodul-Commit) und einer zentralen Diff-Ansicht, die Text-, Binary-, verschachtelte Submodul- und Git-LFS-Payload-Änderungen zwischen den beiden Pointern abbildet
- **Submodul-Badge bei nicht committeten Änderungen** - Jedes Submodul in der Sidebar zeigt ein Inline-Badge, sobald das Submodul selbst lokale, nicht committete Änderungen hat; Wert entspricht dem trailing `+` aus `git submodule status`
- **Klonen mit Gruppe + Bookmark** - Das Klon-Popup bietet beim Klonen die Auswahl einer Workspace-Gruppe und einer Bookmark-Farbe; das geklonte Repository landet bei Erfolg direkt unter der gewählten Gruppe mit dem ausgewählten Bookmark — ohne separaten Edit-Schritt
- **Custom-Action-Argument-Format** - Custom Actions verwenden einen frei wählbaren Argument-Format-String mit Substitution für `${REPO}`, `${BRANCH}`, `${BRANCH_FRIENDLY_NAME}`, `${SHA}`, `${FILE}`, `${REMOTE}` und `${TAG}`; ein neuer Branch-Selector-Control-Typ befüllt `${BRANCH}` / `${BRANCH_FRIENDLY_NAME}` mit Modi für lokale und Remote-Tracking-Branches
- **Globaler Auto-Fetch** - Hintergrund-Auto-Fetch ist jetzt eine einzige globale Einstellung unter Einstellungen → Git → Auto-Fetch und gilt für alle offenen Repositories (ersetzt das frühere Per-Repository-Toggle); das Intervall (Default 10 Minuten) wird im selben Settings-Block konfiguriert

### OPC UA Client

- **Direkte Verbindung** - Verbindung zu jedem OPC UA Server über Endpunkt-URL (z.B. `opc.tcp://192.168.0.1:4840`)
- **Auto-Erkennung** - Automatisches Erkennen von PLC OPC UA Endpunkten aus dem verbundenen TIA Portal-Projekt
- **Authentifizierungsmodi** - Anonym, Benutzername/Passwort und Zertifikatsbasierte Authentifizierung
- **Dockbares Arbeitsbereichs-Layout** - Adressraum-Browser, Knoteninformationen, Referenzen, Struktur-Felder und Beobachtungstabelle liegen jeweils in einem eigenen dockbaren Panel, das per Drag-Griff am Titelbalken abgedockt, angepinnt, umsortiert oder gestapelt werden kann
- **Adressraum-Browser** - Vollständigen OPC UA Adressraum in einer Baumansicht mit Knotenklassen-Symbolen durchsuchen
- **Knoten aktualisieren** - Aktualisieren-Schaltfläche in der Werkzeugleiste lädt die Kinder des ausgewählten Knotens direkt vom Server neu und umgeht den lokalen Cache, um serverseitige Änderungen seit dem letzten Erweitern aufzugreifen
- **Knotensuche** - Adressraum-Knoten nach Namen filtern, um Variablen schnell zu finden
- **Knoteninformationen-Panel** - Beim Auswählen eines Knotens werden alle OPC UA-Attribute angezeigt: Node Id, Browse Name, Display Name, Node Class, Description, Write-/User-Write-Masks und bei Variablen zusätzlich Data Type, Value Rank, Array Dimensions, Access Level, User Access Level, Minimum Sampling Interval, Historizing, aktueller Value, Status Code sowie Source- und Server-Timestamp (entspricht UaExpert)
- **Referenzen-Panel** - Eigenes Panel mit jeder eingehenden und ausgehenden Referenz des ausgewählten Knotens, Spalten Richtung, Referenztyp, Browse-Name, Knotenklasse und Ziel-Knoten-ID
- **Ereignisprotokoll-Panel** - OPC-UA-Ereignisse von einem Notifier-Knoten abonnieren und live in einer Zeit / Schweregrad / Quelle / Ereignistyp / Meldung-Tabelle empfangen; Schweregrad-Filter, CSV-Export mit Formel-Injektions-Schutz und 5000-Einträge-FIFO-Ring mit begrenzter UI-Dispatch-Queue bei Ereignisfluten
- **Verlaufsdiagramm-Panel** - Historische Rohwerte eines Variablenknotens über einen Zeitbereich laden und in einem Streudiagramm mit Datum/Uhrzeit-X-Achse darstellen; Schnellauswahl 1h / 6h / 24h / 7T, Kalender-Pickers für eigene Zeitbereiche, CSV-Export und sichere Behandlung von ungültigen Zeitstempeln, nicht-numerischen Werten und bösartigen Server-Payloads
- **Server-Diagnose-Panel** - Live-Anzeige der standardisierten OPC-UA-Server-Object-Hierarchie (Server-Status, Fähigkeiten, Diagnose-Zähler, aktive Subscriptions, aktive Sessions) mit konfigurierbarem Poll-Intervall 1–60 s pro Verbindung gespeichert; Server, die den Diagnose-Subtree nicht freigeben, zeigen statt leerer Tabellen einen "Nicht bereitgestellt"-Hinweis, vorübergehende Ausfälle erscheinen im Inline-Fehlerstreifen, und ein Exponential-Backoff verhindert das Belasten eines angeschlagenen Servers
- **Auto-Reconnect-Banner** - Wenn der Keep-Alive-Watchdog eine verlorene Verbindung erkennt, zählt ein gelbes Banner im Verbindungs-Header die Reconnect-Zeit live mit und bietet einen Abbrechen-Button, der den Versuch sofort beendet — kein Warten auf den 5-Minuten-Timeout
- **Letzte-Endpunkte-Dropdown** - Das Endpunkt-URL-Feld ist eine Autocomplete-Liste der letzten 10 erfolgreichen Verbindungen (pro Installation, übersteht Neustart); URL-Varianten, die auf dasselbe Schema + Host + Port auflösen, werden zu einem Eintrag zusammengeführt statt doppelt geführt
- **Tastenkürzel** - Strg+Eingabe Verbinden, Strg+D Trennen, F5 Markierten Knoten neu lesen, Strg+W Aktuell markierte Watch-Table-Zeile schreiben — alle im OPC-UA-Tab gebunden und an die aktive Verbindung geroutet
- **NodeId kopieren / Browse-Pfad kopieren** - Rechtsklick auf einen Knoten im Adressraum kopiert wahlweise die kanonische NodeId oder den lesbaren Browse-Pfad in die Zwischenablage
- **Ansichts-Menü** - Eintrag in der OPC-UA-Toolbar, der jeden geschlossenen Tool-Reiter wiederöffnet (Adressraum, Typdefinitionen, Knotenattribute, Referenzen, Strukturfelder, CPU-Schutz, Beobachtungstabelle, Ereignisprotokoll, Verlauf, Serverdiagnose), ohne den Workspace zurücksetzen zu müssen
- **Methodenaufruf-Dialog** - Rechtsklick auf einen Methodenknoten im Adressraum-Browser öffnet einen modalen Dialog mit Ein- und Ausgabeargumenten, typspezifischen Eingabefeldern (Skalar-Textboxen, Array-Zeilen-Editor), führt den Aufruf aus und zeigt die zurückgegebenen Werte und Status; Dialog schließen bricht einen noch laufenden Aufruf ab
- **Zertifikatsverwaltung-Dialog** - Eigenes Client-Zertifikat sowie alle vertrauten und abgelehnten Server-Zertifikate in einem modalen Drei-Tab-Dialog (Eigenes / Vertrauenswürdig / Abgelehnt) prüfen; ausstehende Server-Zertifikate vertrauen, bisher vertraute ablehnen, obsolete Einträge entfernen oder das Client-Zertifikat neu erstellen. Der zugehörige Schalter „Serverzertifikate automatisch akzeptieren" im OPC UA Einstellungen-Flyout schaltet zwischen automatischem Vertrauen (Default) und manueller Freigabe pro Server
- **Matrix-Editor-Dialog** - Rechtsklick auf eine matrix-typisierte Variable im Adressraum-Browser öffnet einen tabellenartigen Editor mit Zeilen- und Spaltenüberschriften; Zellen einzeln bearbeiten, geänderte Zellen werden markiert und die gesamte Matrix wird mit einem Schreibvorgang zurück zum Server gesendet. Schreibgeschützte Matrizen bleiben sichtbar, der Speichern-Button wird deaktiviert; Matrizen mit mehr als zwei Dimensionen melden einen klaren „Rang nicht unterstützt"-Fehler statt die Daten still zu flatten
- **Struktur-Felder-Panel** - Komplexe Struct-/UDT-Werte lesen und bearbeiten mit verschachtelter Ein-/Ausklappen-Ansicht, Per-Index-Array-Zeilen und Dirty-Feld-Rückschreiben
- **Beobachtungstabelle** - Variablen per Doppelklick oder Drag-and-Drop hinzufügen; Name, Knoten-ID, Datentyp, Wert, Status und Zeitstempel pro Zeile anzeigen
- **Werte lesen** - Alle Beobachtungstabellen-Variablen mit einer einzigen Serveranfrage lesen oder einzelne Zeilen auf Anfrage
- **Werte schreiben** - Werte direkt in PLC-Variablen schreiben durch Bearbeitung von Beobachtungstabellen-Zellen
- **Live-Abonnements** - Wertänderungen mit konfigurierbarem Intervall (in Millisekunden) abonnieren; Werte aktualisieren sich automatisch ohne Polling
- **Variablen-spezifische Abonnements** - Bestimmte Zeilen unabhängig von der vollständigen Beobachtungstabelle abonnieren
- **Konfiguration speichern/laden** - Beobachtungstabellen-Konfigurationen (Endpunkt-URL + Variablenliste) als `.opcua-watch` JSON-Dateien speichern und wiederherstellen
- **Arbeitsbereichs-Persistenz** - Der gesamte OPC UA-Arbeitsbereich (Panel-Layout + offene Verbindungen + Beobachtungstabelle) wird beim nächsten App-Start automatisch wiederhergestellt. Jeder geöffnete Verbindungstab behält seine eigenen Beobachtungen, Abonnements, Ereignisfilter und Verlaufsbereiche — nicht nur der aktive Tab. Ein **Diese Verbindung nicht im Arbeitsbereich speichern**-Toggle pro Tab im Settings-Flyout der Verbindung schliesst einen Tab bei Bedarf aus der Workspace-Datei und dem automatischen Wiederherstellen aus, wenn ein Endpoint privat bleiben soll. Ein **Arbeitsbereich**-Menü in der Dock-Toolbar bietet **Arbeitsbereich speichern unter…**, **Arbeitsbereich laden…** (akzeptiert sowohl neue `.opcua-workspace`- als auch alte `.json`-Watch-Dateien) und **Arbeitsbereich zurücksetzen**. Passwörter wandern nie in die Workspace-Datei — Bediener geben sie beim erneuten Verbinden neu ein
  - Fensteranordnung, Splitter-Positionen und frei bewegte / angeheftete Tool-Fenster bleiben beim Speichern/Laden erhalten.
- **CSV-Export** - Beobachtungstabellen-Daten mit allen Spalten (Name, Knoten-ID, Datentyp, Wert, Status, Zeitstempel) als CSV exportieren
- **JSON-Export** - Beobachtungstabellen-Daten als strukturiertes JSON mit vollständigen Metadaten exportieren
- **MCP-Integration** - Vereinheitlichtes `opcua`-Tool mit 9 Unterbefehlen für KI-Assistenten: connect, disconnect, browse, read, read_complex, write, write_complex, get_types, subscribe

### S7 Nativ (S7 Comm+)

- **Direkte S7-Comm+-Verbindung** - TLS-1.3-gesicherter nativer S7-Protokollzugriff auf S7-1200 (FW ≥ 4.3) und S7-1500 (FW ≥ 2.9) ohne OPC UA
- **Authentifizierung** - Legacy-Passwort und TLS-Benutzer/Passwort über den eingebauten Treiber
- **Symbolisches Browsing** - Alle Block-Typen (DB/FB/FC/OB) mit Tag-/UDT-Expansion; absolute Adressen (I0.0, MW10, QD20) über manuellen Adress-Dialog
- **TIA-Tag-Import** - PLC-Tags aus dem aktiven TIA-Portal-Projekt als "PLC Tags"-Baumknoten importieren; IP-basiertes PLC-Matching
- **Live-Beobachtungstabelle** - Native S7-Comm+-Subscriptions pushen Wertänderungen mit konfigurierbarer Zykluszeit; der alte Timer-Polling-Pfad ist entfernt
- **Verbindungsstatus-Punkt** - Ein farbiger Punkt im Tab-Header zeigt den SPS-Zustand live an (grau = nicht verbunden, grün = läuft, gelb = angehalten oder wird wiederverbunden, rot = nicht erreichbar) mit einem Hover-Tooltip
- **Automatische Wiederverbindung mit sichtbarem Fortschritt** - Ein "Wiederverbinde…"-Banner erscheint unter der Verbindungsleiste, während die App eine unterbrochene Verbindung wiederherstellt; Werte in der Beobachtungstabelle werden auf halbe Deckkraft gedimmt und auf `???` umgestellt, bis frische Werte ankommen; die gesamte Recovery läuft im Hintergrund
- **SPS-Explorer-Seitenleiste** - Eine persistente Liste bekannter SPSen in einem eigenen Aktivitätsleisten-Workspace; jeder Eintrag zeigt einen Live-Erreichbarkeitspunkt aus aktiven Sessions und einem 10-Sekunden-TCP-Check auf Port 102 plus den Zeitstempel der letzten Erreichbarkeit; SPSen über Dialoge hinzufügen, umbenennen und entfernen; Doppelklick öffnet oder fokussiert den PLC-Online-Tab mit bereits ausgefüllter IP und Protokoll; die Liste wird zwischen Sessions gespeichert
- **CPU-Schutz-Kachel** - Rechte-Dock-Tab zeigt die aktuelle Schutzstufe (Kein/Lese/Schreib/Voll) und das Passwort-Erforderlich-Flag der verbundenen S7-1500 / S7-1500F-CPU; aktualisiert sich nach jedem Connect einmal automatisch
- **Diagnosepuffer-Kachel** - Rechte-Dock-Tab listet die letzten CPU-Diagnoseereignisse (Zeitstempel / Ereignis-ID / Klasse / Priorität / OB) aus der SSL-Teilliste `0xA0`; Firmware-Gate auf V3.0+ — auf älteren CPUs erscheint statt einer Log-Spam-Schleife eine klare Firmware-Meldung
- **CPU-Identität-Kachel** - Rechte-Dock-Tab zeigt MLFB, Bestellnummer, Seriennummer, Hardware- und Firmware-Stand aus dem PROFINET-I&M0-Datensatz; funktioniert auf V2.x und V3.0+
- **Speicherauslastung-Kachel** - Rechte-Dock-Tab zeigt live die Lade-/Arbeits-/Remanenzspeicher-Auslastung (belegt vs. gesamt in Megabyte plus 0–100 %-Fortschrittsbalken); aktualisiert sich nach jedem Connect einmal automatisch

### Unit Testing (Enterprise)

Integriertes Unit-Test-Framework für TIA-Bausteine — schreiben, ausführen und auswerten ohne TIA Portal Test Suite. Erfordert PLCSIM Advanced V3.0+.

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
- **Mehrstufige Test-Schritte** — Optionales `act.steps`-Array für `write` / `wait` / `assert`-Sequenzen direkt im Case (z.B. *Reset → 500 ms warten → Start → 2 s warten → prüfen*). Visual-Editor bietet pro Step **+ Write / + Wait / + Assert** plus **↑ / ↓** zum Umsortieren und **−** zum Entfernen. Ein fehlgeschlagener Per-Step-Assert bricht den Case sofort ab mit einer `Step <N> (assert): …`-Meldung; das Top-Level-`assertions[]` läuft danach weiterhin als Final-Gate
- **Dock-Layout** — Test Explorer, Analyse-Tools, Test-Editoren und Ergebnis-Panel sind frei verschiebbare Dock-Tools

### Trace / Signal-Visualisierung

Echtzeit-Oszilloskop für OPC-UA-Signale. Zeichnet PLC-Werte in festem Takt auf, stellt sie als Live-Diagramm dar und bietet Oszilloskop-Werkzeuge für gestoppte Aufzeichnungen.

- **Fortlaufend- und Einzel-Trigger-Modus** — Fortlaufend hält die neuesten Samples in einem rollenden Fenster (30 s bis 1 h), Einzel-Trigger zeichnet ein festes Fenster um eine steigende, fallende oder beidseitige Flanke auf, mit konfigurierbaren Pre-/Post-Samples
- **Auto-Reconnect** — Fällt die OPC-UA-Sitzung aus, startet der Trace nach Wiederherstellung automatisch mit denselben Signalen
- **Multi-Signal-Plots mit Skalierungsgruppen** — Signale auf die Hauptachse, eine von vier geteilten rechten Achsen (A / B / C / D) oder eine eigene rechte Achse pro Signal legen
- **Dual-Cursor mit Delta** — Klick setzt t1, erneuter Klick setzt t2, beide sind draggbar. Die Zeitdifferenz Δt erscheint im Plot; die Signal-Tabelle zeigt Y(t1), Y(t2) und ΔY pro Signal im gewählten Anzeigeformat
- **Toolbar-Toggle für Cursor** — Beide Messcursor per Toolbar-Button ein- und ausblenden. Beim ersten Einschalten nach Stopp platzieren sich die Cursor automatisch bei 25 % und 75 % des sichtbaren Zeitfensters. Jeder Cursor trägt ein kleines t1/t2-Label; am zweiten Cursor stehen Δt und ΔY live direkt an der Linie und wandern beim Ziehen mit
- **Pro-Signal-Format** — Dezimal, Hex, Binär, Bool oder Wissenschaftlich, direkt in der Signal-Tabelle editierbar, wirkt live auf Cursor-Anzeigen
- **Linear- oder Stufen-Darstellung pro Signal** — Die Signal-Tabelle hat eine Linie-Spalte mit Linear (Schräge zwischen Samples) oder Stufen (Rechteckverlauf, passt zu Bool oder bitweisen Signalen). Wird das Format eines Signals auf Bool gestellt, wird automatisch Stufen vorausgewählt
- **Berechnete Signale aus Formeln** — Kombiniere Quell-Signale mit `+`, `-`, `*`, `/`, Klammern, Built-in-Math (`abs`, `sqrt`, `min`, `max`, `sin`, `cos`, `log`, ...) und zustandsbehafteten `deriv` / `integ`; ungültige Formeln werden mit rotem Zellrahmen markiert, der Fehlertext erscheint als Tooltip, der Start-Button bleibt deaktiviert, bis jede Formel gültig ist
- **Overview-Minimap** — Kompakter Streifen unter dem Hauptplot zeigt die gesamte Aufzeichnung; das markierte Rechteck per Drag verschieben scrollt den Hauptplot mit, Zoomen verschiebt das Rechteck mit
- **FFT-Tab nach Stopp** — Gestoppte Aufzeichnungen bieten einen Frequenz-Tab mit Rectangular- / Hann- / Hamming- / Blackman-Fensterfunktionen plus optionaler dB- und Log-Y-Anzeige
- **Plot-Interaktion** — Pan, Rechteck-Zoom, schrittweises Zoomen, 100 % Reset, Fit aufs aktuelle Zeitfenster — alles nach Stopp verfügbar
- **CSV-Export** — Ganze Aufzeichnung (Quell- und berechnete Signale) mit ISO-8601-Zeitstempeln auf die Festplatte schreiben
- **MCP-Integration** — `tia_trace`-Tool mit start / stop / status / export; AI-Agenten können Quell- und berechnete Signale direkt verkabeln

### Problem-Meldung

Melde Bugs und schlage neue Funktionen vor, ohne die App zu verlassen. Der Help-Menü-Eintrag „Problem melden" öffnet einen Dialog, in dem du das Problem beschreibst; die App sammelt System-Informationen (App-Version, Betriebssystem, .NET-Runtime, aktive TIA-Portal-Version, Sprache, Lizenz-Tier) und aktuelle Logs und öffnet dann GitHub im Browser mit dem vorausgefüllten Issue. Kein GitHub-Login innerhalb der App nötig — die eigentliche Einreichung machst du selbst auf GitHub.

### Ein Fenster pro Windows-Sitzung

Pro Windows-Sitzung läuft nur eine Instanz des TIA Openness Managers. Wird eine Datei oder ein Ordner aus dem Windows Explorer geöffnet, während die App bereits läuft, holt das vorhandene Fenster sich nach vorn und öffnet das Element dort, statt eine zweite Kopie zu starten. Ein erneuter Doppelklick auf das Anwendungssymbol oder ein zweites Ausführen der Exe holt ebenfalls nur das laufende Fenster nach vorn. Verschiedene Windows-Benutzer (auch getrennte RDP-Sitzungen) bekommen jeweils eine eigene unabhängige Instanz.

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
- KI-Chat
- Projektbibliothek-Operationen
- Priority Support

### Enterprise (CHF 29.99/Monat oder CHF 299.99/Jahr)
- **Unbegrenzte Dateien**
- **Jahresabo spart 17%** (2 Monate gratis)
- Alles aus Professional, plus:
- Passwort-Tresor
- Unit Testing
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
2. Aktivierungscode per E-Mail erhalten
3. Code im Programm eingeben unter **View → Einstellungen → Lizenz verwalten**
4. Lizenz ist an Ihre Hardware gebunden

### Abonnement verwalten
- Klicken Sie auf **Abonnement verwalten** im Lizenz-Dialog
- Öffnet das Stripe-Portal für Zahlungen, Rechnungen und Kündigung

---

- **Mehrsprachig** - Deutsch, Englisch, Französisch, Italienisch

---

## Haftungsausschluss

Die Software wird „as is" geliefert. Der Anbieter übernimmt keine Haftung für Schäden, die durch die Nutzung entstehen. Der Anwender trägt die volle Verantwortung für die Prüfung aller generierten Inhalte. Siehe EULA auf https://www.tiaopenessmanager.ch

---

**Kontakt:** Für Fragen kontaktieren Sie uns unter [support@tiaopenessmanager.ch]

**© 2025-2026 AnyAutomation. Alle Rechte vorbehalten.**
