---
layout: default
---

Enigma Engine is a project developed as a love letter to the open source game development community, and to the many talented people who have been developing mods for Friday Night Funkin'.

Built on Kade Engine v1.7.0, Enigma is striving to provide features to help hardcore players improve, as well as let casual players have more fun with the game. It's focused on providing powerful and useful features that modders need to create great mods with as little refactoring of the game's code as possible.

## Defining Features

### Actual modding, made simple for both users and developers

Engima's flagstone feature is its ModCore feature. Utilizing new improvements made to the Polymod library for Haxe, Enigma Engine boasts true mod support. No, not like the literal tens of thousands of people rebuilding the game with edited code to include new characters and songs, and no, not like Psych Engine which just reads the image files that you put in a folder.

For developers, it means being able to create custom characters, songs, and weeks without having to recompile the game. 

For users, this means installing a mod is as easy as dragging the download into the `mods` folder. It also means installing multiple mods at once without conflicts, using the mod menu to easily reorder, enable, or disable mods with as much ease as managing texture packs in Minecraft. Unlike vanilla FNF, uninstalling a skin pack just means deleting a folder.

No more 11GB Friday Night Funkin' folders. One release build, for all the mods.

Without having to ever touch the code, and in a manner compatible with existing mods, you can:
- Replace any existing assets (as in Skin Packs)
- Add new characters.
- Add new songs to Free Play.
- Add new weeks to Story Mode.
- Add new difficulties.

You can learn more about ModCore and its capabilities [here.](https://github.com/EnigmaEngine/EnigmaEngine/wiki/Modding-Guide)
Experience ModCore in action by playing the [Tricky Mod](https://github.com/EnigmaEngine/ModCore-Tricky-Mod), made compatible with ModCore!

### And lots more!

Enigma Engine also currently has the following features worth mentioning:
* Full 9-key support, including a charter and keybindings.
  * Enigma actually supports 1-key, 2-key, 3-key, 4-key, 5-key, 6-key, 7-key, 8-key, and 9-key.
* An improved charter and improved animation/stage debug views.

### Even more to come

Enigma Engine is constantly evolving, and we're looking to develop more features, such as the following:

* Allow for easy custom stages in 
* A rebuilt custom sound engine, to provide dy
* Actual working cutscenes for all platforms, including HTML5.
* A powerful scripting system powered by HScript (rather than Lua). Modcharts for Mac/HTML5 is just the tip of the iceberg, you can add custom functionality without touching the EXE.
* Localization support. Provide separate text or even separate assets (such as logos) to users in a foreign language. Want to make your mod available in Spanish? You can.
* Android support, to provide the same easy mod support to a fully maintained Android app.
