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

The built-in code editor provides professional editing features for SCL and other file types.

- **Split View** — Split editors horizontally or vertically, drag tabs between groups, dock and pin panels (file tree, markdown preview)
- **Syntax Highlighting** — SCL, C#, XML, JSON, Python, and 60+ other languages
- **Code Folding** — Collapse/expand code regions, IF/FOR blocks, and VAR sections
- **Auto-Completion** — Type 2+ characters to see SCL keywords, data types, and functions
- **Search** — Press Ctrl+F for find and replace with regex support
- **Code Snippets** — Type `if`, `for`, `while`, `case`, `fb`, `fc`, or `region` and press Tab to insert templates
- **Current Line Highlight** — Visual indicator for the current cursor line
- **Theme Support** — Editor colors automatically adapt when switching between Dark and Light themes
- **Inline Chat (Ctrl+I)** — Press Ctrl+I to open an AI chat directly in the code editor. Optionally select code first, then type your question or request — the AI responds and can propose changes inline. Accept with Tab, reject with Escape
- **Block Details** - Shows metadata like number, language, author
- **Quick Navigation** - Search in project tree

#### Keyboard Shortcuts
| Shortcut | Action |
|----------|--------|
| Ctrl+F | Find and Replace |
| Ctrl+I | Inline AI Chat (SCL Editor only) |
| Tab | Insert snippet (when trigger word is typed) |
| Tab | Accept AI edit |
| Escape | Reject AI edit |

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
- **Configurable Analysis Scope** - Toggle inclusion of Blocks (FC/FB), Data Blocks (DB), UDTs, and Tags individually
- **Exclusion Patterns** - Define wildcard patterns (e.g. `FB_Test*;DB_Temp*`) to exclude items from results
- **Reuse Exports** - Optionally reuse previous XML exports for faster repeated analysis
- **Persistent Settings** - All analysis preferences saved via gear icon in toolbar
- **Export Function** - Export results as text file
- **Copy to Clipboard** - Copy all results for documentation
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
- **Skills** - Place `.md` files in `%LocalAppData%\TiaOpennessManager\skills\` to create reusable prompt commands accessible via the `/` command palette in the chat input; no frontmatter required (just plain text works), optional YAML frontmatter for name, description, and icon
- **Agent Configs** - Place `.json` files in `%LocalAppData%\TiaOpennessManager\agents\` to define AI personas with custom system prompts and tool access; three built-in agents included (General Assistant, Git Assistant, SCL Expert)
- **File Attachments** - Drag and drop images (`.png`, `.jpg`, `.bmp`, `.gif`, `.webp`) or text files (`.cs`, `.xml`, `.json`, `.txt`, `.md`, `.yaml`, `.csv`, `.log`, `.scl`, `.cfg`) into the chat; images are resized and sent as multimodal content
- **Clipboard Paste** - Press Ctrl+V to paste a screenshot from the clipboard directly into the chat; also available via the attach menu
- **Chat Sessions** - Conversations are saved automatically; create new chats, switch between sessions, and resume previous conversations from the history panel
- **Session Archive** - Archive old sessions to keep the session list clean; restore or permanently delete archived sessions
- **Terminal Mode** - Embedded PowerShell terminal with MCP integration; auto-configures `.mcp.json` and optionally writes `CLAUDE.md` with project context for Claude CLI; terminal opens in the TIA Portal project directory
- **CLAUDE.md Setting** - Toggle whether a `CLAUDE.md` file is written to the project directory on terminal start (AI Chat Settings → Context); disable if not using Claude CLI
- **Agent Memory** - Each agent has its own persistent memory store across sessions with scope isolation (Local, Project, or User); the agent automatically saves important facts and injects relevant memories into context at session start; supports `memory_store`, `memory_search`, `memory_list`, `memory_update`, and `memory_delete` tools; configurable embedding provider (OpenAI, Google, Ollama, LM Studio) for semantic search, with keyword fallback; Memory Settings panel to view, delete, export (JSON), import, and clean up old memories; Memory Snapshots allow pre-seeding agents with team-shared knowledge via JSON files
- **Sub-Agent Steering** - Agent can dispatch sub-tasks to independent sub-agents (`run_subagent`); up to 5 concurrent sub-agents; manage running sub-agents via `manage_subagents list/kill/steer`; non-blocking mode allows the main agent to continue working while sub-tasks run in the background
- **Hooks** - Configurable event hooks that run before/after AI tool calls; add custom hooks in AI Chat Settings as shell commands or HTTP callbacks; built-in hooks protect safety blocks and log TIA operations; hooks can modify tool input, block execution, or add context to results; configurable timeout per hook (default 60s)
- **Inline Tool Approvals** - Approve or deny each AI tool call directly inside the tool-call message in the chat; the approval buttons are part of the scrollable content, so you can continue reading messages, scrolling history, and switching tabs while an approval is pending; four choices per call: Deny, Allow Once, Allow for Session, or Always Allow (persisted to disk); if the application is closed during an approval, the session can be resumed safely
- **Permission Modes** - Cycling toggle button next to the send button selects how write operations are approved: **Default** asks for every write, **Accept Edits** auto-approves file edits while still asking for shell commands and destructive operations like delete or force-push, **Auto** auto-approves everything except dangerous operations (PowerShell, process access, network writes); the current mode is shown with a colored icon and tooltip; Plan Mode is a separate dedicated toggle that forces the AI to submit an approved plan before any writes
- **Inline Plan Approval** - When the AI submits an execution plan, the plan appears as an editable text area directly inside the chat with Approve and Reject buttons; you can modify the plan before approving; non-blocking — scroll history or switch tabs while reviewing
- **Command Queue** - Send messages while the AI agent is working; messages are queued with priority levels (Now/Next/Later) and processed automatically after each turn; queue indicator shows pending message count; ESC cancels the current operation and clears the queue, or pops queued messages back into the input field when idle
- **Multi-Session** - Run multiple AI chat sessions simultaneously; the Agent Sidebar (toggle via PanelLeftOpen/PanelLeftClose icon) slides out as an overlay from the left and shows all sessions grouped by status (In Progress / Completed); each session has its own chat context, canvas, and agent/provider; sub-agents are routed to their parent session automatically; unread message badges with blink animation notify you of activity in other sessions; double-click a session name to rename it; close sessions via the X button (with confirmation if still running); the canvas state is preserved per session and replayed on switch; live preview text under each session name shows incoming messages and responses from other sessions
- **Per-Session Agent** - Each session remembers its agent/provider/model selection independently; switch to a different provider in one session without affecting other sessions; the agent switches automatically when you change sessions
- **Cross-Session Communication** - Agents can send messages to other sessions via send_agent_message; target sessions auto-resume without manual input; the AI sees all active sessions with their provider/model in the system prompt

### Git Client

- **Integrated Git UI** - Full visual Git workflow built into the application
- **Commit History** - Visual commit graph with branch and tag badges, author, date, and subject
- **Issue Tracker Links** - Commit messages show clickable links for issue references matching configurable patterns (e.g. `#123`, `PROJ-456`); opens the issue page in your browser; configure patterns per repository via Repository Settings → Issue Tracker tab; built-in presets for GitHub, GitLab, JIRA, and more
- **Clickable URLs** - HTTP(S) and FTP URLs in commit messages are auto-detected and open in the browser on click
- **Commit SHA Navigation** - SHA references in commit messages are clickable and navigate to the referenced commit in the history graph
- **Inline Code Rendering** - Backtick code spans in commit messages rendered in monospace with a distinct background
- **Rich Context Menus on Links** - Right-click links to: Copy Link, Open in Browser, Navigate to Commit, Copy SHA
- **Working Copy** - Stage/unstage files, write commit messages, commit with Sign-Off / No-Verify / Reset-Author options
- **Diff View** - Unified and side-by-side diff with TextMate syntax highlighting and hunk-level staging/discarding
- **Stash** - Create, apply, pop, and drop stashes; stash detail view with diff preview
- **Branches & Tags** - Visual branch tree, create/delete/rename/merge/rebase branches, push/pull tags
- **Remotes** - Fetch, pull, push, manage remotes
- **Submodules & Worktrees** - Full support for git submodules and worktrees
- **GitFlow** - GitFlow workflow support (init, start, finish feature/release/hotfix)
- **File History & Blame** - Per-file commit history and git blame view
- **Interactive Rebase** - Visual interactive rebase with drag-and-drop commit ordering
- **Branch Descriptions** - Branch descriptions visible in tooltips
- **Bisect** - Good/bad markers per commit for binary search debugging
- **Colored Status Badges** - File change states (Modified, Added, Deleted, Renamed, etc.) in the Working Copy and Commit Detail views are displayed as colored, rounded badges instead of plain text
- **LFS File Operations** - Right-click any file in the Working Copy to access LFS Track (by filename or extension) and LFS Lock/Unlock; for repositories with multiple remotes, lock/unlock shows a submenu per remote
- **Command Palette** - Press Ctrl+Shift+P to open a fuzzy-searchable palette with 14 quick actions (checkout, merge, compare, blame, file history, open file, create branch, create tag, fetch, pull, push, stash, apply patch, configure); commands requiring branch/tag/file selection open a secondary picker; Backspace on an empty filter returns to the main palette; Escape or backdrop click closes
- **GPG Signature Verification** - Commits show a colored shield badge (green = good, orange = expired/revoked, red = bad) in the commit detail SHA row; hover the badge to see signer identity and key ID; configure GPG signing per repository in Repository Settings
- **Rich Commit Message Editor** - AvaloniaEdit-based editor with subject line guide (dashed "SUBJECT END" line), subject character counter with warning when exceeding 72 characters, column position indicator, and auto-completion for 13 Git trailers (Signed-off-by, Co-authored-by, etc.); toolbar with commit template/history picker and conventional commit builder
- **External Diff/Merge Tools** - Configure an external diff/merge tool per repository in Repository Settings → Diff / Merge Tool tab; supports 13 tools on Windows, 9 on macOS, 9 on Linux (VS Code, Visual Studio, KDiff3, Beyond Compare, WinMerge, Meld, and more); use from context menus on changed files in Working Copy and Commit Detail
- **Stash Apply with Options** - Right-click a stash to apply or pop with options: "Restore index" (--index) re-stages previously staged changes, "Drop after apply" combines apply + drop into a pop operation
- **Multi-Branch Merge** - Select multiple branches in the sidebar or multiple commits in the history, then merge them all at once with strategy selection (Default, Octopus, or Ours) and optional auto-commit
- **Revision File Syntax Highlighting** - Files browsed at any commit in the "Files" tab are displayed with full TextMate syntax highlighting (consistent with the diff view)

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
- **MCP Integration** - Unified `opcua` tool with 9 subcommands for AI assistants: connect, disconnect, browse, read, read_complex, write, write_complex, get_types, subscribe

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
