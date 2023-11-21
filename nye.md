# New Year, New Code!
### @diffs true

```typescript
// background code
scene.setBackgroundImage(nyeImg.backgroundImage)
let nyePole = sprites.create(nyeImg.poleImage, SpriteKind.Player)
nyePole.setPosition(80, 60)

// countdown image array
let countdownArray = [
    nyeImg.img10,
    nyeImg.img09,
    nyeImg.img08,
    nyeImg.img07,
    nyeImg.img06,
    nyeImg.img05,
    nyeImg.img04,
    nyeImg.img03,
    nyeImg.img02,
    nyeImg.img01
]

// nye ball drop code
let nyeBall = sprites.create(nyeImg.ballImageLarge, SpriteKind.Player)
nyeBall.setPosition(80, 0)
let isBallDropStarted = false
game.splash("Press A to start the", "New Years Countdown!")

// nye ball drop event
controller.A.onEvent(ControllerButtonEvent.Pressed, function () {
    if (!(isBallDropStarted)) {
        isBallDropStarted = true
        callBallDrop()
    }
    music.play(music.createSong(nyeImg.nyeSong), music.PlaybackMode.InBackground)
    callFireworks()
})

// nye ball drop functions
function callBallDrop () {
    for (let index = 0; index < 10; index++) {
        let countdownNum = sprites.create(countdownArray.shift(), SpriteKind.Player)
        countdownNum.setPosition(80, 60)
        for (let index = 0; index < 5; index++) {
            pause(200)
            countdownNum.changeScale(0.5, ScaleAnchor.Middle)
        }
        nyeBall.y += scene.screenHeight() / 10
        sprites.destroy(countdownNum)
    }
}

function callFireworks () {
    let fireworks1 = sprites.create(nyeImg.fireworkImageOrange, SpriteKind.Player)
    let fireworks2 = sprites.create(nyeImg.fireworkImageGreen, SpriteKind.Player)
    fireworks1.setPosition(43, 57)
    fireworks2.setPosition(117, 73)
    animation.runImageAnimation(fireworks1, assets.animation`fireworkAnimOrange`, 100, true)
    animation.runImageAnimation(fireworks2, assets.animation`fireworkAnimGreen`, 200, true)
}
```

```template
// background code
scene.setBackgroundImage(nyeImg.backgroundImage)
let nyePole = sprites.create(nyeImg.poleImage, SpriteKind.Player)
nyePole.setPosition(80, 60)

// countdown image array
let countdownArray = [
    nyeImg.img10,
    nyeImg.img09,
    nyeImg.img08,
    nyeImg.img07,
    nyeImg.img06,
    nyeImg.img05,
    nyeImg.img04,
    nyeImg.img03,
    nyeImg.img02,
    nyeImg.img01
]

// nye ball drop code

// nye ball drop event
controller.A.onEvent(ControllerButtonEvent.Pressed, function () {

})

// nye ball drop functions
function callBallDrop () {

}

function callFireworks () {

}
```

## New Year, New Code! @showdialog

The New Year is a great time to try something new! Let's try out some coding in JavaScript - which is what you'll use in IMPACT's Orange, Green, and Blue belt - to ring in the new year!

Click ``||loops:Ok||`` to get started!

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo") 

## Explore the starter code!

Take a look at the JavaScript code already in the code editor. Be sure not to delete any of it, because you will need it for your project!

---

- :null: Lines of code that start with **//** are called **code comments** and are used to give the coder or someone reading the code more information. They do not affect how the program runs. How many **code comments** do you see on screen?

- :play: Click the Play button to see what parts of the project are already in the starter code. You should see a night sky background image and a New Years Eve Pole in the middle of the screen, ready for the ball drop at midnight!

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo") 

## Position the New Years Eve Ball so it is ready to drop at midnight!

Learn how to add a sprite and set its position in MakeCode Arcade's JavaScript editor!

---

