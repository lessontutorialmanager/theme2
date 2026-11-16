# ゴールと基本ルールを作ろう！

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
})
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


```

```template

player.onChat("run", function () {

})

```

## ゴールと基本ルールを作ろう！ @unplugged
相対座標(そうたいざひょう)でゴールを作り、基本的(きほんてき)なルールをプログラムしよう！
<n></n>
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson8/L8_complete1.gif">



## 目標
``||blocks.ブロックを並(なら)べる||``でゴールを作り、プレイヤーがスタートした時、ゴールした時、落ちた時にどうするかプログラムしよう！
今回は、ゴールを作るときと、ルールを作るときで、**2回に分けてプログラムを実行(じっこう)しよう！**
・チャットコマンドで「run」と入力すると、相対座標でゴールが作られる
・ゴールは、**白色のコンクリート**、**青色のコンクリート**、**黄色のコンクリート**を使う
・プレイヤーがスタートした時、「スタート！」と画面にタイトルを表示(ひょうじ)する
・プレイヤーがゴールした時、「ゴール！」と画面にタイトルを表示する
・プレイヤーが下に落ちた時、「落ちてしまった！」とメッセージを送信(そうしん)し、スタート地点にもどす
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson8/L8_complete1.gif">
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson8/L8_title.gif">
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson8/L8_fall.gif">



## ゴールを作る手順を考える
**上から見た図**でゴールを作る手順(てじゅん)をかんがえよう！
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson8/L8_square.png">
**白色のコンクリート**、**青色のコンクリート**、**黄色のコンクリート**をどの位置(いち)にどんな順番(じゅんばん)で並べれば良(よ)いか考えてみよう！


## 相対座標の意味
ここで、**相対座標**の意味をおさらいしよう！
相対座標とは、**プレイヤーがいるところを基準(きじゅん)として、東西、上下、南北に何ブロックの位置かを表したもの**のことです！
今回は、**赤色の色付きガラス**の上にプレイヤーが立って、そこからの相対座標で考えるようにしましょう
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson8/L8_square2.png">



## プログラムを用意する
考えた手順をもとにして、ブロックを並べるコードを用意しよう！
・``||player.チャットコマンドrunを入力した時||``にブロックを並べる
・ブロックの種類(しゅるい)は、**白色のコンクリート**、**青色のコンクリート**、**黄色のコンクリート**を使う
・範囲(はんい)の始まりと範囲の終わりや、ブロックを並べる順番は、**自分で考えてプログラミングする**
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson8/L8_square.png">



## 実行しよう！①
プログラミングができあがったら、一度▶ボタンを押(お)して実行しよう
ゴールを作ったあと、続(つづ)きのプログラミングをするので、**もう一度Cを押してこの画面を開こう！**
<br></br>
<img height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/1st/execute.gif">
<br></br>
ゲーム画面にもどったら、チャットで「run」と入力してゴールを並べよう
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson8/L8_complete1.gif">
<br></br>
うまくいかなかったときは、**自分で考えて修正(しゅうせい)しよう**

```blocks

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

