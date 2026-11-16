# 落ちる足場を作ろう！

```blocks

loops.forever(function () {
    if (blocks.testForBlock(ORANGE_CONCRETE, pos(0, -1, 0))) {
        if (スイッチ == false) {
            gameplay.title(mobs.target(LOCAL_PLAYER), "スタート！", "")
            スイッチ = true
            player.runChatCommandWithArguments("a", "")
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

```template
loops.forever(function () {
    if (blocks.testForBlock(ORANGE_CONCRETE, pos(0, -1, 0))) {
        if (スイッチ == false) {
            gameplay.title(mobs.target(LOCAL_PLAYER), "スタート！", "")
            スイッチ = true
            player.runChatCommandWithArguments("a", "")
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
let スイッチ = false
スイッチ = false
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
player.onChat("a", function () {
})

```

## 落ちる足場を作ろう！ @unplugged
上に立っていると砂(すな)に変(か)わって落ちる足場を作ろう！
<br></br>
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson9/L9_complete2.gif">



## 目標
上に立っていると砂に変わって落ちる足場を作るようプログラムしよう！
・ゲーム中、エメラルドブロックの上に立つと、エメラルドブロックが**砂に変わって落ちる**
・エメラルドが砂に変わって落ちた後は、**元にもどす**
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson9/L9_jump.gif">



## 砂に変える仕組(しく)み
エメラルドの足場は作られるようになっているので、**プレイヤーが上に立った時に砂に変わる仕組みを考えよう！**
①ゲームがスタートしていることをチェックする仕組み
➁プレイヤーがエメラルドブロックの上にいることをチェックする仕組み
③どの部分を砂にするのかを決める座標
④指定(してい)した範囲(はんい)のエメラルドブロックを砂に変える仕組み
⑤砂に変わってなくなったエメラルドブロックをもう一度並べる仕組み
の5つを、``||player.チャットコマンドaを入力した時||``の中にプログラムしよう！
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson9/L9_jump.gif">



## ①ゲームがスタートしていることをチェックする仕組み
ゲームがスタートしているかどうかは、``||variables.スイッチ||``のオン・オフでわかるようです
ゲームがスタートしている間は、これから作るプログラムをずっとチェックするよう、**自分で考えて条件分岐(じょうけんぶんき)しよう！**

```blocks

player.onChat("a", function () {
    while (スイッチ == true) {}
})
let スイッチ = false
スイッチ = false
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



## ➁プレイヤーがエメラルドブロックの上にいることをチェックする仕組み
プレイヤーがエメラルドブロックの上にいることをチェックする仕組みを**自分で考えてプログラミングしよう！**
・**プレイヤーの1ブロック下**にエメラルドブロックがあるときにプログラムを実行(じっこう)できるように**条件分岐**する

```blocks

player.onChat("a", function () {
    while (スイッチ == true) {
        if (blocks.testForBlock(EMERALD_BLOCK, pos(0, -1, 0))) {}
    }
})
let スイッチ = false
スイッチ = false
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



## ③どの部分を砂にするのかを決める座標
砂ブロックに変える座標の基準にするために、プレイヤーが立った場所の1ブロック下を変数``||variables.エメラルドの座標||``に入るよう、**自分で考えてプログラミングしよう！**

```blocks

player.onChat("a", function () {
    while (スイッチ == true) {
        if (blocks.testForBlock(EMERALD_BLOCK, pos(0, -1, 0))) {
            エメラルドの座標 = pos(0, -1, 0)
        }
    }
})
let エメラルドの座標: Position = null
let スイッチ = false
スイッチ = false
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


## ④指定した範囲のエメラルドブロックを砂に変える仕組み
エメラルドブロックを砂ブロックに変えるには、``||blocks.ブロック||``にある``||blocks.次のブロックに置き換える||``を使いましょう！
このコードは、指定した範囲にある、指定したブロックを好きなものに変えることができます
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson9/L9_replace.png">
範囲の中のこのブロックだけ変えたい！というときに便利です！
これを使って、下の画像のように、``||エメラルドの座標||``を中心に、東西南北に3ブロック分のエメラルドブロックを砂ブロックに変えるよう、**自分で考えてプログラミングしよう！**
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson9/L9_jump.gif">

```blocks

player.onChat("a", function () {
    while (スイッチ == true) {
        if (blocks.testForBlock(EMERALD_BLOCK, pos(0, -1, 0))) {
            エメラルドの座標 = pos(0, -1, 0)
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
        }
    }
})
let エメラルドの座標: Position = null
let スイッチ = false
スイッチ = false
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



## ⑤砂に変わってなくなったエメラルドブロックをもう一度並べる仕組み
砂に変わってなくなったエメラルドブロックを、もう一度並べよう！
``||blocks.次のブロックに置き換える||``を使って、並んでいるエメラルドブロックの中の、空気ブロックになっている部分をエメラルドブロックに変えよう！
エメラルドブロックは、以下の3か所に並んでいるので、これをヒントにしてそれぞれ**自分で考えてプログラミングしよう**
①``||positions.ワールド(-17, 108, 130)||``から``||positions.ワールド(-15, 108, 160)||``
➁``||positions.ワールド(-13, 108, 155)||``から``||positions.ワールド(-11, 108, 170)||``
③``||positions.ワールド(-17, 108, 165)||``から``||positions.ワールド(-15, 108, 175)||``

```blocks

player.onChat("a", function () {
    while (スイッチ == true) {
        if (blocks.testForBlock(EMERALD_BLOCK, pos(0, -1, 0))) {
            エメラルドの座標 = pos(0, -1, 0)
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


## プレイヤーに特殊効果を与える
最後に、プレイヤーがエメラルドブロックの上にいる間、速く走れるようにしよう！
・プレイヤーがエメラルドブロックの上にいる時、プレイヤーに**移動速度上昇**を**3秒間**、**効果レベル1**で与える

```blocks

player.onChat("a", function () {
    while (スイッチ == true) {
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
ゲーム画面にもどったら、**スタート地点の上に立って、「スタート！」と表示されたらゴールへ向かおう！**
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson9/L9_complete2.gif">
<br></br>
足場が砂に変わっても落ちないように、ジャンプしたり走ったりしながらゴールを目指そう！
