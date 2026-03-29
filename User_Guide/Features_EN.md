# TIA Openness Manager - Feature Overview

## Product Description

The **TIA Openness Manager** is a powerful tool for Siemens TIA Portal developers that revolutionizes the export, import, and management of PLC program blocks. With an intuitive user interface and advanced features like difference comparison, protection profiles, and AI integration, it significantly increases productivity and reduces errors in project management.

---

## Main Features

### Import & Export

- **Bulk Export** - Export hundreds of blocks with a single click
- **Selective Export** - Choose exactly the blocks you need
- **XML & SCL Support** - Full support for Simatic ML and SCL files
- **S7DCL Export (V20+)** - Additional text-based export format (.s7dcl) for better version control
- **Folder Structure Preservation** - TIA Portal folder structure is maintained
- **Automatic Compilation** - Automatically compiles and saves after import
- **Configurable Folder Names** - Customize export folder names (Source, Blocks, Tags, etc.)
- **Optional Source Folder** - Enable/disable the Source folder wrapper in exports

### HMI Export/Import

- **Screen Export** - Export HMI screens as XML
- **Screen Template Export** - Export reusable screen templates
- **HMI Tag Tables** - Export/import HMI tag tables
- **VB Scripts** - Export HMI VB scripts
- **Connections** - Export HMI connection configurations
- **Text Lists & Graphic Lists** - Full support for HMI lists

### Hardware Tab

- **Device List** - Complete overview of all devices (PLCs, HMIs, Drives, Switches)
- **PROFINET Names** - View and edit PROFINET device names directly
- **IP Addresses** - Display IP address configuration for all devices
- **Firmware Versions** - Show firmware version for each device
- **Article Numbers** - Display Siemens article/order numbers
- **I/O Mapping** - Show input/output address ranges
- **CSV Export** - Export complete hardware list to CSV for documentation
- **WinCC Unified Support** - Full support for WinCC Unified HMI panels

### Hardware Export

- **Device Configuration** - Export hardware configuration as XML
- **Module Configuration** - Export individual module settings
- **Network Configuration** - Export network/communication settings

### Watch/Force Tables

- **Table Export** - Export Watch Tables and Force Tables
- **Variable Lists** - Export monitored variable configurations
- **Debug Support** - Preserve debugging setups across projects

### Project Library Management

- **Create Master Copy** - Copy blocks to Project Library for reuse
- **Instantiate from Library** - Create blocks from Master Copies
- **Export Type Versions** - Export committed Library Type versions as XML
- **Folder Organization** - Create folders in library for better structure
- **Rename Items** - Rename Master Copies, Types, and folders
- **Delete Items** - Remove library items with confirmation
- **Clean Up Library** - Remove unused types and versions automatically
- **MCP Integration** - 7 library tools available for AI assistants

### Difference Comparison (Preview Diff)

- **Fingerprint-based** - Fast comparison without full export
- **Change Detection** - Detects modified, new, and deleted blocks
- **Detailed Diff Viewer** - Shows differences line by line
- **Selective Re-Export** - Export only changed blocks

### Code Editor

- **Integrated Editor** - View and edit block code directly
- **Syntax Highlighting** - For SCL, STL, and other languages
- **Block Details** - Shows metadata like number, language, author
- **Quick Navigation** - Search in project tree

### Protection System (Protected Items)

- **Block Protection** - Protect important blocks from accidental overwriting
- **Export Protection** - Optionally exclude protected blocks from export while preserving folder structure
- **Profiles** - Save and load protection configurations
- **Visual Marking** - Protected blocks are clearly marked with a green shield
- **Hierarchical Protection** - Protect entire folders or individual blocks

### Password Vault

- **Secure Storage** - AES-256-GCM encrypted vault for TIA Portal know-how protection passwords
- **Master Password** - Single master password protects all vault entries (PBKDF2 key derivation)
- **Block Assignment** - Assign vault passwords to blocks or folders via context menu or vault toggle checkboxes
- **Bulk Protect/Unprotect** - Apply or remove know-how protection on all assigned blocks at once
- **Crash Recovery** - Blocks left unprotected due to a crash are automatically re-protected on next project open
- **CSV Export** - Export all vault entries to CSV for backup (includes plaintext passwords, available when vault is unlocked)
- **Localized** - Available in English, German, French, and Italian

