# ゲームのルールを追加(ついか)しよう！

```blocks
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
        スイッチ = false
        gameplay.title(mobs.target(LOCAL_PLAYER), "終了！", "")
        gameplay.setDifficulty(PEACEFUL)
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
        矢の数 = 64
        gameplay.setDifficulty(NORMAL)
        gameplay.title(mobs.target(LOCAL_PLAYER), "スタート！", "")
        player.runChatCommandWithArguments("tp", "")
        player.runChatCommandWithArguments("z", "")
    }
})
player.onTravelled(WALK, function () {
    if (blocks.testForBlock(BLOCK_OF_QUARTZ, pos(0, -1, 0))) {
        mobs.applyEffect(NIGHT_VISION, mobs.target(LOCAL_PLAYER), 60, 10)
    }
})
player.onChat("timer", function () {})
let 矢の数 = 0
let スイッチ = false
スイッチ = false

```

## ゲームルールを追加しよう！ @unplugged
制限(せいげん)時間内に何体ゾンビを倒せるかちょうせんするゲームにしよう！
<n></n>
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson10/L10_complete3.gif">



## 目標
ゲームのルールをさらに追加しよう！
・**30秒間**で何体ゾンビを倒せるかちょうせんするゲームにする
・30秒たってゲーム終了したときに、**何体倒したかわかるようにする**
・ゾンビを1体倒すと、**1～3体のゾンビががスポーンするようにする**
・ゲーム開始時にプレイヤーに**棒(ぼう)**をわたし、**棒を使うとすべてのゾンビをテレポートさせる**
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson10/L10_complete3.gif">



## ちがいを考える①
先ほどのゲームとくらべて、ルールのどの部分が変わったか考えよう！
<br></br>
先ほどのゲーム
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson10/L10_complete2.gif">
<br></br>
今回のゲーム
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson10/L10_complete3.gif">



## ちがいを考える➁
変わった部分をまとめよう！
・先ほどのゲームは、ゾンビを1体倒したら終わりだったが、今回はゾンビが1～3体追加で出る⇒①**ゾンビを倒した時のプログラムを変える必要がある**
・先ほどのゲームは、ゾンビは1体だったので倒した数は数えなかったが、今回は何体倒したかチェックする⇒**➁倒した数を数える**
・先ほどのゲームは、制限時間がなかったが、今回は30秒という制限時間がある⇒**③タイマーの仕組みを考える**



## ①ゾンビを倒した時のプログラムを変える
ゾンビを倒した時のプログラムを、**自分で考えて修正(しゅうせい)しよう！**
・ゾンビを倒した時、1～3体ゾンビをスポーンさせる
・くりかえす回数は、**1～3のランダムな数字**にする
・ゾンビを1体スポーンさせる仕組みは、``||player.チャットコマンドzを入力した時||``に作っているので、これを使う

```blocks

mobs.onMobKilled(mobs.monster(ZOMBIE), function () {
    if (スイッチ == true) {
        for (let index = 0; index < randint(1, 3); index++) {
            player.runChatCommandWithArguments("z", "")
        }
    }
})
let スイッチ = false
スイッチ = false

```



## ➁倒した数を数える
ゾンビを倒した数をかぞえる仕組みを考えよう！
・``||variables.倒した数||``という変数を作って、これを使ってかぞえる
・``||variables.倒した数||``は、ゲームがスタートした時は0体のはず⇒いつ0にすれば良いか、**自分で考えてプログラミングしよう！**
・いつ数えればよいか、**自分で考えてプログラミングしよう！**

```blocks

mobs.onMobKilled(mobs.monster(ZOMBIE), function () {
    if (スイッチ == true) {
        倒した数 += 1
        for (let index = 0; index < randint(1, 3); index++) {
            player.runChatCommandWithArguments("z", "")
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
        矢の数 = 64
        倒した数 = 0
        gameplay.setDifficulty(NORMAL)
        gameplay.title(mobs.target(LOCAL_PLAYER), "スタート！", "")
        player.runChatCommandWithArguments("tp", "")
        player.runChatCommandWithArguments("z", "")
    }
})
let タイム = 0
let 矢の数 = 0
let 倒した数 = 0
let スイッチ = false
スイッチ = false

```



## タイマーの仕組みを考える
タイマーの仕組みを考えよう！
・ゲームがスタートしたとき、残(のこ)り時間は30秒で、1秒ずつへっていく⇒``||variables.タイム||``という変数を用意(ようい)する
・時間を数える仕組みは、❶1秒間(1000ミリ秒)一時停止⇒❷``||variables.タイム||``を1へらす、という動きを``||variables.スイッチ||``が**オン**の間くりかえす
・残り時間が10になったら**のこり10秒！**とメッセージ送信する
・残り時間が0になったらゲーム終了=``||variables.スイッチ||``を**オフ**にする
この仕組みを、``||player.チャットコマンドtimerを入力した時||``の中に作ろう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson10/L10_timer.png">



## ③タイマーの仕組みを作る
先ほど考えたことをもとに、タイマーの仕組みを**自分で考えてプログラミングしよう！**
また、ゲームがスタートした時に、``||variables.タイム||``の数字が30になり、チャットコマンドtimerが実行されるようプログラミングしよう
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson10/L10_timer.png">

```blocks

player.onChat("timer", function () {
    while (スイッチ == true) {
        loops.pause(1000)
        タイム += -1
        if (タイム == 10) {
            player.say("のこり10秒！")
        }
        if (タイム == 0) {
            スイッチ = false
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
let タイム = 0
let 矢の数 = 0
let 倒した数 = 0
let スイッチ = false
スイッチ = false


```


## ゲームを終了した時の仕組みを考える
``||variables.スイッチ||``をオフにしたあとの仕組みを**自分で考えてプログラミングしよう！**
・**終了！**とタイトルを表示する
・サブタイトルで、「倒した数○」と、``||variables.倒した数||``に入った数字を表示する
・次のゲームのために、ゾンビをすべて倒しておく
・ゲームの難易度をピースフルにもどす
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson10/L10_timer.png">

```blocks

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
let タイム = 0
let 矢の数 = 0
let 倒した数 = 0
let スイッチ = false
スイッチ = false


```


## 棒を使った時
棒を使った時に**すべてのゾンビをテレポートさせる**よう、**自分で考えてプログラミングしよう！**
・ゲーム開始時にプレイヤーに**棒**を1つわたす
・棒を使った時、**すべてのゾンビ**を、**ワールド(136, 63, 175)**から**ワールド(145, 63, 183)**のランダムな位置にテレポートさせる

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
player.onItemInteracted(STICK, function () {
    mobs.teleportToPosition(
    mobs.entitiesByType(mobs.monster(ZOMBIE)),
    randpos(
    world(136, 63, 175),
    world(145, 63, 183)
    )
    )
})
let タイム = 0
let 矢の数 = 0
let 倒した数 = 0
let スイッチ = false
スイッチ = false

```


## 実行しよう！
プログラミングができあがったら、▶ボタンを押して実行しよう
<br></br>
<img height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/1st/execute.gif">
<br></br>
ゲーム画面にもどったら、足場の上に立ってチャットで「run」と入力してゲームをスタートしよう！
ゲームが始まったら、弓矢でゾンビをたおそう
ゾンビが近づいてきたら、棒を使ってテレポートさせよう
ゲームが終了したら、**村人に話しかけよう**
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson10/L10_complete3.gif">
