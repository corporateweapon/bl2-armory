# Armory for Borderlands 2

By **44M0N**.

The Armory adds **new weapons** to Borderlands 2 (Steam, Windows). Not reskins: each
weapon has its own model, parts, name, red text, stats and loot-pool entry. It also loads
**character skins** that replace a vault hunter's body and first-person arms. None of the
game's files are changed.

This repo is the Armory itself: the mod that loads weapon packs, plus a double-click
installer. Weapons and skins come as separate **packs**, each a small zip, made by anyone
with the [bl2-part-pipeline](https://github.com/corporateweapon/bl2-part-pipeline). The
Armory ships with one weapon, the **Boxgun**, so you can check that everything works.

## What you need first

1. **Borderlands 2 on Steam**, on Windows.
2. **The willow2-mod-manager** (the Python SDK), from https://bl-sdk.github.io/willow2-mod-db/.
   Follow its install instructions. It works when the game's title screen has a **Mods**
   entry. The Armory installer checks for it and stops if it's missing.
3. **Back up your saves**: copy `Documents\My Games\Borderlands 2\WillowGame\SaveData\`
   somewhere safe. (Steam Cloud also keeps a copy.)

Close the game before installing anything.

## Step 1: install the Armory

1. Download **`Armory-1.1.0.zip`** from [Releases](../../releases).
   (Or use the green **Code → Download ZIP** button on this page; it's the same files.)
2. *Optional, skips a Windows warning:* right-click the zip → **Properties** → tick
   **Unblock** → **OK**.
3. Right-click the zip → **Extract All...** → **Extract**.
4. Open the extracted folder and double-click **`Install.bat`**.

The installer finds your Borderlands 2 folder through Steam (if you have several Steam
libraries or it can't tell, it asks). It copies the files in, checks each copy, switches the
Armory on in the Mods menu and prints what it did. Press Enter to close it.

If Windows warns you when you double-click:
* **"Windows protected your PC"**: click **More info** → **Run anyway**.
* **"Open File - Security Warning"**: click **Run**.

This happens for any script from a downloaded zip. Step 2 above avoids it.

## Step 2: check it in game

1. Start Borderlands 2 and **wait for the title screen** before loading a character.
2. Open **Mods**. **Armory** should be listed and enabled. **Armory → Packs** lists every
   pack that loaded.
3. Load a character and press **F5**: a Boxgun appears in your hands at your level.

| How | What it does |
|---|---|
| **F5** | Spawns the weapon selected under **Mods → Armory → Weapon**. Rebind it under **Mods → Armory → Keybinds**. |
| Console `armory list` | Every weapon id you have installed |
| Console `armory spawn boxgun` | Spawns by id. Add `--level 50` for a level, `--no-equip` to send it to the backpack |
| Console `armory packs` | What loaded and **why anything didn't** |
| **Mods → Armory → Characters** | Shown when a skin pack is installed: pick a skin or the game's own model per vault hunter |

The console opens with the `~` key. Armory weapons also drop in the world, from the loot pool
each pack's creator chose. The Boxgun drops from the legendary assault rifle pool.

## Step 3: add weapons and skins

A pack is a zip laid out exactly like the Armory's. Install it the same way: extract it, then
double-click its **`Install.bat`**. Install the Armory first, and restart the game after
adding a pack. Its `HOW_TO_INSTALL.txt` lists every file it adds, and its `Uninstall.bat`
removes exactly those.

Want to make one? The [bl2-part-pipeline](https://github.com/corporateweapon/bl2-part-pipeline)
turns a 3D model into a pack. The guide is `sdk_mods\Armory\CREATING_PACKS.md`, included here.

## Updating, uninstalling

* **Update:** install the new zip over the old one. Settings, keybinds and weapon records are
  kept.
* **Remove one pack:** double-click that pack's **`Uninstall.bat`** and type **Y**.
* **Remove everything:** run each pack's `Uninstall.bat`, then the Armory's.

The installer only ever writes into `sdk_mods\` and adds `Pipeline*.upk` files to
`WillowGame\CookedPCConsole\`. It never replaces or deletes the game's own files, so
uninstalling puts the game back as it was.

## Rather do it by hand? (no scripts)

Every zip is laid out like the game folder, so you can drag and drop instead:

1. Open your game folder: in Steam, right-click Borderlands 2 → **Manage** → **Browse local
   files**. It's the folder with `Binaries`, `WillowGame` and `sdk_mods` in it.
2. From the extracted zip, drag the **`sdk_mods`** and **`WillowGame`** folders onto that
   window. When Windows asks, choose **Replace the files in the destination**. The folders
   merge; none of the game's files are replaced.
3. Don't copy `Install.bat`, `Uninstall.bat`, `_installer` or `HOW_TO_INSTALL.txt`. Each
   zip's `HOW_TO_INSTALL.txt` lists exactly which files belong in the game.

To uninstall by hand, delete the files that `HOW_TO_INSTALL.txt` lists.

## Before you play: saves and co-op

* The game can't save a custom weapon's parts on its own, so the Armory records them in
  `sdk_mods\_pipeline_saves\` and restores them when you load. **If you load a save while the
  Armory or a pack is missing, those weapons lose their parts.** Reinstalling before the next
  load brings them back. Don't delete `_pipeline_saves`.
* **Co-op:** every player needs the Armory and the same packs.

## If something goes wrong

| What you see | What to do |
|---|---|
| Installer: `the willow2-mod-manager (the Python SDK) is not installed in this game folder` | Install the mod manager (see *What you need first*), start the game once, then run `Install.bat` again. |
| Installer: `Borderlands 2 is running` | Quit the game, then press Enter in the installer window. |
| Installer asks for the game folder | Pick the folder that has `Binaries`, `WillowGame` and `sdk_mods` in it. |
| Installer: `nothing to install next to this script` | You ran it from inside the zip. Extract the zip first (Step 1.3). |
| No **Armory** in the Mods menu | Check that `Borderlands 2\sdk_mods\Armory\__init__.py` exists. If it doesn't, run `Install.bat` again. |
| A weapon or skin is missing | Run `armory packs` in the console. It names the pack and the reason. Usually running the pack's `Install.bat` again fixes it. |

When asking for help, send the installer's output and the `Borderlands 2\sdk_mods\Armory\logs\`
folder.

## What's in this repo

This repo holds the files of `Armory-1.1.0.zip`:

```
Install.bat, Uninstall.bat      double-click installer / uninstaller
_installer\armory_install.ps1   the PowerShell script they run (readable, no downloads)
HOW_TO_INSTALL.txt              the same steps in plain text, with the file list
sdk_mods\Armory\                the Armory mod (its README.md has the full manual)
sdk_mods\ArmoryPacks\boxgun\    the Boxgun test weapon
WillowGame\CookedPCConsole\PipelineMeshesBoxgun.upk
```

The Armory is MIT licensed. The Boxgun is CC0. Built on the BL-SDK willow2-mod-manager;
thanks to its developers.
