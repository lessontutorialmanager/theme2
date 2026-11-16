# 金の足場を作ろう！

```blocks

let 開始位置: Position = null
player.onChat("run", function () {
    開始位置 = positions.add(
    player.position(),
    pos(0, -1, 0)
    )
    for (let index = 0; index < 4; index++) {
        blocks.fill(
        GOLD_BLOCK,
        positions.add(
        開始位置,
        pos(1, 0, 1)
        ),
        positions.add(
        開始位置,
        pos(3, 0, 1)
        ),
        FillOperation.Replace
        )
        開始位置 = positions.add(
        開始位置,
        pos(0, 1, 1)
        )
    }
    for (let index = 0; index < 4; index++) {
        blocks.fill(
        GOLD_BLOCK,
        positions.add(
        開始位置,
        pos(1, 0, 1)
        ),
        positions.add(
        開始位置,
        pos(3, 0, 1)
        ),
        FillOperation.Replace
        )
        開始位置 = positions.add(
        開始位置,
        pos(0, -1, 1)
        )
    }
    for (let index = 0; index < 4; index++) {
        blocks.fill(
        GOLD_BLOCK,
        positions.add(
        開始位置,
        pos(1, 0, 1)
        ),
        positions.add(
        開始位置,
        pos(3, 0, 1)
        ),
        FillOperation.Replace
        )
        開始位置 = positions.add(
        開始位置,
        pos(0, 1, 1)
        )
    }
})




```

```template

let 開始位置: Position = null

player.onChat("run", function () {
    開始位置 = positions.add(
    player.position(),
    pos(0, -1, 0)
    )
})

```

## 金の足場を作ろう！ @unplugged
相対座標で金の足場を作ろう！
<n></n>
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson9/L9_complete1.png">



## 目標(もくひょう)
``||blocks.ブロックを並(なら)べる||``と**ループ**、**変数(へんすう)**を使ってで足場を作ろう！
・チャットコマンドで「run」と入力すると、相対座標(そうたいざひょう)で足場が作られる
・足場は**金のブロック**を使う
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson9/L9_complete1.gif">



## 足場を作る手順(てじゅん)を考える①
**上から見た図**と**横から見た図**で足場の形をチェックしよう！
``||variables.開始位置(いち)||``を基準(きじゅん)にして、どうすればこの形を作れるでしょうか？
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson9/L9_gold_platform.png">
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson9/L9_gold_platform_side.png">



## 足場を作る手順を考える➁
今回は、階段(かいだん)のような形が**3つ**並んだ形になっています
一度に全部考えるのは大変(たいへん)なので、図のように3つの部分に分けて考えてみよう！
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson9/L9_loop.png">
<br></br>
まずは、3つに分けた階段の形のうち、**一番左の部分**の作り方を考えよう！
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson9/L9_loop_1.png">



## 階段の形に足場を作る
``||variables.開始位置||``を利用して、階段の形にブロックを並(なら)べるにはどうすれば良いでしょうか？
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson9/L9_set_and_move.gif">
①**ブロックを1列並べる**⇒➁``||variables.開始位置||``**を動かす**、を**4回**くりかえせば作ることができそうです！



## ブロックを1列並べる
まずは、``||variables.開始位置||``を基準にして、画像(がぞう)のように**金のブロック**を1列並べるよう**自分で考えてプログラミングしよう！**
・チャットコマンドで**run**と入力すると、**金のブロック**が**東に3ブロック**並ぶ
・``||variables.開始位置||``(プレイヤーの位置の**1ブロック下**)を基準にして、**相対座標**で並べる
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson9/L9_set_1_line.gif">

```blocks

let 開始位置: Position = null
player.onChat("run", function () {
    開始位置 = positions.add(
    player.position(),
    pos(0, -1, 0)
    )
    blocks.fill(
    GOLD_BLOCK,
    positions.add(
    開始位置,
    pos(1, 0, 1)
    ),
    positions.add(
    開始位置,
    pos(3, 0, 1)
    ),
    FillOperation.Replace
    )
})

```



## 開始位置を動かす
次にブロックを置(お)き始める位置に、``||variables.開始位置||``に入った座標を動かすよう、**自分で考えてプログラミングしよう！**
・先ほどのプログラムの下に、``||variables.開始位置||``に入った座標を**上に1、南に1**動かすプログラムを作る

```blocks

let 開始位置: Position = null
player.onChat("run", function () {
    開始位置 = positions.add(
    player.position(),
    pos(0, -1, 0)
    )
    blocks.fill(
    GOLD_BLOCK,
    positions.add(
    開始位置,
    pos(1, 0, 1)
    ),
    positions.add(
    開始位置,
    pos(3, 0, 1)
    ),
    FillOperation.Replace
    )
    開始位置 = positions.add(
    開始位置,
    pos(0, 1, 1)
    )
})

```



