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
    if (!isBallDropStarted) {
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

```assetjson
{
  "README.md": " ",
  "assets.json": "",
  "images.g.jres": "{\n    \"2bps[zYE[t`=Y@5`-[xj\": {\n        \"namespace\": \"myImages\",\n        \"id\": \"2bps[zYE[t`=Y@5`-[xj\",\n        \"mimeType\": \"application/mkcd-animation\",\n        \"data\": \"YzgwMDIwMDAyMDAwMDcwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwNDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwNTA0MDAwMDAwNDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDA1MDQwMDA0MDUwMDAwMDAwMDAwMDAwMDAwMDAwMDAwNTQwNDQwNTA0MDAwMDAwMDAwMDAwMDAwMDAwMDAwMDU0MDA1NDAwNTA0MDQwMDAwMDAwMDAwMDAwMDAwMDA1MDQwNDU0MDQ1NDQwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDU1NDU0NDQ1MDA1MDAwMDAwMDAwMDAwMDAwMDUwMDU1MDQwNDQ1NDA1MDAwMDAwMDAwMDAwMDAwMDAwNDA1NDQ1NDU0NDU1NTU1NTA1MDAwMDAwMDAwMDAwMDAwMDQwNDQ0NDU0MDUwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDQ1NDQ1NDU1NDQ0NDAwMDAwMDAwMDAwMDAwMDAwMDU1MDAwMDAwMDA1NTAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDUwMDU0MDAwMDAwMDAwMDAwMDAwNDQwMDAwMDAwMDAwMDAwNTQwMDQwMDAwMDAwMDAwNDAwMDAwMDAwMDAwMDA0NDAwMDA0NDAwMDAwMDAwMDQwMDAwMDA1MDA1MDAwMDAwMDQwMDQwMDAwMDAwNDAwMDAwNDAwMDUwMDAwMDAwMDAwMDAwMDAwMDAwMDAwNDAwNDA0NDAwMDAwMDAwMDAwMDAwMDAwMDA0MDA0MDAwNTUwMDAwMDAwMDAwMDAwMDA0MDQwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDQ0MDAwMDAwMDAwMDAwMDAwMDQwMDAwMDUwNTUwMDAwNDAwMDAwMDA1MDAwNDQwMDAwMDA0NDAwMDAwMDA1MDAwMDA0NDQwMDQ1NDQwNDAwMDAwMDAwMDAwMDAwMDAwMDAwMDA0MDA0NDU0MDAwMDAwMDAwMDAwMDAwMDA0NDA0MDA1NDQ0NTQ0NDAwMDAwMDQ0MDQwMDAwMDAwMDAwNDA0NDQwNDU1NDQ0NDQ0NDAwMDAwNDAwMDAwMDAwMDAwMDQwMDA1MDQ0NDQwNDQwMDQwMDAwNTUwMDAwNTA1NTA1MDA0MDQ0NDQ0NDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDQwNTA1NDQ0MDAwMDQwNDQwMDAwMDAwMDAwMDAwMDQ0MDQ0NTQ0NDU0NDAwMDAwMDQ0NDQwMDAwNDA0NDQwMDA0NDA0NDQ1MDQ0MDAwMDAwMDAwMDAwMDAwNDAwMDA0MDA0MDAwNDAwNDAwMDQ0MDAwMDAwMDAwMDAwMDAwMDAwMDAwMDA0NTAwMDAwMDA0NDAwMDAwMDAwMDAwMDAwMDAwMDAwMDA1MDA1MDAwMDAwMDQwMDAwMDAwMDAwNDAwMDQwMDQ0MDAwNDAwMDAwMDAwMDAwMDAwMDAwMDQ0MDAwMDQwMDQwNDQwMDA0MDAwMDAwMDAwMDAwNDAwNDAwMDAwNDAwMDA0MDA0NDAwMDAwMDA1MDAwMDA0MDAwMDAwMDA0NDAwNDAwMDAwMDA0MDAwMDAwNTUwMDAwMDA1MDQwMDAwMDQ0MDAwMDAwMDQwMDQwMDAwMDAwMDAwMDA1NDAwMDA1NDAwMDAwMDAwMDAwNDAwNDAwMDAwMDA0MDA0MDUwMDUwMDA0MDAwMDAwMDAwMDA0MDAwMDQwMDAwMDAwNTAwMDAwMDQwMDAwNTAwMDAwMDQwMDAwNDAwMDAwMDAwMDAwMDAwMDAwMDAwMDU1MDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwNTAwNTQwMDAwMDAwMDAwMDAwMDA0NDAwMDAwMDAwMDAwMDA1MDAwNDAwMDAwMDAwMDA0MDAwMDAwMDAwMDAwNTQ0MDAwMDAwMDAwMDAwMDAwNDAwMDA0NTAwMDAwMDAwMDAwNDQwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDQwMDA1MDAwMDAwNDAwMDAwMDAwMDQwMDAwMDA1NTAwMDAwMDAwMDAwMDAwMDQwMDAwMDAwMDAwMDAwMDAwMDAwNDAwMDAwMDAwMDAwMDAwNDQ0MDAwMDAwMDAwMDAwMDAwNDAwMDAwNTAwNTAwMDA0MDAwMDAwMDAwMDA0NDAwMDAwMDQwMDAwMDAwMDUwMDAwMDA0MDAwNDAwNDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDQ0MDAwMDAwNDAwMDAwNDAwMDUwMDQ0MDQwMDAwMDAwNDAwMDAwMDAwMDAwMDAwMDAwMDQwMDAwMDA0NDAwNTAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDA1NTAwNDA1MDAwMDUwMDQwMDAwMDQ0MDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDUwMDAwMDAwNDA0NDAwMDAwMDAwMDAwMDAwNDQwMDAwMDQ0MDAwMDAwMDAwMDQ0MDAwMDA0MDAwNDAwMDA0MDQwNDUwMDQwMDAwMDAwMDAwMDAwMDA0MDAwMDQwMDQwMDAwMDA0MDAwMDQwMDAwMDAwMDAwMDAwMDAwMDQwMDAwMDQwMDAwMDAwMDA0MDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDUwMDAwMDAwMDA1MDAwMDA0MDA0MDAwMDAwMDAwMDA0MDAwMDAwMDAwMDAwMDAwMDAwMDQwMDAwMDAwMDA0MDAwMDQwMDAwMDAwMDAwMDAwNDAwMDAwMDAwMDAwMDAwMDQ0MDAwMDAwMDAwMDAwMDQwMDAwMDAwMDA0MDA0MDAwMDAwMDQwMDAwNTA1MDAwMDAwMDUwNDAwMDAwNDAwMDAwMDAwNDAwMDAwMDAwMDAwNDAwMDUwMDAwMDAwMDAwMDAwMDAwMDQwMDA0MDAwMDAwMDAwMDAwNTAwMDAwMDQwMDAwMDAwMDAwMDQwMDAwNDAwMDAwMDA1MDAwMDAwNDAwMDAwMDAwMDAwNDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDU0MDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDQwMDAwMDAwMDAwNDAwMDAwMDAwMDAwMDUwNDAwMDAwMDAwMDAwMDAwMDAwMDAwMDUwMDAwMDAwMDAwMDA0MDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDA0MDAwNTAwMDAwMDQwMDAwMDAwMDA0MDAwMDAwNTAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDQwMDAwMDAwMDAwMDAwMDQ0NDAwMDAwMDAwMDAwMDAwMDQwMDAwMDUwMDAwMDAwNDAwMDAwMDAwMDAwMDQwMDAwMDA0MDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwNDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDQwNTAwMDAwMDAwMDAwMDA0NDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDA1MDAwMDAwMDQwMDQwMDAwMDAwMDAwMDAwMDAwMDAwMDA0NDAwMDAwMDAwMDAwNDAwMDAwNDAwMDAwMDAwMDAwMDQwMDA0MDAwMDAwMDAwMDAwMDAwNDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDA0MDAwMDAwMDAwMDAwMDAwNDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwNTAwMDAwNDAwNDAwMDAwMDAwMDAwNDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDA0MDAwMDAwMDAwMDAwMDQwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDA0MDAwMDAwMDAwMDAwNDAwMDAwMDA0MDAwMDUwNTAwMDAwMDAwMDQwMDAwMDQwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwNDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDQwMDAwMDAwMDAwMDAwMDQwMDAwMDAwMDAwMDAwMDAwMDAwMDA1MDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwNDAwMDUwMDAwMDAwMDAwMDAwMDAwNDAwMDAwMDUwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDA0MDAwMDAwMDAwMDAwMDA0MDQwMDAwMDAwMDAwMDAwMDA0MDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwNDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDQwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDA0MDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDQwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDQwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDQwMDQwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwNDAwMDAwMDAwMDA=\",\n        \"displayName\": \"fireworkAnimOrange\"\n    },\n    \"UKGeDo-[Xv]e0O0[n4Q4\": {\n        \"namespace\": \"myImages\",\n        \"id\": \"UKGeDo-[Xv]e0O0[n4Q4\",\n        \"mimeType\": \"application/mkcd-animation\",\n        \"data\": \"YzgwMDIwMDAyMDAwMDcwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDA3MDAwNzAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwNTc3MDAwNzAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDA3MDc1MDAwNzA1MDcwMDAwMDAwMDAwMDAwMDAwMDA1Nzc1NzU3MDU1NzAwMDAwMDAwMDAwMDAwMDAwMDAwMDcwNTc3NTU1NzAwNzAwMDAwMDAwMDAwMDAwMDAwMDAwMDA3NzU3Nzc3NzAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDcwNzc3Nzc3NTcwNTAwMDAwMDAwMDAwMDAwMDAwMDAwMDA3NzA3NTAwNTAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDc3NzcwNzAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwNzcwMDAwMDAwMDAwMDAwMDA3NTAwNTAwMDAwMDAwMDAwMDA3MDAwMDAwMDAwMDcwMDc1MDAwMDAwMDUwMDUwMDAwMDA3MDAwMDAwMDAwNzcwMDAwNzcwMDAwMDAwNTAwMDcwMDAwMDcwMDAwMDAwNzAwNzAwMDAwMDAwMDAwMDA3NzA3MDA3MDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDA1NTAwMDcwMDcwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwNzA3MDAwMDAwMDAwMDcwMDAwMDAwMDAwMDAwMDAwNzcwMDAwMDAwMDAwNzcwMDAwMDA3NzAwMDUwMDAwMDAwNzAwMDA1NTA1MDAwMDAwMDAwMDcwNzc1NzAwNzc3MDAwMDA1MDAwMDAwMDAwMDAwMDAwMDAwNzU3NzAwNzAwMDAwMDAwMDAwMDAwMDA3MDc3MDAwMDAwNzc3NTc3NzUwMDcwNzcwMDAwMDAwMDcwMDAwMDc3Nzc3Nzc1NTcwNzc3MDcwMDAwMDAwMDU1MDAwMDcwMDc3MDc3NzcwNTAwMDcwMDAwMDAwMDAwMDAwMDAwMDAwMDAwNzc3Nzc3MDcwMDUwNTUwNTAwMDAwMDAwNzcwNzAwMDA3Nzc1MDUwNzAwMDAwMDAwMDAwMDc3NzcwMDAwMDA3NzU3Nzc1NzcwNzcwMDAwMDAwMDAwMDAwMDAwMDAwMDc3MDU3NzcwNzcwMDA3NzcwNzAwMDAwMDAwMDA3NzAwMDcwMDcwMDA3MDA3MDAwMDcwMDAwMDAwMDA3NzAwMDAwMDA1NzAwMDAwMDAwMDAwMDAwMDAwMDA3MDAwMDAwMDUwMDUwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDcwMDA3NzAwNzAwMDcwMDAwMDAwMDAwMDAwMDAwNzAwMDc3MDcwMDcwMDAwNzcwMDAwMDAwMDUwMDAwMDAwNzcwMDcwMDAwNzAwMDAwNzAwNzAwNTUwMDAwMDA3MDAwMDAwMDcwMDc3MDAwMDAwMDA3MDAwMDAwMDcwMDcwMDAwMDAwNzcwMDAwMDcwNTAwMDAwMDAwNzAwNzAwMDAwMDAwMDAwNzUwMDAwNzUwMDAwMDAwMDA3MDAwMDAwMDAwMDA3MDAwNTAwNTA3MDA3MDAwMDAwMDcwMDAwMDA1MDAwMDcwMDAwMDA1MDAwMDAwMDcwMDAwMDAwMDU1MDAwMDAwMDAwMDAwMDAwMDAwMDAwNzAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwNzcwMDAwMDAwMDAwMDAwMDA3NTAwNTAwMDAwMDAwNzAwMDA3MDAwMDAwMDAwMDAwNzA1MDAwMDAwMDUwMDUwNzAwMDA3MDAwMDAwMDAwMDAwMDA3NzcwNTAwMDAwNTAwMDcwMDAwMDcwMDAwMDAwNzAwMDA3MDAwMDAwNTAwMDA3NzA3MDAwMDAwMDAwMDAwMDAwMDAwMDcwMDAwMDA3MDAwMDAwMDAwMDAwMDcwMDAwMDAwMDAwMDAwMDAwMDcwMDAwMDAwMDAwMDAwMDAwNzAwMDA3MDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwNzcwMDAwMDA3NzAwMDUwMDAwMDAwMDAwMDA1NTA1NzAwMDAwMDAwMDcwNzc1MDAwNzcwMDAwMDAwMDAwMDA3MDAwMDAwMDAwMDAwNzU3MDAwMDAwMDAwMDAwMDAwNTAwMDAwMDc3MDAwMDAwMDc3MDc3NzUwMDAwNzcwMDAwMDAwMDcwMDAwMDA3MDc3MDc1NTAwNzAwMDc3MDAwMDAwMDU1MDAwMDAwMDA3MDc3MDAwMDUwMDcwMDcwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwNTAwNTAwMDAwMDcwNzAwMDAwMDcwMDUwNzAwMDAwMDUwMDAwMDc3NzcwMDAwMDA3MDAwMDc1NzAwMDAwMDAwMDAwMDAwMDcwMDAwMDAwMDAwMDA3MDAwMDAwMDA3NzcwNzAwMDAwNzAwMDAwMDAwMDAwMDAwNTAwMDA3NzAwMDcwMDAwMDAwMDAwNzAwMDAwMDA1MDAwMDAwMDAwMDA3MDAwNzAwMDA3MDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDcwMDAwMDAwMDAwMDA3NzAwNzAwMDcwMDAwMDAwMDAwNzAwMDAwNzAwMDc3MDcwMDcwMDA3NzAwMDAwMDAwMDUwMDAwMDAwMDcwMDcwMDAwMDAwMDAwMDAwNzAwNTUwMDAwMDAwMDAwMDAwMDAwMDA3MDAwMDAwMDA3MDAwMDAwMDAwMDcwMDAwMDAwNzcwMDAwMDcwNTAwNzAwMDA1MDAwMDAwMDAwMDAwMDAwMDUwMDAwNzAwMDAwMDAwMDA3MDAwMDAwMDAwMDA3MDAwMDAwMDAwMDUwMDAwMDAwMDcwMDAwMDA1MDAwMDcwMDAwMDA1MDAwMDAwMDcwMDAwMDAwMDU1MDAwMDAwMDAwMDAwMDAwMDAwMDAwNzAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDA3NTAwNTAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDA1MDAwMDAwMDUwMDAwMDAwMDA3MDAwMDAwMDAwMDAwMDAwNzAwNTAwMDAwMDAwMDAwMDAwMDcwMDAwMDAwNzAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDcwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDA3MDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwNzcwMDAwMDAwNzAwMDUwMDAwMDAwMDAwMDAwMDA1NzAwMDAwMDAwMDcwNzcwMDAwMDAwMDAwMDAwMDAwMDA3MDAwMDAwMDAwMDAwNzAwMDAwMDAwMDAwMDAwMDAwNTAwMDAwMDAwMDAwMDAwMDcwMDc3MDUwMDAwNzAwMDAwMDAwMDAwMDAwMDA3MDAwMDA1NTAwNzAwMDcwMDAwMDAwMDU1MDAwMDAwMDA3MDcwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwNTAwMDAwMDcwMDAwMDAwMDAwMDAwNzAwMDAwMDAwMDAwMDc3NzAwMDAwMDAwMDAwMDc1MDAwMDAwMDAwMDAwMDAwMDcwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwNzAwMDAwNzAwMDAwMDAwMDAwMDAwMDAwMDA3NzAwMDAwMDAwMDAwMDAwNzAwMDAwMDA1MDAwMDAwMDAwMDA3MDAwNzAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwNzAwNzAwMDcwMDAwMDAwMDAwNzAwMDAwNzAwMDA3MDcwMDcwMDA3NzAwMDAwMDAwMDAwMDAwMDAwMDcwMDcwMDAwMDAwMDAwMDAwMDAwNTAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwNzAwMDAwMDcwMDAwNzAwMDAwMDAwMDAwMDAwMDAwMDAwMDUwMDAwMDAwMDAwMDAwMDA3MDAwMDAwMDAwMDA3MDAwMDAwMDAwMDUwMDAwMDAwMDcwMDAwMDAwMDAwMDcwMDAwMDAwMDAwMDAwMDcwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDcwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDUwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDA3MDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDA3MDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwNzAwMDcwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwNzAwMDAwMDAwNTAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwNzAwMDAwMDAwMDAwMDA3MDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwNzUwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDA3MDAwMDA3MDAwMDAwMDAwMDAwMDAwMDAwMDA3MDAwMDAwMDAwMDAwMDA3MDAwMDAwMDUwMDAwMDAwMDAwMDAwMDA3MDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDA3MDAwMDA3MDAwMDAwMDAwMDAwMDA3MDAwMDAwMDAwMDAwMDAwMDAwNzAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDA3MDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDA=\",\n        \"displayName\": \"fireworkAnimGreen\"\n    },\n    \"song1\": {\n        \"data\": \"005a000408050300001c00010a006400f401640000040000000000000000000000000005000004b40008000c00011910001400011e16001800011d18001c00011e1c002000012220002400012026002800011e28002c0001202c002e0001222e003000012030003400011e36003800011e38003c0001223c00400001254000480001274c005000012750005400012556005800012258005c0001225c006000011e60006400012066006800011e68006c0001206c006e0001226e007000012070007400011e76007800011b78007c00011b7c008000011980008800011e05001c000f0a006400f4010a0000040000000000000000000000000000000002360010001800011220002800011930003800011240004800015750005800011260006800011970007800011278008000011480008800011206001c00010a006400f4016400000400000000000000000000000000000000023f001000180002222a200028000225293000380002222a4000480002632a5000580002222a600068000225297000780002222a7800800002632780008800022225\",\n        \"mimeType\": \"application/mkcd-song\",\n        \"displayName\": \"nyeSong\",\n        \"namespace\": \"mySongs.\"\n    },\n    \"*\": {\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"dataEncoding\": \"base64\",\n        \"namespace\": \"myImages\"\n    }\n}",
  "images.g.ts": "// Auto-generated code. Do not edit.\nnamespace myImages {\n\n    helpers._registerFactory(\"image\", function(name: string) {\n        switch(helpers.stringTrim(name)) {\n\n        }\n        return null;\n    })\n\n    helpers._registerFactory(\"animation\", function(name: string) {\n        switch(helpers.stringTrim(name)) {\n            case \"fireworkAnimOrange\":\n            case \"2bps[zYE[t`=Y@5`-[xj\":return [img`\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n`, img`\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n`, img`\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n.................4..............\n.........5.4....4...............\n..........5.4...4.5.............\n..........454..4.5.4............\n........5..45..45.4.4...........\n.........5.454.45444............\n..........5.454544.55...........\n.......55..5.444455.............\n.......4455454445555555.........\n.........44444455...............\n............544445554444........\n..........55........55..........\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n`, img`\n................................\n.....55..4..............44......\n......5..44............4........\n....44....44........4........55.\n......4....4.......4.....4...5..\n..................4....444......\n............4....4..55..........\n....4.4.........................\n........44.................4....\n.555.....4.......5..44......44..\n....5.....4.44..54444...........\n.............44.54.4............\n....444...45444544......444.....\n.......444.45445444444....4.....\n.........4...544444..44.....55..\n...5555....4444444..............\n...........4.54544.....444......\n........444.54445444......4444..\n...444.4..444.44.544............\n..4......44...4....4..44........\n..............4..5......44......\n.................55.......4.....\n.......4...44..4...4............\n....4..4..4....444..4...........\n...44.....4......44..4.......5..\n...4......4..44.......4.......55\n.......5.4....44......4....4....\n......5..4..5..4...........44...\n....4....4.55...4...........4...\n...4.......5....4......5....4...\n...4....................55......\n................................\n`, img`\n................................\n................................\n................................\n.....55..4..............44......\n......5...4............4........\n..5.44..............4.....54....\n......4..4......................\n.........................4...5..\n..4.........4.......55..........\n....4...................4.......\n........44.4...............4....\n.55......4..........44.......4..\n....5........4...44.............\n..............4..4....4.....4...\n5...444.......4.................\n...4....4..45...................\n............................55..\n.4.5..5....4....44..............\n...............5.......444......\n........44....4..4........4..4..\n...4...4..4.4.4..54.............\n..4......44........4..4.........\n........4.....4.........4.......\n..................5.........5...\n..4....4...........4............\n.......4.........4..4...........\n..4...............4..4..........\n...4.........44.......4......5.5\n.......5.4.....4......4.........\n..4...5.................4...4...\n...........5....4...........4...\n...4.......5....4...........4...\n`, img`\n................................\n................................\n................................\n................................\n................................\n................................\n......5..4......................\n..........4............4........\n..5.4.....................5.....\n.........4......................\n.........................4...5..\n..4.........4........5..........\n........................4.......\n........44.4...............4....\n.5.......4..........4........4..\n................................\n.................4..............\n................................\n................................\n................................\n.4.5............44..............\n...............5.......44.......\n..............4..4...........4..\n...4..........4...4.............\n..4.............................\n........4...............4.......\n............................5...\n..4....4...........4............\n....................4...........\n..4.............................\n...4..........4.......4......5.5\n.........4.....4................\n`, img`\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n.........4......................\n.......................4........\n....4.....................5.....\n................................\n.........................4...5..\n............4........5..........\n........................4.......\n.........4.4...............4....\n.............................4..\n................................\n.................4..............\n................................\n................................\n................................\n.4..............................\n................................\n.............................4..\n................................\n................................\n........................4.......\n................................\n..4....4........................\n....................4...........\n`];\n            case \"fireworkAnimGreen\":\n            case \"UKGeDo-[Xv]e0O0[n4Q4\":return [img`\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n`, img`\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n`, img`\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n............7...7...............\n............75.7...7............\n.............757..7.5.7.........\n..........755757.755.7..........\n...........7755755.77...........\n............77757777............\n.............7777777755.........\n..............777..55...........\n..............77777.............\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n................................\n`, img`\n................................\n......77..............7..55.....\n........7............77..5......\n.55........7........77....77....\n..5...7.....7.......7....7......\n......777....7..................\n..........55..7....7............\n.........................7.7....\n....7.................77........\n..77......77..5.......7.....555.\n...........77775..77.7.....5....\n............7.75.77.............\n.....777......77577757...777....\n.....7....77777757757.777.......\n..55.....77..777775...7.........\n..............7777777....5555...\n......777.....77575.7...........\n..7777......77757775.777........\n............775.77.777..7.777...\n........77..7....7...77......7..\n......77......5..7..............\n.....7.......55.................\n............7...7..77...7.......\n...........7..777....7..7..7....\n..5.......7..77......7.....77...\n55.......7.......77..7......7...\n....7....7......77....7.5.......\n...77...........7..5..7..5......\n...7...........7...55.7....7....\n...7....5......7....5.......7...\n......55....................7...\n................................\n`, img`\n................................\n................................\n......77..............7..55.....\n.....7..7..............7.5......\n.55.7......7............7.775...\n..5...7.....7.......7......7....\n5.....777...................7...\n.....7.............7............\n.....7..............7......7....\n................................\n..77......77..5.............555.\n.7.........777.5..77............\n.7..........7.75..............5.\n......77......7..77757....77....\n.....7....7.7..757.57...7..7....\n..55.........777.....57....7....\n............................5...\n.5....7.7........75.7........5..\n..7777.......7..7.75............\n..7..............7......7.777...\n..7................5..7..7...7..\n......7.......5...........7...7.\n.....7..........................\n.....7..........7..77...7.......\n.....7.....7..777....7..77......\n..5..........77.............7...\n55...................7......7...\n.........7......77....7.5....7..\n5..................5..7.........\n...7...........7........5.......\n...7....5......7....5.......7...\n......55....................7...\n`, img`\n................................\n................................\n................................\n......................7..55.....\n.........................5......\n.5.........7...............75...\n............7.......7...........\n................................\n...................7............\n...........................7....\n................................\n..77......7...5...............5.\n.7.........777..................\n.7..........7.................5.\n..............7...775......7....\n..........7.....5..57...7.......\n..55.........7.7................\n................................\n.5....7.............7...........\n..77.7..........7..5............\n..7.........................7...\n..7...................7..7......\n......7.......5...........7...7.\n................................\n...................77...7.......\n.....7.....7..7.7....7..77......\n.............77.................\n.5..............................\n.................7....7......7..\n...................5............\n...7...........7........5.......\n...7...........7............7...\n`, img`\n................................\n................................\n................................\n................................\n................................\n......................7.........\n.........................5......\n................................\n....................7...........\n................................\n................................\n................................\n................................\n...7............................\n................................\n................................\n..............7...7.............\n........................7.......\n...5............................\n................................\n......7.............7...........\n................7..5............\n............................7...\n..7......................7......\n......7.......5...............7.\n................................\n................................\n.....7.....7............7.......\n.............7..................\n................................\n.............................7..\n................................\n`];\n        }\n        return null;\n    })\n\n    helpers._registerFactory(\"song\", function(name: string) {\n        switch(helpers.stringTrim(name)) {\n            case \"song1\":\n            case \"nyeSong\":return hex`005a000408050300001c00010a006400f401640000040000000000000000000000000005000004b40008000c00011910001400011e16001800011d18001c00011e1c002000012220002400012026002800011e28002c0001202c002e0001222e003000012030003400011e36003800011e38003c0001223c00400001254000480001274c005000012750005400012556005800012258005c0001225c006000011e60006400012066006800011e68006c0001206c006e0001226e007000012070007400011e76007800011b78007c00011b7c008000011980008800011e05001c000f0a006400f4010a0000040000000000000000000000000000000002360010001800011220002800011930003800011240004800015750005800011260006800011970007800011278008000011480008800011206001c00010a006400f4016400000400000000000000000000000000000000023f001000180002222a200028000225293000380002222a4000480002632a5000580002222a600068000225297000780002222a7800800002632780008800022225`;\n        }\n        return null;\n    })\n\n}\n// Auto-generated code. Do not edit.\n",
  "main.blocks": "<xml xmlns=\"https://developers.google.com/blockly/xml\"><variables><variable type=\"KIND_SpriteKind\" id=\"/Pro]A6CSPx$Fbh|RzZ7\">Player</variable><variable type=\"KIND_SpriteKind\" id=\"BQIX=mv2z)WSD=d`.N`j\">Projectile</variable><variable type=\"KIND_SpriteKind\" id=\"B?2mx1Fisz!d[iLG8!EL\">Food</variable><variable type=\"KIND_SpriteKind\" id=\"ghoMjnl3b,$9{Nz-Lf}_\">Enemy</variable><variable id=\"r3C7;v1RFHU.H0)[(nl4\">isBallDropStarted</variable><variable id=\"ailt`h@CTJl3j}bDt]dh\">countdownNum</variable><variable id=\"mdnbpNheo3HRd/x!c%!I\">countdownArray</variable><variable id=\"Zt~T!tV4R@.Us;;C4K#J\">nyeBall</variable><variable id=\"`[j|||r4U4AKg:1EevA{\">fireworks1</variable><variable id=\"-hJwp,Kljc|hS0gp`|Pd\">fireworks2</variable><variable id=\"X:,4qJEB!BFK^_p!=py`\">nyePole</variable></variables><block type=\"pxt-on-start\" x=\"0\" y=\"0\"></block></xml>",
  "main.ts": "\n",
  "pxt.json": "{\n    \"name\": \"assetjson file New Year New Code\",\n    \"description\": \"\",\n    \"dependencies\": {\n        \"device\": \"*\"\n    },\n    \"files\": [\n        \"main.blocks\",\n        \"main.ts\",\n        \"README.md\",\n        \"assets.json\",\n        \"tilemap.g.jres\",\n        \"tilemap.g.ts\",\n        \"images.g.jres\",\n        \"images.g.ts\"\n    ],\n    \"targetVersions\": {\n        \"branch\": \"v1.12.46\",\n        \"tag\": \"v1.12.46\",\n        \"commits\": \"https://github.com/microsoft/pxt-arcade/commits/e66fb08db35df2249cd64300195259c64d497106\",\n        \"target\": \"1.12.46\",\n        \"pxt\": \"8.5.57\"\n    },\n    \"preferredEditor\": \"blocksprj\"\n}\n",
  "tilemap.g.jres": "{\n    \"transparency16\": {\n        \"data\": \"hwQQABAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA==\",\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"tilemapTile\": true\n    },\n    \"*\": {\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"dataEncoding\": \"base64\",\n        \"namespace\": \"myTiles\"\n    }\n}",
  "tilemap.g.ts": "// Auto-generated code. Do not edit.\nnamespace myTiles {\n    //% fixedInstance jres blockIdentity=images._tile\n    export const transparency16 = image.ofBuffer(hex``);\n\n    helpers._registerFactory(\"tile\", function(name: string) {\n        switch(helpers.stringTrim(name)) {\n            case \"transparency16\":return transparency16;\n        }\n        return null;\n    })\n\n}\n// Auto-generated code. Do not edit.\n"
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
- :numbered list: Delete the image parameter code and replace it with the name of the ``||arrays:countdownArray||``. Add a ``||.||`` and the **array function** ``||arrays:shift()||`` which will remove and use the first item in the **array**.
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
- :game controller: Inside ``||controller:controller.A.onEvent||`` add ``||function:callFireworks()||`` under the ``||function:callBallDrop()||`` code to make the fireworks appear after the ball drop code runs.

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
- :refresh: Replace ``||[]||`` with **assets.animation**, two backticks ``||`||`` and the name of the matching firework animation: **fireworkAnimGreen** or **fireworkAnimOrange**.
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
- :shuffle: Inside the parentheses of the ``||logic:if||`` type ``||logic:!isBallDropStarted||`` to check if the variable is *not true*. 
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
    if (!isBallDropStarted) {
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
- :tree: Use a ``||scene:scene.setBackgroundImage||`` function to create a new background image with a celebratory message that will be displayed after the countdown has ended!
- :headphones: Use ``||music:music.play()||`` with ``||music:music.createSong(), music.PlaybackMode.InBackground||`` inside to play celebratory music before, during, or after the ball drop! Inside the parentheses of ``||music:music.createSong||``, type **assets.song** and 2 backticks ``||`||`` then click the music notes to the left of the line number to open the Music Editor.
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
    if (!isBallDropStarted) {
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
