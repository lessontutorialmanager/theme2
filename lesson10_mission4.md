# ゲームをさらに面白(おもしろ)くしよう！



```template

player.onDied(function () {
    if (スイッチ == true) {
        スイッチ = false
        gameplay.title(mobs.target(LOCAL_PLAYER), "終了！", "")
        mobs.kill(
        mobs.entitiesByType(mobs.monster(ZOMBIE))
        )
        gameplay.setDifficulty(PEACEFUL)
    }
})
mobs.onMobKilled(mobs.monster(ZOMBIE), function () {
    if (スイッチ == true) {
        倒した数 += 1
        for (let index = 0; index < randint(1, 3); index++) {
            player.runChatCommandWithArguments("z", "")
        }
    }
})
player.onChat("set", function () {
    blocks.fill(
    BLOCK_OF_QUARTZ,
    world(136, 63, 163),
    world(145, 63, 167),
    FillOperation.Replace
    )
})
player.onChat("z", function () {
    mobs.spawn(mobs.monster(ZOMBIE), randpos(
    world(136, 63, 173),
    world(145, 63, 183)
    ))
})
player.onArrowShot(function () {
    矢の数 += -1
    if (矢の数 == 0) {
        mobs.give(
        mobs.target(LOCAL_PLAYER),
        ARROW,
        64
        )
        player.say("矢を手に入れた！")
        矢の数 = 64
    }
})
player.onChat("tp", function () {
    while (スイッチ == true) {
        if (player.position().getValue(Axis.Y) < 64) {
            player.say("足場から出てしまった！")
            player.teleport(world(140, 64, 164))
        }
    }
})
player.onItemInteracted(STICK, function () {
    mobs.teleportToPosition(
    mobs.entitiesByType(mobs.monster(ZOMBIE)),
    randpos(
    world(136, 63, 175),
    world(145, 63, 183)
    )
    )
})
player.onChat("timer", function () {
    while (スイッチ == true) {
        loops.pause(1000)
        タイム += -1
        if (タイム == 10) {
            player.say("のこり10秒！")
        }
        if (タイム == 0) {
            スイッチ = false
            gameplay.title(mobs.target(LOCAL_PLAYER), "終了！", "倒した数" + 倒した数)
            mobs.kill(
            mobs.entitiesByType(mobs.monster(ZOMBIE))
            )
            gameplay.setDifficulty(PEACEFUL)
        }
    }
})
player.onChat("run", function () {
    if (スイッチ == false) {
        スイッチ = true
        mobs.give(
        mobs.target(LOCAL_PLAYER),
        BOW,
        1
        )
        mobs.give(
        mobs.target(LOCAL_PLAYER),
        ARROW,
        64
        )
        mobs.give(
        mobs.target(LOCAL_PLAYER),
        STICK,
        64
        )
        矢の数 = 64
        タイム = 30
        倒した数 = 0
        gameplay.setDifficulty(NORMAL)
        gameplay.title(mobs.target(LOCAL_PLAYER), "スタート！", "")
        player.runChatCommandWithArguments("tp", "")
        player.runChatCommandWithArguments("z", "")
        player.runChatCommandWithArguments("timer", "")
    }
})
player.onTravelled(WALK, function () {
    if (blocks.testForBlock(BLOCK_OF_QUARTZ, pos(0, -1, 0))) {
        mobs.applyEffect(NIGHT_VISION, mobs.target(LOCAL_PLAYER), 60, 10)
    }
})
let タイム = 0
let 矢の数 = 0
let 倒した数 = 0
let スイッチ = false
スイッチ = false

```

## ゲームをさらに面白くしよう！@unplugged
工夫してゲームをもっと難(むずか)しくしたり面白くしたりしよう！


## 例①
透明(とうめい)化や再生(さいせい)など、くじの種類(しゅるい)を増(ふ)やしてみよう！



## 例➁
モンスターの種類をゾンビ以外(いがい)にしてみよう！
