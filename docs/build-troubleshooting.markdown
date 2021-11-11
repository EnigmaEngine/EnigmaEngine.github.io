{% include toc.html %}
# Build Troubleshooting

This document lists common problems alongside their solutions. If you try to post an issue about one of these, either give details on why the solution below didn't work, or prepare for [vicious mockery](https://roll20.net/compendium/dnd5e/Vicious%20Mockery#content).

If you have solved a commonly experienced issue, please feel free to expand on it here.

## Error: Source path "C:/HaxeToolkit/haxe/lib/extension-webm/git/ndll/Windows64/extension-webm.ndll" does not exist

Make sure you have installed the latest version of all dependencies. There are convenient setup scripts for most platforms available in the `scripts` directory.

## GetThreadContext failed!

As best I can tell, this issue is caused by an out-of-memory error when trying to build the game. If this error occurs, you're probably multi-tasking by running something computationally expensive in the background.

## source/WebmHandler.hx:33: characters 8-12 : webm.WebmPlayer has no field fuck

You are using an incorrect version of extension-webm. See **extension-webm.ndll** does not exist.

## Could not find haxelib "hxvm-luajit", does it need to be installed?

Make sure you have installed the latest version of all dependencies. There are convenient setup scripts for most platforms available in the `scripts` directory.

## Type not found : StatePointer

Make sure you have installed the latest version of all dependencies. There are convenient setup scripts for most platforms available in the `scripts` directory.

## ../lib/lua/src/lua.hpp: No such file or directory

This error may occur if you are building on a system with case sensitive file system (MacOS or Linux). This is an issue with the linc_luajit and a pull request needs to be merged in order to fix it.

In the meantime, run the following lines in your command prompt to use a fork:

```
haxelib remove linc_luajit
haxelib git linc_luajit https://github.com/MasterEric/linc_luajit.git
```

## Warning: Could not find Visual Studio 2017 VsDevCmd

```
Warning: Could not find Visual Studio 2017 VsDevCmd
Missing HxCppVars
Error: Could not automatically setup MSVC
```

This error occurs if you don't have the proper Windows build dependencies installed. Run the `script/setup_Windows.bat` file and make sure to select Yes when prompted to download the Visual Studio Community tools.

## Error: Cannot copy to "export/debug/windows/bin/lime.ndll", is the file in use?

This error occurs if you try to compile the game while it's still running in the background. Please close the game, then try again.

## Null Object Reference

This is a coding error. It occurs when you attempt to access an attribute of a null object. Check your code and look for places where the object may not be defined.

When diagnosing this error, VSCode can point you to the relevant code if you are using the debugger. See [Development Tools](/docs/development-tools#crash-inspection) for more information.

## Null Function Reference

This is a coding error. It occurs when you attempt to call a function on an object but that function does not exist. Check your code and look for places where the object may be a different type than expected.

When diagnosing this error, VSCode can point you to the relevant code if you are using the debugger. See [Development Tools](/docs/development-tools#crash-inspection) for more information.

## Visual C++ Runtime Library: Assertion Failed!

I get this error all the time, but I haven't the foggiest what's causing it. The program will often work if you abort the program and start it again.

## Uncaught exception - Could not find NekoAPI interface.

No idea what causes this one, sorry.
