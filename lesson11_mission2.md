# 基本(きほん)ルールを作ろう！

```blocks
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
            mobs.clearEffect(mobs.target(LOCAL_PLAYER))
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
})
let 高さ = 0
let スイッチ = false
let 開始位置: Position = null
gameplay.setDifficulty(NORMAL)
開始位置 = world(0, 61, 110)
スイッチ = false



```

```template
loops.forever(function () {})
player.onChat("go", function () {})
player.onChat("lava", function () {})
let 高さ = 0
let スイッチ = false
let 開始位置: Position = null
gameplay.setDifficulty(NORMAL)
開始位置 = world(0, 61, 110)
スイッチ = false

```

## 基本ルールを作ろう！ @unplugged
ゲームのスタートからゴールまでの仕組みを作ろう！
<n></n>
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson11/L11new_complete2.gif">



## 目標
スタートからゴールまでの仕組みを作ろう！
・チャットで**go**と入力した時、プレイヤーがステージの中に入るようにする
・**黄緑色の色付きガラス**をふむと``||variables.スイッチ||``が**オン**になり、ゲームを開始させる
・ゲームが開始すると、プレイヤーに**浮遊**(ふゆう)の特殊効果(とくしゅこうか)をゴールするまで与(あた)える
・スタートからゴールまでのあいだ、1秒(1000ミリ秒)ごとに**溶岩(ようがん)**がステージの下から上へたまっていく
・プレイヤーが天井(てんじょう)のスキマをぬけて上にでると``||variables.スイッチ||``が**オフ**になり、ゲームを終了(しゅうりょう)させる
・プレイヤーが溶岩に当たって死んでしまったとき、``||variables.スイッチ||``が**オフ**になり、ゲームを終了させる
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson11/L11new_complete2.gif">


## 仕組みを考える
このゲームを作るための仕組みを、下の順番(じゅんばん)で考えよう！
①スタートとゴールの仕組み
➁浮遊と溶岩の仕組み
③死んでしまった時の仕組み
④テレポートする仕組み



## ①スタートとゴールの仕組み
スタートとゴールの仕組みを考えよう！
・**黄緑色の色付きガラス**をふむと``||variables.スイッチ||``が**オン**になり、ゲームを開始させる
・プレイヤーが天井のスキマをぬけて上にでると``||variables.スイッチ||``が**オフ**になり、ゲームを終了させる
・スタートした時には**スタート！**、ゴールした時には**ゴール！**と**タイトルを表示(ひょうじ)させる**
・プレイヤーが**いつスタートするか、ゴールするかは分からない**
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson11/L11new_start_and_goal.png">




## スイッチをオンにする
``||variables.スイッチ||``を**オン**(真)にするための条件分岐(じょうけんぶんき)を**自分で考えてプログラミングしよう！**
・いつプレイヤーがスタートするかはわからないので、``||loops.ずっと||``を使ってチェックする
・プレイヤーの1ブロック下に**黄緑色の色付きガラス**があるとき、``||variables.スイッチ||``がオフなら**オン**にして、**スタート！**とタイトルを表示する
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson11/L11new_turn_on.png">

```blocks

loops.forever(function () {
    if (blocks.testForBlock(LIME_STAINED_GLASS, pos(0, -1, 0))) {
        if (スイッチ == false) {
            スイッチ = true
            gameplay.title(mobs.target(LOCAL_PLAYER), "スタート！", "")
        }
    }
})
let スイッチ = false



```



## スイッチをオフにする
``||variables.スイッチ||``を**オフ**(偽(ぎ))にするための条件分岐を**自分で考えてプログラミングしよう！**
・いつプレイヤーがスタートするかはわからないので、``||loops.ずっと||``を使ってチェックする
・プレイヤーが**天井より上にいる**とき、``||variables.スイッチ||``がオンなら**オフ**にして、**ゴール！**とタイトルを表示する
・プレイヤーが天井より上にいるときは、**プレイヤーの位置のy座標(高さ)**が、``||variables.開始位置||``**を基準にしてどうなっているか**考えて条件分岐しよう！
ヒント：「``||variables.開始位置||``より○ブロック上」は、``||math.計算||``の``||math.0 + 0||``を使って、``||variables.開始位置||``の**y座標**に**足し算**する
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson11/L11new_start_and_goal.png">

```blocks

loops.forever(function () {
    if (blocks.testForBlock(LIME_STAINED_GLASS, pos(0, -1, 0))) {
        if (スイッチ == false) {
            スイッチ = true
            gameplay.title(mobs.target(LOCAL_PLAYER), "スタート！", "")
        }
    }
    if (player.position().getValue(Axis.Y) > 開始位置.getValue(Axis.Y) + 24) {
        if (スイッチ == true) {
            スイッチ = false
            gameplay.title(mobs.target(LOCAL_PLAYER), "ゴール！", "")
        }
    }
})
let スイッチ = false
let 開始位置: Position = null
gameplay.setDifficulty(NORMAL)
開始位置 = world(0, 61, 110)

```



## ➁浮遊と溶岩の仕組み
プレイヤーに浮遊の特殊効果を与える仕組みと、溶岩がふえていく仕組みを考えよう！
・``||player.チャットコマンドlavaを入力した時||``の中にプログラミングする
・``||variables.スイッチ||``が**オン**(真)の間、プレイヤーに浮遊の特殊効果を与える
・``||variables.スイッチ||``が**オン**(真)の間、溶岩が**1秒(1000ミリ秒)**ごとにふえていく
・溶岩がステージからあふれないように、**ステージの中が溶岩でいっぱいになったら溶岩をふやすのを止める**
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson11/L11new_complete2.gif">



