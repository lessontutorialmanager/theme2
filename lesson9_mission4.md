# ゲームをさらに面白(おもしろ)くしよう！



```template

loops.forever(function () {
    if (blocks.testForBlock(ORANGE_CONCRETE, pos(0, -1, 0))) {
        if (スイッチ == false) {
            gameplay.title(mobs.target(LOCAL_PLAYER), "スタート！", "")
            スイッチ = true
            player.runChatCommandWithArguments("a", "")
            player.runChatCommandWithArguments("b", "")
        }
    }
    if (blocks.testForBlock(YELLOW_CONCRETE, pos(0, -1, 0))) {
        if (スイッチ == true) {
            スイッチ = false
            gameplay.title(mobs.target(LOCAL_PLAYER), "ゴール！", "")
        }
    }
    if (player.position().getValue(Axis.Y) < 100) {
        player.say("落ちてしまった！")
        player.teleport(world(-17, 109, 105))
    }
})
player.onChat("a", function () {
    while (スイッチ) {
        if (blocks.testForBlock(EMERALD_BLOCK, pos(0, -1, 0))) {
            エメラルドの座標 = pos(0, -1, 0)
            mobs.applyEffect(SPEED, mobs.target(LOCAL_PLAYER), 3, 1)
            blocks.replace(
            SAND,
            EMERALD_BLOCK,
            positions.add(
            エメラルドの座標,
            pos(-1, 0, -1)
            ),
            positions.add(
            エメラルドの座標,
            pos(1, 0, 1)
            )
            )
            blocks.replace(
            EMERALD_BLOCK,
            AIR,
            world(-17, 108, 130),
            world(-15, 108, 160)
            )
            blocks.replace(
            EMERALD_BLOCK,
            AIR,
            world(-13, 108, 155),
            world(-11, 108, 170)
            )
            blocks.replace(
            EMERALD_BLOCK,
            AIR,
            world(-17, 108, 165),
            world(-15, 108, 175)
            )
        }
    }
})
let エメラルドの座標: Position = null
let スイッチ = false
スイッチ = false
let 開始位置: Position = null
開始位置 = world(-15, 108, 184)
blocks.fill(
EMERALD_BLOCK,
world(-17, 108, 130),
world(-15, 108, 160),
FillOperation.Replace
)
blocks.fill(
EMERALD_BLOCK,
world(-13, 108, 155),
world(-11, 108, 170),
FillOperation.Replace
)
blocks.fill(
EMERALD_BLOCK,
world(-17, 108, 165),
world(-15, 108, 175),
FillOperation.Replace
)
player.onChat("b", function () {
    while (スイッチ) {
        for (let index = 0; index < 6; index++) {
            blocks.fill(
            AIR,
            positions.add(
            開始位置,
            pos(0, 0, 0)
            ),
            positions.add(
            開始位置,
            pos(2, 0, 0)
            ),
            FillOperation.Replace
            )
            開始位置 = positions.add(
            開始位置,
            pos(0, 0, 1)
            )
            blocks.fill(
            GOLD_BLOCK,
            positions.add(
            開始位置,
            pos(0, 0, 2)
            ),
            positions.add(
            開始位置,
            pos(2, 0, 2)
            ),
            FillOperation.Replace
            )
            loops.pause(100)
        }
        for (let index = 0; index < 6; index++) {
            blocks.fill(
            AIR,
            positions.add(
            開始位置,
            pos(0, 0, 2)
            ),
            positions.add(
            開始位置,
            pos(2, 0, 2)
            ),
            FillOperation.Replace
            )
            開始位置 = positions.add(
            開始位置,
            pos(0, 0, -1)
            )
            blocks.fill(
            GOLD_BLOCK,
            positions.add(
            開始位置,
            pos(0, 0, 0)
            ),
            positions.add(
            開始位置,
            pos(2, 0, 0)
            ),
            FillOperation.Replace
            )
            loops.pause(100)
        }
    }
})


```

## ゲームをさらに面白くしよう！@unplugged
工夫してゲームをもっと難(むずか)しくしたり面白くしたりしよう！


## 例(れい)①
ランダムな位置にガストやブレイズが出現(しゅつげん)するようにして、プレイヤーに武器(ぶき)と防具(ぼうぐ)をわたそう！
モンスターをスポーンさせたいときは、**難易度(なんいど)をノーマルにする**のを忘(わす)れないようにしよう



## 例➁
アイテムを使った時にプレイヤーに役に立つ特殊効果(とくしゅこうか)を与えよう！
