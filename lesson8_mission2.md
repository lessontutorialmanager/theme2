# 乱数を使って足場を作ろう！

```blocks

let 開始位置: Position = null
let ブロックの種類 = 0
let えらんだ数 = 0
player.onChat("set", function () {
    開始位置 = randpos(
    pos(-5, -1, 2),
    pos(3, -1, 4)
    )
    えらんだ数 = randint(0, 2)
    if (えらんだ数 == 0) {
        ブロックの種類 = AIR
    } else if (えらんだ数 == 1) {
        ブロックの種類 = WHITE_GLAZED_TERRACOTTA
    } else {
        ブロックの種類 = HONEY_BLOCK
    }
    blocks.fill(
    DIAMOND_BLOCK,
    positions.add(
    開始位置,
    pos(1, 0, 1)
    ),
    positions.add(
    開始位置,
    pos(3, 0, 3)
    ),
    FillOperation.Replace
    )
    blocks.place(ブロックの種類, positions.add(
    開始位置,
    pos(2, 0, 2)
    ))
})


```

```template

player.onChat("set", function () {
})

```

## 乱数を使って足場を作ろう！ @unplugged
乱数(らんすう)を使って、ランダムな位置にランダムな足場を作ろう！
<br></br>
<img style="display: block; margin: auto;" height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson8/L8_complete2.gif">



## 目標
ランダムな位置に、真ん中がランダムなブロックの足場を作るようプログラムしよう！
・チャットコマンドで「set」と入力すると、指定(してい)した範囲のランダムな位置に**ダイヤモンドのブロック**でできた足場が作られる
・足場の真ん中は、**空気**、**ハチミツブロック**、**白の彩釉(さいゆう)テラコッタ**のどれかがランダムで置(お)かれる
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson8/L8_complete2.gif">



## 足場を作る手順
ランダムな位置に足場をつくる手順をかんがえよう！
①変数(へんすう)``||variables.開始位置||``に**ランダムな座標を入れる**
➁``||variables.開始位置||``に入れた座標を基準にして、**ブロックを並べる**
上から見た図をもとに、足場を作る座標をかんがえよう！
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson8/L8_platform.png">



## 変数にランダムな座標を入れる方法
ランダムな座標をえらびたいときは、``||positions.ポジション||``にある``||positions.(~0, ~0, ~0)から(~0, ~0, ~0)の間にあるランダムな座標||``を使います
このコードに範囲の始まりと範囲の終わりを入れると、その中からランダムに座標を1つえらんでくれます
これを使って``||variables.開始位置||``にランダムな座標を入れよう！
・変数``||variables.開始位置||``を作り、``||variables.変数 開始位置を0にする||``を取り出して、``||player.チャットコマンドsetを入力した時||``に入れる
・``||positions.ポジション||``から``||positions.(~0, ~0, ~0)から(~0, ~0, ~0)の間にあるランダムな座標||``を取り出して、``||variables.変数 開始位置を0にする||``に入れる

```blocks

let 開始位置: Position = null
player.onChat("set", function () {
    開始位置 = randpos(
    pos(0, 0, 0),
    pos(0, 0, 0)
    )
})

```



## 座標を入れる
下の図の、点線の範囲からランダムな座標をえらぶようにプログラムしよう！
どんな座標にすれば良いか、**自分で考えてプログラミングしよう**
※y座標(高低)は**-1**にする
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson8/L8_random_range.png">

```blocks

let 開始位置: Position = null
player.onChat("set", function () {
    開始位置 = randpos(
    pos(-5, -1, 2),
    pos(3, -1, 4)
    )
})

```



## ブロックを並べる
``||variables.開始位置||``に入った位置を基準にして、足場を並べよう！
・ブロックの種類：**ダイヤモンドのブロック**
・範囲の始まりと範囲の終わりは、**自分で考えてプログラミングしよう**
※y座標(高低)は**0**にする
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson8/L8_fill.png">
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson8/L8_platform.png">

```blocks

let 開始位置: Position = null
player.onChat("set", function () {
    開始位置 = randpos(
    pos(-5, -1, 2),
    pos(3, -1, 4)
    )
    blocks.fill(
    DIAMOND_BLOCK,
    positions.add(
    開始位置,
    pos(1, 0, 1)
    ),
    positions.add(
    開始位置,
    pos(3, 0, 3)
    ),
    FillOperation.Replace
    )
})

```



## 真ん中のブロックをランダムに変える
ゲームを面白(おもしろ)くするために、足場の真ん中に**空気**、**ハチミツブロック**、**白の彩釉テラコッタ**のどれかがランダムで置かれるようにしよう！
``||math.計算||``にある``||math.ランダムな数字を選択(せんたく)||``を使うと、指定した範囲からランダムにひとつ数字をえらんでくれます
``||variables.えらんだ数||``にランダムな数字を入れて、条件分岐で変数``||variables.ブロックの種類||``にランダムにブロックを入れよう！
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson8/L8_random_block.png">



## 条件分岐を作る
ブロックの種類をランダムにえらぶための条件分岐を作ろう！
・``||logic.もし～なら でなければ||``を取り出して、``||player.チャットコマンドsetを入力した時||``の中の``||blocks.ブロックを並べる||``の**上**にいれる
・``||logic.もし～なら でなければ||``の⊕を1回おす
・変数``||variables.えらんだ数||``、``||variables.ブロックの種類||``を作る
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson8/L8_random_num.gif">