- :paper plane: Use the **Enter** key to create a line under the **// nye ball drop code** code comment. Open ``||sprites:Sprites||`` and drag out the ``||sprites:sprite (img) of kind (kind)||`` code block into the blank line.
- :paper plane: Replace **mySprite** with a **variable** name for the sprite, such as ``||sprites:nyeBall||``.
- :art: Click the palette icon to the left of the line number, then select the **ballImageSmall** from the **Gallery** as the sprite image.
- :paper plane: Underneath, type the sprite name followed by a **dot operator** ``||.||`` then select ``||sprites:setPosition||`` from the **code completion** tool.
- :paper plane: Add a parenthesis ``||(||`` then type the x and y position for the sprite, separated by a comma. To center the sprite at the top of the screen, use ``||sprites:(80,0)||``.
- :play: Click the Play button to see the NYE ball sprite appear on screen! 

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo") 

```typescript
// nye ball drop code
let nyeBall = sprites.create(nyeImg.ballImageSmall, SpriteKind.Player)
nyeBall.setPosition(80,0)
```

## Begin the New Year's Eve Ball Drop!

The New Year's Eve Ball Drop usually happens as peopple count down from 10. Let's first program the ball sprite to descend before we add in the countdown!

---

- :function: Find the ``||function: function callBallDrop||`` code under the **// nye ball drop functions** comment. Use the **Enter** key to add an indented line inside the curly brackets **{ }** of the function.
- :repeat: Open ``||loops:Loops||`` and drag out the ``||loops:for||`` code block onto the indented line inside the **function definition**.
- :repeat: We want the loop to run a total of 10 times, so replace the number 5 with a **10**.
- :paper plane: Indented inside the curly brackets **{}** of the **loop**, type the NYE ball sprite name, a dot operator ``||.||`` and a ``||sprites:y||``. Then type ``||+=||`` to add an **addition assignment operator** that will add and store a value to the y-position of the sprite each time the loop runs.
- :tree: Since we know we want the ball to drop the height of the screen divided by 10, type ``||scene:scene.screenHeight()||`` followed by a ``||math:/||`` and the number **10**.

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo") 

```typescript
// nye ball drop functions
function callBallDrop () {
    for (let i = 0; i < 10; i++) {
        nyeBall.y += scene.screenHeight() / 10
    }
}
```

## Trigger the NYE Ball Drop to begin!

Use the A button to begin the New Year's Eve Ball Drop!

---

- :game controller: Find the ``||controller:controller.A.onEvent||`` code under the **// nye ball drop event** comment. Use the **Enter** key to add an indented line inside the curly brackets **{ }** of the function.
- :function: On the indented line inside, type ``||function:callBallDrop()||`` to call the code just added to the ``||function:callBallDrop||`` **function definition**.
- :game controller: Press the A button on the MakeCode Arcade emulator, or use your computer's space key to start the New Year's Eve Ball Drop!
- :repeat: Oh no! The sprite dropped too quickly! Inside the ``||function:callBallDrop||`` function definition, **above** the ``||sprites:y||`` code, type ``||loops:pause(1000)||`` to add a 1-second pause each time the loop runs.
- :game controller: Press the A button again to test the added code.

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo") 

```typescript
// nye ball drop event
controller.A.onEvent(ControllerButtonEvent.Pressed, function () {
    callBallDrop()
})

// nye ball drop functions
function callBallDrop () {
    for (let i = 0; i < 10; i++) {
        pause(1000)
        nyeBall.y += scene.screenHeight() / 10
    }
}
```

## Display a countdown on screen!

Create a 10 second countdown that displays on screen as the ball drops!

---

- :numbered list: Find the ``||arrays:countdownArray||`` under the **// countdown image array** comment. This **array** is a list of images that will be used to create an on-screen countdown.
- :function: Inside the ``||function:callBallDrop||`` **function definition**, insert a line above the ``||loops:pause||`` code. Add code from ``||sprites:Sprites||`` to add another sprite to the project. Name the new sprite ``||sprites:countdownNum||``.
- :numbered list: Replace the image parameter code with the name of the ``||arrays:countdownArray||``. Add a ``||.||`` and the **array function** ``||arrays:shift()||`` which will remove and use the first item in the **array**.
- :paper plane: On the line below, type the name of the countdown sprite, a ``||.||`` and the ``||sprites:setPosition||`` function to position the countdown numbers on screen. Add parentheses then type an x- and y-position for the sprite inside.

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo") 

```typescript
// nye ball drop functions
function callBallDrop () {
    for (let i = 0; i < 10; i++) {
        let countdownNum = sprites.create(countdownArray.shift(), SpriteKind.Player)
        countdownNum.setPosition(80, 60)
        pause(1000)
        nyeBall.y += scene.screenHeight() / 10
    }
}
```

## Fix the Countdown number display!

Remove the countdown numbers after they have appeared on screen!

---

- :repeat: Inside the ``||loops:for||`` loop, add a new line underneath the existing code.
- :paper plane: Using the **code completion** tool, add the ``||sprites:sprites.destroy||`` function on the blank line.
- :paper plane: Add parentheses then type the countdown sprite name inside.
- :play: Click the Play button to test the countdown to ensure the ball drops and the countdown numbers appear and then disappear on screen, as expected.

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo") 

```typescript
// nye ball drop functions
function callBallDrop () {
    for (let i = 0; i < 10; i++) {
        let countdownNum = sprites.create(countdownArray.shift(), SpriteKind.Player)
        countdownNum.setPosition(80, 60)
        pause(1000)
        nyeBall.y += scene.screenHeight() / 10
        sprites.destroy(countdownNum)
    }
}
```

## Add fireworks to the celebration!

Add some fireworks on either side of the pole that will explode after the New Year's Eve Ball Drop is complete!

---

- :function: Find the ``||function: function callFireworks||`` code under the **// nye ball drop functions** comment. Use the **Enter** key to add an indented line inside the curly brackets **{ }** of the function.
- :paper plane: Inside the ``||function:callFireworks||`` **function definition** add code from ``||sprites:Sprites||`` to create **2** different fireworks sprites.
- :paper plane: Use **fireworkImageOrange** and **fireworkImageGreen** from the **Gallery** for the 2 new sprites.
- :paper plane: Use the ``||sprites:setPosition||`` function to set the position for each sprite, 1 on each side of the NYE Ball Drop pole.
- :game controller: Inside ``||controller:controller.A.onEvent||`` add ``||function:callFireworks||`` under the ``||function:callBallDrop||`` code to make the fireworks appear after the ball drop code runs.

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo") 

```typescript
// nye ball drop event
controller.A.onEvent(ControllerButtonEvent.Pressed, function () {
    callBallDrop()
    callFireworks()
})
function callFireworks () {
    let fireworks1 = sprites.create(nyeImg.fireworkImageOrange, SpriteKind.Player)
    let fireworks2 = sprites.create(nyeImg.fireworkImageGreen, SpriteKind.Player)
    fireworks1.setPosition(43, 57)
    fireworks2.setPosition(117, 73)
}
```

## Animate the fireworks display!

Add animation to enhance the fireworks display!

---

- :refresh: Open ``||animation:Animation||`` to add 2 ``||animation:animate (mySprite) frames (frames)||`` code blocks into the ``||function:callFireworks||`` **function definition** to animate the firework sprites.
- :refresh: Replace ``||null||`` with the name of a firework sprite. 
- :refresh: Replace ``||[]||`` with **assets.animation** and the name of the matching firework animation from the **Assets** tab.
- :refresh: Adjust the **frameInterval** parameter to determine the speed of the firework animation. 
- :refresh: Change the **loop** parameter to True if you want the firework animation to continue running.

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo") 

```typescript
function callFireworks () {
    let fireworks1 = sprites.create(nyeImg.fireworkImageOrange, SpriteKind.Player)
    let fireworks2 = sprites.create(nyeImg.fireworkImageGreen, SpriteKind.Player)
    fireworks1.setPosition(43, 57)
    fireworks2.setPosition(117, 73)
    animation.runImageAnimation(fireworks1, assets.animation`fireworkAnimOrange`, 100, true)
    animation.runImageAnimation(fireworks2, assets.animation`fireworkAnimGreen`, 200, true)
}
```

## Avoid an error if the A button is pressed more than once!

To prevent an error that might occur if the A button is pressed more than once, add this code!

---

- :list: Under the existing code underneath the **// nye ball drop code** comment, declare a new variable with the keyword ``||variables:let||`` and the name **isBallDropStarted**.
- :list: Use an **assignment operator** ``||=||`` to set the variable to **false**.
- :shuffle: Inside the ``||controller:controller.A.onEvent||`` add a blank line above the code inside. Type ``||logic:if()||`` to add a **conditional** that will check the status of the **isBallDropStarted** variable.
- :shuffle: Inside the parentheses of the ``||logic:if||`` type ``||logic:!(isBallDropStarted)||`` to check if the variable is *not true*. 
- :shuffle: Type an open curly brace ``||{||`` after the parentheses. Then indent the other code inside, and type a closed curly brace ``||}||`` on the line below.
- :list: Inside the ``||logic:if||`` statement, set the variable to **true** above the other code by typing **isBallDropStarted = true**.

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo") 

```typescript
// nye ball drop code
let nyeBall = sprites.create(nyeImg.ballImageSmall, SpriteKind.Player)
nyeBall.setPosition(80,0)
let isBallDropStarted = false

// nye ball drop event
controller.A.onEvent(ControllerButtonEvent.Pressed, function () {
    if (!(isBallDropStarted)) {
        isBallDropStarted = true
        callBallDrop()
        callFireworks()
    }
})
```

## Customize your project!

Try out these customizations to enhance your New Year's Eve Ball Drop project!

---

- :circle: Use ``||game:game.splash||`` to display a message at the beginning of your project. Use this to tell the player what key to press to start the ball drop!
- :tree: In the **Assets** tab, duplicate the background image and write a celebratory message on it. Use a ``||scene:scene.setBackgroundImage||`` function to display the new background image after the countdown has ended!
- :headphones: Use ``||music:music.play||`` with the ``||music:music.createSong||`` function to play celebratory music before, during, or after the ball drop!
- :repeat: To add some pizzazz to your countdown, replace ``||loops:pause(1000)||`` with this code to make the countdown numbers grow in **scale** when they appear on screen: ![image](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/countdown%20number%20scale.png?raw=true "countdown number scaling code")

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo") 

```typescript
// background code
scene.setBackgroundImage(nyeImg.backgroundImage)
let nyePole = sprites.create(nyeImg.poleImage, SpriteKind.Player)
nyePole.setPosition(80, 60)
game.splash("Press A to start the", "New Years Countdown!")

// countdown image array
let countdownArray = [
    nyeImg.img10,
    nyeImg.img09,
    nyeImg.img08,
    nyeImg.img07,
    nyeImg.img06,
    nyeImg.img05,
    nyeImg.img04,
    nyeImg.img03,
    nyeImg.img02,
    nyeImg.img01
]

// nye ball drop code
let nyeBall = sprites.create(nyeImg.ballImageSmall, SpriteKind.Player)
nyeBall.setPosition(80,0)
let isBallDropStarted = false

// nye ball drop event
controller.A.onEvent(ControllerButtonEvent.Pressed, function () {
    if (!(isBallDropStarted)) {
        isBallDropStarted = true
        callBallDrop()
        scene.setBackgroundImage(nyeImg.backgroundImage2024)
        music.play(music.createSong(assets.song`nyeSong`), music.PlaybackMode.InBackground)
        callFireworks()
    }
})

// nye ball drop functions
function callBallDrop () {
    for (let i = 0; i < 10; i++) {
        let countdownNum = sprites.create(countdownArray.shift(), SpriteKind.Player)
        countdownNum.setPosition(80, 60)
        for (let index = 0; index < 5; index++) {
            pause(200)
            countdownNum.changeScale(0.5, ScaleAnchor.Middle)
        }
        nyeBall.y += scene.screenHeight() / 10
        sprites.destroy(countdownNum)
    }
}

function callFireworks () {
    let fireworks1 = sprites.create(nyeImg.fireworkImageOrange, SpriteKind.Player)
    let fireworks2 = sprites.create(nyeImg.fireworkImageGreen, SpriteKind.Player)
    fireworks1.setPosition(43, 57)
    fireworks2.setPosition(117, 73)
    animation.runImageAnimation(fireworks1, assets.animation`fireworkAnimOrange`, 100, true)
    animation.runImageAnimation(fireworks2, assets.animation`fireworkAnimGreen`, 200, true)
}
```

## Congratulations on finishing your project!

Happy New Year! There are so many exciting things to learn at Code Ninjas in the year ahead! Keep on working through the belt levels in IMPACT to learn how to code cool games with blocks and JavaScript!

Click Done to open your game in MakeCode Arcade, where you can add to your code and create a link to share your game with others! 

Happy coding!

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo") 

```package
nyeImg=github:Code-Ninjas-Home-Office/new-year-new-code-image-pack
```
