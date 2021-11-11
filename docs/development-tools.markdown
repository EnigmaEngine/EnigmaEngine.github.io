{% include toc.html %}
# Enigma Engine Development Tools

Now that you can compile and run the game from VSCode, you can start developing on features. However, you will likely experience one or more bugs or problems during development. Thankfully, powerful tools have been developed which Enigma Engine utilizes to their FULLEST.

### Breakpoints

When you run FNF as a Debug build from the Run and Debug menu, you get integration with VSCode's debugging tools. A set of controls will pop up, allowing you to stop, restart, or pause the game.

You can also set breakpoints; go to the line of code you are having trouble with, hover your mouse over the line number, and click the red dot on the left side. This creates a breakpoint; when the game reaches that particular line in the program, VSCode will pause it and show you useful information  in the left panel. This includes the call stack (which shows which functions were called by what other functions to get to this line), and a list of all local and member variables, which is very useful for determining the state of the program at a given point and diagnosing behavior.

While stopped at a breakpoint, you can click `Step Over` to move ahead one line in the program, `Step Into` to start stepping through the function being run on the current line, `Step Out` to continue running the program until the end of this function, or `Resume` to continue running the program until another breakpoint is hit.

### Crash Inspection

Sometimes the game will try to do something that doesn't make sense, like accessing an attribute of a null object. In this case, it will fail and the program will crash.

However, if you are running the game using the Run and Debug menu, VSCode will intercept this crash, find the line of code that caused it, and stop there like a breakpoint. This is very useful for diagnosing issues, since simply telling people that a Null Object Reference error occurred isn't useful unless you can show them what code is causing the error.

### HaxeFlixel Debugger

The third useful tool which Enigma has adapated itself to make full use of is the Debugger.

Among other things, the HaxeFlixel Debugger has the following tools:
* A Log view which outputs messages output by Haxe. These messages also show up in the VSCode Debug Console and in the log file (check `export/debug/<PLATFORM>/bin/log`).
* A Stats view with info about frame rate and memory usage.
* A VCR at the top which lets you pause the game or reset the current scene.
* A button at the top right which enables red boxes around each sprite.
* A Tools view that includes tools which allow you to select (Pointer), move (Mover), and transform (Transform) sprites.
* A Watch view, that lets you preview values you have set to be watched.
* A Console view you can type in.

You can drag these views around or hide them to suit your preferred layout.

### HaxeFlixel Console

The most powerful of these tools is definitely the console. You can type in most Haxe code into the console, and it will interpret and run it for you. Additionally, Enigma Engine has the unique feature of including several custom commands for the Debug Console, which are documented below

Name|Example|Description
----|-------|-----------
trackBoyfriend|`trackBoyfriend()`|Create a Tracker window displaying stats about the Boyfriend sprite.
trackGirlfriend|`trackGirlfriend()`|Create a Tracker window displaying stats about the Girlfriend sprite.
trackDad|`trackDad()`|Create a Tracker window displaying stats about the Dad sprite.
setLogLevel|`setLogLevel('WARN')`|Set the logging level; messages with lower significance are not displayed or written to the log file.
playSong|`playSong('Dad Battle', 2)`|Open the song with the given name and the given difficulty in Free Play,
chartSong|`chartSong('Dad Battle', 2)`|Open the song with the given name and the given difficulty in the Chart Editor.

If you have any other suggestions for console commands you feel would be useful for development, feel free to [suggest a feature](https://github.com/MasterEric/Enigma-Engine/issues).
