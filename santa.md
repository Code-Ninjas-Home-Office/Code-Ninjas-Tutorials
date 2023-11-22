# Santa's Present Run!
### @diffs true

```blocks
controller.A.onEvent(ControllerButtonEvent.Pressed, function () {
    if (playerSprite.isHittingTile(CollisionDirection.Bottom)) {
        playerSprite.vy = -200
    }
})
controller.left.onEvent(ControllerButtonEvent.Pressed, function () {
    playerSprite.setImage(santaImg.santaLeft)
})
scene.onOverlapTile(SpriteKind.Player, assets.tile`snowPath13`, function (sprite, location) {
    tiles.placeOnTile(sprite, tiles.getTileLocation(0, 6))
    music.play(music.melodyPlayable(music.bigCrash), music.PlaybackMode.UntilDone)
})
controller.right.onEvent(ControllerButtonEvent.Pressed, function () {
    playerSprite.setImage(santaImg.santaRight)
})
sprites.onOverlap(SpriteKind.Player, SpriteKind.Enemy, function (sprite, otherSprite) {
    sprites.destroy(otherSprite, effects.disintegrate, 500)
    info.changeCountdownBy(-5)
    music.play(music.melodyPlayable(music.zapped), music.PlaybackMode.UntilDone)
})
sprites.onOverlap(SpriteKind.Player, SpriteKind.Food, function (sprite, otherSprite) {
    sprites.destroy(otherSprite, effects.smiles, 500)
    music.play(music.melodyPlayable(music.magicWand), music.PlaybackMode.UntilDone)
    if (sprites.allOfKind(SpriteKind.Food).length == 0) {
        game.gameOver(true)
    }
})

game.splash("Oh no!", "Santa lost his presents!")
game.splash("Collect all the presents", "before the time runs out!")
game.splash("Avoid the milk and cookies", "they take away time!")
info.startCountdown(30)
let playerSprite = sprites.create(santaImg.santaRight, SpriteKind.Player)
tiles.placeOnTile(playerSprite, tiles.getTileLocation(0, 6))
controller.moveSprite(playerSprite, 100, 0)
scene.cameraFollowSprite(playerSprite)
playerSprite.ay = 500
function spawnCookies () {
    for (let value of tiles.getTilesByType(assets.tile`enemySpawnTile`)) {
        let cookieSprite = sprites.create(santaImg.milkGlassCookie, SpriteKind.Enemy)
        tiles.placeOnTile(cookieSprite, value)
        tiles.setTileAt(value, assets.tile`transparency16`)
    }
}
function spawnPresents () {
    for (let value of tiles.getTilesByType(assets.tile`foodSpawnTile`)) {
        let presentSprite = sprites.create(santaImg.greenGift, SpriteKind.Food)
        tiles.placeOnTile(presentSprite, value)
        tiles.setTileAt(value, assets.tile`transparency16`)
    }
}
game.setGameOverEffect(true, effects.confetti)
game.setGameOverPlayable(true, music.powerUp, false)
game.setGameOverMessage(true, "GAME OVER!")
```

