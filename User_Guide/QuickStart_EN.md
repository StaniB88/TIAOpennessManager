# TIA Openness Manager - Quick Start Guide

## System Requirements

- **Operating System:** Windows 10/11 (64-bit)
- **TIA Portal:** Version 15, 16, 17, 18, 19, or 20 installed
- **.NET Framework:** 4.8 or higher
- **Memory:** Minimum 4 GB RAM (8 GB recommended)
- **Disk Space:** 500 MB for the application

## Installation

1. Extract the TiaOpennessManager archive to a folder of your choice
2. Run `TiaOpennessManager.exe`
3. On first launch, a 30-day trial license is automatically activated

> **Note:** TIA Portal must be installed but does not need to be running.

## First Launch

### 1. Connect to TIA Portal Project

Click the **Connect** button in the center of the project tree area. A dialog opens with two tabs:

**Option A: Attach to Running TIA Portal (recommended)**
1. Select the **Attach to Running** tab (selected by default)
2. Choose your running TIA Portal instance from the list
3. Click **Connect**

> **Tip:** The Attach function is faster since the project doesn't need to be reloaded.

**Option B: Open Project File**
1. Select the **Open Project** tab
2. Click **Browse...** and navigate to your TIA Portal project file (`.ap15` to `.ap20`, `.apx`)
3. Click **Connect**

> **Note:** The TIA Portal version is detected automatically from your project file.

### 2. Set Export Directory

1. Switch to the **Import/Export** tab
2. Click **...** next to the "Right directory" field
3. Select a folder where the XML files should be stored

> **Tip:** Use a Git repository folder for automatic version control.

## First Export Operation

### Export All Blocks

1. In the **Import/Export** tab, you'll see the project tree with all PLCs on the left
2. Expand the PLC and navigate to **Blocks**
3. Click **Export All**
4. Blocks will be exported as XML files to the selected directory

### Export Selected Blocks

1. Check the boxes next to the blocks you want to export
2. Click **Export Selected**

## First Import Operation

### Import Blocks from XML

1. In the right panel, you'll see the XML files in the Working Directory
2. Check the boxes next to the files you want to import
3. Click **Import Selected**

> **Important:** Import will overwrite existing blocks with the same name!

## Next Steps

- Read the complete **User Manual** for all features
- Explore the **Preview Diff** function to compare changes
- Use **Find Unused Blocks** to identify unused blocks
- Set up **Protected Items** to prevent important blocks from being overwritten

---

## Disclaimer

The software is provided "as is". The provider assumes no liability for damages. The user bears full responsibility for reviewing all content. See EULA at https://www.tiaopenessmanager.ch

---

**Support:** For questions, contact support or consult the detailed User Manual.

**© 2026 AnyAutomation.**
