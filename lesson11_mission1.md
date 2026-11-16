# ステージを作ろう！

```blocks
player.onChat("run", function () {
    blocks.fill(
    GLASS,
    positions.add(
    開始位置,
    pos(0, 0, 0)
    ),
    positions.add(
    開始位置,
    pos(4, 23, 10)
    ),
    FillOperation.Replace
    )
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
    blocks.place(LIME_STAINED_GLASS, positions.add(
    開始位置,
    pos(2, 0, 5)
    ))
    blocks.fill(
    SEA_LANTERN,
    positions.add(
    開始位置,
    pos(0, 24, 0)
    ),
    positions.add(
    開始位置,
    pos(4, 24, 10)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    AIR,
    positions.add(
    開始位置,
    pos(1, 24, 5)
    ),
    positions.add(
    開始位置,
    pos(3, 24, 5)
    ),
    FillOperation.Replace
    )
})

let 開始位置: Position = null
gameplay.setDifficulty(NORMAL)
開始位置 = world(0, 61, 110)


```

```template

player.onChat("run", function () {})
let 開始位置: Position = null
開始位置 = world(0, 61, 110)
gameplay.setDifficulty(NORMAL)

```

## ステージを作ろう！ @unplugged
ゲームのステージを作ろう！
<n></n>
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson11/L11new_complete1.gif">



## 目標(もくひょう)
ゲームのステージを作ろう！
・変数(へんすう)``||開始位置(いち)||``に入れられている絶対座標(ぜったいざひょう)を基準(きじゅん)にステージを作る
・チャットコマンドで**run**と入力すると、ステージを並(なら)べる
・ブロックは、**ガラス**、**黄緑色の色付(いろつ)きガラス**、**シーランタン**を使う
・大きさは、**東に5ブロック**、**上に25ブロック**、**南に11ブロック**にする
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson11/L11new_complete1.gif">



## 座標を考える
下の図を見て、どの座標にどのブロックを置(お)けばよいか、**自分で考えてみよう！**
・全体
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson11/L11new_complete1.gif">
・上から見た図①　一番下(高さ0)
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson11/L11new_coordinate_bottom.png">
・上から見た図➁　カベ(高さ1～23)
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson11/L11new_coordinate_middle.png">
・上から見た図③　天井(高さ24)
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson11/L11new_coordinate_top.png">



## 手順(てじゅん)を考える
座標を考えたら、次に手順を考えてみよう！
・どのブロックから並べるか
・どういう形に並べるか




## ブロックを並べる
考えたことをもとにして、**自分で考えてプログラミングしよう！**
・変数``||開始位置||``に入れられている絶対座標を基準にステージを作る
・チャットコマンドで**run**と入力すると、ステージを並べる
・ブロックは、**ガラス**、**黄緑色の色付きガラス**、**シーランタン**を使う
・大きさは、**東に5ブロック**、**上に25ブロック**、**南に11ブロック**にする
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson11/L11new_build.gif">

```blocks

player.onChat("run", function () {
    blocks.fill(
    GLASS,
    positions.add(
    開始位置,
    pos(0, 0, 0)
    ),
    positions.add(
    開始位置,
    pos(4, 23, 10)
    ),
    FillOperation.Replace
    )
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
    blocks.place(LIME_STAINED_GLASS, positions.add(
    開始位置,
    pos(2, 0, 5)
    ))
    blocks.fill(
    SEA_LANTERN,
    positions.add(
    開始位置,
    pos(0, 24, 0)
    ),
    positions.add(
    開始位置,
    pos(4, 24, 10)
    ),
    FillOperation.Replace
    )
    blocks.fill(
    AIR,
    positions.add(
    開始位置,
    pos(1, 24, 5)
    ),
    positions.add(
    開始位置,
    pos(3, 24, 5)
    ),
    FillOperation.Replace
    )
})

let 開始位置: Position = null
gameplay.setDifficulty(NORMAL)
開始位置 = world(0, 61, 110)

```



## 実行(じっこう)しよう！
プログラミングができあがったら、▶ボタンを押(お)して実行しよう
<br></br>
<img height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/1st/execute.gif">
<br></br>
ゲーム画面にもどったら、チャットで**run**と入力してステージを作ろう！
できあがったら、**村人に話しかけよう**
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson11/L11new_complete1.gif">