```assetjson
{
  "README.md": " ",
  "assets.json": "",
  "images.g.jres": "{\n    \"*\": {\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"dataEncoding\": \"base64\",\n        \"namespace\": \"myImages\"\n    }\n}",
  "images.g.ts": "// Auto-generated code. Do not edit.\nnamespace myImages {\n\n    helpers._registerFactory(\"image\", function(name: string) {\n        switch(helpers.stringTrim(name)) {\n\n        }\n        return null;\n    })\n\n    helpers._registerFactory(\"animation\", function(name: string) {\n        switch(helpers.stringTrim(name)) {\n\n        }\n        return null;\n    })\n\n    helpers._registerFactory(\"song\", function(name: string) {\n        switch(helpers.stringTrim(name)) {\n\n        }\n        return null;\n    })\n\n}\n// Auto-generated code. Do not edit.\n",
  "main.blocks": "<xml xmlns=\"https://developers.google.com/blockly/xml\"><variables><variable type=\"KIND_SpriteKind\" id=\"},eb:R5Mz])HHd~~oY:z\">Player</variable><variable type=\"KIND_SpriteKind\" id=\"W]IpXjaeOuhb^0%k%a7S\">Projectile</variable><variable type=\"KIND_SpriteKind\" id=\"me=2Llm*DO8~LvwC[EJG\">Food</variable><variable type=\"KIND_SpriteKind\" id=\"9I@(DT8PV1tB-:SfFT6@\">Enemy</variable><variable id=\"0]uOOv$61al8{8WtY%hu\">value</variable><variable id=\"M}(^Z7Q(,ZcBxpZ@tY4-\">cookieSprite</variable><variable id=\",|0wAx%?vY%B5ApbWR@9\">playerSprite</variable><variable id=\"R^V}`uZ#F(ts:]OrB@*N\">value2</variable><variable id=\"R!E32os+h8.:z[LqJjN#\">presentSprite</variable><variable id=\"(vPFE6`Q/MpAvjJ@@xrS\">mySprite</variable></variables><block type=\"pxt-on-start\" x=\"0\" y=\"0\"></block></xml>",
  "main.py": "def on_a_pressed():\n    if playerSprite.is_hitting_tile(CollisionDirection.BOTTOM):\n        playerSprite.vy = -200\ncontroller.A.on_event(ControllerButtonEvent.PRESSED, on_a_pressed)\n\ndef on_left_pressed():\n    playerSprite.set_image(assets.image(\"\"\"\n        santaLeft\n    \"\"\"))\ncontroller.left.on_event(ControllerButtonEvent.PRESSED, on_left_pressed)\n\ndef on_overlap_tile(sprite, location):\n    tiles.place_on_tile(sprite, tiles.get_tile_location(0, 0))\n    music.play(music.melody_playable(music.big_crash),\n        music.PlaybackMode.UNTIL_DONE)\nscene.on_overlap_tile(SpriteKind.player,\n    assets.tile(\"\"\"\n        snowPath13\n    \"\"\"),\n    on_overlap_tile)\n\ndef on_right_pressed():\n    playerSprite.set_image(assets.image(\"\"\"\n        santaRight\n    \"\"\"))\ncontroller.right.on_event(ControllerButtonEvent.PRESSED, on_right_pressed)\n\ndef on_on_overlap(sprite2, otherSprite):\n    sprites.destroy(otherSprite, effects.smiles, 500)\n    music.play(music.melody_playable(music.magic_wand),\n        music.PlaybackMode.UNTIL_DONE)\n    if len(sprites.all_of_kind(SpriteKind.food)) == 0:\n        game.game_over(True)\nsprites.on_overlap(SpriteKind.player, SpriteKind.food, on_on_overlap)\n\ndef on_on_overlap2(sprite3, otherSprite2):\n    sprites.destroy(otherSprite2, effects.disintegrate, 500)\n    info.change_countdown_by(-5)\n    music.play(music.melody_playable(music.zapped),\n        music.PlaybackMode.UNTIL_DONE)\nsprites.on_overlap(SpriteKind.player, SpriteKind.enemy, on_on_overlap2)\n\ncookieSprite: Sprite = None\npresentSprite: Sprite = None\nplayerSprite: Sprite = None\nscene.set_background_image(assets.image(\"\"\"\n    winterBackground\n\"\"\"))\ngame.splash(\"Oh no!\", \"Santa lost his presents!\")\ngame.splash(\"Collect all the presents\", \"before the time runs out!\")\ngame.splash(\"Avoid the milk and cookies\", \"they take away time!\")\ntiles.set_current_tilemap(tilemap(\"\"\"\n    level\n\"\"\"))\ninfo.start_countdown(30)\nplayerSprite = sprites.create(assets.image(\"\"\"\n    santaRight\n\"\"\"), SpriteKind.player)\ntiles.place_on_tile(playerSprite, tiles.get_tile_location(0, 6))\ncontroller.move_sprite(playerSprite, 100, 0)\nscene.camera_follow_sprite(playerSprite)\nplayerSprite.ay = 500\nfor value in tiles.get_tiles_by_type(assets.tile(\"\"\"\n    foodSpawnTile\n\"\"\")):\n    presentSprite = sprites.create(assets.image(\"\"\"\n        greenGift\n    \"\"\"), SpriteKind.food)\n    tiles.place_on_tile(presentSprite, value)\n    tiles.set_tile_at(value, assets.tile(\"\"\"\n        transparency16\n    \"\"\"))\nfor value2 in tiles.get_tiles_by_type(assets.tile(\"\"\"\n    enemySpawnTile\n\"\"\")):\n    cookieSprite = sprites.create(assets.image(\"\"\"\n        milkGlassCookie\n    \"\"\"), SpriteKind.enemy)\n    tiles.place_on_tile(cookieSprite, value2)\n    tiles.set_tile_at(value2, assets.tile(\"\"\"\n        transparency16\n    \"\"\"))",
  "main.ts": "\n",
  "pxt.json": "{\n    \"name\": \"JSON Santas Present Run\",\n    \"description\": \"\",\n    \"dependencies\": {\n        \"device\": \"*\"\n    },\n    \"files\": [\n        \"main.blocks\",\n        \"main.ts\",\n        \"README.md\",\n        \"assets.json\",\n        \"images.g.jres\",\n        \"images.g.ts\",\n        \"tilemap.g.jres\",\n        \"tilemap.g.ts\",\n        \"main.py\"\n    ],\n    \"targetVersions\": {\n        \"branch\": \"v1.12.46\",\n        \"tag\": \"v1.12.46\",\n        \"commits\": \"https://github.com/microsoft/pxt-arcade/commits/e66fb08db35df2249cd64300195259c64d497106\",\n        \"target\": \"1.12.46\",\n        \"pxt\": \"8.5.57\"\n    },\n    \"preferredEditor\": \"blocksprj\"\n}\n",
  "tilemap.g.jres": "{\n    \"tile1\": {\n        \"data\": \"hwQQABAAAAAREYERERERERERERkRERERGREREREREYERERERERERmBEREREREREREREREREREREREREZERERERERERkRERERERERERERERERERERERERERERERERERkREREREYERkRERGRERmBEREZEREREZERERkRERERERERGBERgREREREQ==\",\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"tilemapTile\": true,\n        \"displayName\": \"snow0\"\n    },\n    \"tile2\": {\n        \"data\": \"hwQQABAAAAAYEREREREREZERERkREZERERERkRERgRERERERERERGREREREREREREREREREREREREREREREREREREREREREREREREREREREYERERERERkRERERERkREREREREREYERERGREREREREZERERERERERkRERERERERGBEREZEREREQ==\",\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"tilemapTile\": true,\n        \"displayName\": \"snow1\"\n    },\n    \"tile3\": {\n        \"data\": \"hwQQABAAAACREREZERERERgREREREREREZGYmJiYmJgRgY2NjY2NjRGR2N3d3d3dEYHd3d3d0d0Rkdjd293d3RGB3b3R3d27EZHY3d293bsYgd3d3d3d3RGR2B3d3d3dEYHd3d3d3d0Rkdjd3R3b2xGB3d3dvd3dEZHYHd293d0Rgd0d0d3dHQ==\",\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"tilemapTile\": true,\n        \"displayName\": \"snowPath0\"\n    },\n    \"tile4\": {\n        \"data\": \"hwQQABAAAAARgd3d3d3d3RGR2N3d3d3dEYHd3d290d0Rkdjd3d3b3RGB3d3d3d3dEZHY3d3d3REYgd3d3d3dERGR2N3d3d3bEYHdvdHd3d0Rkdjd293d3RGB3d3d3d3dEZHY3d3d3d0RgY2NjY2NjRGRmJiYmJiYGBERERERERGREREZEREREQ==\",\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"tilemapTile\": true,\n        \"displayName\": \"snowPath1\"\n    },\n    \"tile5\": {\n        \"data\": \"hwQQABAAAADd3d3d3d2NEd3d3d3d3ZgR3d3dvd3djRHd3d3R3d2YEd293d3d3Y0R3Rvd3d3dmBHd3d3d3d2NEd3d3d3d3ZgR3d3d3b3djRHd3d3d292YEd3d3R3d3Y2R3d3d3d3dmBGNjY2NjY2NEZiYmJiYmJgRERERERERERERERERERERkQ==\",\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"tilemapTile\": true,\n        \"displayName\": \"snowPath2\"\n    },\n    \"tile6\": {\n        \"data\": \"hwQQABAAAAARERGBERERmBERERERERERmJiYmJiYmBGNjY2NjY2NEd3d3d3d3ZgR293d3d3djRHd3dHd0d2Ykd0d3d293Y0R3d3d3d3dmJHd3d3d3d2NEd0b3d3d3ZgR3b3d3d3djRHd3d0R3dGYEd3d3Rvd3Y0R3d3d3d3dmBEd3d3d3dGNEQ==\",\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"tilemapTile\": true,\n        \"displayName\": \"snowPath3\"\n    },\n    \"tile7\": {\n        \"data\": \"hwQQABAAAAARERERERERERERERERERERmJiYmJiYmJiNjY2NjY2Njd3d3d3d3d3d3d3dvd3dvd3d3d0b3d0d2x3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d0d0d293d3d3R3R3b3R3dvd3d3d3dvd3d3d3d3d3d3d3dvdHd3d3d3du93d3d3b3Q==\",\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"tilemapTile\": true,\n        \"displayName\": \"snowPath4\"\n    },\n    \"tile8\": {\n        \"data\": \"hwQQABAAAADdHd3d3d3d3d3d0d3R3d293d3d3d3d3dHd3d3d3dvd292x3d290d3d3Rvd3d3d3d3d293d3d3d3d3d3d3d3d3d3d3d3d3du93dHd293d273d3d3b3d3d3d3d3d3d3d3d2NjY2NjY2NjZiYmJiYmJiYEREREREREREREREREREREQ==\",\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"tilemapTile\": true,\n        \"displayName\": \"snowPath5\"\n    },\n    \"tile9\": {\n        \"data\": \"hwQQABAAAAARgd3d0d0d2xGR2N3dHd3dEYHd3d3d3d0Rkdix3d3d3RGB3dvd3d3dEZHY3d3dvd0Rgd3d3d3d3RGR2N0d293dEYHd3b3R3d0Rkbjb3d293RGBvdHd3d3REZHY3d3dvd0Rgd3d3d3d3RGR2B3R3d3dEYHdHdvdvd0Rkdjd3d3d3Q==\",\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"tilemapTile\": true,\n        \"displayName\": \"snowPath6\"\n    },\n    \"tile10\": {\n        \"data\": \"hwQQABAAAAC90d3dHdGYEd293dEd0Y0R3d3d3d3dmBHd3d3d3d2NEd3d3b3d3ZgR3R3R3d3djRHdHdHd3d2YER3d3d3d3Y0R3d3d3R3bmBHd3d3R3d2NEd3d3d3d3ZgRu93d3d3djRG73dvd3d2YEd3dsdvd3Y0R3d3d3R3dmBHd3d3d3d2NEQ==\",\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"tilemapTile\": true,\n        \"displayName\": \"snowPath7\"\n    },\n    \"tile11\": {\n        \"data\": \"hwQQABAAAACREREZERERERgRERERERERERGIiIiIiIgRgZGZmZmZmRGBGZmZmZmREYGZmZmZmRkRgZmZGRmZmRGBmZmZkZGZEYGZmZmZmZkYgZmZmZmZmRGBGRmZmZmZEYGZkZGZmZkRgZmZmZmZmRGBmZmZmZmZEYGRmZmRmZkRgRmZmRmZmQ==\",\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"tilemapTile\": true,\n        \"displayName\": \"snowPath8\"\n    },\n    \"tile12\": {\n        \"data\": \"hwQQABAAAAARgZGZmZmZmRGBGZmZmZmZEYGZmZmZkZkRgZmZmZkZmRGBmZmZmZmREYGZmZmZmZkYgZmZmZmZmRGBmZmZmZmZEYGZmRGZmZkRgZmZGZmZmRGBmZmZmZmZEYGZmZmZmZkRgZGZmZmZmRERiIiIiIiIGBERERERERGREREZEREREQ==\",\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"tilemapTile\": true,\n        \"displayName\": \"snowPath9\"\n    },\n    \"tile14\": {\n        \"data\": \"hwQQABAAAAAREREYERGRGBEREZERERERiIiIiIiIGBGZmZmZmRmJEZmZmZmZmYERmZmZmZmZiRGZmZmZkZmJEZmZmZkZmYkRmZmZmZmZiZGZmZmZmZmJEZmZmZmZmYkRmZmRmZmZiRGZmRmZmZmJEZGZmZGZmYkRGZmZmZkZiRGZmZmZmZmBEQ==\",\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"tilemapTile\": true,\n        \"displayName\": \"snowPath11\"\n    },\n    \"tile13\": {\n        \"data\": \"hwQQABAAAACZmZmZmZmJEZmZmZmZmYkRmZmZmZGRiRGZmZmZGRmJEZmRmZmZmYERmRmZmZmZiRGZmZmZmZmJEZmZmZmZmYmRmZmZmZGZiRGZmZmZGZmJEZGZmZmZmYkRGZmZmZmZiRGZmZmZmZmJEYiIiIiIiBgRERERkREREREREREYERGRGA==\",\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"tilemapTile\": true,\n        \"displayName\": \"snowPath10\"\n    },\n    \"tile17\": {\n        \"data\": \"hwQQABAAAAARgZmZmZmZmRGBmZmZmZmREYGZGZmZmRkRgZmZkZmZmRGBmZmZmZmZEYGZmZkZmZkZgZmZmZmRmZGBmZmZmZmZEYGZmZmZmZkRgZmRmZmZmRGBmZmZmZmZEYGZmZmRmZkRgZmZmRmZGRmBmZmZmZmZEYGZGZmZmZkRgZmZkZmZmQ==\",\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"tilemapTile\": true,\n        \"displayName\": \"snowPath12\"\n    },\n    \"tile18\": {\n        \"data\": \"hwQQABAAAACZmZmZmZmJEZmZmZmZmYkRmZmZmZmZiRGZmRkZmZmJEZmZmZGRmYkRkZmZmRmZiREZmZmZmZmJEZmZmZmZmYmRmZmZmZmZiRGZmZmZmZmJEZmZGZmZmYkRmZmZkZmZiRGZmZmZmZmJEZmRmZmZkYkRmRmZmZmRiRGZmZmZmRmJGQ==\",\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"tilemapTile\": true,\n        \"displayName\": \"snowPath13\"\n    },\n    \"tile19\": {\n        \"data\": \"hwQQABAAAAARGRERERERERERkRERERERiIiIiIiIiIiZGZmZmZmZmZmZkZmZmZmZmZmZmZkZmZmZmZmZmZmRmZmZmZGRmZmZmZmZGZmZmZmZmZmZmZmZmZmZmZmZmZmZmRmZmZmZmZmZmZGZmZmZmZmZmZmZmZmZmZmZmZmRmZmZmZmZmRmZmQ==\",\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"tilemapTile\": true,\n        \"displayName\": \"snowPath14\"\n    },\n    \"tile20\": {\n        \"data\": \"hwQQABAAAACZmZmRmZmZmZmZmRmZmZGZkZmZmZmZGZkZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZGZmZmZmZmZGRmZmZGZmZmZkZGZGZmZmZmZmZmZmZmRmZmZmZmZmRmZmZmZmZmZmZmZmZmZmYiIiIiIiIiIEREREREREREREREREREREQ==\",\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"tilemapTile\": true,\n        \"displayName\": \"snowPath15\"\n    },\n    \"tile16\": {\n        \"data\": \"hwQQABAAAADd3d3d3d3d3d3d3d3d3d3d3d29Hd3d3d3d3b3d3R3b3d3d3d3dvd3d3dHd3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3dHdHdHd3d3d0d0d3d3d29293d3d3d3b3b3d3d3d3d3d3dvd3d3d3d3d3d3d3b3d3d3d3d3d3d3d3d3d3d3Q==\",\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"tilemapTile\": true,\n        \"displayName\": \"snowPath16\"\n    },\n    \"transparency16\": {\n        \"data\": \"hwQQABAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA==\",\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"tilemapTile\": true\n    },\n    \"tile35\": {\n        \"data\": \"hwQQABAAAACZmZmZmZmZmZmZmZkZGZmZmZmZmZmRmZmZGZmZmZmZmZmZkZmZmZmZmZmZmZkZmZmZmZmZmZmRmRmZmZGRmZmZmZmZGZmZmZmZmZmZmZmZmZmZmZmZmZGRmRmZmZmZGZmZmZGZmZmZmZmZmZmZmZmZmZmZmZmRmZmZmZmZmRmZmQ==\",\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"tilemapTile\": true,\n        \"displayName\": \"snowPath30\"\n    },\n    \"tile36\": {\n        \"data\": \"hwQQABAAAAAREREYERGRGBEREZERERERkYGIiIiIGBEYmJmZmRmJERGYkZmZmYEREZiZmZmZiRERmJmZkZmJERGYmZkZmYkREZiZmZmZiZERmJmZmZmJERGYmZmZmYkRkZiRmZmZiRERmBmZmZmJERGYmZGZmYkREZiZmZkZiRERmJmZmZmBEQ==\",\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"tilemapTile\": true,\n        \"displayName\": \"snowPath31\"\n    },\n    \"tile37\": {\n        \"data\": \"hwQQABAAAAARmJmZmZmBERGYmZmZGYkREZiZkZmZiRERmBmZmZmJEZGYkZmZmYkREZiZmZmZiRERmJmZmZmJERGYmZmZmYmREZiZmRmZiRERmJmZkZmJERGYmZmZmYkREZiRmZmZgREYmJmZmRmJEZGBiIiIiBgRERERkREREREREREYERGRGA==\",\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"tilemapTile\": true,\n        \"displayName\": \"snowPath32\"\n    },\n    \"tile38\": {\n        \"data\": \"hwQQABAAAAARmJmZmZmBERGYmZmZGYkREZiZkZmZiRERmBmZmZmJgZGYkZmZmYkREZiZmZmRiRERmJmZmZmJERGYmZmZmYmRGZiZmRmZiRERmJmZkZmJGRGYmZmZmYmBEZiRmZmZgREYmJmZmRmJEZGYmZmRmYkREZiRGZmZiRERmJmZmZmJEQ==\",\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"tilemapTile\": true,\n        \"displayName\": \"snowPath33\"\n    },\n    \"tile33\": {\n        \"data\": \"hwQQABAAAABVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVQ==\",\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"tilemapTile\": true,\n        \"displayName\": \"enemySpawnTile\"\n    },\n    \"tile39\": {\n        \"data\": \"hwQQABAAAAB3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3d3dw==\",\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"tilemapTile\": true,\n        \"displayName\": \"foodSpawnTile\"\n    },\n    \"level2\": {\n        \"id\": \"level2\",\n        \"mimeType\": \"application/mkcd-tilemap\",\n        \"data\": \"MTAzYzAwMDgwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwODAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwODAwMDAwMDAwMDAwMDAwMDAwMDAxMDIwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDQwNjA2MDUwMDAwMDAwMDAwMDAwMDAwMDAwNDA1MDAwMDAwMDAwMDAwMDAwMTAzMDMwMjAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDA4MDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDEwMzAzMDMwMzAyMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAxMDMwMzAzMDMwMzAzMDMwMzAzMDMwMjA3MDcwNzAxMDMwMzAzMDIwNzA3MDcwNzAxMDMwMzAzMDMwMzAzMDIwNzA3MDcwNzAxMDMwMzAzMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMjAwMjAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAyMjIyMDAwMDAwMDAyMDAyMDAwMDAwMjIyMjAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDIwMjIyMjAyMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDIyMjIyMjIyMjIyMjAwMjAyMjIyMDAwMDIyMjIyMjIyMDAwMDIyMjIwMDAwMDAwMDAwMDAwMDAwMDAwMA==\",\n        \"tileset\": [\n            \"myTiles.transparency16\",\n            \"myTiles.tile11\",\n            \"myTiles.tile12\",\n            \"myTiles.tile17\",\n            \"myTiles.tile36\",\n            \"myTiles.tile37\",\n            \"myTiles.tile38\",\n            \"myTiles.tile18\",\n            \"myTiles.tile39\"\n        ],\n        \"displayName\": \"level\"\n    },\n    \"*\": {\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"dataEncoding\": \"base64\",\n        \"namespace\": \"myTiles\"\n    }\n}",
  "tilemap.g.ts": "// Auto-generated code. Do not edit.\nnamespace myTiles {\n    //% fixedInstance jres blockIdentity=images._tile\n    export const tile1 = image.ofBuffer(hex``);\n    //% fixedInstance jres blockIdentity=images._tile\n    export const tile2 = image.ofBuffer(hex``);\n    //% fixedInstance jres blockIdentity=images._tile\n    export const tile3 = image.ofBuffer(hex``);\n    //% fixedInstance jres blockIdentity=images._tile\n    export const tile4 = image.ofBuffer(hex``);\n    //% fixedInstance jres blockIdentity=images._tile\n    export const tile5 = image.ofBuffer(hex``);\n    //% fixedInstance jres blockIdentity=images._tile\n    export const tile6 = image.ofBuffer(hex``);\n    //% fixedInstance jres blockIdentity=images._tile\n    export const tile7 = image.ofBuffer(hex``);\n    //% fixedInstance jres blockIdentity=images._tile\n    export const tile8 = image.ofBuffer(hex``);\n    //% fixedInstance jres blockIdentity=images._tile\n    export const tile9 = image.ofBuffer(hex``);\n    //% fixedInstance jres blockIdentity=images._tile\n    export const tile10 = image.ofBuffer(hex``);\n    //% fixedInstance jres blockIdentity=images._tile\n    export const tile11 = image.ofBuffer(hex``);\n    //% fixedInstance jres blockIdentity=images._tile\n    export const tile12 = image.ofBuffer(hex``);\n    //% fixedInstance jres blockIdentity=images._tile\n    export const tile14 = image.ofBuffer(hex``);\n    //% fixedInstance jres blockIdentity=images._tile\n    export const tile13 = image.ofBuffer(hex``);\n    //% fixedInstance jres blockIdentity=images._tile\n    export const tile17 = image.ofBuffer(hex``);\n    //% fixedInstance jres blockIdentity=images._tile\n    export const tile18 = image.ofBuffer(hex``);\n    //% fixedInstance jres blockIdentity=images._tile\n    export const tile19 = image.ofBuffer(hex``);\n    //% fixedInstance jres blockIdentity=images._tile\n    export const tile20 = image.ofBuffer(hex``);\n    //% fixedInstance jres blockIdentity=images._tile\n    export const tile16 = image.ofBuffer(hex``);\n    //% fixedInstance jres blockIdentity=images._tile\n    export const transparency16 = image.ofBuffer(hex``);\n    //% fixedInstance jres blockIdentity=images._tile\n    export const tile35 = image.ofBuffer(hex``);\n    //% fixedInstance jres blockIdentity=images._tile\n    export const tile36 = image.ofBuffer(hex``);\n    //% fixedInstance jres blockIdentity=images._tile\n    export const tile37 = image.ofBuffer(hex``);\n    //% fixedInstance jres blockIdentity=images._tile\n    export const tile38 = image.ofBuffer(hex``);\n    //% fixedInstance jres blockIdentity=images._tile\n    export const tile33 = image.ofBuffer(hex``);\n    //% fixedInstance jres blockIdentity=images._tile\n    export const tile39 = image.ofBuffer(hex``);\n\n    helpers._registerFactory(\"tilemap\", function(name: string) {\n        switch(helpers.stringTrim(name)) {\n            case \"level\":\n            case \"level2\":return tiles.createTilemap(hex`3c000800000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000008000000000000000000000008000000000000000000010200000000000000000000000000000000000000000000000000000000000000000000000406060500000000000000000004050000000000000001030302000000000000000000000000000000000000000000000000000000000000000000000000000000080000000000000000000000000000000103030303020000000000000000000000000000000000000000000000000000000000010303030303030303030302070707010303030207070707010303030303030207070707010303030000000000000000000000000000000000000000`, img`\n............................................................\n............................................................\n............................................................\n............................................................\n...........................22...............................\n....2222.........22.......2222..............................\n.........................222222.............................\n222222222222...22222....22222222....2222....................\n`, [myTiles.transparency16,myTiles.tile11,myTiles.tile12,myTiles.tile17,myTiles.tile36,myTiles.tile37,myTiles.tile38,myTiles.tile18,myTiles.tile39], TileScale.Sixteen);\n        }\n        return null;\n    })\n\n    helpers._registerFactory(\"tile\", function(name: string) {\n        switch(helpers.stringTrim(name)) {\n            case \"snow0\":\n            case \"tile1\":return tile1;\n            case \"snow1\":\n            case \"tile2\":return tile2;\n            case \"snowPath0\":\n            case \"tile3\":return tile3;\n            case \"snowPath1\":\n            case \"tile4\":return tile4;\n            case \"snowPath2\":\n            case \"tile5\":return tile5;\n            case \"snowPath3\":\n            case \"tile6\":return tile6;\n            case \"snowPath4\":\n            case \"tile7\":return tile7;\n            case \"snowPath5\":\n            case \"tile8\":return tile8;\n            case \"snowPath6\":\n            case \"tile9\":return tile9;\n            case \"snowPath7\":\n            case \"tile10\":return tile10;\n            case \"snowPath8\":\n            case \"tile11\":return tile11;\n            case \"snowPath9\":\n            case \"tile12\":return tile12;\n            case \"snowPath11\":\n            case \"tile14\":return tile14;\n            case \"snowPath10\":\n            case \"tile13\":return tile13;\n            case \"snowPath12\":\n            case \"tile17\":return tile17;\n            case \"snowPath13\":\n            case \"tile18\":return tile18;\n            case \"snowPath14\":\n            case \"tile19\":return tile19;\n            case \"snowPath15\":\n            case \"tile20\":return tile20;\n            case \"snowPath16\":\n            case \"tile16\":return tile16;\n            case \"transparency16\":return transparency16;\n            case \"snowPath30\":\n            case \"tile35\":return tile35;\n            case \"snowPath31\":\n            case \"tile36\":return tile36;\n            case \"snowPath32\":\n            case \"tile37\":return tile37;\n            case \"snowPath33\":\n            case \"tile38\":return tile38;\n            case \"enemySpawnTile\":\n            case \"tile33\":return tile33;\n            case \"foodSpawnTile\":\n            case \"tile39\":return tile39;\n        }\n        return null;\n    })\n\n}\n// Auto-generated code. Do not edit.\n"
}
```

```template
function spawnCookies () {
    for (let value of tiles.getTilesByType(assets.tile`enemySpawnTile`)) {
        let cookieSprite = sprites.create(santaImg.milkGlassCookie, SpriteKind.Enemy)
        tiles.placeOnTile(cookieSprite, value)
        tiles.setTileAt(value, assets.tile`transparency16`)
    }
}
controller.A.onEvent(ControllerButtonEvent.Pressed, function () {
    if (playerSprite.isHittingTile(CollisionDirection.Bottom)) {
    	
    }
})
controller.left.onEvent(ControllerButtonEvent.Pressed, function () {
    playerSprite.setImage(santaImg.santaLeft)
})
scene.onOverlapTile(SpriteKind.Player, assets.tile`snowPath13`, function (sprite, location) {
    tiles.placeOnTile(sprite, tiles.getTileLocation(0, 6))
})
controller.right.onEvent(ControllerButtonEvent.Pressed, function () {
    playerSprite.setImage(santaImg.santaRight)
})
sprites.onOverlap(SpriteKind.Player, SpriteKind.Enemy, function (sprite, otherSprite) {
    sprites.destroy(otherSprite, effects.disintegrate, 500)
})
sprites.onOverlap(SpriteKind.Player, SpriteKind.Food, function (sprite, otherSprite) {
    sprites.destroy(otherSprite, effects.smiles, 500)
    if (sprites.allOfKind(SpriteKind.Food).length == 0) {
        game.gameOver(true)
    }
})
function spawnPresents () {
    for (let value of tiles.getTilesByType(assets.tile`foodSpawnTile`)) {
        let presentSprite = sprites.create(santaImg.greenGift, SpriteKind.Food)
        tiles.placeOnTile(presentSprite, value)
        tiles.setTileAt(value, assets.tile`transparency16`)
    }
}
scene.setBackgroundImage(santaImg.winterBackground)
tiles.setCurrentTilemap(tilemap`level`)
spawnPresents()
spawnCookies()
let playerSprite = sprites.create(santaImg.santaRight, SpriteKind.Player)
```

## Santa's Present Run! @showdialog

Oh no! Santa slipped on the ice and lost all of his presents! Code this game to help Santa get all of his presents back in time for Christmas! But watch out for the milk and cookies - they might be tasty but they will make Santa lose valuable time!

Click ``||loops:Ok||`` to get started!

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo") 

## Position Santa on the tilemap!

Santa is currently stuck in the middle of our screen! Let's add code to position Santa on the **tilemap**!

---

- :tree: Open the ``||scene:Scene||`` code block menu, and drag out a ``||scene:place mySprite on top of  (tilemap)||`` block. 
- :tree: Place the block under the ``||variables:set playerSprite to||`` block, then change ``||variables:mySprite||`` to ``||variables:playerSprite||``.
- :tree: Leave the **col** value set to 0, but change the **row** to **6** so Santa is standing on top of the tilemap ground.
- :play: Click the Play button to see Santa's position change on the MakeCode Arcade emulator screen!

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo") 

```blocks
let playerSprite = sprites.create(santaImg.santaRight, SpriteKind.Player)
tiles.placeOnTile(playerSprite, tiles.getTileLocation(0, 6))
```

## Move Santa around the tilemap!

Add code to let Santa move left and right to explore the **tilemap**!

---

- :game controller: Open the ``||controller:Controller||`` code block menu, and drag out a ``||controller:move mySprite with buttons||`` block.
- :game controller: Place the block underneath the ``||scene:place mySprite on top of  (tilemap)||`` block then change ``||variables:mySprite||`` to ``||variables:playerSprite||``.
- :game controller: Click ``||controller:+||`` to open the **vx** and **vy** parameters, which control how fast and in which direction the sprite can move.
- :game controller: Leave **vx** set to 100, but change **vy** to **0** so Santa can only move left and right on this 2D platformer tilemap.
- :tree: Open ``||scene:Scene||`` and drag a ``||scene:camera follow sprite||`` block underneath the previous block, then update the sprite name in the red bubble.
- :play: Click the Play button to test that Santa moves correctly, and the camera follows him as he moves around the tilemap!

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo") 

```blocks
let playerSprite = sprites.create(santaImg.santaRight, SpriteKind.Player)
tiles.placeOnTile(playerSprite, tiles.getTileLocation(0, 6))
controller.moveSprite(playerSprite, 100, 0)
scene.cameraFollowSprite(playerSprite)
```

## Code Santa to jump!

Santa needs to be able to jump up onto the platforms and over the ice! Let's fix that now!

---

- :paper plane: Open ``||sprites:Sprites||`` and drag a ``||sprites:set mySprite x||`` block underneath the other ``||variables:playerSprite||`` code. 
- :paper plane: Click on ``||sprites:x||`` to open the dropdown menu. Select ``||sprites:ay (acceleration y)||`` then update the sprite name and type **500** in the white bubble.
- :game controller: Find the ``||controller:on A button pressed||`` container already in the code, and notice the ``||logic:if||`` **conditional** statement inside.
- :paper plane: Open the ``||sprites:Sprites||`` code block menu and drag a ``||sprites:set mySprite x||`` block inside the ``||logic:if||`` **conditional**. 
- :paper plane: Click on ``||sprites:x||`` to open the dropdown menu. Select ``||sprites:vy (velocity y)||`` then update the sprite name and type **-200** in the white bubble.
- :play: Click the Play button, then test out the jump with the A button. The **conditional** will only allow your sprite to jump up if the bottom of your sprite is touching a tilemap wall (the ground).

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo") 

```blocks
let playerSprite = sprites.create(santaImg.santaRight, SpriteKind.Player)
tiles.placeOnTile(playerSprite, tiles.getTileLocation(0, 6))
controller.moveSprite(playerSprite, 100, 0)
scene.cameraFollowSprite(playerSprite)
playerSprite.ay = 500