## ループする
①**ブロックを1列並べる**⇒➁``||variables.開始位置||``**を動かす**というプログラムをループさせて、階段を作れるようにしよう！
・下の図を見て、何回くり返せばよいか考えて、ループさせる
・プログラムは自分で考える
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson9/L9_set_and_move.gif">

```blocks

let 開始位置: Position = null
player.onChat("run", function () {
    開始位置 = positions.add(
    player.position(),
    pos(0, -1, 0)
    )
    for (let index = 0; index < 4; index++) {
        blocks.fill(
        GOLD_BLOCK,
        positions.add(
        開始位置,
        pos(1, 0, 1)
        ),
        positions.add(
        開始位置,
        pos(3, 0, 1)
        ),
        FillOperation.Replace
        )
        開始位置 = positions.add(
        開始位置,
        pos(0, 1, 1)
        )
    }
})

```



## 2つ目の階段を考える①
3つに分けたうち、2つ目の階段について考えよう！
先ほど作ったプログラムと比べて、**どの部分が同じで、どの部分がちがうでしょうか？**
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson9/L9_loop_2.png">



## 2つ目の階段を考える➁
同じところ：①**ブロックを1列並べる**⇒➁``||variables.開始位置||``**を動かす**、を**4回**くりかえせば作ることができる、というのは先ほどと同じ
ちがうところ：``||variables.開始位置||``を動かす方向が、上ではなく**下**
``||variables.開始位置||``を動かす方向以外は、**ほとんど同じプログラムでできそう**です！こんなときは、**プログラムをコピーして、ちがう部分だけ作りかえよう！**



## プログラムをコピーする
先ほどのプログラムをコピーして、必要(ひつよう)な部分を修正(しゅうせい)しよう！
``||loops.くりかえし4回||``の上で**右クリック**(タブレットなどの場合は長押(お)し、または2本指でタップ)して**複製(ふくせい)する**をえらぶ
コピーしたプログラムを下に入れて、必要な部分を**自分で考えて修正する**
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson9/L9_duplicate.gif">

```blocks

let 開始位置: Position = null
player.onChat("run", function () {
    開始位置 = positions.add(
    player.position(),
    pos(0, -1, 0)
    )
    for (let index = 0; index < 4; index++) {
        blocks.fill(
        GOLD_BLOCK,
        positions.add(
        開始位置,
        pos(1, 0, 1)
        ),
        positions.add(
        開始位置,
        pos(3, 0, 1)
        ),
        FillOperation.Replace
        )
        開始位置 = positions.add(
        開始位置,
        pos(0, 1, 1)
        )
    }
    for (let index = 0; index < 4; index++) {
        blocks.fill(
        GOLD_BLOCK,
        positions.add(
        開始位置,
        pos(1, 0, 1)
        ),
        positions.add(
        開始位置,
        pos(3, 0, 1)
        ),
        FillOperation.Replace
        )
        開始位置 = positions.add(
        開始位置,
        pos(0, -1, 1)
        )
    }
})

```



## 3つ目の階段を作る
同じように、プログラムをコピーして、3つ目の階段の形を作るようにしよう！
下の図を見ながら、**自分で考えてやってみよう！**
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson9/L9_loop_3.png">

```blocks

let 開始位置: Position = null
player.onChat("run", function () {
    開始位置 = positions.add(
    player.position(),
    pos(0, -1, 0)
    )
    for (let index = 0; index < 4; index++) {
        blocks.fill(
        GOLD_BLOCK,
        positions.add(
        開始位置,
        pos(1, 0, 1)
        ),
        positions.add(
        開始位置,
        pos(3, 0, 1)
        ),
        FillOperation.Replace
        )
        開始位置 = positions.add(
        開始位置,
        pos(0, 1, 1)
        )
    }
    for (let index = 0; index < 4; index++) {
        blocks.fill(
        GOLD_BLOCK,
        positions.add(
        開始位置,
        pos(1, 0, 1)
        ),
        positions.add(
        開始位置,
        pos(3, 0, 1)
        ),
        FillOperation.Replace
        )
        開始位置 = positions.add(
        開始位置,
        pos(0, -1, 1)
        )
    }
    for (let index = 0; index < 4; index++) {
        blocks.fill(
        GOLD_BLOCK,
        positions.add(
        開始位置,
        pos(1, 0, 1)
        ),
        positions.add(
        開始位置,
        pos(3, 0, 1)
        ),
        FillOperation.Replace
        )
        開始位置 = positions.add(
        開始位置,
        pos(0, 1, 1)
        )
    }
})


```



## 実行しよう！
プログラミングができあがったら、▶ボタンを押して実行しよう
<br></br>
<img height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/1st/execute.gif">
<br></br>
ゲーム画面にもどったら、**赤の色付きガラスの上に立って**チャットで**run**と入力しよう
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson9/L9_complete1.gif">
<br></br>
できあがったのを確認(かくにん)したら、**村人に話しかけよう**
