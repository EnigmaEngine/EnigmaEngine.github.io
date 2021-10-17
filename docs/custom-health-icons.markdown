{% include toc.html %}
# Modding Guide: Custom Health Icons

## Basic Health Icons

To create a basic health icon for your mod, perform the following steps.

* Create a basic mod with a character, see the [Modding Basics]() guide.
* Add an image to `images/icons/icon-<char>.png`, replacing `<char>` with the ID of your custom character.

This image is expected to be a 2-icon spritesheet, of size 300x150, like what Kade Engine uses.

## Advanced Health Icons

You may be wondering why an entire page was necessary for two sentences, here's why.

With a little extra work, and no extra code, you can create and implement animated health icons. This is more elaborate than even the implementation in Entity Origins: Breakout (the first mod I've seen use animated icons).

Here are the steps to create an animated health icon.
* Create a set of animations in Adobe Animate (or whatever software you use that can create Sparrow sprite atlases).
* Set the names of the animations to the following:
    - `idle-base`: This is the animation that will play most of the time.
    - `winning-base`: Plays when the current character is winning (for BF characters this is >80% health and for opponents this is when BF is <20% health)
    - `losing-base`: Plays when the current character is winning (<20% health for BF and >80% health for Dad)
    - `idle-winning`: Transition animation. When the `idle-base` animation is currently playing and the character would move to the winning state, the `idle-winning` animation will play, then the `winning-base` animation will play once complete.
    - `idle-losing`: Transition animation. Plays before moving to the `losing` state.
    - `winning-idle`: Transition animation. Plays when transitioning from the winning state back to the idle state.
    - `losing-idle`: Transition animation. Plays when transitioning from the losing state back to the idle state.
    - Note that the only mandatory animation here is `idle-base`. ANY other animation can be excluded and it just won't be played 
* Export the animation with the filename `icon-<char>.png`.
* Place the `icon-<char>.png` file in the `images/icons` folder of your mod, and the XML file directly next to it (make sure the XML has the same name!).
* No other steps are needed. Enigma Engine will detect the spritesheet is there and use the animations it finds.

For example, you can have your character's health icon play a normal animation, then play an animation of the character becoming angry, then play an angry animation until the player's health drops back down again.

See the flow graph below:

[INSERT IMAGE HERE]
