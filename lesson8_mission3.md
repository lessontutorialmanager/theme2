# ゲームの仕組みを作ろう！

```blocks
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

```

```template
loops.forever(function () {
    if (blocks.testForBlock(ORANGE_CONCRETE, pos(0, -1, 0))) {
        gameplay.title(mobs.target(LOCAL_PLAYER), "スタート！", "")
    }
    if (blocks.testForBlock(YELLOW_CONCRETE, pos(0, -1, 0))) {
        gameplay.title(mobs.target(LOCAL_PLAYER), "ゴール！", "")
    }
    if (player.position().getValue(Axis.Y) < 100) {
        player.say("落ちてしまった！")
        player.teleport(world(-17, 109, 105))
    }
})
player.onChat("timer", function () {
})

```

## ゲームの仕組みを作ろう！@unplugged
ゲームを面白くするための仕組みを作ろう！
<br></br>
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson8/L8_complete3.gif">



## 目標
ゲームを面白くするために、仕組みを作ろう！
①プレイヤーが**白の彩釉テラコッタ**の上に立った時に、ランダムな特殊効果(とくしゅこうか)を与(あた)える
➁プレイヤーがゴールした時に、タイムを表示する
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson8/L8_complete3.gif">



## ①プレイヤーにランダムな特殊効果を与える手順
プレイヤーが**白の彩釉テラコッタ**の上に立った時に、ランダムな特殊効果を与える手順をかんがえよう！
・``||blocks.ブロックが(~0, ~0, ~0)に存在する||``を使って、**プレイヤーの1ブロック下に白の彩釉テラコッタがあるかどうか**で条件分岐する
・``||variable.えらんだ数||``に**0から2までのランダムな数**を入れる
・``||variable.えらんだ数||``に入った数で条件分岐して、プレイヤーに特殊効果を与える
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson8/L8_effect.gif">



## プログラムをはじめるきっかけを作る
まずは、プレイヤーの1ブロック下に白の彩釉テラコッタがあるかどうかを調べる条件分岐を作ろう！
プレイヤーがいつ白の彩釉テラコッタの上に乗るかは分かりません
こんなときはどうすれば良いか、**自分で考えてプログラミングしよう！**
・プレイヤーの**1ブロック下**に**白の彩釉テラコッタ**があるかどうかを調べる**条件分岐**を作る
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson8/L8_effect.gif">




## ランダムな特殊効果を与える条件分岐を作る
プレイヤーが白の彩釉テラコッタの上にいる時、ランダムな特殊効果を与えるようにしよう！
・変数``||variable.えらんだ数||``を作って、**0から2までのランダムな数**を入れる
・``||variable.えらんだ数||``に入った数で条件分岐して、プレイヤーに特殊効果を与える
・下の図を参考(さんこう)にして、特殊効果は好きなものをえらぶ
どうすれば良いか、**自分で考えてプログラミングしよう！**
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson8/L8_apply_effect.png">

```blocks

loops.forever(function () {
    if (blocks.testForBlock(ORANGE_CONCRETE, pos(0, -1, 0))) {
        gameplay.title(mobs.target(LOCAL_PLAYER), "スタート！", "")
    }
    if (blocks.testForBlock(YELLOW_CONCRETE, pos(0, -1, 0))) {
        gameplay.title(mobs.target(LOCAL_PLAYER), "ゴール！", "")
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
let えらんだ数 = 0
```


## ➁プレイヤーがゴールした時に、タイムを表示する手順
プレイヤーがクリアするまでにかかったタイムは、どうすれば分かるか考えよう！
下の図のように、**プレイヤーがスタート地点の上に立った時**に**スイッチをオン**にしてタイムを計り始めて、**ゴール地点の上に立った時**に**スイッチをオフ**にして止めるようにすれば、ゴールまでにかかった時間を調べることができます
2つの変数を使って、この仕組みを作りましょう！
・``||variable.スイッチ||``：時間を計るオン・オフを決める
・``||variable.タイム||``：``||variable.スイッチ||``がオンの間、1秒に1ずつ数字を増(ふ)やす
準備(じゅんび)として、**2つの変数**``||variable.タイム||``、``||variable.スイッチ||``**を作成(さくせい)**しよう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson8/L8_timer_flow.png">



## スイッチのオン・オフについて
``||variable.スイッチ||``の中にオン・オフを入れるには、``||logic.論理||``にある``||logic.真||``と``||logic.偽(ぎ)||``を使います
・``||variable.スイッチ||`` = ``||logic.真||``：スイッチが**オン**という意味
・``||variable.スイッチ||`` = ``||logic.偽||``：スイッチが**オフ**という意味
これを使うと、例(たと)えば、**スイッチがオンの間くりかえす**といったことができるようになります！



