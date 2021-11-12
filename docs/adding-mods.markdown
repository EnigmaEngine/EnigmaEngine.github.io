{% include toc.html %}
# Adding and Configuring Mods

## Adding New Mods

To add a ModCore mod to your installation of Enigma Engine, follow these steps.

1. Download the mod and extract the ZIP file.
2. Place the mod folder into the `mods` folder in your installation folder.

Enigma Engine will detect the mod automatically.

## Configuring Mods

As long as one or more mods are installed, Enigma Engine will automatically detect them and display a splash screen with the following options:

* SPACE/ENTER: Start the game with mods enabled.
  - If you have not configured any mods, Enigma Engine will automatically detect and use all mods it finds.
  - If you have configured mods, Enigma Engine will use the mods you have configured.
* 2: Start the game with mods disabled.
* 3: Configure mods.
  - This will open the Mod Configuration menu.

This is the mod configuration menu:

<img src="/images/docs/mod-config-menu.jpg" />

Mods you have installed will be displayed in the list on the left side. You can enable the mods by clicking the arrow, which will move them to the right side. Once the mod is loaded, you can reorder the mods by clicking the up and down arrows.

Mods which are placed higher in the list will be loaded first. Mods which are placed lower in the list will override the contents of the mods loaded earlier, if applicable.

There are also several buttons:

* Load All Mods: Load all mods from the unloaded mod list.
* Unload All Mods: Unload all mods from the loaded mod list.
* Revert Mod Config: Revert the mod configuration to what it was previously.
* Save and Load Game: Save the current mod configuration and load the game.
* Load Game Without Saving: Discard the current the mod configuration and load the game using the previous mod configuration.

## Uninstalling Mods

To uninstall a mod, follow these steps:

1. Locate the mod you wish to remove within the `mods` folder in your installation folder.
2. Delete the mod folder.
