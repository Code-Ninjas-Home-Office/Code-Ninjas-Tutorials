# Defeat The Malware Tutorial 
```package
malware_assets=github:bmarslandCN/malware_assets
```

## Defeat the Malware! @showdialog
You will be coding a program to destroy the malware that has infected your computer! 

![screen image](https://github.com/Code-Ninjas-Home-Office/Code-Ninjas-Tutorials/blob/master/images/malware_screen.gif?raw=true "screen image")

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo")

```template 
function malwareRemover () { 
    scene.setBackgroundImage(malware_assets.blueScreen) 
    remover = sprites.create(img`
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
    `, SpriteKind.Player) 
    remover.setStayInScreen(true)
} 

sprites.onOverlap(SpriteKind.Player, SpriteKind.Enemy, function (sprite, otherSprite) { 

}) 

info.onCountdownEnd(function () { 
    game.setGameOverMessage(false, "GAME OVER!") 
    game.gameOver(false) 
}) 

sprites.onDestroyed(SpriteKind.Enemy, function (sprite) { 
    count += 1
    if (count == 70) { 
        game.splash("All Malware Removed!") 
        scene.setBackgroundColor(8) 
        game.setGameOverEffect(true, effects.confetti) 
        game.gameOver(true) 
    } else { 
        if (count >= 15 && count < 30) { 
            scene.setBackgroundImage(malware_assets.redScreen)
            controller.moveSprite(remover, -100, -100) 
        } else if (count >= 30 && count < 45) { 
            scene.setBackgroundImage(malware_assets.purpleScreen)
            remover.setVelocity(50, 50) 
            remover.setBounceOnWall(true) 
            controller.moveSprite(remover, 0, 0) 
        } else if (count >= 45 && count < 60) { 
            scene.setBackgroundImage(malware_assets.blackScreen)
            remover.setVelocity(0, 0) 
            controller.moveSprite(remover, 0, 0) 
        } else if (count >= 60 && count < 70) { 
            scene.setBackgroundImage(malware_assets.whiteScreen)
            controller.moveSprite(remover, 10, 10) 
        }
    } 
}) 

function createMalware () { 
    pause(500) 
    for (let index = 0; index < 70; index++) { 
        malware = sprites.create(malware_assets.malwareImage, SpriteKind.Enemy)
        animation.runImageAnimation(malware,  [img`
            ......11.......11...... 
            ...111ff1.....1ff111... 
            ..1fff11111.11111fff1.. 
            ..1ff111ff1.1ff111ff1.. 
            .1ff1111ff111ff1111ff1. 
            1ff111fffffffffff111ff1 
            1ff111fffffffffff111ff1 
            1ff1fff111fff111fff1ff1 
            1ff1fff111fff111fff1ff1 
            1ff1fff111fff111fff1ff1 
            .1f1fff111fff111fff1f1. 
            .1fffffffffffffffffff1. 
            ..1fffffffffffffffff1.. 
            ...11fffffffffffff11... 
            ...1111fff111fff1111... 
            .....11fff1.1fff1...... 
            ....1111111.1111111.... 
            ....1ff1.......1ff1.... 
            ....1ff1.......1ff1.... 
            ....1111.......1111.... 
            `, img`
            ....................... 
            ......11.......11...... 
            ...111ff1.....1ff111... 
            ..1fff11111.11111fff1.. 
            ..1ff111ff1.1ff111ff1.. 
            .1ff1111ff111ff1111ff1. 
            1ff111fffffffffff111ff1 
            1ff111fffffffffff111ff1 
            1ff1fff111fff111fff1ff1 
            1ff1fff111fff111fff1ff1 
            .1f1fff111fff111fff1f1. 
            .1fffffffffffffffffff1. 
            ..1fffffffffffffffff1.. 
            ...11fffffffffffff11... 
            ...1111fff111fff1111... 
            .....11fff1.1fff1...... 
            ....1111111.1111111.... 
            ....1ff1.......1ff1.... 
            ....1ff1.......1ff1.... 
            ....1111.......1111.... 
            `], 200, true) 
        malware.setPosition(randint(0, 120), randint(0, 160)) 
        malware.setVelocity(randint(15, 50), randint(15, 50)) 
        malware.setBounceOnWall(true) 
        pause(100) 
    } 
} 

let malware: Sprite = null 
let count = 0 
let remover: Sprite = null 
malwareRemover() 
createMalware() 
``` 

## Step 1 

Oh no, the malware is everywhere! We need to code a program to remove it. 

- Scroll to the right in your workspace until you see a ``||function:malwareRemover||`` function 

This is where you will start putting your code. Once you found it go ahead and move onto the next step. 

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo")
  
```blocks 
function malwareRemover () { 
    scene.setBackgroundImage(malware_assets.blueScreen)
    let remover = sprites.create(img`
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
    `, SpriteKind.Player) 
} 
``` 

## Step 2 
Good job finding it! Now you need to make your own malware remover. 

- In the ``||sprites:set remover to Player||`` block, select the grey bubble to make your own remover  
- You can click on the ``||sprites:Gallery||`` to pick a ``||sprites:sprite||`` or stay in the ``||sprites:Editor||``  to draw your own 

Spend no more than 10 minutes designing your remover. 

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo")

```blocks 
function malwareRemover () { 
    scene.setBackgroundImage(malware_assets.blueScreen)
    let remover = sprites.create(malware_assets.removerImage, SpriteKind.Player) 
} 
``` 

## Step 3 

Looks awesome. Now we need a way to move the ``||variables:remover||`` around.  

- Open ``||controller:controller||`` and drag out a ``||controller:move mySprite with buttons||`` block and place it inside the ``||function:malwareRemover||`` function 
- Select ``||variables:mySprite||`` and change it to ``||variables:remover||``  
- Try moving the remover around! 

What happens when more malware spawns? 

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo")

```blocks 
function malwareRemover () { 
    scene.setBackgroundImage(malware_assets.blueScreen)
    let remover = sprites.create(malware_assets.removerImage, SpriteKind.Player) 
    controller.moveSprite(remover) 
} 
``` 

## Step 4 

Ok now we need to start removing this malware. 

- Scroll to the left until you see an ``||sprites:on sprite overlap||`` container 

This will make something happen when your ``||sprites:sprite||``  of kind Player ``||variables:remover||`` overlaps with an other ``||sprites:sprite||`` of kind Enemy ``||variables:malware||`` 

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo")

```blocks 
sprites.onOverlap(SpriteKind.Player, SpriteKind.Enemy, function (sprite, otherSprite) { 

}) 
``` 

## Step 5 

Time for the if-then statements. When the remover overlaps with the malware, and if the A button is pressed the malware will get destroyed. 

- Open ``||logic:Logic||``, and drag out an ``||logic:if true then||`` block and place it inside the ``||sprites:on sprite overlap||`` container 
- Open ``||controller:Controller||``, and drag out an ``||controller:is A button pressed||`` condition 
- Replace the ``||logic:true||`` condition with the ``||controller:is A button pressed||`` condition 

The rest of our code is going to go inside of this ``||logic:if then||`` statement so malware is only removed if the remover is overlapping with the malware and the A button is pressed. 

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo")

```blocks 
sprites.onOverlap(SpriteKind.Player, SpriteKind.Enemy, function (sprite, otherSprite) { 
    if (controller.A.isPressed()) { 

    } 
}) 
``` 

## Step 6 

This malware is pretty powerful! Time to add the code to destroy the malware 

- Open ``||sprites:Sprites||``, and drag out a ``||sprites:destroy mySprite||`` block into the  ``||sprites:on sprite overlap||`` container 
- Drag the  ``||variables:otherSprite||`` variable from the overlap container into the  ``||sprites:destroy mySprite||`` block 
- Click the  ``||sprites:+||`` to change the effect and how long the effect lasts 
- Test out different effects to see what happens 

Defeat all the malware! What happens the more you destroy the malware? 

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo")

```blocks 
sprites.onOverlap(SpriteKind.Player, SpriteKind.Enemy, function (sprite, otherSprite) { 
    if (controller.A.isPressed()) { 
        sprites.destroy(otherSprite, effects.disintegrate, 200) 
    } 
}) 
``` 

## Step 7 

Time to add some difficulty with a timer! 

- Open ``||info:Info||``, and drag out a ``||info:start countdown||`` block into the ``||function:malwareRemover||`` function 
- Click the white circle and type in the number ``||info:60||`` 

Now you will have 60 seconds to destroy all the malware before the time runs out! 

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo")

```blocks 
function malwareRemover () { 
    scene.setBackgroundImage(malware_assets.blueScreen)
    let remover = sprites.create(malware_assets.removerImage, SpriteKind.Player) 
    controller.moveSprite(remover) 
    info.startCountdown(60) 
} 
``` 

## Step 8 

Great work! Add some customizations 

- Can edit the ``||variables:remover||`` sprite  
- Can change the ``||sprites:destroy sprite||`` effect 
- Add a ``||music:sound effect||`` into the ``||logic:if then ||`` block 
- Change the ``||info:start countdown||`` block 
- Adjust the ``||game:game over message||`` in the ``||info:on countdown end||`` block 

Have fun with this! 

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo")

```blocks 
sprites.onOverlap(SpriteKind.Player, SpriteKind.Enemy, function (sprite, otherSprite) { 
    if (controller.A.isPressed()) { 
        sprites.destroy(otherSprite, effects.disintegrate, 200) 
        music.play(music.melodyPlayable(music.beamUp), music.PlaybackMode.UntilDone)
        effects.bubbles.startScreenEffect(200) 
    } 
}) 

function malwareRemover () { 
    scene.setBackgroundImage(malware_assets.blueScreen)
    let remover = sprites.create(malware_assets.removerImage, SpriteKind.Player) 
    controller.moveSprite(remover) 
    info.startCountdown(100) 
} 

info.onCountdownEnd(function () { 
    game.setGameOverMessage(false, "YOU LOSE") 
    game.gameOver(false) 
}) 
``` 