```blocks

let 開始位置: Position = null
player.onChat("set", function () {
    開始位置 = randpos(
    pos(-5, -1, 2),
    pos(3, -1, 4)
    )
    if (true) {
    	
    } else if (false) {
    	
    } else {
    	
    }
    blocks.fill(
    DIAMOND_BLOCK,
    positions.add(
    開始位置,
    pos(1, 0, 1)
    ),
    positions.add(
    開始位置,
    pos(3, 0, 3)
    ),
    FillOperation.Replace
    )
})

```



## ランダムな数を入れる
``||variables.えらんだ数||``に**0～2までのランダムな数**を入れよう！
・``||variables.変数||``から``||variables.変数 えらんだ数を0にする||``を取り出して、``||player.チャットコマンドsetを入力した時||``の中の条件分岐の**上**にいれる
・・``||math.計算||``から``||math.ランダムな数字を選択||``を取り出して、``||variables.変数 えらんだ数を0にする||``にいれる
・**0から10まで**を**0から2まで**にする
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson8/L8_random_choice.gif">

```blocks

let 開始位置: Position = null
player.onChat("set", function () {
    開始位置 = randpos(
    pos(-5, -1, 2),
    pos(3, -1, 4)
    )
    えらんだ数 = randint(0, 2)
    if (true) {
    	
    } else if (false) {
    	
    } else {
    	
    }
    blocks.fill(
    DIAMOND_BLOCK,
    positions.add(
    開始位置,
    pos(1, 0, 1)
    ),
    positions.add(
    開始位置,
    pos(3, 0, 3)
    ),
    FillOperation.Replace
    )
})

```




## 条件分岐する
``||variables.えらんだ数||``に入った数字で条件分岐するようにしよう！
・``||variables.えらんだ数||``**=0**のとき：``||variables.ブロックの種類||``を**空気ブロック**にする
・``||variables.えらんだ数||``**=1**のとき：``||variables.ブロックの種類||``を**白の彩釉テラコッタ**にする
・``||variables.えらんだ数||``**=2**のとき：``||variables.ブロックの種類||``を**ハチミツブロック**にする
条件分岐を**自分で考えてプログラミングしよう！**
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson8/L8_random_block_flow.png">

```blocks

let 開始位置: Position = null
player.onChat("set", function () {
    開始位置 = randpos(
    pos(-5, -1, 2),
    pos(3, -1, 4)
    )
    えらんだ数 = randint(0, 2)
    if (えらんだ数 == 0) {
        ブロックの種類 = AIR
    } else if (えらんだ数 == 1) {
        ブロックの種類 = WHITE_GLAZED_TERRACOTTA
    } else {
        ブロックの種類 = HONEY_BLOCK
    }
    blocks.fill(
    DIAMOND_BLOCK,
    positions.add(
    開始位置,
    pos(1, 0, 1)
    ),
    positions.add(
    開始位置,
    pos(3, 0, 3)
    ),
    FillOperation.Replace
    )
})

```



## ブロックを置く
``||variables.ブロックの種類||``に入ったブロックを、足場の真ん中に置こう！
・``||blocks.ブロックを(~0, ~0, ~0)に置く||``を使う
・下の図をもとに、``||variables.開始位置||``を基準にしてどの位置に置くか**自分で考えてプログラミングする**
・置くブロックには、``||variables.ブロックの種類||``を入れる
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson8/L8_random_block.png">

```blocks
let 開始位置: Position = null
let ブロックの種類 = 0
let えらんだ数 = 0
player.onChat("set", function () {
    開始位置 = randpos(
    pos(-5, -1, 2),
    pos(3, -1, 4)
    )
    えらんだ数 = randint(0, 2)
    if (えらんだ数 == 0) {
        ブロックの種類 = AIR
    } else if (えらんだ数 == 1) {
        ブロックの種類 = WHITE_GLAZED_TERRACOTTA
    } else {
        ブロックの種類 = HONEY_BLOCK
    }
    blocks.fill(
    DIAMOND_BLOCK,
    positions.add(
    開始位置,
    pos(1, 0, 1)
    ),
    positions.add(
    開始位置,
    pos(3, 0, 3)
    ),
    FillOperation.Replace
    )
    blocks.place(ブロックの種類, positions.add(
    開始位置,
    pos(2, 0, 2)
    ))
})
```


## 実行しよう！
プログラミングができあがったら、▶ボタンを押して実行しよう
<br></br>
<img height="50%" width="50%" src="https://vcode-esia.com/images_for_world_data/school/1st/execute.gif">
<br></br>
ゲーム画面(がめん)にもどったら、スタート地点のはしに立ってチャットで「set」と入力し、足場を作ろう！
<br></br>
<img width="100%" src="https://vcode-esia.com/images_for_world_data/Basic/Theme2/Lesson8/L8_complete2.gif">
<br></br>
足場にジャンプして移動(いどう)する⇒次の足場を作る…を何回かくりかえして、ゴールまでたどりつこう！
