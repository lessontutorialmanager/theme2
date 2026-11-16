# 射的(しゃてき)の準備(じゅんび)をしよう！

```blocks
player.onChat("set", function () {
    blocks.fill(
    BLOCK_OF_QUARTZ,
    world(136, 63, 163),
    world(145, 63, 167),
    FillOperation.Replace
    )
})
player.onChat("tp", function () {
    while (スイッチ == true) {
        if (player.position().getValue(Axis.Y) < 64) {
            player.say("足場から出てしまった！")
            player.teleport(world(140, 64, 164))
        }
    }
})
player.onTravelled(WALK, function () {
    if (blocks.testForBlock(BLOCK_OF_QUARTZ, pos(0, -1, 0))) {
        mobs.applyEffect(NIGHT_VISION, mobs.target(LOCAL_PLAYER), 60, 10)
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
    }
})
let スイッチ = false
スイッチ = false


```

```template

player.onChat("run", function () {})
player.onChat("set", function () {})
player.onChat("tp", function () {})

```

## 射的の準備をしよう！ @unplugged
足場を作り、ゲームの準備をしよう！
<n></n>
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson10/L10_complete1.gif">



## 目標(もくひょう)
ゲームを作る準備をしよう！
・チャットコマンドで「run」と入力すると、``||variables.スイッチ||``が**偽(ぎ)**のとき**真**にし、プレイヤーに弓矢をわたす
・チャットコマンドで「set」と入力すると、**クォーツブロック**の足場を並(なら)べる
・プレイヤーが歩いた時、プレイヤーの1ブロック下にクォーツブロックがあるなら、**60秒間**、**効果レベル10**の**暗視(あんし)**の特殊効果(とくしゅこうか)を与(あた)える
・チャットコマンドで「tp」と入力すると、もし``||variables.スイッチ||``が**真**ならくりかえし、プレイヤーが足場をおりたときに足場にもどす
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson10/L10_complete1.gif">



## スイッチを用意する
変数(へんすう)``||variable.スイッチ||``を用意して、プログラムを実行(じっこう)したときに**偽**(オフ)になるように**自分で考えてプログラミングしよう！**

```blocks

let スイッチ = false
スイッチ = false

```

## プレイヤーにアイテムをわたす
チャットコマンドで「run」と入力すると、もし``||variables.スイッチ||``が**偽**のなら**真**にして、プレイヤーに**弓と矢**をわたすように**自分で考えてプログラミングしよう！**
・弓は1つ、矢は64本わたす

```blocks

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
    }
})
let スイッチ = false
スイッチ = false

```



## 足場を並べる
**クォーツブロック**で、足場を並べよう！
・座標(ざひょう)は自分でワールドを見て調べよう！
・``||blocks.ワールド(0, 0, 0)||``を使うのをわすれないようにしよう！

```blocks

player.onChat("set", function () {
    blocks.fill(
    BLOCK_OF_QUARTZ,
    world(136, 63, 163),
    world(145, 63, 167),
    FillOperation.Replace
    )
})


```


## プレイヤーに特殊効果を与える
プレイヤーが歩いた時、プレイヤーの1ブロック下にクォーツブロックがあるなら、**10秒間**、**効果レベル10**の**暗視**の特殊効果を与えるように、**自分で考えてプログラミングしよう！**
・**プレイヤーが歩いた**というイベントを検知(けんち)する
・プレイヤーの**1ブロック下**に**クォーツブロック**があるかどうかで**条件分岐(じょうけんぶんき)**する
・プレイヤーに**60秒間**、**効果レベル10**の**暗視**の特殊効果を与える

```blocks

player.onTravelled(WALK, function () {
    if (blocks.testForBlock(BLOCK_OF_QUARTZ, pos(0, -1, 0))) {
        mobs.applyEffect(NIGHT_VISION, mobs.target(LOCAL_PLAYER), 10, 10)
    }
})

```


## プレイヤーが足場の上にいるかどうかを調べる方法(ほうほう)
プレイヤーが足場の上にいるかどうかは、どうすれば調べることができるでしょうか？
下の図を見て考えてみよう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson10/L10_height.png">




## プレイヤーを足場にもどす
チャットコマンドで「tp」と入力すると、もし``||variables.スイッチ||``が**真**ならくりかえし、プレイヤーが足場をおりたときに足場にもどすよう、**自分で考えてプログラミングしよう！**
・``||player.チャットコマンドtpを入力した時||``の中にプログラミングする
・``||variables.スイッチ||``が**真**の間くりかえすよう**ループ**する
・プレイヤーの**y座標(高低)**の数字で条件分岐して、プレイヤーが足場からおりたかどうか調べる
・**足場から出てしまった！**とメッセージを送信(そうしん)して、``||positions.ワールド(140, 64, 164)||``にプレイヤーをテレポートさせる
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson10/L10_height.png">

```blocks

player.onChat("tp", function () {
    while (スイッチ == true) {
        if (player.position().getValue(Axis.Y) < 64) {
            player.say("足場から出てしまった！")
            player.teleport(world(140, 64, 164))
        }
    }
})
let スイッチ = false
スイッチ = false

```



## 実行しよう！
プログラミングができあがったら、▶ボタンを押(お)して実行しよう
<br></br>
<img height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/1st/execute.gif">
<br></br>
ゲーム画面にもどったらチャットで「set」と入力して足場を作ろう！
できあがったら、**村人に話しかけよう**
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson10/L10_complete1.gif">


