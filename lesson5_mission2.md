# 変数で生き物を出そう！➁

```blocks
player.onChat("run", function (num1) {
    blocks.fill(
    BLOCK_OF_QUARTZ,
    pos(1, 0, 1),
    pos(5, 0, 4),
    FillOperation.Replace
    )
    blocks.fill(
    SAND,
    pos(2, 0, 2),
    pos(4, 0, 3),
    FillOperation.Replace
    )
    blocks.fill(
    GLASS,
    pos(1, 1, 1),
    pos(5, 4, 4),
    FillOperation.Replace
    )
    blocks.fill(
    AIR,
    pos(2, 1, 2),
    pos(4, 4, 3),
    FillOperation.Replace
    )
    blocks.fill(
    BLOCK_OF_QUARTZ,
    pos(1, 5, 1),
    pos(5, 5, 4),
    FillOperation.Replace
    )
    blocks.fill(
    SEA_LANTERN,
    pos(2, 5, 2),
    pos(4, 5, 3),
    FillOperation.Replace
    )
    if (num1 == 0) {
        mobs.spawn(CAMEL, pos(3, 1, 2))
    } else if (num1 == 1) {
        mobs.spawn(LLAMA, pos(3, 1, 2))
    } else {
        mobs.spawn(RABBIT, pos(3, 1, 2))
    }
})

```

```template
player.onChat("run", function () {})
```

## 変数で生き物を出そう！ @unplugged
変数によってちがう生き物を出せるようにしよう！
<n></n>
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson5/L5_complete2.png">



## 目標
囲いを作って、変数によって違う種類の生き物が中に入るようにしよう！
・チャットコマンドで「run ○」と入力すると、指定した座標に囲いが作られる
・○に入った数字が0ならラクダ、1ならラマ、2ならウサギが入るようにする
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson5/L5_complete2.png">



## 囲いを作る
囲いの全体の形を確認しよう！
・クォーツブロック、砂、ガラス、空気、シーランタンを使う
・東西(X座標)は1～5、高さ(Y座標)は0～5、南北(Z座標)は1～5
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson5/L5_from_side.png">
<br></br>
1番下の0段目から順番に考えていこう！



## 0段目
0段目の形を確認しよう！
・まずクォーツブロックを並べて、その後に砂を並べる
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson5/L5_bottom2.png">
<br></br>
テラコッタの位置を中心として、まずは座標を確認しよう！



## Step1 0段目のブロックを並べる
確認した内容に沿ってブロックを並べよう！
・``||blocks.ブロック||``から``||blocks.ブロックを並べる||``を2つ取り出してワークスペースの``||player.チャットコマンドrunを入力した時||``にはめ込む
①ブロックの種類：クォーツブロック、範囲の始まり：``||positions.(~1, ~0, ~1)||``、範囲の終わり：``||positions.(~5, ~0, ~4)||``
➁ブロックの種類：砂、範囲の始まり：``||positions.(~2, ~0, ~2)||``、範囲の終わり：``||positions.(~4, ~0, ~3)||``

```blocks
player.onChat("run", function () {
    blocks.fill(
    BLOCK_OF_QUARTZ,
    pos(1, 0, 1),
    pos(5, 0, 4),
    FillOperation.Replace
    )
    blocks.fill(
    SAND,
    pos(2, 0, 2),
    pos(4, 0, 3),
    FillOperation.Replace
    )
})

```



## 1～4段目
1～4段目の形を確認しよう！
・まずガラスを並べて、その後に空気を並べて穴を空ける
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson5/L5_middle2.png">
<br></br>
テラコッタの位置を中心として、まずは座標を確認しよう！


## Step2 1～4段目のブロックを並べる
確認した内容に沿ってブロックを並べよう！
・``||blocks.ブロック||``から``||blocks.ブロックを並べる||``を2つ取り出してワークスペースの``||player.チャットコマンドrunを入力した時||``にはめ込む
①ブロックの種類：ガラス、範囲の始まり：``||positions.(~1, ~1, ~1)||``、範囲の終わり：``||positions.(~5, ~4, ~4)||``
➁ブロックの種類：空気、範囲の始まり：``||positions.(~2, ~1, ~2)||``、範囲の終わり：``||positions.(~4, ~4, ~3)||``