```



## スタート、ゴールのルールを考える①
スタート地点とゴール地点の上に立った時にタイトルを表示するにはどうすれば良いか考えてみよう！
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson8/L8_title.gif">
・**プレイヤーがどこに立ったとき**にすれば良いか
・それをプログラミングで作ろうと思ったら、**どのコードを使えばよいか**



## スタート、ゴールのルールを考える➁
今回は``||blocks.ブロックが(~0, ~0, ~0)に存在(そんざい)する||``を使って**条件分岐(じょうけんぶんき)**してみましょう！
スタート地点、ゴール地点の真ん中にはそれぞれ**橙(だいだい)色のコンクリート**、**黄色のコンクリート**があります
プレイヤーがこの上に立った時＝**相対座標でプレイヤーの1ブロック下にこれらのブロックがある**ときにタイトルを出すようにしましょう
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson8/L8_test_for_block.png">



## ループを使う
**プレイヤーがいつスタート地点やゴール地点の上に来るかはわからない**ので、**条件分岐をずっとチェックしないといけません**
こんなときは、``||loops.ループ||``にある``||loops.ずっと||``を使いましょう！
``||loops.ずっと||``に入れたコードは、**プログラムを実行したあと、１秒間に何回もくり返(かえ)すことができます**
こうすれば、いつプレイヤーがスタート地点やゴール地点に来ても一瞬(いっしゅん)でチェックすることができます！
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson8/L8_forever_loop.png">



## プログラムを作る
``||loops.ずっと||``と条件分岐を使って、**自分で考えてプログラミングしよう！**
・``||loops.ずっと||``を使う
・もし**プレイヤーの1ブロック下**に**橙色のコンクリート**があれば**スタート！**とタイトルを出す
・もし**プレイヤーの1ブロック下**に**黄色のコンクリート**があれば**ゴール！**とタイトルを出す
・タイトルを出すには、``||gameplay.ゲームプレイ||``にある``||gameplay.～にタイトル～サブタイトル～を表示する||``を使う

```blocks

loops.forever(function () {
    if (blocks.testForBlock(ORANGE_CONCRETE, pos(0, -1, 0))) {
        gameplay.title(mobs.target(LOCAL_PLAYER), "スタート！", "")
    }
    if (blocks.testForBlock(YELLOW_CONCRETE, pos(0, -1, 0))) {
        gameplay.title(mobs.target(LOCAL_PLAYER), "ゴール！", "")
    }
})

```



## プレイヤーが落ちたとき
プレイヤーが落ちた時に、「落ちてしまった！」とメッセージを送信して、スタート地点にもどすようにプログラムしよう
・``||loops.ずっと||``に入れて、いつでも落ちていないかチェックできるようにする
・落ちているかどうかは、プレイヤーの位置の**Y座標**(高さ)が**100より小さい**かどうかで**条件分岐**する
・もどす位置は、``||positions.ワールド(-17, 109, 105)||``にする
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson8/L8_fall.gif">



## 条件分岐を作る
プレイヤーの位置の**Y座標**(高さ)が**100より小さい**ならという条件分岐を作ろう
・``||logic.論理(ろんり)||``から``||logic.もし～なら||``を取り出して、``||loops.ずっと||``に入れる
・``||logic.論理||``から``||logic.0 < 0||``を取り出して、``||loops.もし～なら||``に入れ、**右側(みぎがわ)**を100にする
・``||positions.ポジション||``から``||positions.positionのx(東西)座標||``を取り出して、``||logic.0 < 100||``の**左**に入れ、**y(高低)座標**に変える
・``||player.プレイヤー||``から``||player.プレイヤーの位置||``を取り出して、``||positions.positionのy(高低)座標||``に入れる
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson8/L8_if_fallen.gif">

```blocks

loops.forever(function () {
    if (blocks.testForBlock(ORANGE_CONCRETE, pos(0, -1, 0))) {
        gameplay.title(mobs.target(LOCAL_PLAYER), "スタート！", "")
    }
    if (blocks.testForBlock(YELLOW_CONCRETE, pos(0, -1, 0))) {
        gameplay.title(mobs.target(LOCAL_PLAYER), "ゴール！", "")
    }
    if (player.position().getValue(Axis.Y) < 100) {
    }
})

```


## プログラムを作る
プレイヤーが落ちた時にすることを、**自分で考えてプログラミングしよう**
・「落ちてしまった！」とメッセージを送信する
・``||positions.ワールド(-17, 109, 105)||``にテレポートする
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson8/L8_fall.gif">

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
})

```



## 実行しよう！➁
プログラミングができあがったら、▶ボタンを押して実行しよう
<br></br>
<img height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/1st/execute.gif">
<br></br>
ゲーム画面にもどったら、スタート地点やゴール地点の上に乗ったり、下に落ちてみたりしよう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson8/L8_title.gif">
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson8/L8_fall.gif">
<br></br>
できあがったのを確認(かくにん)したら、**村人に話しかけよう**
