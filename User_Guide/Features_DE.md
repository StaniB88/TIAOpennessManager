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

### Code Editor

- **Integrierter Editor** - Betrachten und bearbeiten Sie Blockcode direkt
- **Syntax-Highlighting** - Für SCL, STL und andere Sprachen
- **Block-Details** - Zeigt Metadaten wie Nummer, Sprache, Autor
- **Schnelle Navigation** - Suche im Projektbaum

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
- **Export-Funktion** - Ergebnisse als CSV exportieren
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
- **Terminal-Modus** - Eingebettetes PowerShell-Terminal mit MCP-Integration; konfiguriert automatisch `.mcp.json` und schreibt optional eine `CLAUDE.md` mit Projektkontext für Claude CLI; Terminal öffnet im TIA Portal-Projektverzeichnis
- **CLAUDE.md-Einstellung** - Steuert, ob beim Terminal-Start eine `CLAUDE.md`-Datei ins Projektverzeichnis geschrieben wird (AI Chat Settings → Context); deaktivieren, wenn Claude CLI nicht verwendet wird
- **Agenten-Gedächtnis** - Jeder Agent hat einen eigenen, sitzungsübergreifenden Gedächtnisspeicher; der Agent speichert automatisch wichtige Fakten und fügt relevante Erinnerungen beim Sitzungsstart in den Kontext ein; unterstützt die Tools `memory_store`, `memory_search`, `memory_list` und `memory_delete`; konfigurierbarer Embedding-Anbieter (OpenAI, Google, Ollama, LM Studio) für semantische Suche mit Schlüsselwort-Fallback; Gedächtnis-Einstellungen zum Anzeigen, Löschen, Exportieren (JSON), Importieren und Aufräumen alter Erinnerungen
- **Subagenten-Steuerung** - Agent kann Teilaufgaben an unabhängige Subagenten delegieren (`run_subagent`); bis zu 5 gleichzeitige Subagenten; laufende Subagenten verwalten mit `manage_subagents list/kill/steer`; nicht-blockierender Modus ermöglicht dem Hauptagenten, weiterzuarbeiten, während Teilaufgaben im Hintergrund laufen

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
- **MCP-Integration** - 8 OPC UA Tools für KI-Assistenten: `opcua_connect`, `opcua_disconnect`, `opcua_browse`, `opcua_read`, `opcua_read_complex`, `opcua_write`, `opcua_get_types`, `opcua_subscribe`

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
