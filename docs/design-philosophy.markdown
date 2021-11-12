{% include toc.html %}
# Enigma Engine's Design Principles

When working on the Enigma Engine project, I've had several goals to direct development of features for the engine. Enigma Engine should be:

* **Featureful for pros**

Practicing and experienced rhythm game players want features like downscroll and accuracy reports to help them improve, and those who want a special challenge should be able to use modifiers like Hardcore.

* **Easy to use for beginners**

All that fancy stuff for pros should be optional, and players wanting a stable and standard FNF experience should be able to find it with Enigma. No more frustratingly hard to use, no more frustratingly hard to learn. Just a simple, intuitive experience. 

* **Painless for beginner coders**

The ideal end goal is that a person should be able to create a basic full week mod, with custom songs, characters, stages, and cutscenes, without touching a line of code.

* **Powerful for experienced coders**

The modding system provides a system of script hooks, FAR more powerful than Lua modcharts can be, with near-limitless potential to allow hooking into the game without recompiling it. Custom note types, custom menus, and more. 

* **Free, open source software**

Enigma Engine is free, open source software, and should be available to anyone who wants to make a rhythm game mod or use it for their personal projects. In the spirit of open source, Enigma Engine is distributed under the [Apache 2.0 license](https://www.apache.org/licenses/LICENSE-2.0).

[Contributions](https://github.com/EnigmaEngine/EnigmaEngine/pulls) and [bug reports](https://github.com/EnigmaEngine/EnigmaEngine/issues) are welcome, and we will to respond to them as quickly as possible.

* **Accessible for users with special needs**

Some users experience problems with flashing lights and colors and options should be available for them. Other users have special needs in terms of controls; while many use keyboard others use things like gamepads, guitar controllers, or special controllers built for rhythm games. Enigma should provide support for all of these.

* **Inclusive for users of other languages**

One major feature in development is native support for localization. Modders wanting to make their creations available in French, Italian, German, Spanish, Russian,  Portuguese, or whatever language they want should be able to substitute dialogue and even assets (like logos) without requiring advanced coding knowledge. The base game should be available in multiple languages, and mods should be able to be translated into any language.

Mods such as vs Rosie and Doki Doki Takeover support localization, but this is hardcoded into the game.
