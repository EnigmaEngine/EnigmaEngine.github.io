{% include toc.html %}
# Modding Basics: Custom Story Weeks

Custom weeks are simultaneously easy to implement and highly flexible. You can create custom story weeks using mods without having to modify the code.

A custom week manages the following:
• What songs are in the week
• What graphics are used for the week
• Whether the week is unlocked by default and how to unlock it.

Follow these steps:

• Follow the [Modding Basics](/docs/modding-basics) guide to create a basic mod.
• Create a file `data/storymenu/weeks/<weekid>.json`. A week ID should be alphanumeric with dashes.
• Copy the below template into the new data file.
• Create a graphic to use for the week text
• Create a file `_append/data/weeknames.txt` in your mod folder.

## Important Notes
• To add additional weeks in the same mod, simply add another week data file and add another entry to the `weeknames` folder.
• Your mod can add as many weeks as you like, within reason.
• A week will be available on any difficulty its songs are available on, and ONLY on difficulties where all listed songs are available. At least one difficulty should be available but not all difficulties are necessary and custom difficulties can be used (see [Custom Difficulties]).

## Template

Here is the `dad.json` story week file as an example. The story week file specifies basic information about the story week.

```jsonc
{
    "name": "Daddy Dearest", // The name of the story week, as seen in the top right
    "assets": {
        "characters": ["dad", "bf", "gf"], // The black outline characters to render, as retrieved from `images/storymenu/characters/<name>.png`
        "title": "storymenu/weeks/week1", // The asset file to use for the title graphic, relative to `assets/images`
        "background": "#9271FD" // The background to use behind the story characters. This can either be the path to an asset or a hex color.
    },
    "startSound": "confirmMenu", // The sound to play when the week starts
    "unlocked": true, // Whether the week is unlocked by default
    "nextWeek": "pico", // The week to unlock after this week is completed
    "songs": [ // The songs that are in the week
        "bopeebo",
        "fresh",
        "dadbattle"
    ]
}
```