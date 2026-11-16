# ゲームをさらに面白くしよう！



```template

player.onChat("run", function () {
    blocks.fill(
    BLUE_CONCRETE,
    pos(1, 0, 1),
    pos(5, 0, 5),
    FillOperation.Replace
    )
    blocks.fill(
    WHITE_CONCRETE,
    pos(2, 0, 2),
    pos(4, 0, 4),
    FillOperation.Replace
    )
    blocks.place(YELLOW_CONCRETE, pos(3, 0, 3))
})
player.onChat("set", function () {
    開始位置 = randpos(
    pos(-5, -1, 2),
    pos(3, -1, 4)
    )
    えらんだ数 = randint(0, 2)
    if (えらんだ数 == 0) {
        ブロックの種類 = AIR
    } else if (えらんだ数 == 1) {
        ブロックの種類 = WHITE_GLAZED_TERRACOTTA
    } else {
        ブロックの種類 = HONEY_BLOCK
    }
    blocks.fill(
    DIAMOND_BLOCK,
    positions.add(
    開始位置,
    pos(1, 0, 1)
    ),
    positions.add(
    開始位置,
    pos(3, 0, 3)
    ),
    FillOperation.Replace
    )
    blocks.place(ブロックの種類, positions.add(
    開始位置,
    pos(2, 0, 2)
    ))
})
player.onChat("timer", function () {
    while (スイッチ == true) {
        loops.pause(1000)
        タイム += 1
    }
})
loops.forever(function () {
    if (blocks.testForBlock(ORANGE_CONCRETE, pos(0, -1, 0))) {
        if (スイッチ == false) {
            gameplay.title(mobs.target(LOCAL_PLAYER), "スタート！", "")
            スイッチ = true
            タイム = 0
            player.runChatCommandWithArguments("timer", "")
        }
    }
    if (blocks.testForBlock(YELLOW_CONCRETE, pos(0, -1, 0))) {
        if (スイッチ == true) {
            gameplay.title(mobs.target(LOCAL_PLAYER), "ゴール！", "タイム " + タイム + "秒")
            スイッチ = false
        }
    }
    if (player.position().getValue(Axis.Y) < 100) {
        player.say("落ちてしまった！")
        player.teleport(world(-17, 109, 105))
    }
    if (blocks.testForBlock(WHITE_GLAZED_TERRACOTTA, pos(0, -1, 0))) {
        えらんだ数 = randint(0, 2)
        if (えらんだ数 == 0) {
            mobs.applyEffect(SPEED, mobs.target(LOCAL_PLAYER), 5, 5)
        } else if (えらんだ数 == 1) {
            mobs.applyEffect(JUMP_BOOST, mobs.target(LOCAL_PLAYER), 5, 5)
        } else {
            mobs.applyEffect(LEVITATION, mobs.target(LOCAL_PLAYER), 2, 2)
        }
    }
})
let タイム = 0
let えらんだ数 = 0
let スイッチ = false
スイッチ = false
let 開始位置: Position = null
let ブロックの種類 = 0

```

## ゲームをさらに面白くしよう！@unplugged
工夫(くふう)してゲームをもっと難(むずか)しくしたり面白くしたりしよう！


## 例①
足場の真ん中に置くブロックの種類を増(ふ)やしてみよう！



## 例➁
白の彩釉テラコッタの上に立った時の特殊効果の種類を増(ふ)やしてみよう！



## 例③
倒(たお)したときに出てくるモンスターの数を増(ふ)やそう！
``||mobs.モンスターが死んだ時||``のくり返しの数を変(か)えて、もっとたくさんのモンスターがスポーンするようにしよう！
