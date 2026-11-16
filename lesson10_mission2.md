# 射的の基本的(きほんてき)な流れを作ろう！

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
let 矢の数 = 0
let スイッチ = false
スイッチ = false

```

```template
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
        mobs.applyEffect(NIGHT_VISION, mobs.target(LOCAL_PLAYER), 10, 10)
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

## 射的の基本的な流れを作ろう！ @unplugged
ゾンビをスポーンさせて、倒(たお)したらゲームが終了するようにしよう！
<n></n>
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson10/L10_complete2.gif">



## 目標
ゲームの基本的なルールをプログラミングしよう！
①矢の本数が0本になった時に、矢を手に入れた！とメッセージを送信して、プレイヤーに矢を64本わたすようにする
➁ゾンビをランダムな位置(いち)にスポーンさせる
③プレイヤーが死んだ時、ゾンビを倒した時にゲームが終了するようにする
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson10/L10_complete2.gif">



## のこりの矢を数える方法
のこりの矢を数えるには、``||player.プレイヤー||``にある``||player.プレイヤーが矢を放った時||``が便利(べんり)です！
これを使うと、**プレイヤーが矢を放った**というイベントを検知することができます
``||variables.矢の数||``という変数を作ってはじめの矢の数を入れておき、プレイヤーが矢を放った時に1へらせば、今プレイヤーが何本矢を持っているか数えることができます
これを使って、``||variables.矢の数||``プレイヤーの持っている矢が0本になったら、プレイヤーに矢を64本わたして、``||variables.矢の数||``を64本にするようにプログラムしよう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson10/L10_arrow_shot.png">



## ①矢の本数が0のときにプレイヤーに矢をわたす
下の図をもとにして、**自分で考えてプログラミングしよう！**
・プレイヤーが矢を放ったイベントを検知する
・``||variables.矢の数||``を**1へらす**
・もし``||variables.矢の数||``が0になったら、プレイヤーに矢を64本わたし、``||variables.矢の数||``を**64**にして、**矢を手に入れた！**とメッセージ送信する
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson10/L10_arrow_shot.png">

```blocks

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


```



## ➁ゾンビをランダムな位置にスポーンさせる
ゾンビがランダムな位置にスポーンするよう、**自分で考えてプログラミングしよう！**
・``||player.チャットコマンドzを入力した時||``の中にプログラムする
・ゾンビを1体、``||positions.ワールド(136, 63, 173)||``**から**``||positions.ワールド(145, 63, 183)||``**の中のランダムな位置**にスポーンさせる

```blocks

player.onChat("z", function () {
    mobs.spawn(mobs.monster(ZOMBIE), randpos(
    world(136, 63, 173),
    world(145, 63, 183)
    ))
})

```



## ③プレイヤーが死んだ時、ゾンビを倒した時に終了する
プレイヤーが死んだ時と、ゾンビを倒した時にゲームが終了するように**自分で考えてプログラミングしよう！**
・プレイヤーが死んだ時、``||variables.スイッチ||``が**オン**なら**オフ**にして、**終了！**とタイトルを表示(ひょうじ)する
・ゾンビを倒した時、``||variables.スイッチ||``が**オン**なら**オフ**にして、**終了！**とタイトルを表示する

```blocks
player.onDied(function () {
    if (スイッチ == true) {
        スイッチ = false
        gameplay.title(mobs.target(LOCAL_PLAYER), "終了！", "")
    }
})
mobs.onMobKilled(mobs.monster(ZOMBIE), function () {
    if (スイッチ == true) {
        スイッチ = false
        gameplay.title(mobs.target(LOCAL_PLAYER), "終了！", "")
    }
})
let スイッチ = false
スイッチ = false

```


## プレイヤーが死んだ時について考える
プレイヤーが死んだ時と、ゾンビを倒した時のちがいを考えてみましょう
・プレイヤーが死んで終了した時は、**スポーンしたゾンビがのこっている**
・ゾンビを倒して終了した時は、**ゾンビはいない**
プレイヤーが死んだ時にゾンビがそのまま残(のこ)っていると、次のゲームを始めるときにジャマなので、**プレイヤーが死んだ時は、まわりにいるゾンビをすべて自動で倒すようにしよう！**



## まわりのゾンビをすべて倒す
``||mobs.モブ||``にある``||mobs.～を死亡させる||``を使うと、指定(してい)したプレイヤーや生き物をすべて倒すことができます！
・``||mobs.モブ||``から``||mobs.～を死亡させる||``を取り出して、``||player.プレイヤーが死んだ時||``の条件分岐の中に入れる
・``||mobs.モブ||``から``||mobs.すべての生き物||``を取り出して、``||mobs.～を死亡させる||``に入れる
・``||mobs.モブ||``から``||mobs.モンスター||``を取り出して、``||mobs.すべての生き物を死亡させる||``に入れる
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson10/L10_kill_zombie.gif">

```blocks
player.onDied(function () {
    if (スイッチ == true) {
        スイッチ = false
        gameplay.title(mobs.target(LOCAL_PLAYER), "終了！", "")
        mobs.kill(
        mobs.entitiesByType(mobs.monster(ZOMBIE))
        )
    }
})
let スイッチ = false
スイッチ = false

```



## ゲームをスタートする仕組(しく)みを考える
チャットで**run**と入力した時に、ゲームをスタートする準備をして、これまでに作った仕組みを実行するようにしよう！
・プレイヤーに矢をわたしたあと、``||variables.矢の本数||``を**64本**にする
・**スタート！**とタイトルを表示する
・チャットコマンド**tp**と**z**を実行する

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
        矢の数 = 64
        gameplay.title(mobs.target(LOCAL_PLAYER), "スタート！", "")
        player.runChatCommandWithArguments("tp", "")
        player.runChatCommandWithArguments("z", "")
    }
})
let 矢の数 = 0
let スイッチ = false
スイッチ = false

```



## ゲームの難易度(なんいど)を変える
Minecraftの中でゾンビがスポーンするには、**ゲームの難易度がノーマルかハードである**必要(ひつよう)があります
作ったゲームをやっている間だけゲームの難易度を**ノーマル**にして、終了している時は**ピースフル**にもどすように、**自分で考えてプログラミングしよう！**
・``||gameplay.ゲームプレイ||``にある``||gameplay.ゲームの難易度を～に変更(へんこう)する||``を使おう
・難易度をノーマルに変(か)えた**あと**にチャットコマンドzを実行しないと、ゾンビがスポーンしないことに注意(ちゅうい)しよう

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
        矢の数 = 64
        gameplay.setDifficulty(NORMAL)
        gameplay.title(mobs.target(LOCAL_PLAYER), "スタート！", "")
        player.runChatCommandWithArguments("tp", "")
        player.runChatCommandWithArguments("z", "")
    }
})
let 矢の数 = 0
let スイッチ = false
スイッチ = false
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

```



## 実行しよう！
プログラミングができあがったら、▶ボタンを押して実行しよう
<br></br>
<img height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/1st/execute.gif">
<br></br>
ゲーム画面にもどったら、足場の上に立ってチャットで「run」と入力してゲームをスタートしよう！
ゲームが始まったら、弓矢でゾンビをたおそう
ゲームが終了したら、**村人に話しかけよう**
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson10/L10_complete2.gif">




