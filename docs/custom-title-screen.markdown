{% include toc.html %}
# Modding Guide: Custom Title Screen

The title screen is highly customizable, and almost fully driven by a single data file.

Follow these steps:

1. Prepare any custom assets you want for the custom title. This could include a custom `logoBumpin`, a custom `gfDanceTitle`, a custom `titleEnter` (the blinking text at the bottom), custom credits graphics, or custom backgrounds for the title screen or credits.

2. Copy the [default title screen file](https://github.com/EnigmaEngine/EnigmaEngine/blob/develop/assets/preload/data/titleScreen.json) and paste it to `mods/<mod-id>/data/titleScreen.json`. Modify the content as needed.

## Title Screen Data Format

The title screen is specified in a JSON file containing the following attributes:

* `_comment` : n ignored attribute and can be used to provide documentation to any users reading the file.
* `creditsBackground` : specifies the background of the intro credits. It is either a hex color string (like `#00FF00`) or the name of a graphic (relative to either `assets/preload/images` or `mods/<mod-id>/images`).
* `titleBackground` : specifies the background of the title screen. It is either a hex color string (like `#00FF00`) or the name of a graphic (relative to either `assets/preload/images` or `mods/<mod-id>/images`).
* `beatDropMs` : If the user presses ENTER to skip the intro, the music is skipped to the proper position to match. Use this to set the time it should skip to, in ms. Set the value to `-1` to disable skipping entirely.
* `bpm` : Beats per minute of the song.
  * Affects the speed of the intro credits and of the animations on the title screen.
* `gf` : Attributes that control how the `gfDanceTitle` sprite is rendered. Useful if you have replaced it with a custom one but need to move it around.
  * `x` : The horizontal position.
  * `y` : The vertical position.
  * `scale` : The size.
* `logoBumpin` : Attributes that control how the `logoBumpin` sprite is rendered. Useful if you have replaced it with a custom one but need to move it around.
  * `x` : The horizontal position.
  * `y` : The vertical position.
  * `scale` : The size.
  * `angle` : Aside from playing its animation, the logo also rotates back and forth.
  * `duration` : The animation moves from `-angle` to `+angle` over `duration` seconds, then goes back.
* `credits` : An array of actions to perform at each beat of the song during the intro credits. This can include displaying text or graphics.
  * Each element of credits is either a single action object, or an array of action objects. For each beat of the song, the corresponding  entry (or entries) are read and the actions are performed.
  * Each credits element has some of the following attributes:
    * `action` : The action to perform. Can be `addText`, `clearText`, `addWackyText`, `setTextOffset`, `reloadWackyText`, `setGraphic`, `clearGraphic`, `setBackground`, or `wait`.
    * `value` : If the action takes a single argument, specify it here.
    * `values` : If the action takes multiple arguments, specify it here.

Below are examples of all the credits actions:
```jsonc
// Note that Enigma utilizes a custom JSON parser which provides support for comments.
// You don't need to be picky with your JSON syntax either. Missing commas are fine.
"credits": [
  {
    // This action will be performed at the first beat of the song.
    // addText adds text to the credits screen.
    // It takes multiple arguments, one for each line of text to be added.
    "action": "addText",
    "values": ["Hello, world!", "This is a test."]
  },
  {
    // This action will be performed at the second beat of the song.
    // wait simply does nothing for a beat.
    // If this action weren't here, the next action would be performed on the second beat instead of the third.
    "action": "wait"
  },
  {
    // Add more text
    "action": "addText",
    "values": ["Foobar"]
  },
  [
    // We are performing multiple actions this beat. Note the array these actions were put into to group them together.
    {
      // This action clears all credits text on screen. It takes no arguments.
      "action": "clearText"
    },
    {
      // setTextOffset sets the vertical offset of the text.
      // It takes a single argument, the value to offset by.
      // The offset change lasts until you change it again.
      "action": "setTextOffset",
      "value": -135
    },
    {
      // Add some credits text. It will be offset by the setTextOffset value."
      "action": "addText",
      "values": ["We made this mod."]
    }
  ],
  {
    "action": "wait"
  }
  {
    // setGraphic displays a graphic over the title screen!
    // It takes one argument: The name of a graphic (relative to either `assets/preload/images` or `mods/<mod-id>/images`).
    // If you make an animation for the graphic and title it 'Animation' in the XML file, it'll play when you set the graphic. Pretty cool.
    // Remember, you can only display one graphic at a time, and you can't reposition it.
    "action": "setGraphic",
    "value": "daCrew"
  },
  {
    // Remember, if the credits are going by too fast, add wait actions.
    // If they are going too slow, perform multiple actions in one beat.
    // If they are moving off-beat with your intro song's tempo, remember to change the BPM.
    "action": "wait"
  },
  [
    {
      // clearGraphic removes the graphic you added earlier with setGraphic.
      "action": "clearGraphic"
    },
    {
      // Here we again perform more than one action per beat.
      // addWackyText adds a randomly selected entry from introText.txt to the screen.
      // It takes multiple arguments; an array of which lines of the entry to display.
      // You can display more than one line at once and you can display more than two lines total, unlike the vanilla game.
      "action": "addWackyText",
      "values": [0, 1, 2]
    },
    {
      // setBackground lets you change the background. It takes one value.
      // It is either a hex color string (like `#00FF00`)
      // or the name of a graphic (relative to either `assets/preload/images` or `mods/<mod-id>/images`).
      "action": "setBackground",
      "value": "#330000"
    }
  ],
  [
    {
      "action": "clearText"
    },
    {
      // When the title sequence first starts, a random entry from introText.txt is chosen.
      // If you want to display another entry, you can usse the reloadWackyText action to choose a new one.
      "action": "reloadWackyText"
    },
    {
      "action": "addWackyText",
      "values": [0, 1, 2]
    }
  ]
]
```

If you want a good reference, check out the implementation in the [Tricky Mod example](https://github.com/EnigmaEngine/modCore-Tricky-Mod), which utilizes custom graphics and text to implement [the title screen](https://www.youtube.com/watch?v=bb1YqSiVDQY).