### Find Unused Blocks

- **Dead Code Detection** - Finds unused blocks
- **Call-Graph Analysis** - Based on actual calls, not just references
- **Safety Block Support** - Also supports F-blocks (F_FB, F_FC, F_DB, F_OB)
- **Export Function** - Export results as CSV
- **Delete Function** - Remove unused blocks directly

### AI Integration (MCP Server)

- **Model Context Protocol** - Integration with any MCP-compatible AI assistant
- **Project Context** - AI has access to your project structure
- **Code Generation** - AI can generate SCL source code for blocks
- **DB Generation** - AI can create Data Blocks with Simatic ML templates
- **UDT Generation** - AI can create User-Defined Types
- **Tag Table Generation** - AI can create Tag Tables
- **Auto Import** - Generated code can be automatically imported into TIA Portal
- **Block Analysis** - AI can read and analyze existing blocks

### AI Chat

- **Context Folders** - Register folders the AI can browse using file read and search tools
- **Instruction Files** - Inject Markdown files into the AI's system prompt automatically at session start
- **Git Integration** - AI is aware of your git repository, branch, and changes; can view status, stage files, commit, push, and pull (mutating operations require user approval)
- **Commit Templates** - Define commit message templates; the AI follows the active template when generating commits
- **Skills** - Place `.md` files in `%LocalAppData%\TiaOpennessManager\skills\` to create reusable prompt commands accessible via the `/` command palette in the chat input
- **Agent Configs** - Place `.json` files in `%LocalAppData%\TiaOpennessManager\agents\` to define AI personas with custom system prompts and tool access; three built-in agents included (General Assistant, Git Assistant, SCL Expert)
- **File Attachments** - Drag and drop images (`.png`, `.jpg`, `.bmp`, `.gif`, `.webp`) or text files (`.cs`, `.xml`, `.json`, `.txt`, `.md`, `.yaml`, `.csv`, `.log`, `.scl`, `.cfg`) into the chat; images are resized and sent as multimodal content
- **Clipboard Paste** - Press Ctrl+V to paste a screenshot from the clipboard directly into the chat; also available via the attach menu
- **Chat Sessions** - Conversations are saved automatically; create new chats, switch between sessions, and resume previous conversations from the history panel
- **Session Archive** - Archive old sessions to keep the session list clean; restore or permanently delete archived sessions
- **Terminal Mode** - Embedded PowerShell terminal with MCP integration; auto-configures `.mcp.json` and optionally writes `CLAUDE.md` with project context for Claude CLI; terminal opens in the TIA Portal project directory
- **CLAUDE.md Setting** - Toggle whether a `CLAUDE.md` file is written to the project directory on terminal start (AI Chat Settings → Context); disable if not using Claude CLI
- **Agent Memory** - Each agent has its own persistent memory store across sessions; the agent automatically saves important facts and injects relevant memories into context at session start; supports `memory_store`, `memory_search`, `memory_list`, and `memory_delete` tools; configurable embedding provider (OpenAI, Google, Ollama, LM Studio) for semantic search, with keyword fallback; Memory Settings panel to view, delete, export (JSON), import, and clean up old memories
- **Sub-Agent Steering** - Agent can dispatch sub-tasks to independent sub-agents (`run_subagent`); up to 5 concurrent sub-agents; manage running sub-agents via `manage_subagents list/kill/steer`; non-blocking mode allows the main agent to continue working while sub-tasks run in the background

### OPC UA Client

- **Direct Connection** - Connect to any OPC UA server by endpoint URL (e.g., `opc.tcp://192.168.0.1:4840`)
- **Auto-Discovery** - Automatically detect PLC OPC UA endpoints from the connected TIA Portal project
- **Authentication Modes** - Anonymous, Username/Password, and Certificate-based authentication
- **Address Space Browser** - Browse the full OPC UA address space in a TreeView with node class icons
- **Node Search** - Filter address space nodes by name to quickly locate variables
- **Watch Table** - Add variables via double-click or drag-and-drop; view Name, Node ID, Data Type, Value, Status, and Timestamp per row
- **Read Values** - Read all watch table variables with a single server request, or read individual rows on demand
- **Write Values** - Write values directly to PLC variables by editing watch table cells
- **Live Subscriptions** - Subscribe to value changes with a configurable interval (in milliseconds); values update automatically without polling
- **Per-Variable Subscribe** - Subscribe to a selection of rows independently of the full watch table
- **Save/Load Configuration** - Save and restore watch table configurations (endpoint URL + variable list) as `.opcua-watch` JSON files
- **CSV Export** - Export watch table data to CSV with all columns (Name, Node ID, Data Type, Value, Status, Timestamp)
- **JSON Export** - Export watch table data to structured JSON with full metadata
- **MCP Integration** - 8 OPC UA tools available for AI assistants: `opcua_connect`, `opcua_disconnect`, `opcua_browse`, `opcua_read`, `opcua_read_complex`, `opcua_write`, `opcua_get_types`, `opcua_subscribe`