## 特殊効果を与える
プレイヤーに浮遊の特殊効果を与えるよう、**自分で考えてプログラミングしよう！**
・``||player.チャットコマンドlavaを入力した時||``の中にプログラミングする
・``||variables.スイッチ||``が**オン**(真)の間、プレイヤーに**持続(じぞく)時間3秒**、**効果レベル1**の**浮遊**の特殊効果をくりかえし与える

```blocks
player.onChat("lava", function () {
    while (スイッチ == true) {
        mobs.applyEffect(LEVITATION, mobs.target(NEAREST_PLAYER), 3, 1)
    }
})
let スイッチ = false
```


## 溶岩の手順を考える
変数``||variables.高さ||``を使って、溶岩を並べる座標を変えていく手順を考えよう！
・``||variables.高さ||``に、``||variables.開始位置||``**を基準にして何ブロック上か**の数字を入れる
・**1秒(1000ミリ秒)待つ⇒**溶岩で空気ブロックを置きかえて``||variables.高さ||``**を1ふやす**をくりかえす
・ステージの中が溶岩でいっぱいになったら溶岩をふやすのを止める
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson11/L11new_lava_flow.gif">



## 溶岩を並べる準備(じゅんび)をする
ゲーム開始時に、変数``||variables.高さ||``に数字を入れて、チャットコマンド**lava**を実行するようにしよう！
・``||loops.ずっと||``内の、``||variables.スイッチ||``をオンにするときに、``||variables.高さ||``に**1**を入れる
・``||player.チャットコマンドlavaを引数～で実行する||``を入れる

```blocks
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
            gameplay.title(mobs.target(LOCAL_PLAYER), "ゴール！", "")
        }
    }
})

let 高さ = 0
let スイッチ = false
let 開始位置: Position = null
gameplay.setDifficulty(NORMAL)
開始位置 = world(0, 61, 110)

```


## 溶岩を並べる
変数``||variables.高さ||``を使って、ステージ内の空気ブロックを溶岩に置きかえていくように**自分で考えてプログラミングしよう！**
・``||blocks.次のブロックに置き換(か)える||``を使って、**空気**を**溶岩**に置きかえる
・**1秒(1000ミリ秒)待つ⇒ブロックを置きかえて**``||variables.高さ||``**を1ふやす**をくりかえす
・**範囲(はんい)の始まり**、**範囲の終わり**については、``||variables.開始位置||``を基準にして、ステージ内の``||variables.高さ||``の**y座標**にする
・ステージの中が溶岩でいっぱいになったら溶岩をふやすのを止めるよう、``||variables.高さ||``に入った数字で条件分岐する
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson11/L11new_lava_flow.gif">

```blocks
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
let 高さ = 0
let スイッチ = false
let 開始位置: Position = null
gameplay.setDifficulty(NORMAL)
開始位置 = world(0, 61, 110)
```



## ③死んでしまった時の仕組み
プレイヤーが死んでしまった時の仕組みを**自分で考えてプログラミングしよう！**
・ゴールした時の仕組みとほとんど同じなので、コピーして作る
・タイトルの表示は必要(ひつよう)ないので消す

```blocks

player.onDied(function () {
    if (スイッチ == true) {
        スイッチ = false
    }
})
let スイッチ = false

```


## 溶岩を消す仕組み
プレイヤーがゴールした時や死んでしまった時に、次のゲームのためにステージ内の溶岩を消そう！
・``||blocks.次のブロックに置き換える||``を使って、**溶岩**を**空気**に置きかえる
・**範囲の始まり**、**範囲の終わり**については、``||variables.開始位置||``を基準にして**自分で考える**

```blocks

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
            mobs.clearEffect(mobs.target(LOCAL_PLAYER))
            gameplay.title(mobs.target(LOCAL_PLAYER), "ゴール！", "")
        }
    }
})
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
    }
})

let 高さ = 0
let スイッチ = false
let 開始位置: Position = null

```


## ④テレポートする仕組み
最後(さいご)に、チャットでgoと入力した時、プレイヤーをテレポートさせる仕組みを、**自分で考えてプログラミングしよう！**
・プレイヤーを、``||variables.開始位置||``を基準にして、下の図の位置にテレポートさせる
上から見た図
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson11/L11new_tp_top.png">
横から見た図
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson11/L11new_tp_side.png">

```blocks

player.onChat("go", function () {
    player.teleport(positions.add(
    開始位置,
    pos(2, 1, 3)
    ))
})
let 開始位置: Position = null

```



## 実行しよう！
プログラミングができあがったら、▶ボタンを押して実行しよう
<br></br>
<img height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/1st/execute.gif">
<br></br>
ゲーム画面にもどったら、チャットで**go**と入力し、**黄緑色の色付きガラス**の上に立ってゲームをスタートしよう！
ゴールまでたどりつけるか確認(かくにん)しよう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson11/L11new_complete2.gif">
<br></br>
ゴールまでたどりついたら、**テレポートゾーンに入って下にテレポート**して、**村人に話しかけよう！**
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson11/L11new_tp.gif">
