{% include toc.html %}
# Modding Basics: Custom Characters

You can create custom characters to use in songs without having to modify the code. You can also replace the default characters with your own custom skins, even ones that are larger or smaller than the vanilla sprites, without having to worry about broken offsets or mismatched animations.

To add a character using a mod, follow these steps:
• Follow the [Modding Basics](/docs/modding-basics) guide to create a basic mod.
• Create a shared/images/characters folder within 
• Create a data/characters folder within your mod directory, and create a <charid>.json file within that directory.
• Copy the text in the Template section below, and adapt it to your character.

## Important Notes

• No other steps are needed to "register" your character; when the game loads a song, it will simply look for a data file for the provided character ID.
• A character ID should be all alphanumeric characters and dashes.
• You can create a skin for an existing character, or even one for a character added by another mod, by creating a character data file with the same name in your mod.
• A single mod can add as many characters or skins as desired.

## Template

Here is the `bf.json` character file as an example. The character file specifies basic information about the character (such as what asset file to use) as well as information about each of the animations used.

```jsonc
{
  "name": "Boyfriend", // The readable name of the character
  "isGF": false, // If the character is a girlfriend or not
  "flipX": false, // If the character should be flipped horizontally
  "flipY": false, // If the character should be flipped vertically
  "asset": "characters/BOYFRIEND", // The asset file to use for the character
  "barColor": "#31B0D1", // The color of the health bar for the character
  "startingAnim": "idle", // The animation to play when the character is first loaded
  "isPixel": false, // When true, forcibly disable anti-aliasing so that pixel art characters look correct
  "scale": 1, // Multiplier for the character's size. Use 1 for default size and 6 for pixel art.
  "atlasType": "sparrow", // The atlas type to use for the character. Use "sparrow" for default atlas and "packer" for a packer atlas (currently only used on Spirit).
  "animations": [
    {
      "name": "idle", // The name the game uses for this animation
      "prefix": "BF idle dance", // The prefix to reference in the XML for this sprite sheet
      "offsets": [-5, 0], // The x and y offset relative to the other animations.
      "looped": true, // If the animation should loop
      "flipX": false, // If the animation should be flipped horizontally
      "flipY": false, // If the animation should be flipped vertically
      "frameRate": 24, // The frame rate of the animation
      "frameIndices": [] // The frame indices to use for this animation. If empty, use all frames with the given prefix.
    },
    {
      "name": "singUP",
      "prefix": "BF NOTE UP0",
      "offsets": [-29, 27]
    },
    {
      "name": "singLEFT",
      "prefix": "BF NOTE LEFT0",
      "offsets": [12, -6]
    },
    {
      "name": "singRIGHT",
      "prefix": "BF NOTE RIGHT0",
      "offsets": [-38, -7]
    },
    {
      "name": "singDOWN",
      "prefix": "BF NOTE DOWN0",
      "offsets": [-10, -50]
    },
    {
      "name": "singUPmiss",
      "prefix": "BF NOTE UP MISS",
      "offsets": [-29, 27]
    },
    {
      "name": "singLEFTmiss",
      "prefix": "BF NOTE LEFT MISS",
      "offsets": [12, 24]
    },
    {
      "name": "singRIGHTmiss",
      "prefix": "BF NOTE RIGHT MISS",
      "offsets": [-30, 21]
    },
    {
      "name": "singDOWNmiss",
      "prefix": "BF NOTE DOWN MISS",
      "offsets": [-11, -19]
    },
    {
      "name": "hey",
      "prefix": "BF HEY",
      "offsets": [7, 4]
    },
    {
      "name": "firstDeath",
      "prefix": "BF dies",
      "offsets": [37, 11]
    },
    {
      "name": "deathLoop",
      "prefix": "BF Dead Loop",
      "offsets": [37, 5]
    
    },
    {
      "name": "deathConfirm",
      "prefix": "BF Dead confirm",
      "offsets": [37, 69]
    },
    {
      "name": "scared",
      "prefix": "BF idle shaking",
      "offsets": [-4, 0]
    }
  ]
}
```