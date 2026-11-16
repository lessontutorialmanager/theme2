# 動く足場を作ろう！

```blocks
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
            let エメラルドの座標 = pos(0, -1, 0)
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
    while (スイッチ == true) {
        if (blocks.testForBlock(EMERALD_BLOCK, pos(0, -1, 0))) {
            let エメラルドの座標 = pos(0, -1, 0)
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
player.onChat("b", function () {})
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


```

## 動く足場を作ろう！ @unplugged
動く足場を作ろう！
<br></br>
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson9/L9_complete3.gif">



## 目標
動く足場を作ろう！
・前に6ブロック、後ろに6ブロック動く足場を作る
・ゲーム中はくりかえし動き続(つづ)けるようにする
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson9/L9_complete3.gif">



## 足場が動く仕組み①
下の図を見て、足場が動く仕組みを考えよう！
・どうやって動いているように見せているか？
・そのためにはどんなプログラムが必要そうか？
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson9/L9_move.gif">



## 足場が動く仕組み➁
分かりやすくするために、**ループをする前の動き**を見て、具体的(ぐたいてき)な仕組みを考えよう
①``||variables.開始位置||``の列のブロックを消す仕組み
➁``||variable.開始位置||``に入った座標を南に1動かす仕組み
③``||variable.開始位置||``を基準にして、ブロックを1列並べる
の3つの仕組みを作れば、足場を動かすことができそうです！
この仕組みを、``||player.チャットコマンドbを入力した時||``の中にプログラムしよう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson9/L9_move2.gif">



## ゲームがスタートしていることをチェックする仕組み
ゲームがスタートしているかどうかは、``||variables.スイッチ||``のオン・オフでわかるようです
仕組みを作る準備(じゅんび)として、ゲームがスタートしている間は、これから作るプログラムをずっとチェックするよう、**自分で考えて条件分岐しよう！**

```blocks
player.onChat("b", function () {
    while (スイッチ == true) {
    }
})

let 開始位置: Position = null
let スイッチ = false
スイッチ = false
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

```


## ①ブロックを消す仕組み
``||variables.開始位置||``に入っている座標を基準にして、下の画像を参考(さんこう)に、**東に3ブロック分**を消す仕組みを自分で考えてプログラミングしよう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson9/L9_move2.gif">

```blocks
player.onChat("b", function () {
    while (スイッチ == true) {
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
    }
})

let 開始位置: Position = null
let スイッチ = false
スイッチ = false
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

```



## ➁座標を南に1動かす仕組み
``||variables.開始位置||``に入っている座標を**南に1**動かそう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson9/L9_move2.gif">

```blocks
player.onChat("b", function () {
    while (スイッチ == true) {
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
    }
})

let 開始位置: Position = null
let スイッチ = false
スイッチ = false
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

```



## ③ブロックを1列並べる仕組み
``||variables.開始位置||``を基準にして、**南に3ブロック**の位置に、**金のブロックを東にむけて3ブロック分**1列並べるよう、**自分で考えてプログラミングしよう！**
そのあと、``||loops.一時停止(ていし)||``を使って、**100ミリ秒**止まるようにしよう
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson9/L9_move2.gif">

```blocks
player.onChat("b", function () {
    while (スイッチ == true) {
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
})

let 開始位置: Position = null
let スイッチ = false
スイッチ = false
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

```


## ループする
ブロックを消す⇒``||variables.開始位置||``の座標を動かす⇒ブロックを並べて100ミリ秒止まる、のプログラムを**6回くりかえす**ように**自分で考えてプログラミングしよう！**

```blocks
player.onChat("b", function () {
    while (スイッチ == true) {
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
    }
})

let 開始位置: Position = null
let スイッチ = false
スイッチ = false
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

```


## コピーして帰りを作る
これで、**足場が6ブロック南に動く**プログラムができました！
足場がもどってくるように、**足場が6ブロック北に動く**プログラムも必要です
作ったプログラムをコピーして、必要な部分を**自分で考えて修正**し、足場がもどってくるようにしよう！

```blocks
player.onChat("b", function () {
    while (スイッチ == true) {
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
                pos(0, 0, -1)
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
    }
})

let 開始位置: Position = null
let スイッチ = false
スイッチ = false
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

```



## 実行しよう！
プログラミングができあがったら、▶ボタンを押して実行しよう
<br></br>
<img height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/1st/execute.gif">
<br></br>
ゲーム画面にもどったら、スタート地点の上に立って、タイトルが表示(ひょうじ)されるのを確認しよう！
確認出来たら、もう一度ゴールを目指そう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson9/L9_complete3.gif">