controller.A.onEvent(ControllerButtonEvent.Pressed, function () {
    if (playerSprite.isHittingTile(CollisionDirection.Bottom)) {
        playerSprite.vy = -200
    }
})
```

## Finish the tilemap design!

After exploring the tilemap, did you notice it is unfinished? Let's fix that!

---

- :tree: Find the ``||scene:set tilemap to||`` block near the top of the ``||loops:on start||`` container. Click the gray square to open the tilemap editor. ![image](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/tilemap%20unfinished.png?raw=true "unfinished tilemap") 
- :map: Notice the different tiles that make up the tilemap. Find those tiles by clicking on **My Tiles** then use them to finish the tilemap by adding ground tiles for Santa to walk on and platform tiles for Santa to jump up on! ![image](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/my%20tiles.png?raw=true "My Tiles image")
- :map: Turn all of these ground and platform tiles into **walls** by clicking on the **Draw Walls** button and using the Paint Tool to paint over all of the tiles that Santa will need to walk on.
- :map: Click ``||loops:Done||`` then click the Play button to explore your finished tilemap!

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo") 

## Add the presents for Santa to collect!

Where are all the presents?? Add the lost presents to the tilemap for Santa to collect!

---

- :function: Find the ``||function:function spawnPresents||`` container in the coding area. Notice it will place a ``||variables:presentSprite||`` on any green **spawn** tile in the tilemap. Only there are no green tiles yet! Let's add some now!
- :map: Open the tilemap editor again. Find the green **spawn** tile under **My Tiles** then place 8-10 on the tilemap in a location where Santa can reach them. ![image](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/tilemap%20spawn%20tiles.png?raw=true "spawn tiles")
- :map: Click ``||loops:Done||`` then click the Play button to find the present sprites on the tilemap! You'll notice the green **spawn** tiles are gone; the code in the function replaces the tile with a blank tile after placing a sprite on it.


![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo") 


## Add the obstacles for Santa to avoid!

Santa loves some milk and cookies, but they distract him from finding the lost presents! Add some obstacles to the tilemap to make the game more challenging!


---

- :function: Find the ``||function:function spawnCookies||`` container in the coding area. Notice it will place a ``||variables:cookieSprite||`` on any yellow **spawn** tile in the tilemap. Only there are no yellow tiles yet! Let's add some now!
- :map: Open the tilemap editor again. Find the yellow **spawn** tile under **My Tiles** then place 6-8 on the tilemap in a location where Santa can reach them. 
- :map: Click ``||loops:Done||`` then click the Play button to find the milk and cookies sprites on the tilemap! You'll notice the yellow **spawn** tiles are gone; the code in the function replaces the tile with a blank tile after placing a sprite on it.

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo") 

## Add a countdown timer!

Add a countdown timer to make the game more challenging! Reduce the time when Santa gets distracted by milk and cookies!

---

- :id card: Open the ``||info:Info||`` code block menu to drag out a ``||info:start countdown||`` block into the ``||loops:on start||`` container. 
- :id card: Fill in the white bubble with the number of seconds for the timer to start with, such as **30**.
- :id card: Open ``||info:Info||`` again to drag out a ``||info:change countdown by||`` block into the ``||sprites: on sprite of kind (Player) overlaps otherSprite of kind (Enemy)||`` container.
- :id card: Fill in the white bubble with the number of seconds to reduce the time by, such as **-5**.
- :play: Click the Play button to test the timer code, ensuring the countdown timer is reduced when Santa overlaps a milk and cookies sprite.

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo") 

```blocks
let playerSprite = sprites.create(santaImg.santaRight, SpriteKind.Player)
tiles.placeOnTile(playerSprite, tiles.getTileLocation(0, 6))
controller.moveSprite(playerSprite, 100, 0)
scene.cameraFollowSprite(playerSprite)
playerSprite.ay = 500
info.startCountdown(30)