## スイッチを準備する
はじめ、スイッチは**オフ**になっている必要(ひつよう)があるので、プログラムを実行したときにスイッチをオフにするようにプログラミングしよう
・``||loops.ループ||``から``||loops.最初(さいしょ)だけ||``を取り出す
・``||variable.変数||``から``||variable.変数 スイッチを0にする||``を取り出して、``||loops.最初だけ||``に入れる
・``||logic.論理||``から``||logic.偽||``を取り出して、``||variable.変数 スイッチを0にする||``に入れる
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson8/L8_set_switch.gif">

```blocks

let スイッチ = false

```



## スイッチをオンにする
プレイヤーがスタート地点の上に立った時に、もしスイッチが**オフ**ならスイッチをオンにするようにプログラミングしよう！
・``||logic.論理||``から``||logic.もし～なら||``を取り出して、``||gameplay.自分にタイトル スタート！を表示する||``をはさむように入れる
・**もし**``||variables.スイッチ||``** = **``||logic.偽||``**なら**となるように条件分岐する
・条件分岐の中に、``||variable.変数 スイッチを真にする||``となるように入れる
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson8/L8_switch_on.gif">

```blocks

loops.forever(function () {
    if (blocks.testForBlock(ORANGE_CONCRETE, pos(0, -1, 0))) {
        if (スイッチ == false) {
            gameplay.title(mobs.target(LOCAL_PLAYER), "スタート！", "")
            スイッチ = true
        }
    }
    if (blocks.testForBlock(YELLOW_CONCRETE, pos(0, -1, 0))) {
        gameplay.title(mobs.target(LOCAL_PLAYER), "ゴール！", "")
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
let えらんだ数 = 0
let スイッチ = false
```


## スイッチをオフにする
同じようにして、プレイヤーがゴール地点の上に立った時に、もしスイッチが**オン**ならスイッチをオフにするように**自分で考えてプログラミングしよう！**

```blocks

loops.forever(function () {
    if (blocks.testForBlock(ORANGE_CONCRETE, pos(0, -1, 0))) {
        if (スイッチ == false) {
            gameplay.title(mobs.target(LOCAL_PLAYER), "スタート！", "")
            スイッチ = true
        }
    }
    if (blocks.testForBlock(YELLOW_CONCRETE, pos(0, -1, 0))) {
        if (スイッチ == true) {
            gameplay.title(mobs.target(LOCAL_PLAYER), "ゴール！", "")
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
let えらんだ数 = 0
let スイッチ = false
```


## 時間を入れる仕組みを作る
``||player.チャットコマンドtimerを入力した時||``を使って、スイッチが**オン**なら``||variables.タイム||``を**1秒間に1ずつ増やす**ようにプログラミングしよう！
・``||loops.もし～ならくりかえし||``を使って、``||variables.スイッチ||`` = ``||logic.真||``の間くりかえすようにする
・1秒(1000ミリ秒)待つ⇒``||variables.タイム||``を1ふやすをくりかえす
この内容(ないよう)を、**自分で考えてプログラミングしよう！**

```blocks

player.onChat("timer", function () {
    while (スイッチ == true) {
        loops.pause(1000)
        タイム += 1
    }
})
let タイム = 0

```


## チャットコマンドを実行する
スイッチを**オン**にするときに、``||variables.タイム||``の数字をリセットして、作ったチャットコマンドを実行するようにしよう！
・``||variables.変数 タイムを0にする||``を、``||variables.スイッチを真にする||``の**下**に入れる
・``||player.プレイヤー||``から``||player.チャットコマンド～を引数～で実行||``を取り出してその下に入れ、チャットコマンド**timer**を実行できるようにする

```blocks

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
            gameplay.title(mobs.target(LOCAL_PLAYER), "")
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

```


## サブタイトルで結果を表示する
ゴール！と表示した時のサブタイトルで、「タイム：○○秒」と表示できるようにプログラミングしよう
・``||text.文字列||``から``||text.文字列をつなげる||``を取り出して、``||gameplay.自分にタイトル ゴール！ サブタイトル～を表示する||``の**サブタイトル**に入れる
・``||text.文字列をつなげる||``の⊕をおして、左から「タイム：」、``||variable.time||``、「秒」と入力する
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson8/L8_subtitle.png">

```blocks

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

```



## 実行しよう！
プログラミングができあがったら、▶ボタンを押して実行しよう
<br></br>
<img height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/1st/execute.gif">
<br></br>
ゲーム画面にもどったら、スタート地点の上に立って、タイトルが表示されるのを確認しよう！
確認できたら、もう一度ゴールを目指そう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson8/L8_complete3.gif">