---

## Supported TIA Portal Versions

| Version | Status |
|---------|--------|
| TIA Portal V15 | Supported |
| TIA Portal V16 | Supported |
| TIA Portal V17 | Supported |
| TIA Portal V18 | Fully supported |
| TIA Portal V19 | Fully supported |
| TIA Portal V20 | Fully supported |
| TIA Portal V21 | Fully supported |

---

## Supported Block Types

### PLC Blocks
- **OB** - Organization Blocks (incl. F_OB)
- **FB** - Function Blocks (incl. F_FB)
- **FC** - Functions (incl. F_FC)
- **DB** - Data Blocks (Global, Instance, Array, incl. F_DB)
- **UDT** - User-Defined Data Types
- **Tag Tables** - Variable Tables
- **Technology Objects** - Motion Control, PID Controllers, Counters, etc.
- **Software Units** - V18+ Software Unit containers

### HMI Elements
- **Screens** - HMI screens and popups
- **Screen Templates** - Reusable screen templates
- **HMI Tag Tables** - HMI-specific tag tables
- **VB Scripts** - VB script functions
- **Connections** - PLC/HMI connections
- **Text Lists** - Multi-language text lists
- **Graphic Lists** - Graphic/symbol lists

### Hardware
- **Device Configuration** - Hardware setup as AML/XML

---

## License Options

### Basic (FREE)
- **Free forever** - No trial period, no expiration
- 1 file export/import per operation
- Block Compare
- Code Editor
- Hardware Overview

### Professional (CHF 9.99/month or CHF 99.99/year)
- **1,000 files** export/import per operation
- **Annual plan saves 17%** (2 months free)
- Everything in Basic, plus:
- Find Unused Blocks
- Safety Block Support (F_FB, F_FC, F_DB, F_OB)
- Protection Profiles
- MCP Server Integration
- Priority Support

### Enterprise (CHF 29.99/month or CHF 299.99/year)
- **Unlimited files**
- **Annual plan saves 17%** (2 months free)
- Everything in Professional
- Multi-user licenses
- Dedicated support
- Volume discounts

### Trial Period
- **30-day free trial** with all Enterprise-level features
- No credit card required
- After 30 days, falls back to Basic (free)

---

## Activation

### Online Activation
1. Purchase subscription at: https://www.tiaopenessmanager.ch
2. Receive activation code via email (format: `ACT-XXXX-XXXX-XXXX`)
3. Enter code in the program under **View → Settings → Manage License**
4. License is bound to your hardware

### Manage Subscription
- Click "Manage Subscription" in the License dialog
- Opens Stripe portal for payments, invoices, and cancellation

---

- **Multi-language** - German, English, French, Italian

---

## Disclaimer

The software is provided "as is". The provider assumes no liability for damages caused by use. The user bears full responsibility for reviewing all generated content. See EULA at https://www.tiaopenessmanager.ch

---

**Contact:** For questions, contact us at [tiaopenessmanager@outlook.com]

**© 2025-2026 AnyAutomation. All rights reserved.**
