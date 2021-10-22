{% include toc.html %}
# Sparrow v2 - Animation Texture Atlas Format

It is far more efficient for a game to store individual parts of an animated sprite, or separate sprites which are often used in similar parts of a user interface, together in a single PNG texture file. However, in order for the game to know HOW to split up this texture, additional metadata is needed.

Sparrow v2 is the texture atlas format used by Flixel to load and render sprite sheets and animations. It provides a means for a single texture to contain multiple frames, which can later be referenced as needed. When Flixel needs an individual subtexture from a Texture Atlas, it will translate, rotate, scale, and clip the original image before rendering it, rather than loading each individual frame into memory separately. This is convenient to use for animations, but the individual textures can also be referenced as desired.

In Friday Night Funkin' and mods, these sprite sheets are used for nearly everything except Spirit's animations, which use a Packer atlas instead, and some background elements. <!-- We might document these later too. Not sure. - Prokube -->

The information in this document was written to be informative for users of Enigma Engine, but also users of other engines (such as Kade Engine, Psyche Engine, or vanilla Funkin) and of developers for other games using the HaxeFlixel game engine.

## Creating and Modifying Sparrow v2 Texture Atlas Files

You can create a Sparrow v2 texture atlas for what you need using one of the following tools:

* **Adobe Animate**: This is the most common method. If you have an existing animation, you can simply export it (see the directions below). However, it requires a paid subscription (or [sailing the high seas](https://www.youtube.com/watch?v=i8ju_10NkGY)).
* **[FNF Spritesheet and XML Generator](https://github.com/UncertainProd/FnF-Spritesheet-and-XML-Maker/releases)**: If you have a set of individual images you want to use, you can combine them with this program. Includes useful tools like duplicate frame detection and clipping out transparent pixels to make the image smaller (which means better performance for your users!).
* **[TexturePacker](https://www.codeandweb.com/texturepacker)**: Spritesheet building program similar to the FNF XML Generator, but it's a paid program with more features.
* **Manual Editing**: I wouldn't recommend building an XML from scratch, but if you just need to tweak something (one frame is a little too high, or shows a bit of the next frame on one side) it's much easier to do so this way. See the directions below.

### Creating a Texture Atlas in Adobe Animate

## Manual Editing: A Breakdown of the Sparrow v2 Specification

To edit a Sparrow v2 XML file, simply open it in any text editor. Notepad works but a program like [Notepad++](https://notepad-plus-plus.org/downloads/) or [Visual Studio Code](https://code.visualstudio.com/) is much more user friendly for this purpose, since they provide syntax highlighting and make it clear if you've made a mistake (like forgetting a quotation mark).

A Sparrow v2 XML file contains a Texture Atlas, which contains the data for one or more subtextures. Each of these subtextures can be accessed by the game.

See below for a fully valid example Texture Atlas, annotated with information on every attribute supported by HaxeFlixel.

``` xml
<?xml version="1.0" encoding="utf-8"?>
<!--
  The information above is important for the XML file format, but you shouldn't need to touch it.
  Below, we can see that we use a tag to define a Texture Atlas pointing to an image at the path `alphabet.png`.
  In HaxeFlixel in general (and Friday Night Funkin' specifically), the image is loaded separately from the XML,
  and thus the `imagePath` attribute is ignored.
-->
<TextureAtlas imagePath="alphabet.png">
  <!--
    The syntax with the < ! - - followed by - - > (without spaces),
    are used to denote a comment, which will be ignored when the atlas is parsed.
    The below comment is automatically added by Adobe Animate and can be safely ignored or removed. (stubid watermark let me mod in peace)
  -->
	<!-- Created with Adobe Animate version 21.0.1.37179 -->
	<!-- http://www.adobe.com/products/animate.html -->

  <!--
    Here we have a basic subtexture.
    From the top-left of the image, it moves 12 pixels to the left, then 368 pixels down,
    then takes a box 39 pixels wide and 44 pixels tall, and uses that as the sprite.
  -->
	<SubTexture name="Test" x="12" y="368" width="39" height="44" />
	
  <!--
    To create an animation, define multiple images with the same prefix on the name,
    and then a number indicating the frame number in the animation (starting at 0).
  -->
  <SubTexture name="Forward0000" x="0" y="368" width="39" height="44"/>
  <SubTexture name="Forward0001" x="0" y="368" width="39" height="44"/>
  <SubTexture name="Forward0002" x="39" y="368" width="39" height="44"/>
  <SubTexture name="Forward0003" x="39" y="368" width="39" height="44"/>

  <!--
    Fun fact, an easy way to create an animation which is the reverse or remixing of another one is to
    copy the original animation, rearrange the frames as desired, then change the frame numbers
    such that they are in order, like so:
  -->
  <SubTexture name="Backward0000" x="39" y="368" width="39" height="44"/>
  <SubTexture name="Backward0001" x="39" y="368" width="39" height="44"/>
  <SubTexture name="Backward0002" x="0" y="368" width="39" height="44"/>
  <SubTexture name="Backward0003" x="0" y="368" width="39" height="44"/>

  <!--
    Sub-textures can partially or fully overlap each other without conflicts.
  -->
  <SubTexture name="Testing" x="50" y="50" width="100" height="100" />
  <SubTexture name="MoreTesting" x="75" y="75" width="25" height="25"/>

  <!--
    HaxeFlixel supports many additional attributes on subtextures that grant a fine degree of control
    over how an individual frame appears. When used properly, this can save massive amounts of memory,
    since having a large graphic makes your game use more memory than a smaller graphic.
  -->

  <!--
    A frame's attributes allow you to define a larger frame in which your subtexture appears.

    Think of an explosion animation. At certain parts of the animation, parts of the texture
    will be completely empty, but are necessary to ensure the explosion will animate properly.

    With frame attributes, you cut out the transparent parts completely when generating your texture,
    then insert them afterward by defining the full size of the final image, as well as where in your image the texture should be positioned.

    frameWidth and frameHeight define the width and height of the final output image (which should ideally be the same through the whole animation),
    and frameX and frameY determine the horizontal and vertical position of your texture in that image.

    These values can be generated using any of the tools from the Creating Sparrow Atlas Files section above,
    but if one of them is wrong, the easiest fix is to just open up your XML file in a text editor and tweak them by hand.
  -->

  <!--
    The below subtexture only takes up 39 pixels by 63 pixels in the texture file,
    but in game it will render as though it was a 48 by 64 pixel texture,
    with the image itself starting 4 pixels from the left and 8 pixels from the top.
  -->
	<SubTexture name="TestB" x="370" y="202" width="39" height="63" frameX="4" frameY="8" frameWidth="48" frameHeight="64"/>

  <!--
    Why do more work? Why have more sprites in your file than you really need?
    Say we want to include four arrows in our spritesheet; you actually only really need one!

    The following attributes can help us here:
    * The flipX attribute mirrors the image horizontally before it is displayed.
    * The flipY attribute mirrors the image vertically before it is displayed.
    * The rotated attribute turns the image a quarter turn (90 degrees) before it is displayed.
  -->

  <!-- The base subtexture. -->
  <SubTexture name="LeftArrow" x="32" y="0" width="64" height="64"/>
  <!--
    Rotate the left 90 degrees. Now we have a second arrow sprite we can load,
    but the memory usage in-game is still the same! Nice!
  -->
  <SubTexture name="UpArrow" x="32" y="0" width="64" height="64" rotated="true" />
  <!--
    Flip the left arrow horizontally to get a right arrow.
  -->
  <SubTexture name="RightArrow" x="32" y="0" width="64" height="64" flipX="true" />
  <!--
    Flip the up arrow vertically to get a down arrow.
    See how we combine the two attributes to get the exact result we want? Easy!
  -->
  <SubTexture name="DownArrow" x="32" y="0" width="64" height="64" rotated="true" flipY="true" />

<!--
  Every tag in XML needs to be closed.
  For the SubTextures above, we use a / at the end to create a self-closing XML tag.
-->
</TextureAtlas>
```

To recap, the valid attributes of a `SubTexture` are:

* `name`: The name for the subtexture that the game will reference.
  - Required attribute.
  - For animations, use the correct prefix then suffix with numbers.

* `x`: The horizontal position in the image to pick the subtexture from.
  - Required attribute.
  - Cannot be further than the edge of the image.
* `y`: The vertical position in the image to pick the subtexture from.
  - Required attribute.
  - Cannot be further than the edge of the image.

* `width`: The horizontal size of the subtexture.
  - Required attribute.
  - Cannot be larger than the original texture.
* `height`: The vertical size of the subtexture.
  - Required attribute.
  - Cannot be larger than the original texture.

* `frameX`: The horizontal offset to move the sprite to in the final rendered texture.
  - Optional attribute.
  - Mainly used to add whitespace to an image.
* `frameY`: The vertical offset to move the sprite to in the final rendered texture.
  - Optional attribute.
  - Mainly used to add whitespace to an image.
* `frameWidth`: The full width of the final rendered texture.
  - Optional attribute.
  - Mainly used to add whitespace to an image.
* `frameHeight`: The full height of the final rendered texture.
  - Optional attribute.
  - Mainly used to add whitespace to an image.

* `flipX`: Set to `true` to flip the resulting image horizontally.
  - Optional attribute.
* `flipY`: Set to `true` to flip the resulting image vertically.
  - Optional attribute.
* `rotated`: Set to `true` to rotate the resulting image by 90 degrees.
  - Optional attribute.


## Handling Sprites in HaxeFlixel

In order to use a sprite sheet in HaxeFlixel, you simply need to create an FlxFrameCollection object; there is a utility function called `FlxAtlasFrames.fromSparrow` which will do this for you. `fromSparrow` needs the image source and the atlas description (the XML data); this can be either the contents of the file or the path to the file that should be loaded.

Once they're generated, simply assign them to a sprite and add animations based on the frame names (or prefix for frame names) you provide. For animated/sprite-based graphics, rather than use the [FlxSprite.loadGraphic()](https://api.haxeflixel.com/flixel/FlxSprite.html#loadGraphic) function, you should instead assign to `FlxSprite.frames` like so:

``` haxe
var spr = new FlxSprite(x, y);
spr.frames = FlxAtlasFrames.fromSparrow(pngPath, xmlPath);
// You can specify all the frames by individual 
spr.animation.addByNames('idle', ['GF IDLE 0001', 'GF IDLE 0002', 'GF IDLE 0003', 'GF IDLE 0004'])
```

Note that a given `FlxGraphic` will cache its own frame data and it can be retrieved using the static function `FlxAtlasFrames.findFrame(graphic)`;

Also note that, specifically in the case of Enigma, the `GraphicsAssets.loadSparrowAtlas(key, ?library, shouldCache)` function is provided as a convenient wrapper for `FlxAtlasFrames.fromSparrow`.
