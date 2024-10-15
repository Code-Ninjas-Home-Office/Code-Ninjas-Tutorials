# Bug Collector
```package
hopper_assets=github:bmarslandCN/hopper_assets
```

```template
scene.setBackgroundImage(hopper_assets.computer)
let mySprite = sprites.create(hopper_assets.graceHopper, SpriteKind.Player)
```

```blocks
sprites.onOverlap(SpriteKind.Player, SpriteKind.Bug, function (sprite, otherSprite) {
    sprites.destroy(otherSprite)
    music.play(music.melodyPlayable(music.baDing), music.PlaybackMode.UntilDone)
    info.changeScoreBy(1)
})
let moth: Sprite = null
scene.setBackgroundImage(hopper_assets.computer)
game.splash("Bug Collector")
game.setDialogFrame(assets.image`frame`)
game.showLongText("Help computer scientist Grace Hopper collect as many bugs as possible before time runs out!", DialogLayout.Center)
let mySprite = sprites.create(hopper_assets.graceHopper, SpriteKind.Player)
controller.moveSprite(mySprite)
mySprite.setStayInScreen(true)
info.setScore(0)
game.onUpdateInterval(500, function () {
    moth = sprites.createProjectileFromSide(assets.image`moth`, randint(-50, 50), randint(-50, 50))
})
```

## 🦋 Bug Collector 🦋 @showdialog

Follow along with this tutorial to code a game where you help computer scientist Grace Hopper collect as many bugs as possible before time runs out!

