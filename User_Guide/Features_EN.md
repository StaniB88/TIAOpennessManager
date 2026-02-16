# TIA Openness Manager - Feature Overview

## Product Description

The **TIA Openness Manager** is a powerful tool for Siemens TIA Portal developers that revolutionizes the export, import, and management of PLC program blocks. With an intuitive user interface and advanced features like difference comparison, protection profiles, and AI integration, it significantly increases productivity and reduces errors in project management.

---

## Main Features

### Import & Export

- **Bulk Export** - Export hundreds of blocks with a single click
- **Selective Export** - Choose exactly the blocks you need
- **XML & SCL Support** - Full support for Simatic ML and SCL files
- **S7DCL Export (V20+)** - Convert blocks to text-based S7DCL format for better version control
- **Per-Type Export Options** - Configure export settings (None/WithDefaults/WithReadOnly) separately for DBs, UDTs, and Tags
- **Folder Structure Preservation** - TIA Portal folder structure is maintained
- **Automatic Compilation** - Automatically compiles and saves after import
- **Configurable Folder Names** - Customize export folder names (Source, Blocks, Tags, etc.)
- **Optional Source Folder** - Enable/disable the Source folder wrapper in exports
- **Version Control Options** - Clean exports for Git/SVN (normalize timestamps, remove metadata)
- **Export Fingerprints** - Optional fingerprint extraction for change detection (Preview Diff)
- **Export Protected Files** - Optionally skip protected items during export while preserving folder structure
- **Fault Tolerant Import** - Continue importing even if some files fail

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

### Difference Comparison (Preview Diff)

- **Fingerprint-based** - Fast comparison without full export
- **Change Detection** - Detects modified, new, and deleted blocks
- **Detailed Diff Viewer** - Shows differences line by line
- **Selective Re-Export** - Export only changed blocks

### Code Editor

- **Integrated Editor** - View and edit block code directly
- **Syntax Highlighting** - For SCL, STL, and other languages
- **Graphical View** - View LAD/FBD/GRAPH blocks graphically (requires SIMATIC Automation Compare Tool)
- **Block Details** - Shows metadata like number, language, author
- **Quick Navigation** - Search in project tree
- **Create New Blocks** - Create FC, FB, DB, UDT, or Tag Table directly from SCL code
- **Save/Discard** - Edit existing blocks and save or discard changes

### Protection System (Protected Items)

- **Inline Protection** - Protect blocks directly in the project tree via checkboxes
- **Profiles** - Save and load protection configurations
- **Visual Marking** - Protected blocks are clearly marked with lock icon
- **Hierarchical Protection** - Protect entire folders or individual blocks
- **OB Protection Options** - Additional checkboxes for OBs: Allow SCL code updates (C) and Allow Attribute updates (A)
- **Browse Profiles Folder** - Quick access to profiles folder for sharing between team members

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

---

## Supported TIA Portal Versions

| Version | Status |
|---------|--------|
| TIA Portal V15 | Attach mode only |
| TIA Portal V16 | Attach mode only |
| TIA Portal V17 | Attach mode only |
| TIA Portal V18 | Fully supported |
| TIA Portal V19 | Fully supported |
| TIA Portal V20 | Fully supported |

> **Note:** TIA Portal version is detected automatically when you open a project or attach to a running instance.

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
- 1 file export/import
- Block Compare
- Code Editor
- Hardware Overview

### Professional (€25/month or €250/year)
- **1,000 files** export/import
- **Annual plan saves 17%** (2 months free)
- Everything in Basic, plus:
- Find Unused Blocks
- Safety Block Support (F_FB, F_FC, F_DB, F_OB)
- Protection Profiles
- MCP Server Integration
- Priority Support

### Enterprise (€40/month or €400/year)
- **Unlimited files**
- **Annual plan saves 17%** (2 months free)
- Everything in Professional
- Multi-user licenses
- Dedicated support
- Volume discounts

---

## Activation

### Online Activation
1. Purchase subscription at: https://www.tiaopenessmanager.ch
2. Receive activation code via email
3. Enter code in the program under "License" → "Activate"
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

**© 2026 AnyAutomation. All rights reserved.**