sprites.onOverlap(SpriteKind.Player, SpriteKind.Enemy, function (sprite, otherSprite) {
    sprites.destroy(otherSprite, effects.disintegrate, 500)
    info.changeCountdownBy(-5)
})
```

## Add sound and game over effects to the game!

Adding sounds and customizing the Game Over screen will make your game even more fun to play!

---

- :headphones: Open the ``||music:Music||`` code block menu and drag out ``||music:play sound until done||`` blocks into the 2 sprite ``||sprites:overlap||`` and 1 tile ``||scene:overlap||`` containers. 
- :circle: Open the ``||game:Game||`` code block menu and drag out any of the blocks that will customize the Game Over screen into the ``||logic:if||`` statement inside the ``||sprites:on sprite of kind (Player) overlaps otherSprite of kind (Food)||`` container. Be sure to place these blocks above the ``||game:game over||`` block.

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo") 

```blocks
scene.onOverlapTile(SpriteKind.Player, assets.tile`snowPath13`, function (sprite, location) {
    tiles.placeOnTile(sprite, tiles.getTileLocation(0, 6))
    music.play(music.melodyPlayable(music.knock), music.PlaybackMode.UntilDone)
})
sprites.onOverlap(SpriteKind.Player, SpriteKind.Food, function (sprite, otherSprite) {
    sprites.destroy(otherSprite, effects.smiles, 500)
    music.play(music.melodyPlayable(music.magicWand), music.PlaybackMode.UntilDone)
    if (sprites.allOfKind(SpriteKind.Food).length == 0) {
        game.setGameOverEffect(true, effects.smiles)
        game.gameOver(true)
    }
})
sprites.onOverlap(SpriteKind.Player, SpriteKind.Enemy, function (sprite, otherSprite) {
    sprites.destroy(otherSprite, effects.disintegrate, 500)
    music.play(music.melodyPlayable(music.zapped), music.PlaybackMode.UntilDone)
    info.changeCountdownBy(-5)
})
```

## Add game instructions at the beginning!

Before you complete your game, add a splash message with game instructions at the start of the game!

---

- :circle: Open the ``||game:Game||`` code block menu and drag out 1 or more ``||game:splash||`` blocks into the ``||loops:on start||`` container. Place these blocks after the ``||scene:set background image||`` block.
- :circle: Type a short message in the white bubble to be displayed on screen. Press ``||game:+||`` to add a second line to the message.
- :play: Click the Play button to see your splash messages appear on screen, then edit the messages, adding more ``||game:splash||`` blocks as needed to make the entire message fit.

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo") 

```blocks
scene.setBackgroundImage(santaImg.winterBackground)
game.splash("Oh no!", "Santa lost his presents!")
game.splash("Collect all the presents", "before the time runs out")
game.splash("Avoid the milk and cookies", "they take away time!")
tiles.setCurrentTilemap(tilemap`level`)
```

## Congratulations on finishing your game!

Now go help Santa collect all his lost presents!

Click Done to open your game in MakeCode Arcade, where you can add to your code and create a link to share your game with others! 

Happy coding!

![Logo](https://github.com/Code-Ninjas-Home-Office/game-building-session-tutorials/blob/master/images/CN-Logo.png?raw=true "CN Logo") 

```package
santaImg=github:Code-Ninjas-Home-Office/santas-present-run-image-pack
```