![Project Example](https://github.com/sbannonCN/bug-collector/blob/master/bugColEx.gif?raw=true "Here is a project example!")

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo") 

## Who is Grace Hopper?

![Grace Hopper](https://github.com/sbannonCN/bug-collector/blob/master/graceHopper.PNG?raw=true "This is Grace Hopper.")

``|Grace Hopper|`` found the first **"bug"** in a computer program.  *It was an actual moth!*  

We now use the term **debugging** to mean fixing problems in code.

Click the ``|Next|`` button to get started.

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo") 

## Preview the Project

Look at the **Game Window** on the right of your screen to explore the project so far!

![Game Window](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/GameWindow.png?raw=true "Game Window") 


![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo") 

## Player Movement

Get Grace Hopper moving!

- :game controller: Open ``||controller:Controller||`` and drag ``||controller:move (mySprite) with buttons||`` into the *bottom* of the ``||loops(no click):on start||`` container. 
- :paper plane: Open ``||sprites:Sprites||`` and drag ``||sprites:set (mySprite) stay in screen||`` into the *bottom* of ``||loops(no click):on start||``.

Test your game! Use the **directional buttons** or your keyboard's **WASD** or **arrow keys** to move Grace Hopper around the screen.

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo") 

```blocks
scene.setBackgroundImage(hopper_assets.computer)
let mySprite = sprites.create(hopper_assets.graceHopper, SpriteKind.Player)
controller.moveSprite(mySprite)
mySprite.setStayInScreen(true)
```

## So Many Bugs, Part 1

Make a moth appear every 500 milliseconds.

- :circle: Open ``||game:Game||`` and drag ``||game:on game update every||`` 
to an empty spot in the code editor.
- :paper plane: Open ``||sprites:Sprites||`` and drag ``||variables(sprites):set [projectile] to||`` into ``||game(no click):on game update every||``.

Click the 💡 below to see if you're on the right track!

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo") 

```blocks
scene.setBackgroundImage(hopper_assets.computer)
let projectile: Sprite = null
let mySprite = sprites.create(hopper_assets.graceHopper, SpriteKind.Player)
controller.moveSprite(mySprite)
mySprite.setStayInScreen(true)
game.onUpdateInterval(500, function () {
    projectile = sprites.createProjectileFromSide(img`
        . . . . . . . . . . . . . . . . 
        . . . . . . . . . . . . . . . . 
        . . . . . . . . . . . . . . . . 
        . . . . . . . . . . . . . . . . 
        . . . . . . . . . . . . . . . . 
        . . . . . . . . . . . . . . . . 
        . . . . . . . . . . . . . . . . 
        . . . . . . . . . . . . . . . . 
        . . . . . . . . . . . . . . . . 
        . . . . . . . . . . . . . . . . 
        . . . . . . . . . . . . . . . . 
        . . . . . . . . . . . . . . . . 
        . . . . . . . . . . . . . . . . 
        . . . . . . . . . . . . . . . . 
        . . . . . . . . . . . . . . . . 
        . . . . . . . . . . . . . . . . 
        `, 50, 50)
})
```

## So Many Bugs, Part 2

- :mouse pointer: Click on ``||variables(no click):[projectile]||`` and select ``||variables(no click):Rename Variable...||``.  Type **moth** and click ``||loops(no click):Ok||``.
- :mouse pointer: Click the **grey square** and go to the ``||sprites(no click):Gallery||`` tab at the top. Select the **moth** image and click ``||loops(no click):Done||``.

Test your game! Do you see moths move across the screen every 500 ms?

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo") 

```blocks
let moth: Sprite = null
scene.setBackgroundImage(hopper_assets.computer)
let mySprite = sprites.create(hopper_assets.graceHopper, SpriteKind.Player)
controller.moveSprite(mySprite)
mySprite.setStayInScreen(true)
game.onUpdateInterval(500, function () {
    moth = sprites.createProjectileFromSide(hopper_assets.moth, 50, 50)
})
```

## Bugs Everywhere

Place the moth at random positions on screen.

- :calculator: Open ``||math:Math||`` and drag ``||math:pick random||`` into both the ``||sprites(no click):vx||`` **and** ``||sprites(no click):vy||`` bubbles.
- :mouse pointer: Set both to pick randomly from **-50** to **50**. 

Test your game! Do you see moths appear in random places across the screen?

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo") 

```blocks
let moth: Sprite = null
scene.setBackgroundImage(hopper_assets.computer)
let mySprite = sprites.create(hopper_assets.graceHopper, SpriteKind.Player)
controller.moveSprite(mySprite)
mySprite.setStayInScreen(true)
game.onUpdateInterval(500, function () {
    moth = sprites.createProjectileFromSide(hopper_assets.moth, randint(-50, 50), randint(-50, 50))
})
```

## 🎮 Playtest

In the ``||game(no click):on game update every||``, **500** is the interval value that sets how often a bug appears.  

``|Test this out!|``

- :mouse pointer: Change **500** to test out different values and see how they change the game. Select an interval value you like best.

**Iterating** - or making changes - is an important part of coding!

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo") 


## 🤔 Did you know?

Grace Hopper was one of the first computer programmers to work on the Harvard Mark I computer.

![computer](https://github.com/sbannonCN/bug-collector/blob/master/computer.PNG?raw=true "the Harvard Mark I computer")

The Harvard Mark I is one of the world's first programmable computers.

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo") 

## Create an Overlap Event 

Make something happen when Grace touches a bug.

- :paper plane: Open ``||sprites:Sprites||`` and drag ``||sprites:on (sprite) overlaps (otherSprite)||`` into the editor.
- :mouse pointer: Click on the *otherSprite* kind and select ``||sprites:Projectile||`` from the drop-down menu.

Click 💡 to see if you're on the right track!

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo") 

```blocks
sprites.onOverlap(SpriteKind.Player, SpriteKind.Projectile, function (sprite, otherSprite) {
	
})
let moth: Sprite = null
scene.setBackgroundImage(hopper_assets.computer)
let mySprite = sprites.create(hopper_assets.graceHopper, SpriteKind.Player)
controller.moveSprite(mySprite)
mySprite.setStayInScreen(true)
game.onUpdateInterval(500, function () {
    moth = sprites.createProjectileFromSide(hopper_assets.moth, randint(-50, 50), randint(-50, 50))
})
```

## Capture the bug!

- :paper plane: Open ``||sprites:Sprites||`` and drag ``||sprites:destroy (mySprite)||`` into the ``||sprites:overlaps||`` container.
- :mouse pointer: From the ``||sprites:overlaps||`` container, drag the ``||variables(no click):(otherSprite)||`` bubble to replace ``||variables:(mySprite)||`` in the ``||sprites(no click):destroy||`` block.

`||BONUS||` Click **⊕** to choose an effect.

Test your game! Does the bug disappear when Grace Hopper overlaps it?

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo") 

```blocks
sprites.onOverlap(SpriteKind.Player, SpriteKind.Projectile, function (sprite, otherSprite) {
    sprites.destroy(otherSprite)
})
let moth: Sprite = null
scene.setBackgroundImage(hopper_assets.computer)
let mySprite = sprites.create(hopper_assets.graceHopper, SpriteKind.Player)
controller.moveSprite(mySprite)
mySprite.setStayInScreen(true)
game.onUpdateInterval(500, function () {
    moth = sprites.createProjectileFromSide(hopper_assets.moth, randint(-50, 50), randint(-50, 50))
})
```

## Add a Sound Effect

- :headphones: Open ``||music:Music||`` and drag ``||music:play sound||`` into the ``||sprites:overlaps||`` container.
- :mouse pointer: Click ``||music:sound ba ding||`` to select a sound from the drop-down menu.

Test your game! Do you hear a sound when Grace Hopper overlaps a bug?

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo") 

```blocks
sprites.onOverlap(SpriteKind.Player, SpriteKind.Projectile, function (sprite, otherSprite) {
    sprites.destroy(otherSprite)
    music.play(music.melodyPlayable(music.baDing), music.PlaybackMode.UntilDone)
})
let moth: Sprite = null
scene.setBackgroundImage(hopper_assets.computer)
let mySprite = sprites.create(hopper_assets.graceHopper, SpriteKind.Player)
controller.moveSprite(mySprite)
mySprite.setStayInScreen(true)
game.onUpdateInterval(500, function () {
    moth = sprites.createProjectileFromSide(hopper_assets.moth, randint(-50, 50), randint(-50, 50))
})
```

## Set the Score

Earn a point for every bug caught!

- :id card: Open ``||info:Info||`` and drag ``||info:set score||`` into the *bottom* of the ``||loops(no click):on start||``.
- :id card: Open ``||info:Info||`` and drag ``||info:change score||`` into the *bottom* of the ``||sprites(no click):overlaps||`` container.

Test your game! Does the score increase when Grace Hopper overlaps a bug?

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo") 


```blocks
sprites.onOverlap(SpriteKind.Player, SpriteKind.Projectile, function (sprite, otherSprite) {
    sprites.destroy(otherSprite)
    music.play(music.melodyPlayable(music.baDing), music.PlaybackMode.UntilDone)
    info.changeScoreBy(1)
})
let moth: Sprite = null
scene.setBackgroundImage(hopper_assets.computer)
let mySprite = sprites.create(hopper_assets.graceHopper, SpriteKind.Player)
controller.moveSprite(mySprite)
mySprite.setStayInScreen(true)
info.setScore(0)
game.onUpdateInterval(500, function () {
    moth = sprites.createProjectileFromSide(hopper_assets.moth, randint(-50, 50), randint(-50, 50))
})
```

## Add a Timer 

- :id card: Open ``||info:Info||`` and drag ``||info:start countdown||`` into the *bottom* of the ``||loops(no click):on start||``.
- :mouse pointer: Set the timer length by changing the number in the white bubble.

Test your game! How many bugs can you catch before the timer runs out?

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo") 

```blocks
sprites.onOverlap(SpriteKind.Player, SpriteKind.Projectile, function (sprite, otherSprite) {
    sprites.destroy(otherSprite)
    music.play(music.melodyPlayable(music.baDing), music.PlaybackMode.UntilDone)
    info.changeScoreBy(1)
})
let moth: Sprite = null
scene.setBackgroundImage(hopper_assets.computer)
let mySprite = sprites.create(hopper_assets.graceHopper, SpriteKind.Player)
controller.moveSprite(mySprite)
mySprite.setStayInScreen(true)
info.setScore(0)
info.startCountdown(10)
game.onUpdateInterval(500, function () {
    moth = sprites.createProjectileFromSide(hopper_assets.moth, randint(-50, 50), randint(-50, 50))
})
```

## Title & Directions

- :circle: Open ``||game:Game||`` and drag ``||game:splash||`` into the *top* of the ``||loops(no click):on start||``.  
- :mouse pointer: Click the white bubble then type the game's title **Bug Collector**.
- :circle: Open ``||game:Game||`` and drag ``||game:show long text||`` under the ``||game(no click):splash||`` block.  
- :mouse pointer: Click the white bubble then type the directions for the game.

Test your game! Do you see the game title and instructions appear before the game starts?

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo") 

```blocks
sprites.onOverlap(SpriteKind.Player, SpriteKind.Projectile, function (sprite, otherSprite) {
    sprites.destroy(otherSprite)
    music.play(music.melodyPlayable(music.baDing), music.PlaybackMode.UntilDone)
    info.changeScoreBy(1)
})
let moth: Sprite = null
scene.setBackgroundImage(hopper_assets.computer)
game.splash("Bug Collector")
game.showLongText("Help computer scientist Grace Hopper collect as many bugs as possible before time runs out!", DialogLayout.Bottom)
let mySprite = sprites.create(hopper_assets.graceHopper, SpriteKind.Player)
controller.moveSprite(mySprite)
mySprite.setStayInScreen(true)
info.setScore(0)
info.startCountdown(10)
game.onUpdateInterval(500, function () {
    moth = sprites.createProjectileFromSide(hopper_assets.moth, randint(-50, 50), randint(-50, 50))
})
``` 

## 🎮 Playtest

Try these modifications to the on-screen dialog box!

``|Test this out!|``

- :mouse pointer: In ``||game(no click):show long text||``, click on **bottom** and select a different position from the drop-down menu. Try them all and see which one you like best!
- :circle: Open ``||game:Game||`` and drag ``||game:set dialog frame||`` *before* ``||game(no click):show long text||``. Click on the grey oval to draw or choose a frame.

**Iterating** - or making changes - is an important part of coding!

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo") 

```blocks
sprites.onOverlap(SpriteKind.Player, SpriteKind.Projectile, function (sprite, otherSprite) {
    sprites.destroy(otherSprite)
    music.play(music.melodyPlayable(music.baDing), music.PlaybackMode.UntilDone)
    info.changeScoreBy(1)
})
let moth: Sprite = null
scene.setBackgroundImage(hopper_assets.computer)
game.splash("Bug Collector")
game.setDialogFrame(hopper_assets.frame)
game.showLongText("Help computer scientist Grace Hopper collect as many bugs as possible before time runs out!", DialogLayout.Center)
let mySprite = sprites.create(hopper_assets.graceHopper, SpriteKind.Player)
controller.moveSprite(mySprite)
mySprite.setStayInScreen(true)
info.setScore(0)
game.onUpdateInterval(500, function () {
    moth = sprites.createProjectileFromSide(hopper_assets.moth, randint(-50, 50), randint(-50, 50))
})
```

## 😍 Share your project!

Your game is now complete! Click the **Done** button to save your project and create a shareable link so others can play your game, too!

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo") 
