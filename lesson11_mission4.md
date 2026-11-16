# ゲームをさらに面白くしよう！



```template

player.onDied(function () {
    if (スイッチ == true) {
        スイッチ = false
        blocks.fill(
        AIR,
        positions.add(
        開始位置,
        pos(1, 1, 1)
        ),
        positions.add(
        開始位置,
        pos(3, 23, 9)
        ),
        FillOperation.Replace
        )
        mobs.kill(
        mobs.entitiesByType(mobs.monster(SKELETON))
        )
    }
})
player.onChat("set", function () {
    高さ = 4
    while (高さ < 24) {
        blocks.fill(
        SEA_LANTERN,
        positions.add(
        開始位置,
        pos(1, 高さ, 1)
        ),
        positions.add(
        開始位置,
        pos(3, 高さ, 9)
        ),
        FillOperation.Replace
        )
        穴をあける位置 = randint(1, 9)
        blocks.fill(
        AIR,
        positions.add(
        開始位置,
        pos(1, 高さ, 穴をあける位置)
        ),
        positions.add(
        開始位置,
        pos(3, 高さ, 穴をあける位置)
        ),
        FillOperation.Replace
        )
        高さ += 4
        mobs.spawn(mobs.monster(SKELETON), positions.add(
        開始位置,
        pos(1, 高さ, 1)
        ))
    }
})
loops.forever(function () {
    if (blocks.testForBlock(LIME_STAINED_GLASS, pos(0, -1, 0))) {
        if (スイッチ == false) {
            高さ = 1
            スイッチ = true
            player.runChatCommandWithArguments("lava", "")
            gameplay.title(mobs.target(LOCAL_PLAYER), "スタート！", "")
        }
    }
    if (player.position().getValue(Axis.Y) > 開始位置.getValue(Axis.Y) + 24) {
        if (スイッチ == true) {
            スイッチ = false
            blocks.fill(
            AIR,
            positions.add(
            開始位置,
            pos(1, 1, 1)
            ),
            positions.add(
            開始位置,
            pos(3, 23, 9)
            ),
            FillOperation.Replace
            )
            mobs.kill(
            mobs.entitiesByType(mobs.monster(SKELETON))
            )
            gameplay.title(mobs.target(LOCAL_PLAYER), "ゴール！", "")
        }
    }
})
player.onChat("lava", function () {
    while (スイッチ == true) {
        mobs.applyEffect(LEVITATION, mobs.target(NEAREST_PLAYER), 3, 1)
        if (高さ < 24) {
            loops.pause(1000)
            blocks.replace(
            LAVA,
            AIR,
            positions.add(
            開始位置,
            pos(1, 高さ, 1)
            ),
            positions.add(
            開始位置,
            pos(3, 高さ, 9)
            )
            )
            高さ += 1
        }
    }
})
player.onChat("go", function () {
    player.teleport(positions.add(
    開始位置,
    pos(2, 1, 3)
    ))
    mobs.give(
    mobs.target(LOCAL_PLAYER),
    SHIELD,
    1
    )
})
player.onChat("run", function () {
    blocks.fill(
    GLASS,
    positions.add(
    開始位置,
    pos(0, 0, 0)
    ),
    positions.add(
    開始位置,
    pos(4, 23, 10)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    AIR,
    positions.add(
    開始位置,
    pos(1, 1, 1)
    ),
    positions.add(
    開始位置,
    pos(3, 23, 9)
    ),
    FillOperation.Replace
    )
    blocks.place(LIME_STAINED_GLASS, positions.add(
    開始位置,
    pos(2, 0, 5)
    ))
    blocks.fill(
    SEA_LANTERN,
    positions.add(
    開始位置,
    pos(0, 24, 0)
    ),
    positions.add(
    開始位置,
    pos(4, 24, 10)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    AIR,
    positions.add(
    開始位置,
    pos(1, 24, 5)
    ),
    positions.add(
    開始位置,
    pos(3, 24, 5)
    ),
    FillOperation.Replace
    )
})

let 穴をあける位置 = 0
let 高さ = 0
let スイッチ = false
let 開始位置: Position = null
gameplay.setDifficulty(NORMAL)
開始位置 = world(0, 61, 110)
スイッチ = false

```

## ゲームをさらに面白くしよう！@unplugged
工夫(くふう)してゲームをもっと難(むずか)しくしたり面白くしたりしよう！


## 例(れい)①
ステージをもっと大きくしたり、溶岩が上がってくるスピードを上げたりして、難しくしてみよう！



## 例➁
スケルトン以外(いがい)のモンスターもスポーンさせよう
