# TIA Openness Manager V3

**Streamline Your Siemens TIA Portal Workflow**

[![Website](https://img.shields.io/badge/Website-tiaopenessmanager.ch-blue)](https://tiaopenessmanager.ch/)
[![Version](https://img.shields.io/badge/Version-3.0.6-green)](CHANGELOG.md)
[![TIA Portal](https://img.shields.io/badge/TIA%20Portal-V15--V21-orange)]()
[![Platform](https://img.shields.io/badge/Platform-Windows%20x64-lightgrey)]()

---

## What is TIA Openness Manager?

TIA Openness Manager is a powerful tool for Siemens TIA Portal developers that revolutionizes the export, import, and management of PLC program blocks. With an intuitive user interface and advanced features like difference comparison, protection profiles, and AI integration, it significantly increases productivity and reduces errors in project management.

**V3 Highlights:**
- Complete rewrite with modern two-process architecture (.NET 10 + .NET 4.8 Bridge)
- New Avalonia 11.x dark-theme UI (replacing WPF)
- Built-in OPC UA Client for live PLC data access
- AI Chat with context folders, git integration, skills, and agent configs
- Password Vault for encrypted know-how protection credentials
- Project Library Management with full MCP integration
- TIA Portal V21 support

**Key Benefits:**
- Export/import hundreds of blocks with a single click
- Find and remove unused (dead) code from your projects
- Compare block changes with fingerprint-based diff detection
- Protect critical blocks from accidental overwrites
- AI-powered code generation via MCP Server integration
- Browse and write OPC UA variables directly from the app

---

## Features

### Import & Export
- **Bulk Operations** - Export/import hundreds of blocks at once
- **XML & SCL Support** - Full support for Simatic ML and SCL files
- **S7DCL Export (V20+)** - Text-based export format for better version control
- **Configurable Settings** - Import/Export options dialog
- **Folder Structure** - TIA Portal folder hierarchy is preserved
- **Auto Compile & Save** - Automatic compilation after import

### Find Unused Blocks
- **Dead Code Detection** - Identifies blocks not called by any OB
- **Call-Graph Analysis** - Based on actual calls, not just references
- **Safety Block Support** - Full support for F_FB, F_FC, F_DB, F_OB
- **Export/Delete** - Export results as CSV or delete unused blocks directly

### Difference Comparison
- **Fingerprint-Based** - Fast comparison without full re-export
- **Change Detection** - Detects modified, new, and deleted blocks
- **Line-by-Line Diff** - Detailed difference viewer
- **Selective Re-Export** - Export only what changed

### Protection System
- **Block Protection** - Prevent accidental overwrites of critical blocks
- **Protection Profiles** - Save and load protection configurations
- **Visual Indicators** - Protected items clearly marked in tree

### Password Vault
- **Secure Storage** - AES-256-GCM encrypted vault for TIA Portal know-how protection passwords
- **Master Password** - Single master password protects all vault entries
- **Bulk Protect/Unprotect** - Apply or remove know-how protection on all assigned blocks at once
- **Crash Recovery** - Blocks left unprotected due to a crash are automatically re-protected

### HMI Support
- **Screens & Templates** - Export/import HMI screens
- **HMI Tag Tables** - Full tag table support
- **VB Scripts** - Export script functions
- **Text & Graphic Lists** - Multi-language support
- **WinCC Unified Support** - Full support for WinCC Unified HMI panels

### Hardware Management
- **Device Overview** - PLCs, HMIs, Drives, Switches
- **Network Info** - PROFINET names, IP addresses, firmware versions
- **Hardware Export** - Export device/module/network configuration as XML
- **CSV Export** - Document your hardware configuration

### Project Library Management
- **Create Master Copy** - Copy blocks to Project Library for reuse
- **Export Type Versions** - Export committed Library Type versions as XML
- **Folder Organization** - Create, rename, and delete library items
- **Clean Up Library** - Remove unused types and versions automatically

### AI Integration (MCP Server)
- **MCP Support** - Connect with any MCP-compatible AI assistant
- **Code Generation** - AI generates SCL blocks, DBs, UDTs, Tag Tables
- **Auto Import** - Generated code imports directly into TIA Portal
- **Project Context** - AI understands your project structure
- **Library Tools** - 7 library tools available for AI assistants
- **OPC UA Tools** - 8 OPC UA tools for AI-driven live data access

### AI Chat
- **Context Folders** - Register folders the AI can browse
- **Git Integration** - AI-aware of your git repository (status, commit, push, pull)
- **Skills & Agents** - Custom prompt commands and AI personas
- **File Attachments** - Drag and drop images or text files into the chat
- **Chat Sessions** - Automatic save, history, and session archive
- **Terminal Mode** - Embedded PowerShell terminal with MCP integration

### OPC UA Client
- **Direct Connection** - Connect to any OPC UA server by endpoint URL
- **Auto-Discovery** - Detect PLC OPC UA endpoints from the connected TIA Portal project
- **Address Space Browser** - Browse the full OPC UA address space in a TreeView
- **Watch Table** - Add variables, read/write values, live subscriptions
- **Save/Load Configuration** - Save and restore watch table configurations
- **CSV/JSON Export** - Export watch table data for documentation

---

## Supported Versions

| TIA Portal Version | Status |
|-------------------|--------|
| V15 | Supported |
| V16 | Supported |
| V17 | Supported |
| V18 | Fully Supported |
| V19 | Fully Supported |
| V20 | Fully Supported |
| V21 | Fully Supported |

---

## System Requirements

- **OS:** Windows 10/11 (64-bit)
- **Runtime:** Self-contained (.NET 10 bundled, no separate install needed)
- **TIA Portal:** V15, V16, V17, V18, V19, V20, or V21 installed
- **Permissions:** TIA Portal Openness API access configured

---

## Installation

1. Download the latest installer from [Releases](https://github.com/StaniB88/TIAOpenessManager/releases)

2. Run the installer and follow the setup wizard

3. Launch TIA Openness Manager from the Start Menu

4. Connect to your TIA Portal project (Open or Attach)

**Free Trial:** New users get a 30-day trial with all features unlocked.


## Quick Start

1. **Open/Attach Project** - Connect to a TIA Portal project
2. **Browse Tree** - Navigate your PLC blocks in the left panel
3. **Select Items** - Check the blocks you want to export
4. **Export** - Click "Export Selected" to save as XML/SCL
5. **Import** - Select XML files in right panel and import back

See the [User Guide](User_Guide/) for detailed documentation.

## Languages

- English
- Deutsch (German)
- Francais (French)
- Italiano (Italian)

---

## Documentation

- [User Manual (EN)](User_Guide/UserManual_EN.md)
- [User Manual (DE)](User_Guide/UserManual_DE.md)
- [Quick Start (EN)](User_Guide/QuickStart_EN.md)
- [Quick Start (DE)](User_Guide/QuickStart_DE.md)
- [Feature Overview](User_Guide/Features_EN.md)
- [Changelog](CHANGELOG.md)

---

## Auto-Update

TIA Openness Manager includes automatic update checking. When a new version is available, you'll be notified at startup. Updates can be disabled in Settings.

---

## Support

- **Website:** [tiaopenessmanager.ch](https://tiaopenessmanager.ch/)
- **Email:** TIAOpenessManager@outlook.com
- **Issues:** [GitHub Issues](https://github.com/StaniB88/TIAOpenessManager/issues)

---

## Screenshots

### Project Explorer
![Project Explorer](screenshots/ProjectExplorer.png)

### Import & Export
![Import Export](screenshots/ImportExport.png)

### Code Editor
![Code Editor](screenshots/Editor.png)

### Find Unused Blocks
![Find Unused](screenshots/FindUnused.png)

### Difference Comparison
![Compare](screenshots/Compare.png)

### Protection & Vault
![Protection](screenshots/Protection.png)
![Vault](screenshots/Vault.png)

### OPC UA Client
![OPC UA](screenshots/OPCUA.png)

### AI Chat
![AI Assistant](screenshots/AIAssistant.png)

### Version Control
![Version Control](screenshots/VersionControl.png)

---

## Changelog

See [CHANGELOG.md](CHANGELOG.md) for version history and release notes.


## Disclaimer

**The software is provided "as is" without warranty of any kind.**

The provider assumes no liability for:
- Damages caused by faulty LLM outputs or AI-generated code
- Data loss, production downtime, or system failures
- Engineering errors or faulty code generation
- Damages caused by improper use or configuration

**The user bears full responsibility for reviewing and validating all generated content before use in production systems.**

This software uses the official Siemens TIA Portal Openness API. Siemens and TIA Portal are registered trademarks of Siemens AG.

See [EULA](https://www.tiaopenessmanager.ch/eula) and [Terms](https://www.tiaopenessmanager.ch/agb) for full legal details.

---

**© 2026 AnyAutomation. All rights reserved.**

**Made with passion for the automation community**
