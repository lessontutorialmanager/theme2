# ゲームを面白(おもしろ)くしよう！

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
        mobs.kill(
        mobs.entitiesByType(mobs.monster(SKELETON))
        )
    }
})
player.onChat("set", function () {
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
let 穴をあける位置 = 0
let 高さ = 0
let スイッチ = false
let 開始位置: Position = null
gameplay.setDifficulty(NORMAL)
開始位置 = world(0, 61, 110)
スイッチ = false

```

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
            player.teleport(world(-15, 62, 102))
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
let 穴をあける位置 = 0
let 高さ = 0
let スイッチ = false
let 開始位置: Position = null
gameplay.setDifficulty(NORMAL)
開始位置 = world(0, 61, 110)
スイッチ = false


```

## ゲームのルールを作ろう！ @unplugged
ゲームを面白くするためのルールを作ろう！
<n></n>
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson11/L11new_complete3_play.gif">



## 目標
ゲームが面白くなるように仕組みを追加(ついか)しよう！
①ゴールまでの障害物(しょうがいぶつ)になる、**シーランタン**を並べ、**スケルトン**をスポーンさせる
➁テレポートするときに、スケルトンからのこうげきを防(ふせ)ぐための**盾**(たて)をプレイヤーにわたす
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson11/L11new_complete3.gif">



## ①障害物を並べる仕組み
``||player.チャットコマンドsetを入力した時||``を使って、障害物を並(なら)べて、スケルトンをスポーンさせる仕組みを作ろう！
まずは、どうすれば良(よ)いか仕組みを考えよう
・``||variables.高さ||``を使って、障害物を並べる高さを変(か)える
・障害物を並べたあと、``||variables.穴(あな)をあける位置||``を使って、**ランダムなz座標(南北)の位置に通り穴をあける**
・障害物の上に**スケルトン**をスポーンさせる
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson11/L11new_random_ceiling.png">



## 障害物を並べる
シーランタンを並べるプログラムを作ろう！
どうすれば良いか、**自分で考えてプログラミングしよう！**
・はじめに、``||positions.開始位置 + (1, 1, 1)||``から``||positions.開始位置 + (3, 23, 9)||``に**空気ブロック**を並べて、前回のゲームの障害物やマグマがのこらないようにする
・``||variables.開始位置||``を基準にして、``||variables.高さ||``に入った**y座標**の位置にシーランタンを並べる
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson11/L11new_set_ceiling.png">

```blocks

player.onChat("set", function () {
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
})
let 穴をあける位置 = 0
let 高さ = 0
let スイッチ = false
let 開始位置: Position = null
gameplay.setDifficulty(NORMAL)
開始位置 = world(0, 61, 110)
スイッチ = false

```


## 穴をあける
ランダムな位置に穴をあけよう！
どうすれば良いか、**自分で考えてプログラミングしよう！**
・``||variables.穴をあける位置||``に、穴をあけるz座標を決める**ランダムな数字を入れる**
・``||variables.穴をあける位置||``のz座標の位置に**空気**を並べて穴をあける
ランダムな数字を何から何までの間からえらぶかは、自分で考えてみよう
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson11/L11new_set_air.png">

```blocks

player.onChat("set", function () {
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
})
let 穴をあける位置 = 0
let 高さ = 0
let スイッチ = false
let 開始位置: Position = null
gameplay.setDifficulty(NORMAL)
開始位置 = world(0, 61, 110)
スイッチ = false

```



## 変数の数字を決める
障害物を並べ始める前に、``||variables.高さ||``にどんな数字を入れておくか、障害物を並べた後に``||variables.高さ||``の数字をどのように変えるか、図を見て**自分で考えてプログラミングしよう！**
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson11/L11new_random_ceiling.png">

```blocks

player.onChat("set", function () {
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
    高さ = 4
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
})
let 穴をあける位置 = 0
let 高さ = 0
let スイッチ = false
let 開始位置: Position = null
gameplay.setDifficulty(NORMAL)
開始位置 = world(0, 61, 110)
スイッチ = false

```



## スケルトンをスポーンさせる
障害物の上にスケルトンをスポーンさせるよう、**自分で考えてプログラミングしよう！**

```blocks

player.onChat("set", function () {
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
    高さ = 4
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
})
let 穴をあける位置 = 0
let 高さ = 0
let スイッチ = false
let 開始位置: Position = null
gameplay.setDifficulty(NORMAL)
開始位置 = world(0, 61, 110)
スイッチ = false

```


## ループさせる
``||variables.高さ||``の数字を決めた**あと**からスケルトンをスポーンさせるまでを、``||variables.高さ||``が**24より小さい**ときにループするよう**自分で考えてプログラミングしよう！**

```blocks

player.onChat("set", function () {
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
let 穴をあける位置 = 0
let 高さ = 0
let スイッチ = false
let 開始位置: Position = null
gameplay.setDifficulty(NORMAL)
開始位置 = world(0, 61, 110)
スイッチ = false

```



## ゲーム終了時
プレイヤーがゴールした時や死んだ時に、次のゲームのためにスポーンさせたスケルトンを**すべて**倒(たお)しておくように**自分で考えてプログラミングしよう！**

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
            mobs.kill(
            mobs.entitiesByType(mobs.monster(SKELETON))
            )
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
        mobs.kill(
        mobs.entitiesByType(mobs.monster(SKELETON))
        )
    }
})
let 穴をあける位置 = 0
let 高さ = 0
let スイッチ = false
let 開始位置: Position = null
gameplay.setDifficulty(NORMAL)
開始位置 = world(0, 61, 110)
スイッチ = false

```



## 盾をわたす
最後に、プレイヤーがステージの中にテレポートしたときに、プレイヤーに盾をわたすよう**自分で考えてプログラミングしよう！**

```blocks

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

let 開始位置: Position = null

```



## 実行しよう！
プログラミングができあがったら、▶ボタンを押して実行しよう
<br></br>
<img height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/1st/execute.gif">
<br></br>
ゲーム画面にもどったら、まずチャットで**set**と入力して障害物をつくって、スケルトンをスポーンさせよう
障害物やスケルトンが出たのを確認したら、チャットで**go**と入力してステージの中に入り、**黄緑色の色付きガラスの上に立って**ゲームをスタートしよう！
障害物やスケルトンのこうげきをよけながらゴールへ向かおう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson11/L11new_complete3_play.gif">
<br></br>
ゴールまでたどりついたら、**テレポートゾーンに入って下にテレポート**して、**村人に話しかけよう！**
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson11/L11new_tp.gif">
