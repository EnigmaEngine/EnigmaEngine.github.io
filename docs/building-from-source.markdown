{% include toc.html %}
# Building Enigma Engine from Source

Building Enigma Engine is easy, as long as you follow the guide carefully. If you miss a step, and an error pops up, it's your fault and not mine.

Note that this guide is for developers who want to contribute changes to the Enigma Engine itself.

* If you just want to play the game, click the link in the header of this page.
* If you want to make a basic mod, go to the [Modding Basics guide](/docs/modding-basics) instead.

## Prerequisites

* A machine with the platform you want to build for. You can't make a Windows build on a Mac, you can't make a Linux build on Windows, etc.
    * If you're making a build for HTML5/browser, you can use any platform.
* Familiarity with the command line for your operating sytem (Powershell or CMD on Windows, the terminal on Mac/Linux).
* [Visual Studio Code](https://code.visualstudio.com/), the preferred development environment for Enigma Engine. The repo includes several launch configurations and settings for VS Code that make development easier.

## Pro Tip

Make sure you go into your Windows Defender settings and [make an exclusion for any development folders](https://support.microsoft.com/en-us/windows/add-an-exclusion-to-windows-security-811816c0-4dfd-af4a-47e4-c301afe13b26). Otherwise, Windows will scan all your binaries as you generate them, causing a massive performance hit.

## Dependencies

You will need to install the following dependencies:
* Git
    * On Windows and MacOS platforms, you can download this from [git-scm](https://git-scm.com/downloads).
    * On Linux platforms, use the package manager for your distro. If you're on Ubuntu, run `sudo apt install git`. If you're not on Ubuntu, you already know how to install Git.
* Haxe (Latest Version)
    * If you're already using 4.1.5, that should work fine, but the 4.2.x versions are also fully compatible.
    * On Windows and MacOS, you can download Haxe from [haxe.org](https://haxe.org/download/).
    * On Linux, the setup script will install Haxe for you. See [Running the Setup Script](#running-the-setup-script) below.

### Windows Visual Studio Dependencies

This one is a pain. If you're on Windows, building for it requires installing several gigabytes of SDKs.

Thankfully, the setup script will install them for you. See [Running the Setup Script](#running-the-setup-script) below.

## Downloading the Game

We're going to use Git to clone the repository.

PRO TIP: If you're looking to become an experienced programmer, you need to learn to use Git and use it well. Do some research and find some good tutorials that explain how a Git repository is structured and how to properly interact with one.

If you're just looking to build the game, perform the following steps:

* Open the command line and use `cd` to navigate to the directory where you want to put the game.
* Run the following command:
```
git clone https://github.com/MasterEric/Enigma-Engine
```
* The uncompiled game files will now be in the directory you set.
* (OPTIONAL) If you want to use a specific version of Engima Engine, run `cd` to enter the folder, then run `git checkout 0.1-EE` or whatever version you want to download.

## Running the Setup Script

THIS IS AN IMPORTANT STEP. You need to run the setup script even if you have built other Friday Night Funkin' mods, before, including Kade Engine or Psyche Engine.

On the Windows and Linux platforms, scripts are available to perform the process of downloading the necessary dependencies and preparing to build Enigma Engine.

* On Windows, run `scripts/setup_Windows.bat`.
* On Linux Ubuntu, run `scripts/setup_Ubuntu.sh`.

## Compiling the Game
There are two ways to build and run the game during development:

You can simply run `lime build windows`, but this is a bit clunky and it also misses out on a bunch of useful tools.

The recommended method is the following:

* Open Visual Studio Code and open the repository folder.
* When the workspace opens, you will be presented with a popup telling you to install some recommended extensions. Do this (you'll only have to do this once).
    * This will add support for Haxe syntax highlighting, Haxe code style formatting, support for the Lime build tool, and support for the HXCPP debugger.
* Click the arrow in the left side to switch to the Run and Debug tab.
* Select the platform you want from the dropdown and click the Run button.

This will automatically rebuild the game for you, then run the game, with debugging features enabled. Check out the page on [Development Tools](/docs/development-tools) for more information on the game's development tools.
