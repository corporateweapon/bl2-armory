# Boxgun — an Armory weapon pack

The Armory's default pack: the Boxgun, a legendary Vladof assault rifle built from nine primitives by the bl2-part-pipeline's own example recipe. Every part of it (mesh, balance, title, red text, stats) is original and free to reuse; use it as the template for your own pack.

* Pack id `boxgun`, version 1.0.0, by 44M0N
* Licence: CC0-1.0 (see LICENSE.txt)
* Needs the **Armory 1.1.0 or newer** (and the willow2 SDK mod manager it runs on)

| spawn id | weapon | type | balance |
|---|---|---|---|
| `boxgun` | Boxgun | AssaultRifle | `GD_Weap_AssaultRifle.A_Weapons_Legendary.AR_Vladof_5_BOXGUN` |

## Install

Extract the zip into your `Borderlands 2` folder (the one holding `Binaries` and
`WillowGame`) and let it merge folders. That places:

    sdk_mods\ArmoryPacks\boxgun\   (this folder)
    WillowGame\CookedPCConsole\PipelineMeshesBoxgun.upk

Start the game. The Armory registers the weapon(s) at the main menu; load your character,
then press the Armory spawn key (F5 by default) or type `armory spawn boxgun`
in the console. `armory packs` lists what loaded and why anything did not.

## Uninstall

Delete `sdk_mods\ArmoryPacks\boxgun\` and the `.upk` file(s) listed above. Weapons of
this pack in your saves lose their parts while it is removed; their records are kept under
`sdk_mods\_pipeline_saves\`, so putting the pack back restores them.