```blocks
player.onChat("run", function () {
    blocks.fill(
    BLOCK_OF_QUARTZ,
    pos(1, 0, 1),
    pos(5, 0, 4),
    FillOperation.Replace
    )
    blocks.fill(
    SAND,
    pos(2, 0, 2),
    pos(4, 0, 3),
    FillOperation.Replace
    )
    blocks.fill(
    GLASS,
    pos(1, 1, 1),
    pos(5, 4, 4),
    FillOperation.Replace
    )
    blocks.fill(
    AIR,
    pos(2, 1, 2),
    pos(4, 4, 3),
    FillOperation.Replace
    )
})

```



## 5段目
5段目の形を確認しよう！
・まずクォーツブロックを並べて、その後にシーランタンを並べる
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson5/L5_top.png">
<br></br>
テラコッタの位置を中心として、まずは座標を確認しよう！



## Step3 5段目のブロックを並べる
確認した内容に沿ってブロックを並べよう！
・``||blocks.ブロック||``から``||blocks.ブロックを並べる||``を2つ取り出してワークスペースの``||player.チャットコマンドrunを入力した時||``にはめ込む
①ブロックの種類：クォーツブロック、範囲の始まり：``||positions.(~1, ~5, ~1)||``、範囲の終わり：``||positions.(~5, ~5, ~4)||``
➁ブロックの種類：シーランタン、範囲の始まり：``||positions.(~2, ~5, ~2)||``、範囲の終わり：``||positions.(~4, ~5, ~3)||``
これで囲いは完成です！

```blocks
player.onChat("run", function () {
    blocks.fill(
    BLOCK_OF_QUARTZ,
    pos(1, 0, 1),
    pos(5, 0, 4),
    FillOperation.Replace
    )
    blocks.fill(
    SAND,
    pos(2, 0, 2),
    pos(4, 0, 3),
    FillOperation.Replace
    )
    blocks.fill(
    GLASS,
    pos(1, 1, 1),
    pos(5, 4, 4),
    FillOperation.Replace
    )
    blocks.fill(
    AIR,
    pos(2, 1, 2),
    pos(4, 4, 3),
    FillOperation.Replace
    )
    blocks.fill(
    BLOCK_OF_QUARTZ,
    pos(1, 5, 1),
    pos(5, 5, 4),
    FillOperation.Replace
    )
    blocks.fill(
    SEA_LANTERN,
    pos(2, 5, 2),
    pos(4, 5, 3),
    FillOperation.Replace
    )
})

```



## 条件分岐を考える
チャットで「run ○」と入力した時、○の数によって中に入る生き物が変わるようにするために、条件分岐を作りましょう！
「run ○」と入力した時の数字は、``||variables.num1||``に入るので、num1がどんな数字かで条件分岐しよう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson5/L5_flowchart2.png">
<br></br>
``||variables.num1||``が何の数字のとき、何を出現させるのか確認しよう！



## Step4 変数を作る
条件分岐の準備として変数を作ろう！
・``||player.チャットコマンドrunを入力した時||``の⊕を1回押して、``||variables.num1||``を作る

```blocks
player.onChat("run", function (num1) {
    blocks.fill(
    BLOCK_OF_QUARTZ,
    pos(1, 0, 1),
    pos(5, 0, 4),
    FillOperation.Replace
    )
    blocks.fill(
    SAND,
    pos(2, 0, 2),
    pos(4, 0, 3),
    FillOperation.Replace
    )
    blocks.fill(
    GLASS,
    pos(1, 1, 1),
    pos(5, 4, 4),
    FillOperation.Replace
    )
    blocks.fill(
    AIR,
    pos(2, 1, 2),
    pos(4, 4, 3),
    FillOperation.Replace
    )
    blocks.fill(
    BLOCK_OF_QUARTZ,
    pos(1, 5, 1),
    pos(5, 5, 4),
    FillOperation.Replace
    )
    blocks.fill(
    SEA_LANTERN,
    pos(2, 5, 2),
    pos(4, 5, 3),
    FillOperation.Replace
    )
})

```



