# Linux Usage

## Prerequisites

1. Install required dependencies:
   - pixi
   - xdelta3
   - fuse-overlayfs (certainly you can use overlayfs if your filesystem supports it.)

2. Install Python dependencies using pixi or pip:
   ```bash
   pixi shell
   ```

## Setup Steps

### 1. Mount OverlayFS

The application requires an OverlayFS to merge your mo2 files with the base game data. Use the provided `mods_ovlfs_helper` script:

1. Edit `mods_ovlfs_helper` to configure your paths:
   - `MODS_DIR`: Path to your MO2 mods directory
   - `BASE_DIR`: Path to your Skyrim Data directory
   - `MODLIST`: Path to your MO2 profile's modlist.txt

2. Create required directories:
   ```bash
   mkdir -p overwrite tmp merged_data
   ```

3. Run the helper script to mount the OverlayFS:
   ```bash
   ./mods_ovlfs_helper
   ```
### 2. Run the Application

Use the provided `start.sh` script as a reference:

```bash
cd /path/to/your/overlayfs
python /path/to/Dynamic-Interface-Patcher/src/main.py
```
### 3. Configure Paths in the Application

When using the application:
- **Patch Path**: Select the path to your DIP patch folder which has a patch subfolder (e.g., `/path/to/MO2/mods/Edge UI - RaceMenu DIP Patch/Edge UI - RaceMenu - DIP/`)
- **Original Mod Path**: Select the path to your OverlayFS merged data (e.g., `/path/to/merged_data`)

### 4. Output Location

The patched files will be generated in the parent directory of your working directory. You can then move these files to your mod manager for installation.