## Step5 条件分岐を作る
確認した内容に沿って条件分岐を作ろう！
・``||logic.論理||``から``||logic.もし～なら でなければ||``を取り出して``||player.チャットコマンドrunを入力した時||``にはめ込み、⊕を1回押す
・``||logic.論理||``から``||logic.0 = 0||``を2つ取り出して、``||logic.もし～なら でなければ||``にはめ込む
・``||variables.変数||``から``||variables.num1||``を2つ取り出して、``||logic.0 = 0||``にはめ込む
・2つの条件が、①``||logic.num1 = 0なら||``、➁``||logic.num1 = 1なら||``となるようにする

```blocks
player.onChat("run", function (num1) {
    blocks.fill(
    BLOCK_OF_QUARTZ,
    pos(1, 0, 1),
    pos(5, 0, 4),
    FillOperation.Replace
    )
    blocks.fill(
    SAND,
    pos(2, 0, 2),
    pos(4, 0, 3),
    FillOperation.Replace
    )
    blocks.fill(
    GLASS,
    pos(1, 1, 1),
    pos(5, 4, 4),
    FillOperation.Replace
    )
    blocks.fill(
    AIR,
    pos(2, 1, 2),
    pos(4, 4, 3),
    FillOperation.Replace
    )
    blocks.fill(
    BLOCK_OF_QUARTZ,
    pos(1, 5, 1),
    pos(5, 5, 4),
    FillOperation.Replace
    )
    blocks.fill(
    SEA_LANTERN,
    pos(2, 5, 2),
    pos(4, 5, 3),
    FillOperation.Replace
    )
    if (num1 == 0) {

    } else if (num1 == 1) {

    } else {

    }
})

```


## Step6 生き物を出現させる
``||mobs.生き物を(~0, ~0, ~0)にスポーンさせる||``を使って、``||variables.num1||``の数字によってちがう生き物がスポーンするようにしよう！
・``||mobs.モブ||``から``||mobs.生き物を(~0, ~0, ~0)にスポーンさせる||``を取り出して全ての条件分岐にはめ込む
・``||logic.num1 = 0なら||``：ラクダ
・``||logic.num1 = 1なら||``：ラマ
・``||logic.num1 = 2なら||``：ウサギ
・座標は全て、``||positions.(~3, ~1, ~2)||``に設定する

```blocks
player.onChat("run", function (num1) {
    blocks.fill(
    BLOCK_OF_QUARTZ,
    pos(1, 0, 1),
    pos(5, 0, 4),
    FillOperation.Replace
    )
    blocks.fill(
    SAND,
    pos(2, 0, 2),
    pos(4, 0, 3),
    FillOperation.Replace
    )
    blocks.fill(
    GLASS,
    pos(1, 1, 1),
    pos(5, 4, 4),
    FillOperation.Replace
    )
    blocks.fill(
    AIR,
    pos(2, 1, 2),
    pos(4, 4, 3),
    FillOperation.Replace
    )
    blocks.fill(
    BLOCK_OF_QUARTZ,
    pos(1, 5, 1),
    pos(5, 5, 4),
    FillOperation.Replace
    )
    blocks.fill(
    SEA_LANTERN,
    pos(2, 5, 2),
    pos(4, 5, 3),
    FillOperation.Replace
    )
    if (num1 == 0) {
        mobs.spawn(CAMEL, pos(3, 1, 2))
    } else if (num1 == 1) {
        mobs.spawn(LLAMA, pos(3, 1, 2))
    } else {
        mobs.spawn(RABBIT, pos(3, 1, 2))
    }
})

```




## 実行しよう！
プログラミングができあがったら、▶ボタンを押して実行しよう
<br></br>
<img height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/1st/execute.gif">
<br></br>
ゲーム画面にもどったら、作りたい囲いの看板を見て、何の生き物を出せばよいか確認しよう
確認したら、テラコッタの上に立ってチャットで「run ○」と入力して、出したい生き物の番号を指定しよう
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson5/L5_stand.png">
<img width="100%" src="https://vcode-esia.com/images_for_world_data/school/2nd/Lesson5/L5_complete2.png">
<br></br>
できあがったのを確認したら、村長に話しかけよう
